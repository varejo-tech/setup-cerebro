---
name: perfil
description: Aprofunda o seu perfil no cérebro — como você decide, o que te trava, quem são as pessoas que importam — para o agente trabalhar melhor com você. Use quando a pessoa disser "melhora meu perfil", "quero ajustar como você fala comigo", "atualiza meu USER.md", ou depois de já ter usado o cérebro por alguns dias. NÃO use durante o setup inicial.
---

# /perfil

Aprofunda o `USER.md` — o arquivo que diz ao agente quem é você e como trabalhar com você. O
`/setup-cerebro` só fez as perguntas rápidas do início; esta skill pergunta o que ficou faltando,
uma pergunta de cada vez, e só grava depois de te mostrar o texto.

## Antes de perguntar

Leia o `USER.md` e o `contexto/pessoas.md` de agora — para não perguntar de novo o que já está
registrado, e para saber o que já existe antes de propor qualquer mudança.

Confira também se o `CLAUDE.md` da raiz continua trazendo a linha `@USER.md`. É ela que faz o
`USER.md` entrar em toda conversa; sem ela, tudo que esta skill escrever ali fica guardado no
arquivo mas nunca chega ao agente. Se a linha tiver sumido, avise em uma frase e proponha
recolocá-la antes de seguir.

## As perguntas — uma de cada vez, no máximo seis

Faça as quatro perguntas abaixo, sempre uma por vez, esperando a resposta antes de fazer a
próxima. Só faça uma pergunta extra de acompanhamento se a resposta vier vaga demais para
escrever alguma coisa útil com ela — o limite duro da conversa inteira é seis.

1. **Como você decide.** "Quando você precisa decidir algo importante do seu negócio, como
   costuma ser? Você decide rápido, no instinto, ou prefere pensar com calma e ouvir mais gente
   antes?"
2. **O que trava.** "Tem alguma coisa que costuma te travar ou atrasar — enrolar pra decidir,
   começar e não terminar, ficar remoendo o mesmo assunto? Me conta o que costuma acontecer com
   você."
3. **As pessoas mais presentes.** "Quem são as pessoas mais presentes no seu dia a dia — da
   família, do negócio, de quem você mais depende — que vale eu sempre lembrar? Pode citar até
   três."
4. **O que destacar quando algo chega.** "Quando alguma coisa chega pra você — uma mensagem, um
   problema, uma ideia — o que você quer que eu avise primeiro? Hoje eu já destaco, nessa ordem:
   se tem dinheiro envolvido, qual o próximo passo, o que pode dar errado, e com o que aquilo se
   liga. Isso já serve do jeito que está, ou tem alguma coisa que você sempre quer saber na frente
   de tudo?"

Pare assim que der para escrever algo útil com a resposta — a pessoa está aprofundando o perfil,
não preenchendo formulário.

## Onde cada resposta vai

- **Pergunta 1 (decisão) e pergunta 2 (o que trava)** → um parágrafo curto novo na seção "Quem sou
  eu" do `USER.md`, contando como a pessoa é; e, quando a resposta sugerir uma ação concreta para
  o agente (por exemplo, "quando eu notar que você está enrolando, me avisa"), um item novo em
  "Como trabalhar comigo". Escreva a ação, não a teoria — "aponte quando eu estiver adiando uma
  decisão" ajuda mais do que "seja mais decidido".
- **Pergunta 3 (pessoas)** — o destino é pelo **conteúdo** da resposta, não pela pergunta inteira:
  a mesma resposta pode trazer duas coisas diferentes ao mesmo tempo.
  - **Quem a pessoa é, o que ela faz, o que vale lembrar dela** → `contexto/pessoas.md`, nunca o
    `USER.md`. Um bloco por pessoa, no formato que o arquivo já usa: o nome como subtítulo, uma ou
    duas frases sobre quem é e o que vale lembrar dela.
  - **Como o dono trabalha com ela** — o que delega, o que quer aprovar, a partir de que valor ou
    situação quer ser chamado → `USER.md`, em "Como trabalhar comigo", numa linha só com a regra
    (nunca com a descrição da pessoa).

  O teste, para cada trecho: *isto descreve a pessoa, ou descreve como o dono opera?* Exemplo
  real: "Tenho um gerente, o Marcelo, que cuida da reposição de estoque — decide sozinho, só
  confirma comigo pedido acima de R$ 5.000" se divide nos dois lados — o Marcelo (quem é, o que
  faz) vai para `contexto/pessoas.md`, e "só ser consultado em pedido de reposição acima de
  R$ 5.000" vira uma linha em "Como trabalhar comigo" — é o `USER.md` que carrega toda sessão, e é
  ali que o agente confere se escala algo ao dono ou resolve sozinho. Já "minha esposa cuida do
  financeiro", sem nenhuma regra de trabalho embutida, é só descrição: vai inteira para
  `contexto/pessoas.md`, e **nada** sobe para o `USER.md`. Não transforme isto em "toda resposta
  sobre pessoa alimenta os dois arquivos" — o que sobe para o `USER.md` é só a regra de trabalho,
  quando ela existir de verdade na resposta; nome, cargo e histórico da pessoa nunca incham o
  `USER.md`.

  A mesma divisão vale para qualquer pergunta, não só a 3: se a resposta sobre "o que trava"
  trouxer o nome de um fornecedor, o fato do fornecedor segue a "Fronteira" abaixo (vai pela
  `inbox/`, não para o perfil), e só a preferência de trabalho fica registrada aqui.
- **Pergunta 4 (destaque)** → ajusta a lista "O que destacar quando algo chega" do `USER.md`:
  reordena, acrescenta um item, ou confirma que a lista de hoje já serve. Só mexa se a resposta
  pedir mudança de verdade.

## Fronteira do que entra no `USER.md`

Só preferência, jeito de decidir e jeito de trabalhar. **Fato sobre fornecedor, cliente, projeto
ou data não entra aqui** — isso é conteúdo do cérebro, e tem caminho próprio. Se a pessoa contar
algo desse tipo no meio da conversa (um fornecedor, uma dívida, uma reunião), não escreva no
`USER.md`: diga a ela que isso vai pela `/salvar`, e sugira guardar assim.

## O bloco "Como falar comigo" é intocável

Não mexa nesse bloco por conta própria, mesmo que a conversa pareça sugerir um jeito diferente de
falar. Só edite se a pessoa pedir **explicitamente** para mudar o jeito de você falar com ela — e
mesmo assim, mostre o texto novo antes de gravar, como em qualquer outra mudança.

## O teto do `USER.md` — por que existe e o que fazer quando estourar

O `USER.md` carrega em toda conversa, com todo agente — cada trecho ali é custo fixo, cobrado de
novo a cada vez, mesmo nas conversas em que não faz diferença nenhuma. Por isso ele guarda só o
que o agente precisa saber **sempre**; o que ele só consulta **quando precisa** vai para
`contexto/`.

Depois de montar o texto novo inteiro do `USER.md`, veja se ele passaria de cerca de três mil
caracteres. Se passar, o excedente não é descartado — ele muda de casa:

- o que for sobre pessoa vai para `contexto/pessoas.md` (é para lá que já estava indo, pela regra
  acima);
- o resto — o detalhe mais longo, o exemplo, a explicação que só faz sentido de vez em quando —
  vai para o `contexto/geral.md` da área mais relacionada com aquela resposta (se a pessoa tiver
  mais de uma área, escolha a que a resposta mais se refere; pergunte se não estiver óbvio — essa
  pergunta é operacional, sobre onde guardar, e **não conta** no limite de seis perguntas da
  entrevista). Fica no `USER.md` só a frase-resumo.

Avise disso numa frase, junto da confirmação — diga o que ficou no `USER.md` e para onde foi o
excedente.

## Mostrar antes de gravar

O `USER.md` é da pessoa; a `/perfil` propõe, ela aprova. Antes de gravar qualquer arquivo —
`USER.md`, `contexto/pessoas.md` ou o `contexto/geral.md` de alguma área —, mostre o trecho exato
que vai entrar, já no lugar onde vai ficar, e espere o sinal de que está certo. Se ela pedir
ajuste, ajuste e mostre de novo antes de gravar. Nada é gravado antes disso.

## Depois de gravar

Confirme em uma frase o que mudou e onde — por exemplo: "Atualizei 'Como trabalhar comigo' no
USER.md e guardei o Miguel e a Andressa em contexto/pessoas.md." Se alguma coisa foi para
`contexto/geral.md` por causa do teto, diga isso também, na mesma frase.

## A primeira linha do `USER.md` não muda

O `USER.md` nunca leva frontmatter — a primeira linha continua sendo o título (`# <nome do
dono>`), nunca `---`. Se a edição tocou o topo do arquivo, confira que continua assim antes de
terminar.

## O que NÃO fazer

- Não reescreva o bloco "Como falar comigo" sem pedido explícito da pessoa.
- Não grave fato sobre fornecedor, cliente, projeto ou data no `USER.md` — isso é conteúdo de
  cérebro, vai pela `/salvar`.
- Não faça mais de seis perguntas na sessão.
- Não grave nada antes de mostrar o trecho e ouvir o OK.
- Não deixe o `USER.md` crescer acima do teto sem mover o excedente para `contexto/`.
