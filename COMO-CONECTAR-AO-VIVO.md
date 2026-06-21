# Sincronização ao vivo — Painel do Mestre

Com isto, sempre que um jogador mudar o equipamento, você (Mestre) vê na hora no **Painel do Mestre**. Usa o Firebase (Google), de graça. A configuração é feita **uma vez só por você**; os jogadores só colam o que você mandar.

---

## Parte 1 — Você (Mestre) cria o projeto (uma vez, ~10 min)

1. Acesse **https://console.firebase.google.com** e faça login com uma conta Google.
2. Clique em **Adicionar projeto** (Add project). Dê um nome (ex: `dcc-mesa`). Pode desativar o Google Analytics. Crie.
3. No menu lateral, vá em **Criar → Realtime Database** (Build → Realtime Database). Clique em **Criar banco de dados**.
   - Escolha a localização (qualquer uma; `us-central` serve).
   - Em regras de segurança, escolha **iniciar em modo de teste** (test mode). *(Veja a seção de segurança no fim.)*
4. Ainda no Realtime Database, copie a **URL do banco** — algo como
   `https://dcc-mesa-default-rtdb.firebaseio.com`. (Você vai conferir que ela aparece no config.)
5. Volte para a engrenagem **⚙ → Configurações do projeto**. Role até **Seus apps** e clique no ícone **Web `</>`**.
   - Registre um app (qualquer apelido, ex: `web`). **Não** precisa de Hosting.
   - O Firebase mostra um bloco de código com o **`firebaseConfig`**. É isto que importa:

```js
const firebaseConfig = {
  apiKey: "AIza............",
  authDomain: "dcc-mesa.firebaseapp.com",
  databaseURL: "https://dcc-mesa-default-rtdb.firebaseio.com",
  projectId: "dcc-mesa",
  storageBucket: "dcc-mesa.appspot.com",
  messagingSenderId: "1234567890",
  appId: "1:1234567890:web:abcdef"
};
```

> ⚠️ **O campo `databaseURL` PRECISA estar presente.** Se não aparecer no config, copie-o do passo 4 e adicione na mão. Sem ele a sincronização ao vivo não funciona.

6. Copie esse objeto `firebaseConfig` inteiro. Esse texto é o que todos vão usar.

---

## Parte 2 — Distribuir para a mesa

Mande para os 5 jogadores **quatro coisas**:

- O **`firebaseConfig`** (o bloco do passo 5).
- Um **código de mesa** combinado, igual para todos. Ex: `corredor-do-carl`. *(Pode ser qualquer texto sem espaços; funciona como a "sala".)*
- O arquivo **`DCC-Dashboard-Equipamento.html`** (cada jogador usa o seu).
- Os **dois links de catálogo** (itens e skills) — veja abaixo.

**Os dois catálogos.** O jogo tem dois baralhos compartilhados que você publica na nuvem (passo a passo em `COMO-SINCRONIZAR.md`, mesma técnica para os dois):

- **`DCC-Catalogo-Itens.json`** → o baralho de loot (armas, armaduras, consumíveis…).
- **`DCC-Catalogo-Skills.json`** → o baralho de skills/spells.

Mande os **dois links diretos** para os jogadores. No dashboard há duas barras no topo: uma "Catálogo" (itens) e uma "Skills". Cada jogador cola o link na barra certa e clica em carregar — depois o dashboard recarrega sozinho a cada abertura.

---

## Parte 3 — Cada jogador conecta (uma vez)

1. Abre o `DCC-Dashboard-Equipamento.html`.
2. Cola o **link do catálogo de itens** na barra "Catálogo" e clica **🔗 Carregar do link**; cola o **link do catálogo de skills** na barra "Skills" e clica **🔗 Carregar skills**.
3. Clica em **⚙ Configurar Firebase**, cola o `firebaseConfig` e clica **Salvar config**.
4. Digita o **código da mesa** no campo e clica **📡 Conectar mesa**.
5. Pronto. O status fica **● ao vivo**. A partir daí, tudo que ele mudar (atributos, equipamento, skills, PM, ouro, caixas) é publicado automaticamente. Nas próximas vezes reconecta e recarrega os catálogos sozinho.

## Parte 4 — Você abre o Painel do Mestre

1. Abre o **`DCC-Painel-Mestre.html`**.
2. **⚙ Configurar Firebase** → cola o mesmo `firebaseConfig` → **Salvar config**.
3. Digita o **mesmo código de mesa** → **📡 Conectar mesa**.
4. Os 5 crawlers aparecem em cards, **atualizando ao vivo**: atributos, HP máx, **PM atual/máx**, Defesa, Iniciativa, **Ataque Desarmado**, equipamento, **skills (nome · rank · custo)**, inventário, ouro, PS e caixas. Cartas sem update há mais de 2 min aparecem esmaecidas ("inativo").

---

## Segurança (importante de saber)

O "modo de teste" deixa o banco **aberto para leitura e escrita por qualquer um que tenha o config** (e o config fica visível no HTML — é o normal de apps web do Firebase). Para uma mesa privada de amigos, isso costuma ser aceitável: o código da mesa serve de "senha" informal e o banco só guarda fichas de RPG.

Se quiser fechar mais, no Realtime Database → **Regras**, você pode trocar para algo como:

```json
{
  "rules": {
    "mesas": {
      "$mesa": {
        ".read": "$mesa === 'corredor-do-carl'",
        ".write": "$mesa === 'corredor-do-carl'"
      }
    }
  }
}
```

Isso limita o acesso à sua mesa específica. (O modo de teste também expira sozinho em ~30 dias; quando isso acontecer, volte nas Regras e renove, ou aplique a regra acima.)

---

## Resumo dos arquivos

| Arquivo | Quem usa | Pra quê |
|---|---|---|
| `DCC-Dashboard-Equipamento.html` | cada jogador | montar a ficha, equipar cartas e gerir skills |
| `DCC-Painel-Mestre.html` | só o Mestre | ver todos ao vivo (atributos, PM, skills, equipamento…) |
| `DCC-Catalogo-Itens.json` | Mestre mantém | baralho de loot compartilhado (175 itens, v6) |
| `DCC-Catalogo-Skills.json` | Mestre mantém | baralho de skills/spells compartilhado (223 skills, v9) |
| `COMO-SINCRONIZAR.md` | Mestre | como publicar os catálogos na nuvem |
| `COMO-CONECTAR-AO-VIVO.md` | Mestre | este guia (Firebase) |

> **Checklist de "está tudo pronto?"** ✓ Firebase criado e `firebaseConfig` copiado · ✓ código de mesa combinado · ✓ os dois catálogos publicados (links diretos) · ✓ cada jogador com o dashboard, os dois links e o config · ✓ você com o `DCC-Painel-Mestre.html` aberto e conectado. Se os 5 cards aparecerem no painel, está no ar.
