---
name: setup-cerebro
description: Cria um segundo cérebro completo em uma pasta vazia — estrutura, constituição, perfil do dono, skills e repositório privado no GitHub. Use quando a pessoa quiser montar seu segundo cérebro do zero, disser "criar meu segundo cérebro", "montar meu cérebro", "quero começar meu segundo cérebro" ou rodar /setup-cerebro. NÃO use se a pasta já tiver arquivos — um cérebro existente migra pela inbox, não por conversão.
---

# /setup-cerebro

Isso monta o segundo cérebro da pessoa do zero — pasta, constituição, perfil, repositório privado no GitHub e as primeiras skills — em cerca de 15 minutos, com só três perguntas pelo caminho.

**Regra que atravessa a skill inteira: cada etapa abaixo descreve o que precisa acontecer, nunca o comando exato para chegar lá.** Você conhece o sistema operacional e o shell desta máquina; a skill, não. Escolha você a ferramenta certa para cada verificação. Se um passo parecer pedir uma sequência de comandos encadeados, quebre em passos simples e rode um de cada vez — não monte uma combinação supondo que funciona em qualquer lugar.

## E0 — Pré-voo

Confira, nesta ordem, e **pare na primeira falha** — não siga para a etapa seguinte nem faça nenhuma pergunta da entrevista enquanto o pré-voo não passar inteiro.

1. **Git instalado.** Confirme que o Git está instalado nesta máquina e responde normalmente (peça a ele a própria versão, por exemplo). Se não responder, identifique o sistema operacional desta máquina, oriente a instalação pelo canal apropriado a ele — o instalador de git-scm.com serve para qualquer um dos três — e pare aqui. Só continue depois que o Git estiver respondendo de verdade.
2. **Pasta vazia.** Verifique se a pasta atual não tem nenhum arquivo nem subpasta, incluindo ocultos. Se houver qualquer coisa aí dentro, **pare** e responda, em prosa, exatamente isto — sem criar nada e sem fazer nenhuma pergunta:

   > Esta pasta já tem coisa dentro, e eu não escrevo por cima do que é seu.
   > Crie uma pasta nova e vazia para o cérebro, e me chame lá.
   > Se o que está aqui são notas antigas que você quer aproveitar: elas entram
   > depois, aos poucos, pela pasta `inbox/` do cérebro novo — assim eu leio cada
   > uma, organizo no lugar certo e nada seu é alterado.

3. **Sistema operacional.** Identifique se esta máquina é Windows, macOS ou Linux e guarde essa informação — etapas futuras desta skill (a instalação do Git acima, e mais adiante a instalação do `gh`) precisam se adaptar a ela, e é mais barato descobrir uma vez do que redescobrir a cada etapa.

Só avance para a entrevista (E1) depois que os três itens acima passarem.

## E1 — Entrevista

Três perguntas, **uma de cada vez** — só faça a próxima depois de ler a resposta da anterior. **Não faça nenhuma pergunta além destas três**: cada pergunta a mais custa minuto na régua dos 15 que este produto promete.

1. **"Como você quer que eu te chame?"** — guarde a resposta como `DONO`.
2. **"Em poucas linhas: o que você faz? Quais são as frentes do seu dia a dia?"** — guarde a resposta inteira, literal, como `RESPOSTA_PERGUNTA_2`. A partir dela, proponha de **2 a 5 áreas**, cada uma com um nome de exibição (o nome natural da frente, do jeito que se fala — pode ter acento e mais de uma palavra, ex.: "Família") e o slug correspondente (minúsculo, sem acento, sem espaço — troque espaço por hífen), e **mostre a lista para a pessoa confirmar antes de criar qualquer coisa**. Isso faz parte da pergunta 2, não é uma pergunta nova. Se a resposta não permitir inferir nenhuma frente, proponha "Trabalho" e "Pessoal" (slugs `trabalho` e `pessoal`). Guarde a lista final — já com os ajustes que a pessoa pedir — como `AREAS_SLUGS` (os slugs) e `AREAS_NOMES` (os nomes de exibição correspondentes, na mesma ordem).
3. **"Prefere que eu te trate por *você* ou por *senhor*?"** — guarde a resposta como `TRATAMENTO`.

Com as três respostas em mãos e a lista de áreas confirmada, siga para E2.

## E2 — Estrutura

Os modelos vêm junto desta skill, na subpasta `modelos/` (sufixo `.modelo` em cada arquivo). Para cada um, copie o conteúdo para o destino indicado, sem o sufixo, substituindo os marcadores pelo valor correspondente:

- `{{DONO}}` → a resposta da pergunta 1.
- `{{RESPOSTA_PERGUNTA_2}}` → a resposta da pergunta 2, literal, sem resumir nem reescrever.
- `{{TRATAMENTO}}` → a resposta da pergunta 3.
- `{{DATA}}` → a data de hoje, no formato `DD/MM/AAAA`.
- `{{AREA_NOME}}` → o nome de exibição de uma área específica, o que está guardado em `AREAS_NOMES` para aquela área — **nunca** o slug capitalizado: se a pessoa chamou a área de "Família", o nome de exibição leva o acento (`Família`), mesmo que a pasta dela (`areas/familia/`) não leve. Usado uma vez por área, nos dois modelos de área.
- `{{AREAS}}` → aparece em dois arquivos, com formato diferente em cada um, mas sempre usando o nome de exibição de `AREAS_NOMES`, nunca o slug:
  - em `CLAUDE.md`: os nomes de exibição de todas as áreas, em prosa, separados por vírgula e com "e" antes do último (ex.: "Loja, Família e Financeiro");
  - em `MAPA.md`: uma lista markdown, um item por área, o nome de exibição como texto do link e o slug no caminho (ex.: `- [Família](areas/familia/MAPA.md)`).

Arquivos únicos (uma cópia cada):

| Modelo | Destino |
|---|---|
| `CLAUDE.md.modelo` | `CLAUDE.md` |
| `USER.md.modelo` | `USER.md` |
| `MAPA.md.modelo` | `MAPA.md` |
| `README.md.modelo` | `README.md` |
| `gitignore.modelo` | `.gitignore` |
| `inbox-index.md.modelo` | `inbox/_index.md` |
| `contexto-decisions.md.modelo` | `contexto/decisions.md` |
| `contexto-lessons.md.modelo` | `contexto/lessons.md` |
| `contexto-pessoas.md.modelo` | `contexto/pessoas.md` |

Arquivos por área (repita para cada slug confirmado em `AREAS_SLUGS`):

| Modelo | Destino |
|---|---|
| `area-MAPA.md.modelo` | `areas/<slug>/MAPA.md` |
| `area-geral.md.modelo` | `areas/<slug>/contexto/geral.md` |

Além desses arquivos, garanta que existam:

- `inbox/<slug-do-dono>/` — vazia; a caixa de entrada pessoal da pessoa. O slug do dono segue a mesma regra das áreas (minúsculo, sem acento, sem espaço).
- `arquivo/`, com um `.gitkeep` dentro — vazia por enquanto, mas precisa existir e sobreviver ao primeiro commit; pasta sem nenhum arquivo dentro não entra no Git.
- `.claude/skills/` — vazia por enquanto; as skills do cérebro chegam aqui numa etapa futura desta mesma skill.

**Não crie** `projetos/`, `tarefas/` nem `clientes/` dentro de nenhuma área, e não crie uma pasta `sistema/` na raiz — essas nascem quando o primeiro item de cada tipo chegar (no caso de `sistema/`, na Etapa 2 deste produto, que é outra skill).

## E3 — Verificação

Este é um **gate**, não um relatório: enquanto sobrar algo, você não segue nem comenta com a pessoa.

Antes de seguir, confira se sobrou algum marcador no formato `{{ALGUMA_COISA}}` em qualquer arquivo que você acabou de criar. Use a ferramenta de busca que preferir nesta máquina.

Se encontrar algum, corrija o arquivo e confira de novo. **Não avance nem comente com a pessoa enquanto sobrar um.** Só siga quando a busca vier vazia.

## E4 — GitHub

Com o E3 limpo, esta etapa transforma a pasta local num repositório git e publica um repositório privado no GitHub — é o que faz o cérebro sair da máquina da pessoa.

### E4.1 — Garantir o `gh`

Confira se a ferramenta de linha de comando do GitHub (`gh`) está instalada nesta máquina. Se não estiver, instale usando o gerenciador de pacotes que existir aqui e confirme que passou a funcionar antes de seguir.

Se a instalação falhar, leia o erro e tente outro caminho disponível. Só se nenhum funcionar, pare e mostre à pessoa o endereço do instalador manual — explicando em uma frase o que ela precisa fazer.

### E4.2 — Autenticar

Verifique se a pessoa já está conectada à conta do GitHub. Se ela contar que não tem conta nenhuma, oriente-a a criar uma de graça em github.com/signup — é rápido, leva poucos minutos — e espere ela voltar antes de seguir; não tente criar a conta por ela. Com a conta em mãos (nova ou já existente) e sem estar conectada ainda, avise antes de rodar qualquer coisa:

> "Agora você precisa entrar na sua conta do GitHub. Vai aparecer um código aqui na tela e o navegador vai abrir. Cole o código lá, autorize, e me avise quando terminar."

Inicie a autenticação pelo navegador e **espere a confirmação dela**. Não tente contornar nem siga adiante sem resposta. Se ela disser que não conseguiu, ofereça o caminho por token pessoal e explique onde gerar.

### E4.3 — Versionar o cérebro

Transforme a pasta em um repositório git com a branch principal chamada `main`, adicione tudo que existe e faça o primeiro registro com a mensagem "cerebro: estrutura inicial".

Se a pasta já for um repositório git — sinal de uma tentativa anterior que não chegou ao fim —, não recomece do zero: confira o que já está feito (a branch, o que já foi adicionado ou commitado) e continue dali, sem duplicar o que já aconteceu.

### E4.4 — Criar o repositório privado e publicar

Proponha à pessoa o nome do repositório: o **slug do dono que você já calculou no E2** — o mesmo usado em `inbox/<slug-do-dono>/` — seguido de `-cerebro`. Nunca use o nome literal da pergunta 1 para isso: ele pode ter espaço e acento, e o GitHub não aceita isso em nome de repositório. Essa proposta é confirmada com a pessoa em uma linha — não é uma quarta pergunta da entrevista, é a confirmação de um valor que você já derivou.

**Só crie o repositório depois que a pessoa confirmar o nome.** Enquanto ela não responder, não crie nada no GitHub — criar antes é uma ação externa feita sem consentimento.

Se o nome confirmado já existir na conta dela (por exemplo, de uma tentativa anterior que não terminou), avise e proponha outro nome, em vez de falhar.

Com o nome confirmado, crie no GitHub um repositório **privado**, ligue a pasta a ele e envie tudo.

Depois de enviar, **consulte o GitHub para confirmar que o repositório está mesmo privado** — não confie no comando que você rodou, leia o estado real. Se por qualquer motivo ele estiver público, **torne-o privado imediatamente** — é isso que tira o conteúdo do ar, e você consegue fazer isso sem pedir nenhuma permissão nova. Se essa correção falhar por qualquer razão, **pare na hora** e avise a pessoa, em linguagem simples, que o cérebro dela ficou visível publicamente, que ela mesma precisa entrar na conta do GitHub e trocar o repositório para privado (ou apagá-lo), e explique em uma frase onde essa opção fica. Não siga para nenhuma etapa seguinte enquanto isso não estiver resolvido.

## E5 — Skills do dia a dia

Com o repositório no ar, instale as três skills que fazem o cérebro ser usado no dia a dia, não só
guardado. Esta skill trouxe as três junto de si, em `skills/salvar/`, `skills/ingestao/` e
`skills/perfil/` — copie o conteúdo de cada `SKILL.md` para o destino indicado.

1. **`/salvar` é global.** Copie para `~/.claude/skills/salvar/SKILL.md` — a pasta de skills
   globais desta máquina, a mesma de onde qualquer skill roda não importa em que projeto a pessoa
   esteja. É a única das três que precisa de ajuste: ela carrega o marcador `{{CEREBRO_PATH}}`,
   e você substitui pelo caminho absoluto do cérebro que acabou de criar. É global porque captura
   tem que funcionar de onde a pessoa estiver, não só de dentro do cérebro.

   **Nunca copie esta skill para dentro do cérebro.** Se `/salvar` for parar também em
   `<cerebro>/.claude/skills/`, o `{{CEREBRO_PATH}}` daquela cópia fica cru — ninguém vai
   substituí-lo ali —, e o cérebro passa a carregar um placeholder que o gate do E3 já devia ter
   eliminado antes mesmo do repositório existir.

2. **`/ingestao` e `/perfil` são do cérebro.** Copie, sem alterar nada, para
   `<cerebro>/.claude/skills/ingestao/SKILL.md` e `<cerebro>/.claude/skills/perfil/SKILL.md` —
   nenhuma das duas tem marcador para substituir. Elas só fazem sentido lendo o `CLAUDE.md`, o
   `USER.md` e a `inbox/` deste cérebro específico, e por isso viajam versionadas com o
   repositório: quando a pessoa clonar em outra máquina, já chegam prontas, sem precisar reinstalar
   nada.

**Verificação, antes de seguir para o E6:** o `{{CEREBRO_PATH}}` que você acabou de preencher é o
único marcador de toda a skill que sobrevive ao gate do E3 — ele nem existia até agora. Confira,
nas três skills que você acabou de instalar (a global e as duas dentro do cérebro), se sobrou
algum marcador no formato `{{ALGUMA_COISA}}` em qualquer uma delas. Se encontrar algum, corrija e
confira de novo. Só siga para o E6 quando a busca vier vazia.

Com a verificação limpa, registre `/ingestao` e `/perfil` no controle de versão do cérebro, num
commit próprio (a `/salvar`, por ser global, fica de fora — ela não mora dentro do repositório).
Não deixe essas duas skills penduradas sem commit até o E6: se a sessão parar entre agora e o OK
que o E6 pede, elas ficam presas só nesta máquina, sem nenhum sinal de que falta enviá-las.

## E6 — Primeiro ciclo ao vivo

O setup não termina no repositório publicado — termina com a pessoa vendo o ciclo inteiro
funcionar, uma vez, com material dela de verdade. Um cérebro que nasce sem nenhuma escrita nasce
com o hábito já morto.

1. Diga, em uma frase, que vai usar a resposta que ela deu na pergunta 2 da entrevista (o que ela
   faz, guardada como `RESPOSTA_PERGUNTA_2`) para mostrar o cérebro funcionando de ponta a ponta.
2. Rode a `/salvar` que você acabou de instalar, com aquele conteúdo exatamente como a pessoa
   escreveu — sem resumir, sem reescrever.
3. Mostre a ela o arquivo que apareceu dentro da `inbox/` — o caminho que a própria `/salvar`
   confirmou ao gravar.
4. Rode a `/ingestao`. Ela vai ler o item, apresentar o resumo em prosa e esperar o OK da pessoa
   antes de gravar qualquer coisa — este é o portão da `/ingestao`, espere a resposta de verdade,
   não presuma o OK para ir mais rápido.
5. Depois do OK e da gravação, mostre a nota no destino final onde a `/ingestao` a colocou, com o
   caminho completo dela.
6. Leve essa gravação para o controle de versão e envie ao repositório remoto que você publicou no
   E4 — é isso que tira também esta primeira nota da máquina da pessoa.
7. Feche com exatamente três linhas, nada além disso: o endereço do repositório que você publicou
   no E4; que `/salvar` guarda qualquer coisa em segundos, de qualquer pasta; que `/ingestao`
   organiza o que se acumulou ali. Sem lista de próximos passos, sem tour pelo que mais o cérebro
   faz — cada linha a mais aqui é uma linha que a pessoa não vai ler.
