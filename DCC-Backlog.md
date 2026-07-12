# BACKLOG — Dungeon Crawler Carl RPG

*Documento vivo. Atualizado em 2026-07-12. Marque `[x]` quando concluir.*

Legenda de prioridade: **P0** = trava a Sessão 1 · **P1** = importante para campanha · **P2** = polimento/expansão.

---

## ✅ Pronto (base jogável da Sessão 1)

- [x] Sistema Central (regras, rolagem única, dano, condições, morte)
- [x] Regeneração de HP/PM (1 por turno por nível)
- [x] Regras de Sala Segura, Descanso Diário e upgrade de Cama
- [x] Combate Desarmado/Improvisado + trilha de evolução
- [x] Catálogo de Itens (171, v5) + Lista de Itens (PDF)
- [x] Catálogo de Skills (203, v5) + Lista de Skills (PDF)
- [x] Tabela de Loot por caixa (PDF)
- [x] Bestiário do Andar 1 (PDF)
- [x] Tabela de Falha Crítica (PDF)
- [x] Loadout inicial (a roupa do corpo)
- [x] Módulo jogável do Andar 1
- [x] Regra-base de Companheiros e Invocações + opções (doc)
- [x] 20 Conquistas do Andar 1 (PDF)
- [x] One-pager do jogador (ficha + referência) (PDF)
- [x] Dashboard de Equipamento + Skills + PM + Desarmado (HTML) + sincronização

---

## 🔜 Próximo passo imediato

- [x] **Firebase + GitHub Pages no ar** — projeto criado, dashboard hospedado e Pages ativo. Falta só testar a conexão ao vivo com os jogadores na Sessão 1.
- [x] **Portal de gestão com login (email/senha)** — `index.html` (URL única de entrada, a raiz do site) + `DCC-Portal.html`: menu Jogador (lista de mesas + ficha) e menu Mestre (criar mesa, gerar/copiar código). `DCC-Portal-Login.html` virou redirect de compatibilidade. Reaproveita o projeto Firebase existente (Auth + Realtime Database). Guia completo em `COMO-ATIVAR-LOGIN.md`.
  - [x] Ativar Email/Password no Firebase Console (Passo 1 do guia). Feito.
  - [x] Apertar regras do Realtime Database para exigir login (Passo 2 do guia). Feito — regras de `usuarios`/`mesasInfo`/`mesas` aplicadas.
  - [x] Migrar a mesa `dungeon-crawler-world` pelo portal (Passo 3 do guia) — mesa recriada com código customizado, fichas dos jogadores preservadas. Feito.
  - [ ] **Pendente de você:** avisar os 5 jogadores pra criarem conta em `index.html` e entrarem na mesa com o código `dungeon-crawler-world` (mesmo nome de personagem de antes).
- [x] **Correção: `permission_denied` no Painel do Mestre/Dashboard** — as regras apertadas exigiam login, mas essas duas páginas nunca autenticavam no Firebase. Agora carregam o SDK de Auth e só conectam na mesa depois de confirmar a sessão logada (senão redirecionam pro login). Feito.
- [x] **Correção: redirect prematuro de volta pro login** — o gate de auth do Painel/Dashboard disparava o redirect assim que via `user=null` (estado transitório enquanto a sessão salva ainda carrega), e não cancelava esse redirect se o login real chegasse logo em seguida — derrubava a página no meio do carregamento das fichas. Corrigido: agora cancela o redirect pendente assim que o usuário é confirmado. Feito.
- [x] **URL única de entrada** — `index.html` é a página raiz do site (login/cadastro); depois de logar vai direto pro Portal. `DCC-Portal-Login.html` ficou como redirect de compatibilidade pra quem tinha o link antigo salvo. Feito.
  - [ ] **Pendente de você:** dar commit + push dessas mudanças pro repositório do GitHub Pages pra valerem no site ao vivo (se ainda não fez).

---

## 📋 Pendências

### Regras
- [x] **Tabela de XP** — XP individual (Tier × andar; golpe final = dobro), curva `50×nível` sem teto, ~6 níveis/andar (nv20 ≈ Andar 3). No Sistema §14.2. Feito.
- [x] **Regras de Audiência/Patrocínio** — PA é placar único (só sobe, nunca se gasta) e define o patrocinador; Andar 3+ ganha Caixa premium por andar. No Sistema §11. Feito.
- [x] **Combate avançado + novas condições** — §6A + Derrubado/Medo/Imobilizado/Provocado/Oculto. Feito.
- [x] **Exaustão.** Formalizada como condição graduada 0-5 (acumula sem Descanso Diário / farm longo). No Sistema §14.1. Feito.
- [ ] **P1 — Crafting (forja/receitas).** Sistema para transformar materiais monstruosos (ex.: partes de chefe) em itens. Definir: fonte de materiais, bancada na Sala Segura, receitas, custo. *(Falar depois — por ora, batalhas épicas entregam itens prontos, sem craft.)*

### Conteúdo
- [ ] **P1 — Loja da Sala Segura.** Lista de preços em ouro: consumíveis, consertos, upgrade de Cama, e itens fixos do Bopca. Definir custo do **upgrade de Cama**. *(Adiado a pedido — só o Guia/atmosfera por enquanto.)*
- [ ] **P1 — Guias de Masmorra.** Conceito dos NPCs que orientam cada crawler (lore, missões, personalidade). Falas-base já no módulo do Andar 1 (Sala Segura) — o Mestre interpreta. Falta o conceito de campanha.
- [ ] **P2 — Andar 2+ (bestiário, tema, chefe) e moldura de campanha.**
- [ ] **P2 — Engordar Épicos/Lendários/Celestiais temáticos** conforme a campanha avança (pool atual: Raro 26 · Épico 13 · Lendário 7 · Celestial 3).
- [ ] **P1 — Mais itens + curva de valor.** Expandir o catálogo (mais variedade em todos os slots) e **melhorar a progressão de valor entre raridades** — garantir que cada degrau (Comum→Incomum→Raro→Épico→Lendário→Celestial) tenha um salto claro e consistente em dano/Defesa/efeito, sem buracos nem sobreposição entre tiers.
- [ ] **P2 — Mais conquistas** por andar/feito (deck cresce com a campanha).

### Dashboard / fichas digitais
- [ ] **P1 — Barras de vida (jogadores e monstros) no dashboard do jogador.** Exibir no dashboard do jogador uma **barra de HP de cada crawler da mesa** (puxando os HP atual/máx já publicados no Firebase) e uma **área de HP dos monstros do combate atual** (controlada/sincronizada pelo Mestre — provável novo nó `mesas/{sala}/combate`). Definir: quem edita o HP dos monstros (Mestre adiciona/dá dano), atualização ao vivo, e visual compacto (barra + número, cor por % de vida).
- [ ] **P1 — Banco de pontos de atributo não usados.** Campo na ficha (dashboard + ficha impressa) para guardar **pontos de atributo ganhos mas ainda não distribuídos** — o jogador acumula ao subir de nível / por recompensas e gasta quando quiser. Definir: quantos pontos por nível, se há trava por andar, e refletir o saldo no Painel do Mestre.
- [ ] **P1 — Troca de itens entre jogadores da mesa.** Permitir transferir cartas/itens (e talvez ouro) de uma ficha para outra via Firebase, sem copiar/colar manual. Definir: fluxo de oferta→aceite, alcance (precisa estar na mesma cena/Sala Segura?), e o que pode ou não ser trocado.
- [ ] **P1 — Atualizar o XP ao subir de nível.** Hoje o XP é um campo solto. Ao bater o alvo (`50×nível`), o dashboard deve **subir o nível e debitar/zerar o XP** automaticamente (ou avisar), em vez de o jogador fazer a conta na mão. Mostrar barra de progresso até o próximo nível.
- [ ] **P1 — Lista de Conquistas no dashboard.** Trazer o deck de conquistas (hoje só em PDF) para dentro da ficha digital — exibir as do andar, marcar as desbloqueadas, e somar o XP/loot ao concedê-las. Idealmente o Mestre marca e sincroniza via Firebase.
- [ ] **P1 — Busca e filtro por raridade no catálogo.** Campo de **pesquisa por nome** e **filtro por raridade** (e talvez por slot/tipo) ao escolher itens no dashboard — hoje a lista é só rolar. Mesma ideia para as skills.
- [ ] **P1 — Total de pontos de atributo disponíveis.** Mostrar na ficha o **total de pontos que o jogador tem para distribuir** (calculado a partir do nível + bônus), não só o saldo não usado — para ele saber quanto pode alocar. Liga-se ao "Banco de pontos de atributo não usados".
- [ ] **P1 — Loot automático das Caixas.** O dashboard **rola a Tabela de Loot sozinho** ao abrir uma Caixa (do tier certo) e mostra o resultado; o jogador só **confirma e adiciona ao inventário**. Tira a rolagem manual em `DCC-Tabela-Loot.pdf`. Definir: animação/registro, e regras especiais das Caixas de Patrocínio (sem sucata, +1 raridade, rola 2× e escolhe).
- **Fichas na nuvem acessíveis por URL** — em duas partes:
  - [x] **Parte B (carregar por URL)** — o dashboard lê `?mesa=...&pid=...`, usa o `pid` como identidade fixa, conecta sozinho e **puxa a ficha salva no Firebase** ao abrir + botão "☁ Puxar ficha". Feito.
  - [x] **Sincronização "mais recente vence"** — ao abrir em qualquer lugar, compara `updatedAt` local x nuvem e carrega a versão mais nova (não sobrescreve mais a nuvem com uma ficha antiga). Feito e testado.
  - [x] **Backup das fichas (Mestre)** — botão "⬇ Backup das fichas" no Painel do Mestre baixa um JSON com todas as fichas para guardar no repositório. Feito.
  - [x] **Parte A (hospedar)** — dashboard no **GitHub Pages**; cada jogador tem link pessoal `…?mesa=dungeon-crawler-world&pid=NOME` (config + catálogos embutidos como padrão). Feito.
- [x] **Ataques computados na ficha** — desarmado + armas + spells/skills de dano, empilhados na coluna de Ataques. Feito.
- [x] **Bug do √ dos atributos** — corrigido (o ⌊√⌋ atualiza ao mudar o atributo).
- [x] **Dano estruturado nas skills** — as 12 spells de dano (Bola de Fogo, Relâmpago, Meteoro, etc.) ganharam faixas `d1/d2/d3 + attr` (catálogo v6); a ficha calcula e mostra todas, e a Lista de Skills exibe o dano. Feito.
- [x] **HP atual, PA e Companheiros na ficha** — o dashboard agora rastreia HP atual, PA e uma lista de companheiros, e publica tudo. Feito.
- [x] **Tooling de XP/PA individual** — dashboard tem campos de **XP** (ao lado do Nível) e **PA (Audiência)** nos Recursos, e publica tudo; o Painel do Mestre mostra **XP e PA por card**. (Fama removida — PA é placar único.) Feito.

### Material de mesa / ferramentas
- [x] **Cartas/tokens físicos de Condição** — `DCC-Cartas-Condicao.pdf` (17 condições imprimíveis). Feito.
- [x] **Painel do Mestre: companheiros, PA e HP atual** dos jogadores — exibidos ao vivo. Feito.
- [x] **Colapso do andar no Painel do Mestre** — clock de colapso (pips) salvo no Firebase. A barra coletiva de XP foi **removida**: XP é individual, controlado pelo card de cada jogador. Feito.

---

## Notas de manutenção
- Versões atuais: **Itens v6 (175; com tipo de dano)** · **Skills v9 (223; 32 spells de dano)** · **Sistema v1.5 (§6A Combate avançado · PA placar único · Exaustão §14.1 · XP/Audiência · Farm §14.4)**. Módulo Andar 1 = **caverna clássica** + 2 Batalhas Épicas de farm + falas do Guia na Sala Segura.
- Ao mudar catálogos, regerar: `DCC-Lista-Itens.pdf`, `DCC-Lista-Skills.pdf`, `DCC-Tabela-Loot.pdf` (pool é dinâmico).
- Jogadores recarregam os links dos catálogos para puxar versões novas.
