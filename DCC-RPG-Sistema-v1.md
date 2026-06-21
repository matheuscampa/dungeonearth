# DUNGEON CRAWLER CARL — RPG DE MESA

## Sistema Central — Versão 1.3

*Um RPG de dungeon crawl brutal, sarcástico e cheio de loot, inspirado na série de Matt Dinniman, em TTRPGs e em MMOs.*

---

## 1. Filosofia do sistema

Três princípios guiam todo o desenho:

**O dado decide a qualidade, os atributos decidem a escala.** O d20 nunca compete com os seus números. Ele decide *se* você acertou e *quão bom* foi o golpe (a faixa de dano). Os atributos decidem o *tamanho* do número. Por isso o d20 nunca perde a força, mesmo quando a Força chega a 100 — quanto maior o seu personagem, mais a faixa que o dado escolhe vale a pena.

**Duas curvas de propósito.** Tudo que é dano, cura e vida cresce de forma **linear e sem teto** (os números grandes de MMO). Tudo que toca a rolagem do dado — Precisão e Defesa — usa uma curva **comprimida de raiz quadrada**, que cresce devagar e nunca estoura. É isso que mantém o d20 relevante do nível 1 ao 50.

**Letal e caótico.** A masmorra quer te matar e o Sistema acha graça. Mortes acontecem, o loot salva runs, e o azar é parte do espetáculo.

---

## 2. Atributos

Cinco atributos definem cada personagem. **O valor do atributo é usado diretamente** — não existe cálculo de "modificador" separado.

| Atributo | Sigla | Governa |
|---|---|---|
| Força | **FOR** | Dano e precisão corpo a corpo, carga, forçar/quebrar |
| Inteligência | **INT** | Dano mágico, Mana, perícias técnicas e de conhecimento |
| Destreza | **DEX** | Dano e precisão à distância e com armas ágeis, Defesa, Iniciativa |
| Carisma | **CHA** | Influência social e **Audiência/Patrocínio** (a moeda do show) |
| Constituição | **CON** | Pontos de Vida, fôlego, resistência a venenos e atordoamento |

### Criação de personagem

Distribua **15 pontos** entre os cinco atributos.

- **Mínimo 1** ponto por atributo (nada de zero).
- **Máximo 6** em qualquer atributo no nível 1.

### Ganho por nível

A cada nível você recebe pontos para distribuir livremente, e o ritmo acelera em limiares — bem como um MMO em que cada faixa de nível te dá mais poder por nível:

| Faixa de nível | Pontos por nível |
|---|---|
| 1 a 20 | **+3** |
| 21 a 50 | **+4** |
| 51+ | **+5** |

Não há teto de atributo após a criação. É esperado e desejado que atributos cheguem a 100 ou mais em níveis altos.

---

## 3. Estatísticas derivadas

### 3.1 A curva comprimida (raiz quadrada)

Sempre que uma estatística vai **modificar a rolagem do d20**, ela passa pela raiz quadrada arredondada para baixo: `⌊√atributo⌋`. Isso cria retornos decrescentes naturais e mantém esses valores sempre pequenos (na prática, entre 0 e ~12 o jogo inteiro).

Tabela de referência de `⌊√x⌋`:

| Atributo | ⌊√x⌋ | Atributo | ⌊√x⌋ |
|---|---|---|---|
| 1–3 | 1 | 49–63 | 7 |
| 4–8 | 2 | 64–80 | 8 |
| 9–15 | 3 | 81–99 | 9 |
| 16–24 | 4 | 100–120 | 10 |
| 25–35 | 5 | 121–143 | 11 |
| 36–48 | 6 | 144–168 | 12 |

### 3.2 Precisão (comprimida)

A **Precisão** é a sua pontaria/perícia com uma arma. Cada arma tem um **atributo regente** (o mesmo que impulsiona o dano dela): armas de FOR usam FOR, arcos e adagas usam DEX, magias e cajados usam INT.

```
Precisão = ⌊√(atributo regente da arma)⌋ + bônus de Precisão do item
```

A Precisão entra na rolagem de ataque como bônus. Como passa pela raiz quadrada, mesmo um bárbaro de FOR 100 tem só Precisão +10 — o suficiente para acertar bem, longe de tornar o dado irrelevante.

*Exemplo:* uma guerreira com FOR 25 empunhando um machado (arma de FOR) tem Precisão = ⌊√25⌋ = **+5**. Se o machado também tiver "+1 Precisão" gravado, vira **+6**.

### 3.3 Defesa (comprimida + equipamento)

A **Defesa** representa toda a sua capacidade de não tomar um golpe cheio: esquivar, aparar e bloquear. Por isso ela combina a sua agilidade (DEX, comprimida) com tudo que você está vestindo e segurando. **Escudos somam aqui** — é por isso que chamamos de Defesa, e não de Esquiva.

```
Defesa = ⌊√DEX⌋ + Armadura + Escudo + outros bônus
```

- `⌊√DEX⌋` — sua esquiva natural, comprimida (sempre pequena).
- **Armadura** — valor de Defesa impresso na carta da peça (peito, elmo, botas, etc., somados).
- **Escudo** — valor de Defesa impresso na carta do escudo. Empunhar um escudo é o jeito mais direto de elevar a Defesa.
- **Outros bônus** — buffs, posturas, skills, terreno.

A Defesa do alvo é **subtraída** da rolagem de ataque do atacante. Quanto maior a Defesa, mais o atacante é empurrado para faixas baixas de dano — ou para o erro.

*Exemplo:* um ladino com DEX 16, peitoral de couro (Armadura 2) e um broquel (Escudo 1) tem Defesa = ⌊√16⌋ + 2 + 1 = 4 + 2 + 1 = **7**. Troque o broquel por uma pavês (Escudo 4) e a Defesa sobe para **10**, ao custo de ocupar a mão (sem arma de duas mãos).

### 3.4 Vida e Mana (lineares — números grandes)

```
HP máximo  = 8 + (CON × 3)
Mana máxima = INT × 3
```

Lineares e sem teto: crescem junto com os atributos e atingem números altos de MMO. Recalcule o HP máximo sempre que a CON subir. **PM (Pontos de Mana)** é a Mana gasta por spells; skills marciais usam **cooldown** (recarga em turnos) em vez de PM. Cada carta de skill diz qual.

*Exemplo:* CON 4 → HP 20 no nível 1. CON 60 no nível alto → HP 188.

### 3.4.1 Regeneração de HP e PM (rápida)

```
Regeneração = nível, por turno (HP e PM, cada)
```

No **início de cada turno seu**, recupere HP e PM iguais ao seu **nível** (nível 1 = +1/+1; nível 5 = +5/+5). Em combate é marginal diante do dano; **fora de combate, suas barras enchem em poucos turnos**. Por isso a cura não depende de poções nem da Sala Segura — você se regenera sozinho. Enquanto **Caído** (0 HP) você **não** regenera: faça Testes de Morte (§8).

### 3.5 Iniciativa (comprimida)

```
Iniciativa = d20 + ⌊√DEX⌋
```

Comprimida de propósito, como tudo que toca o dado: mesmo com DEX altíssima, a ordem do turno continua sendo uma disputa de verdade. **Modificadores de Iniciativa** de skills e itens (ex: +1 de Reflexos Felinos, −1 de armadura pesada) somam-se a esse valor — some todos. *(O dashboard calcula só o ⌊√DEX⌋; os bônus fixos de gear/skill o jogador soma na hora.)*

---

## 4. O coração do sistema: a rolagem única

Todo ataque é **uma só rolagem de d20** que responde duas coisas ao mesmo tempo: se acertou e qual a faixa de dano.

```
RESULTADO = d20 + Precisão − Defesa do alvo
```

Cruze o resultado com a tabela de faixas:

| Resultado | Faixa | Efeito |
|---|---|---|
| **nat 1** | Falha crítica | Erra e algo dá errado (ver §6) |
| **≤ 5** | Erro | Nenhum dano |
| **6 – 10** | **Baixa** | Dano da faixa Baixa do item |
| **11 – 17** | **Média** | Dano da faixa Média do item |
| **18 – 19** | **Alta** | Dano da faixa Alta do item |
| **20+ ou nat 20** | **Crítico** | Faixa Alta × 2 + efeito de crítico |

"nat 1" e "nat 20" são o número bruto no dado, antes dos modificadores, e sempre têm efeito.

### Por que isso escala para sempre

Contra um inimigo do seu nível, Precisão e Defesa tendem a se cancelar, então a distribuição de faixas é praticamente **a mesma no nível 1 e no nível 25** — o que muda é só o tamanho do número (próxima seção). Contra um inimigo fraco, a Precisão domina e você empurra tudo para Média/Alta. Contra um chefe muito acima de você, a Defesa dele domina e você arranha em Baixa ou erra. É exatamente o "gating de nível" de um MMO.

---

## 5. Dano: a escala de MMO

O dano **multiplica** a faixa pelo atributo regente. É aqui que os números explodem.

```
Multiplicador = atributo regente ÷ 5
Dano = valor da faixa do item × Multiplicador     (arredonde para baixo, mínimo 1)
Dano crítico = valor da faixa Alta × Multiplicador × 2
```

O atributo **nunca entra na rolagem** — ele só multiplica o resultado. Por isso pode crescer sem limite sem nunca quebrar o d20.

### Demonstração de escala

Mesma distribuição de chances, números completamente diferentes:

| | Baixa | Média | Alta | Crítico |
|---|---|---|---|---|
| **Nível 1** — FOR 5, arma 2/5/9 (×1) | 2 | 5 | 9 | 18 |
| **Nível 25** — FOR 100, arma 20/50/90 (×20) | 400 | 1.000 | 1.800 | **3.600** |

Repare: no nível 25 o d20 decide entre **400 e 3.600 de dano** numa rolagem. O dado importa *mais*, não menos. Esse é o motivo de o sistema inteiro existir.

---

## 6. Combate

### Ordem e estrutura do turno

No início do combate, todos rolam **Iniciativa** (d20 + ⌊√DEX⌋) e agem do maior para o menor.

No seu turno você tem:

- **1 Ação Principal** — atacar, conjurar uma skill, usar um item, uma manobra.
- **1 Movimento** — deslocar-se até o seu alcance.
- **Reações** — respostas fora do seu turno (aparar, oportunidade), liberadas por skills.
- **Ações Bônus** — algumas skills concedem uma ação extra menor.

### Crítico (nat 20 ou resultado 20+)

Dano da faixa Alta dobrado, **mais** um efeito: aplique uma condição à escolha (§7), ignore parte da Defesa, ou ative o efeito de crítico gravado no item.

### Falha crítica (nat 1)

O ataque erra e o Sistema ri. Role na **Tabela de Falha Crítica** ou improvise: a arma escapa da mão, você acerta um aliado, tropeça (Derrubado), seu equipamento racha, ou um inimigo ganha uma reação grátis. Em masmorra letal, o azar é conteúdo.

### Skills com recarga vs. Mana

Skills ativas custam **PM/Mana** (pool de INT × 3) ou têm **cooldown** (X turnos até poder usar de novo). Spells tendem a usar PM; skills físicas e marciais tendem a usar cooldown. Cada carta de skill diz qual. PM se recupera com a regeneração (§3.4.1) e no Descanso (§14).

### Combate desarmado e improvisado

Você nunca fica indefeso — mesmo sem arma, de cueca, no Andar 1.

```
Desarmado     = 1 / 2 / 4   [maior entre FOR e DEX]   — sempre disponível
Improvisada   = 1 / 3 / 6   [FOR]                      — objeto do cenário; quebra num nat 1
```

O Desarmado usa as regras normais (Precisão = ⌊√regente⌋; dano = faixa × regente÷5). **Lutar desarmado é uma build de verdade:** manoplas (slot de mão) e gear de luta (braçadeiras, joelheiras, caneleiras) somam aos campos **+faixa** e **+Precisão** do Desarmado, e há uma trilha de **skills de luta** (Punhos de Ferro, Sequência de Golpes, Nocaute, Mestre das Artes, etc.) que o fazem escalar. O dashboard calcula o Ataque Desarmado automaticamente.

---

## 6A. Combate avançado (o que as skills usam)

As skills citam um punhado de mecânicas espaciais e táticas. Aqui estão todas, resolvidas de forma leve e balanceada. **A masmorra roda em "teatro da mente":** distâncias são abstratas; os metros das cartas são só referência que o Mestre traduz para *adjacente / perto / longe*.

### Movimento, alcance e posicionamento

- **Adjacente** (corpo a corpo): coladinho, ≤ 2 m.
- **Perto:** ~6 m — alcançável com **1 Movimento**.
- **Longe:** ~12 m+ — exige 2 Movimentos (ou correr).
- Seu **Movimento** padrão (1 por turno) cruza uma faixa de distância (até *Perto*). Cada **"+1 de Movimento"** de skill/item deixa você cruzar uma faixa extra (≈ +3 m num grid).
- **Alcance de skill/arma:** corpo a corpo = adjacente; "à distância" = na linha de visão; "X m" = use *perto* (≤6 m) ou *longe* conforme o número.

### Ataque de oportunidade (regra-base)

Sair do alcance corpo a corpo de um inimigo (afastar-se dele) **provoca um Ataque de Oportunidade**: ele gasta a **Reação** para um ataque grátis em faixa **Baixa**. Você tem **1 Reação por rodada** (skills concedem mais). *Teleportar, recuar com skills específicas e ser empurrado **não** provocam.*

### Surpresa e emboscada

Se um lado começa o combate **sem ser notado** (furtividade vencida, monstro escondido, ataque traiçoeiro), ele tem uma **rodada-surpresa**: age uma rodada inteira **antes** da Iniciativa normal, e os surpreendidos **não agem nem reagem** nessa rodada. Detectar a emboscada (percepção do alvo vs DEX do furtivo) cancela a surpresa.

### Empurrão, derrubada e colisão

- **Empurrão:** move o alvo na direção indicada (ex: 3 m). Não provoca Ataque de Oportunidade.
- **Colisão:** se o empurrado bate numa parede ou em outra criatura antes de completar, ele **para** e sofre **faixa Baixa** extra; a criatura atingida também sofre faixa Baixa.
- **Derrubar:** deixa o alvo **Derrubado** (no chão — ver §7).

### Cobertura e flanco

- **Cobertura:** alvo parcialmente protegido (mureta, batente, aliado grande) tem **+2 de Defesa** contra ataques à distância. Cobertura **total** = não pode ser alvo direto.
- **Flanco:** atacar um inimigo que já está em corpo a corpo com um aliado seu concede **+1 na rolagem de ataque**. (É o que "atacar pelo flanco/pelas costas" das skills representa.)

### Ataques em área (cone, linha, explosão)

Formas-padrão (guias; no teatro da mente, "quem está agrupado" é atingido):

- **Cone:** quarto de círculo ~6 m à frente.
- **Linha:** reta de ~12 m.
- **Explosão/Raio:** círculo de ~4 m em torno do ponto.

**Como rolar:** faça **uma** rolagem (d20 + Precisão) e compare contra a **Defesa de cada alvo** separadamente — cada um pode cair numa faixa diferente. Quando a carta pedir **teste de resistência** (d20 + ⌊√CON⌋ ou ⌊√INT⌋ vs 10), use isso em vez da rolagem de ataque.

### Terreno difícil

Escombros, gelo, lama, fogo no chão: cada faixa de distância custa o **dobro** de Movimento. Combinado com **Lento**, o alvo praticamente não se move.

### Esquiva vs. Armadura (ignorar Defesa)

A Defesa tem **duas partes**:

```
Defesa = Esquiva (⌊√DEX⌋ + bônus de esquiva)  +  Equipamento (Armadura + Escudo + acessórios)
```

- **"Ignora Armadura" / "atravessa armadura"** → desconsidera a parte de **Equipamento** (só a Esquiva conta). Típico de mísseis de força e ataques mentais.
- **"Não pode ser esquivado" / "ignora esquiva"** → desconsidera a parte de **Esquiva** (só o Equipamento conta).
- **"Ignora X de Defesa"** → subtrai X da Defesa total do alvo só para aquele ataque.

### Tipos de dano e resistência

Todo dano tem um **tipo**: físico (cortante/perfurante/contundente) ou especial (fogo, gelo, raio, ácido, **força**, **psíquico**, **necrótico**, **radiante**, **sônico**, veneno…). O tipo importa para interações:

- **Resistência (a um tipo):** o dano daquele tipo é **reduzido à metade**. **Vulnerabilidade:** **dobrado**. **Imunidade:** zerado.
- Por padrão, ninguém tem resistência/imunidade — **só quando a carta do inimigo indica** (ex: a Barata ignora a 1ª faixa com Contundente; mortos-vivos tomam dano dobrado de Radiante). Skills que "ignoram a primeira resistência" anulam uma resistência do alvo.

### HP Temporário (HPt)

Uma reserva extra concedida por skills/itens que **absorve o dano antes do HP real**. Regras: **não regenera**, **não acumula** (pegue o maior valor), a cura **não** o recupera, e ele **some ao fim do combate** (salvo indicação). Em jogo: subtraia o dano do HPt primeiro; o que sobrar atinge o HP.

### Execução

Efeitos que **"executam"** matam o alvo na hora se ele estiver **abaixo do limiar de HP** indicado (1/4, 1/3…). **Chefes são imunes a execução** — em vez disso, sofrem o dano dobrado ou um efeito reduzido (a carta diz).

### Concentração

Alguns efeitos **sustentados** (auras, paredes, controle contínuo) exigem **Concentração** quando a carta indicar. Você mantém **no máximo 1** efeito de concentração por vez. Se sofrer dano enquanto concentra, faça **⌊√INT⌋ vs 10** (ou perca o efeito). Skills que **"quebram concentração"** cancelam na hora a conjuração sustentada do alvo.

### Voo e levitação

Enquanto **voando/levitando**, você ignora terreno difícil e armadilhas de chão, não pode ser atingido por ataques corpo a corpo de quem está no solo (salvo armas de alcance) e cruza abismos. Dura o tempo da skill/item; ao acabar, você desce **sem dano de queda**.

### Janelas de uso ("1× por…")

As recargas especiais valem assim: **1×/combate** reseta quando um novo combate começa · **1×/cena** por cena de ficção · **1×/andar** reseta ao descer um andar · **1×/descanso** reseta no Descanso Diário (§14.1) · **1×/sessão** uma vez por sessão de jogo · **"fora de combate"** só pode ser usada sem combate ativo.

---

## 7. Condições (buffs e debuffs)

Condições são padronizadas para virarem cartas (§13). Salvo indicação, duram até o fim do próximo turno do alvo ou até um teste de resistência (d20 + ⌊√CON⌋ ou ⌊√INT⌋ vs 10, conforme a fonte).

| Condição | Efeito |
|---|---|
| **Atordoado** | Perde a próxima Ação Principal |
| **Sangrando (X)** | Sofre X de dano no início de cada turno |
| **Em Chamas (X)** | Como Sangrando, mas se espalha e ignora armadura |
| **Envenenado (X)** | Dano por turno + reduz cura recebida pela metade |
| **Lento** | Sem Movimento e sem Reações |
| **Marcado** | Atacantes ganham +3 na rolagem contra o alvo |
| **Amaldiçoado** | Trata todo nat alto como se fosse menor (sem críticos) |
| **Fúria** | +1 Multiplicador de dano, −2 de Defesa |
| **Abençoado** | Rola o ataque duas vezes e usa o melhor |
| **Protegido (X)** | Reduz cada dano sofrido em X |
| **Derrubado** | No chão. Ataques **corpo a corpo** contra ele: **+2**; ataques **à distância** contra ele: **−2**. Levantar custa metade do Movimento. *(≠ Caído a 0 HP, §8.)* |
| **Medo** | Ataca com **−2** e não pode se aproximar voluntariamente da fonte do medo. Se for forte, foge no próximo turno. |
| **Imobilizado** | Sem Movimento (preso, agarrado, na teia). Ataques contra ele têm **+2**. Soltar-se gasta a Ação (teste de FOR/DEX vs 10). |
| **Provocado** | Obrigado a usar a Ação Principal para atacar quem o provocou (se puder alcançá-lo); ataca qualquer outro com **−2**. *(Diferente de Marcado, que só dá +3 a quem ataca o alvo.)* |
| **Oculto** | Escondido/invisível. Não pode ser alvo direto enquanto oculto; o primeiro ataque saindo da ocultação ganha o bônus de surpresa/bote da skill. Atacar ou conjurar quebra a ocultação. |

> **HP Temporário** e os tipos/resistências de dano são tratados em **§6A** (Combate avançado).

---

## 8. Morte, queda e revive

Tom letal: a morte é real, mas a masmorra dá segundas chances a quem encontra os recursos certos.

**A 0 HP você está Caído** (à beira da morte — não confunda com **Derrubado**, que é apenas estar no chão, §7). No início de cada turno seu, faça um **Teste de Morte**:

```
Teste de Morte = d20 + ⌊√CON⌋   vs   dificuldade 10
```

- **Sucesso:** acumula 1 sucesso. **3 sucessos → estabilizado** (1 HP, mas fora de combate até curar).
- **Falha:** acumula 1 falha. **3 falhas → morte.**
- **Receber um Crítico enquanto Caído → morte imediata.**
- **nat 20 no Teste de Morte:** levanta com HP igual a CON.

**Revive.** Só acontece com recursos específicos: um item de revive saído de uma Caixa de Loot, um efeito de skill de alto nível, ou ser arrastado até uma **Sala Segura** (§11) antes da terceira falha. A masmorra não devolve crawlers de graça.

---

## 9. Skills e Spells

Spells são skills com sabor mágico — **mesma mecânica**. São os efeitos, talentos e capacidades do personagem, de **rank 1 a 15**.

### Pontos de Skill (PS)

Você sobe skills gastando **Pontos de Skill**:

- **~2 PS por nível.**
- PS extras vêm de **Conquistas** (§12) e de **Caixas de Loot** — bem na veia da série, onde uma conquista vira poder.

### Custo para subir de rank

Cada rank fica mais caro, então avançar nas pontas custa muito mais que começar uma skill nova:

| Rank | Custo (PS por rank) |
|---|---|
| 1 → 5 | 1 PS cada |
| 6 → 10 | 2 PS cada |
| 11 → 15 | 4 PS cada |

Assim, levar uma skill de 1 a 5 custa 4 PS, mas de 5 a 7 já custa outros 4 PS em só dois ranks — a progressão desacelera de propósito.

### Marcos de evolução (ranks 5, 10 e 15)

Não é só +número. Ao atingir **rank 5, 10 e 15**, a skill ganha uma **evolução**: uma nova forma, alvo extra, ou efeito inédito. São os grandes saltos de poder do personagem.

*Exemplo — Investida Brutal (skill de FOR):*

- **Rank 1–4:** avance e ataque com +1 faixa de dano por rank de bônus.
- **Rank 5 (evolução):** empurra o alvo e aplica Atordoado em crítico.
- **Rank 10 (evolução):** atinge todos os inimigos na linha da investida.
- **Rank 15 (evolução):** derruba (Caído) e aplica Sangrando a todos os atingidos.

---

## 10. Loot e raridade

Inimigos e baús dropam itens e **Caixas de Loot** (abra para receber um item aleatório da raridade da caixa). A raridade vira **cor de borda** na carta física — perfeito para o estilo TCG.

| Raridade | Cor da borda |
|---|---|
| Comum | Cinza |
| Incomum | Verde |
| Raro | Azul |
| Épico | Roxo |
| Lendário | Laranja/Dourado |
| Celestial | Branco iridescente |

**Ouro** é a moeda da loja da masmorra (compra suprimentos, consertos e itens fixos). **Caixas de Loot** são a moeda da sorte (RNG de drop). Itens de raridade maior têm faixas de dano mais altas, mais bônus de Precisão/Defesa e efeitos gravados (procs, condições em crítico, auras).

---

## 11. Audiência e Patrocínio (a mecânica-assinatura)

O dungeon do Carl é um **reality show intergaláctico**. Esta é a recompensa de CHA e o que separa este RPG de um dungeon crawler qualquer.

**Pontos de Audiência (PA)** são a meta-moeda do show. O Mestre concede PA a quem entretém os espectadores. Jogar seguro e entediante **seca a audiência**; ousadia, humor e risco a alimentam.

### Como ganhar PA

Conceda na hora em que o momento acontece. Valores-guia:

| Momento | PA |
|---|---|
| Tirada engraçada, pose, provocação à câmera | **+1** |
| Risco ousado, jogada criativa, uso esperto do cenário | **+2** |
| Morte espetacular, vitória improvável, salvar um aliado no limite | **+3** |
| Momento "clipe da temporada" (a mesa inteira reage) | **+5** |

**Bônus de Carisma:** quem tem CHA alto rende mais — some **+⌊√CHA⌋** a cada ganho de PA. *(Teto saudável: ~10 PA por crawler por combate, para a audiência não inflacionar.)* Algumas skills (Provocação da Plateia, Selfie com a Morte, etc.) também dão PA.

### Fama × PA (saldo)

São dois números:

- **PA (saldo):** o que você tem para **gastar** agora — em buffs temporários, presentes e nas skills de audiência (Patrocínio Relâmpago, Cura da Torcida…). Sobe e desce.
- **Fama (PA acumulado na carreira):** a **soma de todo PA que você já ganhou** na campanha. **Nunca diminui** (gastar PA não reduz a Fama). É ela que define o seu **nível de patrocinador**.

### Patrocinadores (a partir do Andar 3)

Quando o show ganha tração — **do Andar 3 em diante** — cada crawler atrai patrocinadores conforme a **Fama** acumulada. A cada andar, você recebe **1 Caixa de Patrocínio grátis** (uma por crawler, por andar), do tier abaixo:

| Fama acumulada | Patrocinador | Caixa de Patrocínio (1×/andar) |
|---|---|---|
| 30+ | **Local** | Prata |
| 60+ | **Regional** | Ouro |
| 100+ | **Galáctico** | Platina |
| 160+ | **Estrela** | Lendária |
| 250+ | **Megacorporação** | Divina |

*(Abaixo de 30 de Fama, ou antes do Andar 3, ainda não há patrocínio fixo — mas dá para sacar uma Caixa de Patrocínio gastando PA com a skill Patrocínio Relâmpago.)*

**As Caixas de Patrocínio são premium** — feitas para impactar a build, não para encher inventário. Ao abrir uma, na *Tabela de Loot*:

- **Nunca dá Sucata** (role de novo se cair).
- **+1 nível de raridade** no resultado (um Raro vira Épico, etc.).
- Você **rola duas vezes e escolhe** o item que ficar — garantia de algo útil para o seu personagem.

Ou seja: a Fama não é enfeite. Um crawler que se joga para a plateia sai dos andares profundos com itens visivelmente melhores que o grupo "careta".

---

## 12. Conquistas

**Conquistas** são cartas desbloqueadas por feitos notáveis. Cada uma concede **XP** e **loot** (e, às vezes, um **título** com buff permanente ou PS extras). São um motor de progressão paralelo aos níveis — exatamente como na série. O **deck inicial de 20 conquistas do Andar 1** já existe (ver `DCC-Conquistas-Andar1.pdf`); conceda na hora em que o feito acontecer e narre alto.

---

## 13. A voz do Sistema

O **Sistema** é a IA sarcástica que narra a masmorra. Use-o como ferramenta de Mestre: anúncios entre andares, notificações de nível e conquista lidas em voz alta, provocações em falhas críticas, e eventos de andar ("Atenção, crawlers: o saguão será inundado em 10 minutos"). O tom — debochado, brutal, surpreendentemente comovente — é parte do sistema, não enfeite.

---

## 14. Estrutura de andares (moldura de campanha)

A campanha é uma **masmorra de andares descendentes**. Cada andar tem um **tema**, inimigos próprios, **chefe** e, frequentemente, um **timer de colapso** (o andar fecha/desaba, forçando o grupo a descer). Entre seções há **Salas Seguras**. Descer é progredir; demorar é morrer.

### 14.1 Sala Segura e Descanso

Como a cura é automática (§3.4.1), a Sala Segura **não serve para curar** — serve para tudo o mais. Numa Sala Segura (zona sem combate) você pode:

- **Abrir Caixas de Loot** com calma e **organizar/reequipar** o inventário.
- **Conversar com seu Guia de Masmorra** (o NPC/IA que orienta cada crawler: dicas, missões, lore).
- **Usar a loja** do andar (comprar, vender, consertar).
- Cumprir o **Descanso Diário**.

**Descanso Diário (obrigatório).** A cada "dia" da masmorra (8 horas de ficção), todo crawler **precisa** dormir um turno. O descanso **zera cooldowns de recarga "descanso"**, **remove exaustão** e condições de longa duração, e enche HP/PM. Sem a **Cama**, o descanso consome as 8 horas in-fiction — o que **avança o relógio do andar** (não durma em lugar errado). Pular o Descanso Diário acumula **Exaustão**: −1 em todas as rolagens por dia sem dormir, até descansar.

> **Upgrade de Cama** — comprável na loja da Sala Segura. Permite **descansar imediatamente**, sem gastar as 8 horas. É um dos primeiros upgrades que todo grupo deveria querer.

### 14.2 XP e ganho de nível

- Cada inimigo abatido concede **XP para TODO o grupo** (não se divide — todos recebem o cheio). Recompensa a cooperação e mantém a mesa no mesmo nível.
Cada crawler tem **o próprio XP** e sobe de nível individualmente (não há teto — a campanha vai fundo).

**XP por inimigo abatido = Tier × o número do Andar.**

| Tier do inimigo | XP base (Andar 1) | No Andar F |
|---|---|---|
| Lacaio | 5 | 5 × F |
| Padrão | 10 | 10 × F |
| Elite | 25 | 25 × F |
| Chefe | 80 | 80 × F |

- **Todos do grupo** recebem esse XP a cada abate. **Quem dá o golpe final recebe o DOBRO** (o incentivo para arriscar o finish).
- **Conquistas** dão o XP impresso na carta (deck do andar).
- O XP escala com o andar de propósito: inimigos mais fundos valem mais, mantendo o ritmo conforme o custo de nível sobe.

**Subir de nível:** o XP necessário para o **próximo** nível é **50 × (nível atual)**.

```
XP (N → N+1) = 50 × N        (1→2 = 50 · 9→10 = 450 · 49→50 = 2450)
XP acumulado p/ atingir o nível N = 25 × N × (N−1)
```

| Atingir nível | XP acumulado |
|---|---|
| 5 | 500 |
| 10 | 2 250 |
| 20 | 9 500 |
| 30 | 21 750 |
| 50 | 61 250 |

**Ritmo esperado:** ~5–7 níveis por andar. Na prática, **nível ~20 ao fim do Andar 3**; os andares profundos levam o grupo a 50+ (onde entram os ganhos de +4 e +5 pontos de atributo por nível, §2). O Mestre ajusta o XP dos inimigos se o ritmo fugir disso (o tracker de XP do Painel do Mestre ajuda a acompanhar).

**Ao subir de nível:** ganhe os pontos de atributo da sua faixa (+3 níveis 1–20 · +4 níveis 21–50 · +5 níveis 51+) e ~2 PS. Recalcule HP/PM máximos.

### 14.3 Companheiros e Invocações

Várias skills e itens concedem aliados controlados pelos jogadores (Conjurar Servo, Invocar Familiar, Companheiro Fiel, Domador, Cetro Real Goblin). A regra-base e as opções de carta estão em **`DCC-Companheiros.md`**. Em resumo: o companheiro tem carta própria, rola Iniciativa e age no turno dele sob ordens do dono; cada jogador controla **1 permanente + invocações temporárias**; a 0 HP ele sai de combate (sem Teste de Morte) e volta após um Descanso.

---

## 15. Cartas físicas (dashboard do jogador)

Cinco tipos de carta, todos no mesmo layout-base, para o jogador montar o personagem na mesa.

**Item / Arma**
```
┌─────────────────────────────┐
│ PÉ DE CABRA ENFERRUJADO   ⚔ │  ← borda cinza (Comum)
│ Arma · Contundente · [FOR]  │
│ Dano:  2 / 5 / 9            │  ← Baixa / Média / Alta
│ Precisão +0                 │
│ "Crítico: aplica Atordoado."│
└─────────────────────────────┘
```

**Skill / Spell**
```
┌─────────────────────────────┐
│ INVESTIDA BRUTAL      Rank 3│
│ Skill Física · Recarga 2    │
│ Avance e ataque com +1 faixa│
│ ► R5: empurra + Atordoado   │
│ ► R10: atinge a linha toda  │
│ ► R15: derruba + Sangrando  │
└─────────────────────────────┘
```

**Condição**
```
┌─────────────────────────────┐
│ SANGRANDO (X)            🩸 │
│ X de dano no início do turno│
│ Dura: até teste de CON vs 10│
└─────────────────────────────┘
```

**Conquista**
```
┌─────────────────────────────┐
│ "PRIMEIRO SANGUE"         🏆│
│ Derrote o primeiro chefe.   │
│ Recompensa: +2 PS · título  │
│ Título: +1 Precisão vs chefes│
└─────────────────────────────┘
```

**Inimigo** (carta do Mestre)
```
┌─────────────────────────────┐
│ GOBLIN BATEDOR        Nv 2  │
│ HP 24 · Defesa 5 · Precisão 3│
│ Garra: 3 / 6 / 10 [DEX]     │
│ Loot: Caixa Comum (40%)     │
└─────────────────────────────┘
```

---

## 16. Personagem de exemplo (nível 1)

**Brincalhão, o Quebrador de Caixas** — guerreiro improvisado.

- **Atributos (15 pts):** FOR 6 · DEX 4 · CON 3 · INT 1 · CHA 1
- **HP:** 8 + (3×3) = **17**
- **Mana:** 1×3 = **3**
- **Defesa:** ⌊√4⌋ + couro (2) + broquel (1) = 2 + 2 + 1 = **5**
- **Iniciativa:** d20 + ⌊√4⌋ = d20 + 2
- **Arma:** Pé de Cabra [FOR], dano 2/5/9 → **Precisão = ⌊√6⌋ = +2**, **Multiplicador = 6÷5 = ×1,2**
- **Ataque contra goblin (Defesa 5):** rola 13 → 13 + 2 − 5 = 10 → faixa **Baixa** → 2 × 1,2 = **2 de dano**. Rolasse 16 → 13 → faixa **Média** → 5 × 1,2 = **6**. Nat 20 → Alta×2 → 9 × 1,2 × 2 = **21** + Atordoado.

---

## 17. CHEAT SHEET DO MESTRE *(para o escudo)*

### A rolagem (uma só)
**d20 + Precisão − Defesa do alvo**

| d20 final | Faixa |
|---|---|
| nat 1 | Falha crítica |
| ≤ 5 | Erro |
| 6–10 | **Baixa** |
| 11–17 | **Média** |
| 18–19 | **Alta** |
| 20+ / nat 20 | **Crítico** (Alta×2 + efeito) |

### Fórmulas
| | |
|---|---|
| **Precisão** | ⌊√atributo da arma⌋ + item |
| **Defesa** | ⌊√DEX⌋ + Armadura + Escudo |
| **HP máx** | 8 + (CON × 3) |
| **Mana** | INT × 3 |
| **Iniciativa** | d20 + ⌊√DEX⌋ |
| **Dano** | faixa × (atributo ÷ 5) |
| **Crítico** | faixa Alta × (atrib÷5) × 2 |
| **Teste de Morte** | d20 + ⌊√CON⌋ vs 10 |
| **Regeneração** | nível por turno (HP e PM) |
| **Desarmado** | 1/2/4 [maior FOR/DEX] + gear |
| **Improvisada** | 1/3/6 [FOR] |

### Tabela de raiz `⌊√x⌋`
| x | √ | x | √ | x | √ |
|---|---|---|---|---|---|
| 1–3 | 1 | 16–24 | 4 | 64–80 | 8 |
| 4–8 | 2 | 25–35 | 5 | 81–99 | 9 |
| 9–15 | 3 | 36–48 | 6 | 100–120 | 10 |

### Morte (a 0 HP → Caído)
Teste no início do turno · 3 sucessos = estável (1 HP) · 3 falhas = morto · Crítico recebido = morto · nat 20 = levanta com HP = CON.

### Condições rápidas
**Atordoado:** perde Ação · **Sangrando/Em Chamas/Envenenado (X):** X por turno · **Lento:** sem Movimento/Reação · **Marcado:** +3 contra ele · **Amaldiçoado:** sem críticos · **Fúria:** +1 Mult, −2 Def · **Abençoado:** rola 2× pega melhor · **Protegido (X):** −X por golpe · **Derrubado:** +2 corpo a corpo / −2 à distância contra ele · **Medo:** ataca com −2, não se aproxima · **Imobilizado:** sem Movimento, +2 contra ele · **Provocado:** deve atacar quem provocou (−2 nos outros) · **Oculto:** não pode ser alvo; bote/surpresa ao sair.

### Combate avançado (rápido)
**Distância:** adjacente (≤2 m) · perto ≤6 m (1 Movimento) · longe 12 m+ (teatro da mente). **+1 Movimento ≈ +3 m.**
**Ataque de oportunidade:** afastar-se do corpo a corpo dá ao inimigo 1 ataque grátis (faixa Baixa, gasta a Reação). Empurrão/teleporte não provocam.
**Surpresa:** lado não-notado age 1 rodada antes; surpreendidos não agem nem reagem.
**Empurrão/colisão:** bateu em parede/criatura = para + faixa Baixa nos dois.
**Cobertura:** +2 Defesa vs distância. **Flanco** (aliado no corpo a corpo): +1 na rolagem.
**Área:** 1 rolagem vs a Defesa de cada alvo (ou teste de resistência se a carta pedir). Cone ~6 m · linha ~12 m · explosão ~4 m.
**Defesa = Esquiva (⌊√DEX⌋) + Equipamento.** "Ignora armadura" = só esquiva conta · "não pode ser esquivado" = só equipamento conta · "ignora X de Defesa" = −X na total.
**Tipos de dano:** Resistência = metade · Vulnerabilidade = dobro · Imunidade = zero (só quando a carta diz).
**HP Temporário:** absorve antes do HP; não regenera, não acumula, some no fim do combate.
**Execução:** mata abaixo do limiar de HP; chefes são imunes (sofrem dano dobrado).
**Concentração:** 1 efeito sustentado por vez; tomou dano = ⌊√INT⌋ vs 10 ou perde.
**Janelas:** 1×/combate · /cena · /andar · /descanso · /sessão · "fora de combate".

### Progressão
**Atributos/nível:** +3 (1–20) · +4 (21–50) · +5 (51+) — criação: 15 pts, máx 6.
**PS:** ~2/nível + conquistas. **Skill ranks:** 1–5 = 1 PS · 6–10 = 2 PS · 11–15 = 4 PS · evoluções em 5/10/15.

### XP (individual · sem teto)
**XP do inimigo = Tier × Andar:** Lacaio 5 · Padrão 10 · Elite 25 · Chefe 80 (× nº do andar). Todos recebem; **golpe final = dobro.** Conquistas dão o XP da carta.
**Subir:** XP p/ próximo nível = **50 × nível**. Acumulado: nv5 = 500 · nv10 = 2 250 · nv20 = 9 500 · nv50 = 61 250. Ritmo ~6 níveis/andar (nv20 ≈ Andar 3).

### Audiência (PA) & Patrocínio
**Ganhar PA:** tirada/pose +1 · risco/criatividade +2 · morte espetacular/clutch +3 · momento da temporada +5. **+⌊√CHA⌋** por ganho · teto ~10/combate.
**Fama** (PA de carreira, nunca cai) define o patrocinador · **PA (saldo)** se gasta em skills/buffs.
**Patrocínio (Andar 3+):** 1 Caixa grátis/andar por Fama — 30:Prata · 60:Ouro · 100:Platina · 160:Lendária · 250:Divina. **Premium:** sem Sucata · +1 raridade · role 2× e escolha.

### Sala Segura & Descanso
Sem combate: abrir Caixas · organizar/reequipar · falar com o Guia · loja. **Descanso Diário (8h, obrigatório):** zera cooldowns de "descanso", remove exaustão/condições longas. **Cama** (upgrade) = descansa na hora.

### Raridade (cor da borda)
Cinza · Verde · Azul · Roxo · Laranja/Dourado · Branco iridescente

---

*Sistema Central v1.3 — documento vivo. Novidades v1.3: regras de XP (individual, golpe final = dobro, curva sem teto, ~6 níveis/andar) e Audiência/Patrocínio (Fama, patrocinadores a partir do Andar 3, Caixas de Patrocínio premium). v1.2: §6A Combate avançado e novas condições (Derrubado, Medo, Imobilizado, Provocado, Oculto). Materiais existentes: bestiário, falha crítica, tabela de loot, lista de itens (171), lista de skills (203), loadout, conquistas, companheiros, módulo do Andar 1, ficha do jogador e dashboard. Pendências organizadas em `DCC-Backlog.md`.*
