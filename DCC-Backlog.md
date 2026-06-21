# BACKLOG — Dungeon Crawler Carl RPG

*Documento vivo. Atualizado em 2026-06-17. Marque `[x]` quando concluir.*

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
