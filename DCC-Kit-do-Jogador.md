# 🎮 Kit do Jogador — Dungeon Crawler Carl (mesa online)

Você vai receber do Mestre um **link pessoal**. Abrir esse link já faz quase tudo sozinho: conecta na mesa, carrega os catálogos de itens e skills e abre a **sua** ficha. Você só monta o personagem. Use no **computador**, com Chrome, Edge ou Firefox.

---

## 1. Abra o seu link pessoal

O Mestre te manda um link assim (com o **seu nome** no final). Abra no navegador e salve nos favoritos:

```
https://matheuscampa.github.io/dungeonearth/DCC-Dashboard-Equipamento.html?mesa=dungeon-crawler-world&pid=SEU-NOME
```

Em poucos segundos o topo deve mostrar **“Catálogo: 175 cartas”**, **“Skills: 223 no catálogo”** e o status **“● ao vivo · mesa dungeon-crawler-world · id: seu-nome”**. Se aparecer isso, está tudo conectado. 🎉

## 2. Monte a sua ficha

- **Atributos:** distribua **15 pontos** entre FOR/DEX/CON/INT/CHA (mínimo 1, máximo 6 na criação). HP, PM, Defesa, Iniciativa e os Ataques são calculados sozinhos.
- **Equipamento:** clique num slot (mão, cabeça, etc.) e escolha uma carta do catálogo.
- **Skills & Spells:** clique em **+ Adicionar skill**, filtre por trilha e escolha. Suba o rank com **+ / −**.
- Tudo **salva sozinho** e aparece ao vivo para o Mestre. Não precisa apertar “salvar”.

## 3. Trocar de aparelho / recuperar a ficha

Sua ficha fica salva na nuvem sob o seu link. Para abrir em outro computador, é só abrir o **mesmo link** — ela carrega sozinha. Se precisar forçar, clique em **☁ Puxar ficha**.

---

## Se algo não carregar (configuração manual)

Caso os catálogos ou a conexão não venham sozinhos, dá para configurar na mão pelas barras do topo:

- Barra **“Catálogo”** → 🔗 Carregar do link:
  ```
  https://raw.githubusercontent.com/matheuscampa/dungeonearth/refs/heads/main/DCC-Catalogo-Itens.json
  ```
- Barra **“Skills”** → 🔗 Carregar skills:
  ```
  https://raw.githubusercontent.com/matheuscampa/dungeonearth/refs/heads/main/DCC-Catalogo-Skills.json
  ```
- **⚙ Configurar Firebase** (cole e Salvar config):
  ```js
  const firebaseConfig = {
    apiKey: "AIzaSyCWfU58HVTvLK4ej5yDH06mr2CQtxsde-8",
    authDomain: "dungeonearth.firebaseapp.com",
    databaseURL: "https://dungeonearth-default-rtdb.firebaseio.com",
    projectId: "dungeonearth",
    storageBucket: "dungeonearth.firebasestorage.app",
    messagingSenderId: "528605528507",
    appId: "1:528605528507:web:8bf62f719a9e773607449e",
    measurementId: "G-6C91MQ4W56"
  };
  ```
- **Código da mesa:** `dungeon-crawler-world`

---

## Problemas comuns

- **O link abre página em branco / 404** → o Mestre ainda não publicou o site (GitHub Pages). Avise-o.
- **Status fica “offline”** → clique em **📡 Conectar mesa**. Se persistir, use a configuração manual acima.
- **A ficha sumiu** → abra o seu link e clique em **☁ Puxar ficha**. Ela volta da nuvem.

Nos vemos na masmorra. Tentem morrer de um jeito interessante. 🎲
