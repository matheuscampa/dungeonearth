# Como ativar o Portal de Mesas (login + menu Jogador/Mestre)

## O que mudou

Agora existe um **portal com login por email e senha**, em vez de cada um só digitar um código solto. Três arquivos novos:

| Arquivo | Pra quê |
|---|---|
| **`index.html`** | **A URL única que você manda pra todo mundo.** Tela de entrar / criar conta — é a página inicial do site (a raiz), então o link fica só o domínio, sem nome de arquivo. |
| `DCC-Portal-Login.html` | Mantido só por compatibilidade com links antigos — redireciona sozinho pra `index.html`. Não precisa mais divulgar esse. |
| `DCC-Portal.html` | Home depois de logar: lista suas mesas como **Jogador** (com link pra ficha) e suas mesas como **Mestre** (criar mesa, gerar/copiar código) |
| (já existiam) `DCC-Dashboard-Equipamento.html` e `DCC-Painel-Mestre.html` | Ganharam um botão **← Portal** e agora **também exigem login** — se abrir sem estar logado (nesse navegador), redirecionam pra tela de entrar |

> **Importante:** se você aplicou o Passo 2 (regras exigindo login), o Dashboard e o Painel do Mestre só conseguem ler/escrever a mesa se a pessoa estiver **logada no mesmo navegador**. Por isso ambos agora checam a sessão automaticamente antes de conectar — se você abrir sem ter logado antes, eles mandam pra `index.html`. Depois de logar uma vez, o navegador lembra e não pede de novo.

O login usa o **mesmo projeto Firebase** que já estava configurado (`dungeonearth`), então não precisa criar nada novo na nuvem — só **ligar uma chave** no Console.

---

## Passo 1 — Ativar login por email/senha (você faz uma vez, ~2 min)

1. Acesse **https://console.firebase.google.com**, entre no projeto **dungeonearth**.
2. Menu lateral → **Build → Authentication**.
3. Aba **Sign-in method** → clique em **Email/Password** → **Enable** (ativar) → **Save**.

Pronto. Sem isso, os botões de entrar/criar conta do `index.html` vão dar erro.

---

## Passo 2 (recomendado) — Apertar as regras do Realtime Database

Hoje o banco provavelmente está em "modo de teste" (aberto pra qualquer um com o link). Como agora existe login de verdade, dá pra exigir que a pessoa esteja logada para ler/escrever. Vá em **Realtime Database → Regras** e use:

```json
{
  "rules": {
    "usuarios": {
      "$uid": {
        ".read": "auth !== null && auth.uid === $uid",
        ".write": "auth !== null && auth.uid === $uid"
      }
    },
    "mesasInfo": {
      "$mesaId": {
        ".read": "auth !== null",
        ".write": "auth !== null && (!data.exists() || data.child('mestreUid').val() === auth.uid)",
        "membros": {
          "$uid": {
            ".write": "auth !== null && auth.uid === $uid"
          }
        }
      }
    },
    "mesas": {
      ".read": "auth !== null",
      ".write": "auth !== null"
    }
  }
}
```

O que isso garante: só quem tem conta acessa qualquer coisa; cada um só edita o próprio nó em `usuarios`; só o Mestre que criou a mesa pode alterar os dados dela em `mesasInfo`; qualquer jogador logado pode entrar como membro (escrevendo só o seu próprio `membros/<uid>`). As fichas em `mesas/*` continuam abertas entre quem está logado — igual ao esquema informal de hoje (o código da mesa já funciona como "senha"), só que agora atrás de login.

*(Esse passo é opcional pra tudo funcionar, mas recomendado — sem ele, o banco continua "modo de teste" e qualquer pessoa com o link do Firebase config consegue ler/escrever, logada ou não.)*

---

## Passo 3 — Migrar a mesa atual (`dungeon-crawler-world`)

Sua mesa já em andamento — com as fichas dos 5 jogadores salvas em `mesas/dungeon-crawler-world/jogadores/...` — precisa ganhar um "registro" no novo sistema pra aparecer no portal. Isso é feito **pelo próprio portal**, sem mexer no Firebase Console:

1. Abra `index.html` e **crie sua conta de Mestre** (email + senha).
2. Você cai no `DCC-Portal.html`. Na seção **🛡 Mesas que eu mestro**, preencha:
   - **Nome da mesa:** `Dungeon Crawler World` (ou o nome que preferir mostrar)
   - **Código customizado:** `dungeon-crawler-world` ← **exatamente esse**, pra apontar pro mesmo lugar onde as fichas já estão salvas
3. Clique **Criar mesa**. Pronto — a mesa existente agora é sua no portal, com todas as fichas dos jogadores intactas (nada foi apagado ou movido).
4. Abra **Painel do Mestre** pelo card da mesa — vai carregar os 5 crawlers normalmente, como sempre carregou.

### Cada um dos 5 jogadores

1. Cria a própria conta em `index.html` (é só o link do site, sem precisar de nome de arquivo).
2. No portal, usa **"Entrar em uma mesa com código"**:
   - **Código da mesa:** `dungeon-crawler-world`
   - **Nome do personagem:** **o mesmo nome que já vinha usando** no link antigo (`?pid=SEU-NOME`) — isso é importante, é o que identifica a ficha dele na nuvem. Se digitar um nome diferente, o sistema vai achar que é um personagem novo (ficha vazia).
3. Depois de entrar, o card da mesa aparece com o botão **"Abrir minha ficha"**, que leva direto pra ficha de sempre.

> Dica: se algum jogador não lembrar o nome exato usado antes, você (Mestre) vê os nomes de todos abrindo o Painel do Mestre — os PIDs aparecem em `mesas/dungeon-crawler-world/jogadores/` no Firebase Console (Realtime Database), sem o prefixo `pid-`.

---

## Fluxo novo, resumido

```
index.html  →  (cria conta ou entra)  →  DCC-Portal.html
                                            ├── 🎮 Jogador: lista mesas + "Entrar em mesa com código"
                                            └── 🛡 Mestre: lista mesas + "Criar nova mesa"
                                                     ↓ abre
                            DCC-Dashboard-Equipamento.html (ficha)
                            DCC-Painel-Mestre.html (painel ao vivo)
```

Depois de migrada, distribua só **um link** pros jogadores: o link raiz do site (ex: `https://matheuscampa.github.io/dungeonearth/`), que abre direto o `index.html`. Eles criam a conta, colam o código da mesa (`dungeon-crawler-world`) uma vez, e depois disso o portal já lembra de tudo — não precisam mais do link cheio de parâmetros.

## Segurança — o que muda

- Antes: qualquer um com o `firebaseConfig` (que fica visível no HTML) lia/escrevia tudo.
- Agora: precisa de conta (email/senha) pra sequer entrar no portal. Com o Passo 2 aplicado, também precisa estar logado pra tocar no banco de dados.
- O código da mesa continua funcionando como uma "senha informal" pra entrar numa mesa específica — igual já era, só que agora atrelado a uma conta de verdade em vez de um dispositivo/navegador solto.
