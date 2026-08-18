---
name: ingestao
description: Lê tudo que está parado na inbox do cérebro, mostra um resumo do que entendeu e, depois do seu OK, organiza cada coisa no lugar certo e manda para o GitHub. Use quando a pessoa disser "organiza minha inbox", "processa o que eu salvei", "esvazia a inbox", ou quiser trazer notas antigas para o cérebro. NÃO use para gravar algo novo (isso é /salvar).
---

# /ingestao

Esvazia a caixa de entrada de verdade: lê o lote inteiro, resume em prosa o que entendeu, espera
o OK, grava cada item no lugar certo e manda tudo para o GitHub. Cinco fases, nesta ordem —
nenhuma pula a anterior.

## Fase 1 — Ler o lote inteiro

**Comece trazendo para esta máquina o que está no GitHub.** A caixa de entrada não recebe só o que
foi salvo neste computador: se a pessoa tiver um agente rodando em outro lugar — num servidor,
atendendo pelo celular —, ele deposita direto no repositório, e o que ele guardou desde a última
vez só aparece aqui depois que você o trouxer. Sem isso a ingestão trabalha com um lote incompleto
**e sem nenhum aviso**, e o envio da Fase 5 acaba recusado no fim, porque o repositório andou para
a frente enquanto esta máquina ficou parada.

Se não der para trazer — sem internet, acesso à conta expirado, qualquer outro motivo —, **pare e
diga o motivo em uma linha**, em linguagem simples, sem processar nada. Seguir com o que está no
disco faz a pessoa fechar a ingestão achando que a caixa está vazia, enquanto o que o agente dela
depositou continua lá, invisível.

Com isso feito, abra e leia **tudo** que está pendente — qualquer arquivo dentro de `inbox/`,
solto na raiz da pasta ou dentro de qualquer subpasta:

- os itens dentro de `inbox/<dono>/` — o que caiu ali pelo `/salvar`;
- os itens dentro de qualquer outra subpasta — é onde deposita um agente que roda fora deste
  computador, numa subpasta com o nome dele;
- qualquer arquivo solto direto na raiz de `inbox/`, **inclusive `.md` que a pessoa tenha
  copiado de um cérebro antigo dela** — mesmo que venha num formato diferente deste (sem
  frontmatter, com `[[wikilinks]]`, cabeçalhos ou convenções próprias). Trate como material bruto
  e leia do mesmo jeito.
- `inbox/_index.md` **não é item a processar** — é o índice da própria caixa; fica onde está,
  do jeito que está.

Leia o lote inteiro antes de propor destino para qualquer um deles — um item isolado às vezes só
faz sentido ao lado de outro que chegou junto, e decidir cedo demais perde essa ligação.

## Fase 2 — Resumir em prosa (o portão)

Depois de ler tudo, escreva um resumo em prosa — não uma lista técnica de comandos — do que você
entendeu, item por item: do que se trata, para onde você propõe mandar, que tipo de nota vira,
com o que no cérebro isso se liga. Diga também, quando for o caso, qual pessoa ou empresa vai
ganhar pasta própria por causa deste lote (Decisão 2 da Fase 3) — e deixe claro que isso não muda
a pasta de nenhum item. Se um item não tiver dono claro — não dá para saber a área, ou é ambíguo
demais para decidir sozinho —, diga isso também, e proponha deixá-lo onde está.

**Nada é gravado antes do OK da pessoa.** Este resumo é o portão da skill inteira. Espere a
resposta. Se ela pedir ajuste no destino de algum item, ajuste o plano e só depois grave.

## Fase 3 — Gravar

Só depois do OK, item por item. Em cada item existem **duas decisões separadas**, que se
respondem uma de cada vez e nunca disputam entre si:

- **Decisão 1 — em que pasta este item vai.** Sai da ordem de precedência abaixo, e só dela.
- **Decisão 2 — a pessoa ou empresa citada no item ganha pasta própria.** Se resolve depois, à
  parte, e vale para qualquer item que cite um nome próprio.

**A Decisão 2 nunca muda o resultado da Decisão 1.** Criar a pasta de uma entidade não move o
item para dentro dela: o item fica onde a Decisão 1 mandou. As duas se encontram num lugar só —
no campo `relacionado:` do frontmatter do item, que aponta para o arquivo da entidade.

### Decisão 1 — em que pasta este item vai

- **Comece pela regra de destino do `CLAUDE.md` deste cérebro** (seção "Regra de destino"):
  evento de uma das áreas vai para `areas/<área>/`; conhecimento vindo de fora (artigo, vídeo,
  curso) vai para a área de estudo, se houver, senão a mais parecida; decisão que atravessa mais
  de uma área vai para `contexto/decisions.md`; lição aprendida vai para `contexto/lessons.md`;
  pessoa importante vai para `contexto/pessoas.md`; **sem dono claro fica na inbox** — não force
  um destino só para não deixar nada pendente.
- **Dentro de uma área, a subpasta certa segue uma ordem — pare no primeiro nível que servir,
  mesmo que outro também pareça se aplicar:**
  1. **Tem alguma coisa para fazer? Teste assim, não no chute:** tente escrever o próximo passo
     em uma frase começando por um verbo, dizendo o que a pessoa precisa fazer — e que ainda não
     foi feito. Se você consegue escrever essa frase e é a própria pessoa quem executa, **é
     tarefa** → `areas/<área>/tarefas/`. "Decidir se aceita o reajuste até dia 15" é uma frase
     dessas — decidir é fazer.

     **Também conta como algo a fazer, mesmo sem verbo escrito no texto do item:**
     - problema, defeito ou coisa quebrada que ninguém resolveu ainda;
     - reclamação que ficou sem resposta;
     - prazo, vencimento ou data se aproximando com decisão pendente — **um contrato, um
       boleto ou uma assinatura com data de vencimento citada conta sempre, por mais longe que
       a data pareça estar**, e a decisão pendente é a de renovar, pagar, aceitar ou deixar
       vencer, mesmo que o item não diga isso com essas palavras.

     Nesses três casos, escreva você mesmo o próximo passo com a ação óbvia de resolver — não
     precisa estar escrita no item para existir. "A balança do açougue está desregulada" vira
     "Chamar o técnico para regular a balança do açougue"; "cliente reclamou do atendimento no
     caixa 3 na sexta" vira "Apurar a reclamação do caixa 3 de sexta e responder ao cliente".

     **Não é tarefa** quando o item registra uma coisa que aconteceu e se encerrou, sem sobrar
     nada pendente — como uma reunião que já ocorreu e não gerou compromisso, ou um material que
     chegou e ficou disponível (uma tabela de preços, um catálogo, um comunicado) sem que a fonte
     diga que alguém precisa responder ou decidir algo por causa dele. **O que decide é o que o
     item diz, não o que ele poderia estar escondendo:** um item que só nomeia um encontro, um
     assunto ou um contato, sem dizer o que ficou pendente para a pessoa, é registro — mesmo que
     não dê para saber se aquilo já aconteceu ou ainda vai acontecer. Não é o tempo do verbo que
     decide; é o item apontar, ou não, alguma coisa pendente.

     **Na dúvida entre tarefa e registro, escolha tarefa.** Uma tarefa que não era tarefa
     aparece na lista e a pessoa descarta em dois segundos; um registro que era tarefa
     desaparece, e ela só descobre quando o prazo já passou — o custo de errar não é o mesmo
     dos dois lados.

     Escreva a frase que você formou no campo `proximo_passo` do frontmatter da nota; se depois
     de tentar tudo isso você ainda não conseguiu formar nenhuma frase, é sinal de que o item
     não é tarefa, e você segue para o passo 2. **Vale mesmo que a ação envolva um cliente ou
     fornecedor com nome próprio: sendo tarefa, a nota fica em `tarefas/` e o nome dele entra só
     no `relacionado:` do frontmatter.** O que fazer com a entidade em si é a Decisão 2, logo
     abaixo, e ela não mexe nesta pasta. Uma tarefa guardada dentro da pasta de um fornecedor
     deixa de ser fácil de achar, e tarefa só serve enquanto for fácil de achar.
  2. **Não tem ação, mas o item é sobre uma pessoa ou empresa de fora com nome próprio?** →
     `areas/<área>/clientes/<nome>/`. **Só conta nome próprio de verdade** — razão social, nome
     fantasia ou o nome da pessoa (ex.: "Distribuidora Rio Doce", "Fazenda Santa Luzia", "Seu
     Adão"). Descrição genérica não serve aqui ("o fornecedor de bebidas", "o distribuidor de
     refrigerante", "aquele fornecedor"): sem nome próprio, o item segue para o passo 3.
     Isso vale inclusive para o que pareceria "frente contínua" do passo 3: se a frente tem
     nome próprio de parceiro externo, o passo 2 pega antes do 3.
  3. **Não tem nem ação nem entidade nomeada, mas é o andamento de uma frente que continua ao
     longo do tempo?** → `areas/<área>/projetos/`. **Frente contínua não se adivinha pelo
     assunto — ela se comprova de uma destas duas maneiras:** já existe em `projetos/` uma nota
     sobre essa mesma frente, ou o próprio item se apresenta como continuação de algo que começou
     antes (fala em andamento, em etapa, em resultado parcial, em "continuando"). Se nenhuma das
     duas se verifica, o item é registro isolado e desce para o passo 4 — mesmo que o assunto
     pareça daqueles que voltam sempre (preço de fornecedor, layout da loja, reforma). Uma
     reunião única sobre um assunto recorrente é evento isolado, não frente: tratá-la como
     projeto inventa um andamento que ninguém começou.
  4. **Nenhum dos três** → solto dentro de `areas/<área>/`.

  Crie a subpasta na primeira vez que precisar dela — é assim que o `MAPA.md` da área já avisa
  que elas nascem.

### Decisão 2 — a pessoa ou empresa citada ganha pasta própria

Esta decisão é sobre a **entidade**, não sobre o item. Responda-a para todo item que cite uma
pessoa ou empresa de fora com **nome próprio** — razão social, nome fantasia ou nome de pessoa —,
**não importa onde o item caiu na Decisão 1**: tarefa, projeto, evento solto ou nota já dentro de
`clientes/`, a regra é a mesma.

- **A entidade ainda não tem pasta?** Crie `areas/<área>/clientes/<nome-em-minúsculo-com-hífen>/`
  e, dentro dela, um arquivo com o nome da entidade escrito por extenso (ex.: `Distribuidora Rio
  Doce.md`), com frontmatter (`tipo: cliente`, mais `area`, `tags`, `status`, `data`) e três
  informações no corpo: quem é, o que fornece ou compra, e o que importa lembrar dela. Preencha
  com o que der para inferir do item; o que não souber, diga que não sabe em vez de inventar.
  Sem esse arquivo, a pasta vira uma pilha de eventos soltos sem ninguém dizer de quem eles são.
- **A entidade já tem pasta?** Não crie nada de novo — nem uma segunda pasta, nem um segundo
  arquivo, nem uma variação do nome. Antes de criar qualquer coisa, procure a entidade entre as
  pastas de `clientes/` que já existem: nome quase igual é a mesma entidade ("Rio Doce" e
  "Distribuidora Rio Doce" são uma empresa só, com um arquivo só). Se o item trouxer informação
  nova sobre ela, acrescente ao arquivo que já existe, em vez de abrir outro.
- **Criar a pasta da entidade não move o item.** O item continua exatamente onde a Decisão 1 o
  colocou. O vínculo entre os dois é o `relacionado:` do frontmatter do item, apontando para o
  caminho do arquivo da entidade — e nada mais.
- **Descrição genérica não é nome próprio e não cria nada** ("o fornecedor de bebidas", "aquele
  distribuidor"): sem nome, não há entidade para abrir. O motivo: duas descrições diferentes da
  mesma empresa criariam duas pastas sem vínculo entre si, e o arquivo que existe para juntar
  tudo sobre ela se fragmenta. Se o nome próprio aparecer numa entrada futura, a pasta nasce
  naquele momento — e, mesmo então, as notas antigas continuam onde estão; nada é remanejado
  por causa disso.

### Como escrever a nota

- **Escreva o frontmatter da nota nova** com os campos que o `CLAUDE.md` deste cérebro define:
  `tipo`, `area`, `tags`, `status`, `data`, e `relacionado` quando a nota se ligar a alguma outra
  que já existe no acervo — inclusive o arquivo da entidade que a Decisão 2 criou ou encontrou.
  Toda nota com `tipo: tarefa` leva também `proximo_passo` — a frase com verbo que o teste do
  passo 1 da precedência produziu.
- **Nunca ponha frontmatter em índice ou configuração — sem exceção**, mesmo que o conteúdo do
  item pareça pedir isso: `MAPA.md`, `_index.md`, `CLAUDE.md`, `README.md`, `USER.md`, o
  quarteto `contexto/decisions.md`, `contexto/lessons.md`, `contexto/pessoas.md` — e também o
  `contexto/geral.md` de cada área: ele mora dentro de `areas/`, mas é texto corrido que só
  cresce, igual aos da raiz, e por isso nunca leva cabeçalho. Quando o
  destino de um item for um desses arquivos — uma decisão, uma lição, uma pessoa —, ele vira um
  bloco de texto **acrescentado** ao arquivo, no formato que ele já usa (veja o topo de cada um
  para o modelo do bloco); nunca um arquivo novo com cabeçalho próprio.
- **Decisão nova que derruba uma antiga: volte e marque a antiga.** É a única vez em que se mexe
  em texto já escrito no `contexto/decisions.md`, e só na linha do status dela. Antes de
  acrescentar uma decisão, leia as que já estão ali: se a nova desfaz alguma, troque o status da
  antiga por `⛔ REVOGADA em DD/MM por [a decisão nova]`, seguido de uma frase dizendo o que vale
  hoje. **Não apague nem reescreva o resto do bloco dela.** Sem isso a decisão velha continua
  dizendo "ativa" para sempre, e quem ler primeiro vai seguir a regra errada — ninguém lê o
  arquivo inteiro antes de agir. O formato completo está no topo do próprio `decisions.md`.
- **Item vindo de transcrição de reunião ou conversa não vira tarefa de alguém automaticamente.**
  Ferramentas de transcrição atribuem responsável sozinhas, e erram. Registre como "ponto
  levantado" dentro da nota, em prosa — nunca como compromisso assumido.
- **Preserve o literal** do que veio na fonte — número, valor, nome, data — do mesmo jeito que o
  `/salvar` já preserva. Não interprete, não arredonde, não troque "talvez" por "vai".
- **Nomeie o arquivo novo** como `AAAA-MM-DD-<slug-curto>.md` — minúsculo, sem acento, hífen no
  lugar de espaço. A data é a **do que aconteceu** (a data do fato, da reunião, do evento
  relatado no item), não a data em que você está processando a inbox; se não der para saber a
  data do fato, use a de hoje.

## Fase 4 — Drenar

- Depois de gravar a nota no acervo, mova o arquivo bruto correspondente para `arquivo/`, com a
  data incorporada ao nome, para não colidir com outro arquivo do mesmo nome ali dentro. Se o
  nome já começar com a data — é o caso de tudo que a `/salvar` gera —, ele já cumpre isso:
  **não carimbe a data de novo**. Se mesmo assim o nome já existir em `arquivo/`, acrescente um
  sufixo numérico — o mesmo recurso
  que o `/salvar` já usa quando duas capturas do mesmo dia colidem. Mencione na nota nova, em uma
  linha, onde o bruto foi parar — assim dá para rastrear a origem depois.
- Item que ficou na `inbox/` por falta de dono claro **não é movido** — continua exatamente onde
  estava, esperando alguém decidir.
- Se você criou uma pasta que não existia (uma subpasta `projetos/`, `tarefas/` ou `clientes/`
  dentro de uma área, a pasta de uma entidade dentro de `clientes/`, ou qualquer outra), atualize
  o `MAPA.md` daquele nível para apontar para ela — sem isso o mapa fica desatualizado e ninguém
  acha o que acabou de ser guardado.

## Fase 5 — Registrar e enviar

A primeira lei deste cérebro é que o **GitHub é a fonte da verdade**. Uma nota que existe só no
disco desta máquina ainda não está guardada: some com o computador, não aparece em outro
aparelho, e o repositório congela no dia em que o cérebro foi criado. É esta skill que fecha esse
ciclo — a `/salvar` só deposita na caixa de entrada, e ninguém mais faz isso depois.

Por isso, **depois de tudo gravado e drenado**, e sem perguntar nada à pessoa (ela já deu o OK do
conteúdo na Fase 2 — este passo é consequência daquele, não uma decisão nova):

1. **Acrescente uma linha ao `log.md`** — o diário do cérebro, na raiz. Vai **no fim do arquivo**,
   embaixo de tudo, sem apagar nem reescrever nada do que já está lá:

   ```
   ## [AAAA-MM-DD] resumo de uma linha do que entrou
   Onde foi parar: as áreas e pastas que receberam alguma coisa
   ```

   A data é a de hoje — a data em que a ingestão rodou, não a dos fatos que entraram (essa já está
   dentro de cada nota). O resumo é uma linha só, em português, do mesmo teor da descrição do
   registro do passo seguinte.

   **Por que isso importa e não é burocracia:** a nota guarda a data **do fato**, e um fato de hoje
   muitas vezes vai parar numa nota criada semanas atrás. Quando isso acontece, procurar pela data
   de hoje não acha nada — e o lote inteiro fica invisível para qualquer pergunta de tempo ("o que
   entrou essa semana?"). Esta linha é o único lugar do cérebro que responde isso.

   Se o `log.md` não existir — cérebro montado antes de ele passar a existir —, crie o arquivo com
   um título na primeira linha (`# Diário do cérebro`) e comece a partir daí, sem tentar recuperar
   o histórico antigo.
2. Registre no controle de versão do cérebro **tudo que mudou nesta ingestão** — as notas novas,
   as pastas e arquivos de entidade criados, os `MAPA.md` atualizados, a linha nova do `log.md` e
   os brutos que foram para `arquivo/`. A descrição do registro diz, em uma linha e em português,
   o que entrou (por exemplo: "ingestao: 3 itens — fornecedor Rio Doce, reclamação do caixa 3,
   reforma do estacionamento").
3. Envie esse registro ao repositório do cérebro no GitHub.
4. Confirme em uma linha, junto do resumo final, que o que foi gravado já está no GitHub.

**Se o envio não funcionar** — sem internet, acesso à conta expirado, qualquer outro motivo —
**não desfaça nada e não repita a gravação**: o trabalho está salvo no computador e não se perde.
Diga à pessoa, sem jargão, o que aconteceu e o que ficou pendente. Algo como: *"Organizei tudo e
salvei aqui no seu computador, mas não consegui mandar para o GitHub agora — [o motivo, em
linguagem simples]. Está tudo guardado; quando você quiser, é só me pedir para enviar de novo."*
Se der para identificar a causa provável (internet caída, precisa entrar na conta do GitHub de
novo), diga qual é e o que ela pode fazer a respeito — em uma frase, sem passo a passo técnico.

Se este cérebro nem tiver um repositório no GitHub ligado a ele — coisa que o setup deixa pronta,
mas que pode não existir num cérebro montado à mão —, registre mesmo assim no controle de versão
local e avise, em uma linha, que falta ligar o cérebro ao GitHub para que ele saia desta máquina.

## O que NÃO fazer

- Não grave nada antes do OK da Fase 2 — nem os itens "óbvios".
- Não termine a ingestão sem tentar enviar ao GitHub (Fase 5) — e não esconda a falha, se ela
  acontecer.
- Não termine a ingestão sem a linha no `log.md` — um lote sem linha no diário some de qualquer
  pergunta de data.
- Não acrescente decisão nova sem olhar se ela derruba alguma antiga — e, se derrubar, não deixe a
  antiga marcada como ativa.
- Não mova uma tarefa para a pasta de um cliente só porque ela cita o nome dele — as duas decisões
  da Fase 3 são independentes, e a pasta do item sai só da Decisão 1.
- Não crie uma segunda pasta para uma entidade que já tem a sua, nem com o nome escrito de outro
  jeito.
- Não ponha frontmatter em `MAPA.md`, `_index.md`, `CLAUDE.md`, `README.md`, `USER.md`, em
  qualquer arquivo do quarteto de `contexto/` na raiz, nem no `contexto/geral.md` de uma área.
- Não decida um destino forçado para item sem dono claro — deixe-o na inbox e diga isso no
  resumo da Fase 2.
- Não use esta skill para gravar algo novo que a pessoa acabou de dizer agora — isso é
  `/salvar`; esta skill organiza o que já está parado na caixa de entrada.
