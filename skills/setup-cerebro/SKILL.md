---
name: setup-cerebro
description: Cria um segundo cérebro completo em uma pasta vazia — estrutura, constituição, perfil do dono, skills e repositório privado no GitHub. Use quando a pessoa quiser montar seu segundo cérebro do zero, disser "criar meu segundo cérebro", "montar meu cérebro", "quero começar meu segundo cérebro" ou rodar /setup-cerebro. Serve também para retomar um setup que parou no meio, na mesma pasta. NÃO use se a pasta tiver arquivos que não sejam de uma tentativa anterior deste próprio setup — um cérebro existente migra pela inbox, não por conversão.
---

# /setup-cerebro

Isso monta o segundo cérebro da pessoa do zero — pasta, constituição, perfil, repositório privado no GitHub e as primeiras skills — em cerca de 15 minutos, com só três perguntas pelo caminho.

**Regra que atravessa a skill inteira: cada etapa abaixo descreve o que precisa acontecer, nunca o comando exato para chegar lá.** Você conhece o sistema operacional e o shell desta máquina; a skill, não. Escolha você a ferramenta certa para cada verificação. Se um passo parecer pedir uma sequência de comandos encadeados, quebre em passos simples e rode um de cada vez — não monte uma combinação supondo que funciona em qualquer lugar.

## E0 — Pré-voo

Confira, nesta ordem, e **pare na primeira falha** — não siga para a etapa seguinte nem faça nenhuma pergunta da entrevista enquanto o pré-voo não passar inteiro.

1. **Git instalado.** Confirme que o Git está instalado nesta máquina e responde normalmente (peça a ele a própria versão, por exemplo). Se não responder, identifique o sistema operacional desta máquina, oriente a instalação pelo canal apropriado a ele — o instalador de git-scm.com serve para qualquer um dos três — e pare aqui. Só continue depois que o Git estiver respondendo de verdade.
2. **Pasta vazia — ou uma tentativa anterior deste mesmo setup.** Liste o que existe **na raiz da pasta atual**, incluindo arquivos e pastas ocultos. Não use o git para isso: o `.gitignore` deste produto esconde quase tudo, e uma pasta suja pode parecer limpa por ali.

   **Duas coisas não contam como conteúdo, nunca:**
   - **Lixo que o próprio sistema operacional cria sozinho** — `.DS_Store` no macOS, `Thumbs.db` e `desktop.ini` no Windows. Eles aparecem só por alguém ter aberto a pasta no Finder ou no Explorador, que é exatamente o que o README manda a pessoa fazer. Ignore-os.
   - **O que está *dentro* das entradas da lista abaixo** — se `areas/` está na lista, tudo que mora dentro dela vem junto.

   Feito isso, enquadre em uma destas três situações:

   - **Nada dentro** → caminho normal. Siga.
   - **Só entradas desta lista, e nada além delas** — `.git/`, `.claude/`, `.gitignore`, `CLAUDE.md`, `USER.md`, `MAPA.md`, `log.md`, `README.md`, `contexto/`, `inbox/`, `areas/`, `arquivo/` → é tudo que este próprio setup cria, e **isso quer dizer duas coisas diferentes**: pode ser uma tentativa que parou no meio (o ponto mais comum é a hora de entrar na conta do GitHub, que depende do navegador e de uma ação da pessoa), mas pode ser também um cérebro que já ficou pronto e está em uso. Pela lista de arquivos, os dois são idênticos. **Não anuncie nada ainda e não escreva nada**: siga para o E0.1, logo abaixo, que separa um caso do outro antes de qualquer outra coisa.
   - **Qualquer outra coisa** — um documento, uma planilha, uma pasta que não está nessa lista → **pare**, sem criar nada e sem fazer nenhuma pergunta. Duas respostas, conforme o caso:

   Se **não houver** sinal de tentativa anterior, responda em prosa exatamente isto:

   > Esta pasta já tem coisa dentro, e eu não escrevo por cima do que é seu.
   > Crie uma pasta nova e vazia para o cérebro, e me chame lá.
   > Se o que está aqui são notas antigas que você quer aproveitar: elas entram
   > depois, aos poucos, pela pasta `inbox/` do cérebro novo — assim eu leio cada
   > uma, organizo no lugar certo e nada seu é alterado.

   Se **houver** sinal de tentativa anterior (as entradas da lista acima) **e mais alguma coisa**, também pare — mas não mande recomeçar do zero, porque não é preciso. É o caso mais delicado dos três: a pessoa está voltando de uma tentativa que não terminou, e uma resposta ríspida aqui é onde ela desiste. Responda em prosa exatamente isto, trocando `notas.txt` pelo nome do que estiver sobrando de verdade (se for mais de um, liste todos):

   > Você já tem um cérebro começado aqui, e ele está inteiro — não precisa refazer nada.
   > Só que tem um arquivo nesta pasta que não é dele: `notas.txt`. Enquanto ele estiver
   > aqui eu não escrevo nada, porque não mexo no que é seu.
   > Tire o `notas.txt` daqui — para outra pasta, para a área de trabalho, onde você
   > preferir — e me chame de novo, que eu continuo de onde paramos.
   > Se for coisa que você quer aproveitar no cérebro, ela entra depois pela `inbox/`:
   > eu leio, organizo no lugar certo, e o arquivo original continua intacto.

   Não mova nem apague nada você mesmo — é material dela.

3. **Sistema operacional.** Identifique se esta máquina é Windows, macOS ou Linux e guarde essa informação — etapas futuras desta skill (a instalação do Git acima, e mais adiante a instalação do `gh`) precisam se adaptar a ela, e é mais barato descobrir uma vez do que redescobrir a cada etapa.

Só avance depois que os três itens acima passarem: para a entrevista (E1) no caminho normal, ou para o E0.1 quando a pasta tiver só aquilo que este setup cria.

### E0.1 — Tentativa interrompida ou cérebro já pronto?

O item 2 aceitou esta pasta porque tudo que existe nela é do feitio deste setup. Só que isso descreve **duas situações bem diferentes**: um setup que morreu no meio, e um cérebro terminado, com anotações de verdade e cópia guardada no GitHub. Tratar o segundo como se fosse o primeiro é o erro caro desta skill: mais adiante você criaria um repositório novo e trocaria a ligação do cérebro para ele — nada se perde no computador, mas o cérebro se desliga em silêncio da cópia que já tinha, e ninguém percebe. **Descubra em qual dos dois você está antes de escrever, perguntar ou criar qualquer coisa.**

**O sinal de cérebro pronto são estas três coisas, e só valem juntas:**

- **a estrutura está completa** — existem os arquivos da raiz (`CLAUDE.md`, `USER.md`, `MAPA.md`) e as pastas `contexto/`, `inbox/`, `areas/` e `arquivo/`. **Não exija o `log.md` aqui**: cérebros montados antes de ele existir não têm o arquivo, e cobrar isso faria um cérebro pronto e em uso ser confundido com uma tentativa interrompida — que é justamente o erro caro desta etapa;
- **a pasta já está ligada a um repositório remoto** — é um repositório git com um endereço de origem configurado, para onde ele envia;
- **o histórico tem mais de um registro** — alguma coisa foi salva depois do commit inicial que o próprio setup faz.

Faltando qualquer uma das três, é tentativa interrompida: siga para a recuperação, logo abaixo.

**Com as três juntas, não diga que achou uma tentativa anterior e não continue sozinho** — a frase seria falsa, e seguir adiante é o que quebra o cérebro dela. Fale em prosa, sem jargão, mais ou menos assim:

> Nesta pasta já tem um cérebro montado e funcionando — com as suas anotações e com cópia
> guardada no GitHub. Não parece ter sobrado nada para eu montar aqui, e eu não vou mexer no
> que já está pronto.
> Me diga o que você prefere: continuar usando esse cérebro do jeito que ele está, ou montar um
> cérebro novo, do zero, numa outra pasta vazia.

**Espere a resposta de verdade. Não decida por ela.**

- **Continuar com o que existe** → o setup não tem o que fazer. Diga em uma linha que está tudo no lugar e **encerre aqui**: não crie repositório, não troque nenhuma ligação, não avance para nenhuma etapa.
- **Montar um cérebro novo** → explique que ele nasce em uma pasta nova e vazia, que ela precisa criar essa pasta e abrir o Claude Code lá dentro, e **encerre aqui também** — este cérebro fica intocado.
- **Se ela responder outra coisa** — por exemplo, que aquele setup parou no meio e ela quer terminá-lo, ou que aquilo ali não é dela — trate como tentativa interrompida e siga para a recuperação abaixo.

#### Recuperação de uma tentativa interrompida

Uma tentativa que parou no meio já respondeu as perguntas da entrevista, e refazê-las é o motivo pelo qual as pessoas desistem na segunda vez. **Não repita a entrevista: recupere as respostas do que já está escrito na pasta.**

- `DONO` → o título da primeira linha do `USER.md` (ou do `CLAUDE.md`).
- `TRATAMENTO` → a linha "Me trate por ..." do `USER.md` — o valor é só a palavra que está ali (`você` ou `senhor`), sem as aspas nem o ponto final.
- `RESPOSTA_PERGUNTA_2` → o texto da seção "Quem sou eu" do `USER.md`.
- `AREAS_SLUGS` → os nomes das pastas dentro de `areas/`.
- `AREAS_NOMES` → o texto dos links da seção "Áreas" do `MAPA.md` da raiz, que é onde o nome de exibição está escrito por extenso; se ali não der, use o título da primeira linha do `MAPA.md` de cada área.

Diga em uma ou duas frases que achou uma tentativa anterior e vai continuar de onde ela parou, mostrando o nome e as áreas que recuperou. **Pergunte só o que não conseguiu recuperar** — se recuperou tudo, não pergunte nada. Se a pasta estiver tão incompleta que nada disso exista (por exemplo, só `.git/` dentro), aí sim faça a entrevista (E1) normalmente.

Se algum valor existir mas estiver estragado, **não recomece por causa disso e não sobrescreva o arquivo**: pergunte aquele valor específico à pessoa (isso conta como "não consegui recuperar") e conserte só o trecho errado. Estragado quer dizer uma destas duas coisas, e nada além delas — no resto, aceite o que recuperou e siga:

- sobrou um marcador `{{...}}` cru no valor;
- o nome de exibição de uma área é **idêntico ao slug, caractere por caractere** (`familia` para a pasta `familia/`, quando deveria ser `Família`). "Loja" para a pasta `loja/` **não** é estragado — é o nome escrito do jeito certo.

Se a pessoa disser que aquele material não é dela nem de uma tentativa dela, trate como pasta suja: pare e devolva a mensagem do item 2 acima.

Depois disso, siga para o E2 — que na retomada só completa o que falta.

## E1 — Entrevista

Três perguntas, **uma de cada vez** — só faça a próxima depois de ler a resposta da anterior. **Nesta etapa, não faça nenhuma pergunta além destas três**: cada pergunta a mais custa minuto na régua dos 15 que este produto promete. (Mais tarde, no E6, você vai pedir uma coisa a mais — mas ali não é entrevista, é o cérebro rodando de verdade.)

1. **"Como você quer que eu te chame?"** — guarde a resposta como `DONO`.
2. **"Em poucas linhas: o que você faz? Quais são as frentes do seu dia a dia?"** — guarde a resposta inteira, literal, como `RESPOSTA_PERGUNTA_2`. A partir dela, proponha de **2 a 5 áreas**, cada uma com um nome de exibição (o nome natural da frente, do jeito que se fala — pode ter acento e mais de uma palavra, ex.: "Família") e o slug correspondente (minúsculo, sem acento, sem espaço — troque espaço por hífen), e **mostre a lista para a pessoa confirmar antes de criar qualquer coisa**. Isso faz parte da pergunta 2, não é uma pergunta nova. Se a resposta não permitir inferir nenhuma frente, proponha "Trabalho" e "Pessoal" (slugs `trabalho` e `pessoal`). Guarde a lista final — já com os ajustes que a pessoa pedir — como `AREAS_SLUGS` (os slugs) e `AREAS_NOMES` (os nomes de exibição correspondentes, na mesma ordem).
3. **"Prefere que eu te trate por *você* ou por *senhor*?"** — guarde a resposta como `TRATAMENTO`.

Com as três respostas em mãos e a lista de áreas confirmada, siga para E2.

## E2 — Estrutura

Os modelos vêm junto desta skill, na subpasta `modelos/` (sufixo `.modelo` em cada arquivo). Para cada um, copie o conteúdo para o destino indicado, sem o sufixo, substituindo os marcadores pelo valor correspondente:

**Se você chegou aqui por retomada (E0.1), crie só o que ainda não existe e não recopie o modelo por cima de nenhum arquivo já escrito** — o que está lá é da tentativa anterior, e a pessoa pode ter mexido nele desde então. A única edição permitida é consertar um trecho especificamente quebrado (um `{{...}}` cru que sobrou), no lugar onde ele está.

- `{{DONO}}` → a resposta da pergunta 1.
- `{{RESPOSTA_PERGUNTA_2}}` → a resposta da pergunta 2, literal, sem resumir nem reescrever.
- `{{TRATAMENTO}}` → a resposta da pergunta 3.
- `{{DATA}}` → a data de hoje, no formato `DD/MM/AAAA`.
- `{{DATA_ISO}}` → a data de hoje no formato `AAAA-MM-DD` (ex.: `2026-08-13`). É a mesma data do marcador acima, escrita de outro jeito: no `log.md` a data vem primeiro para as entradas ficarem em ordem sozinhas. Aparece só nesse arquivo.
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
| `log.md.modelo` | `log.md` |
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

- `inbox/<slug-do-dono>/`, com um `.gitkeep` dentro — a caixa de entrada pessoal da pessoa. O slug do dono segue a mesma regra das áreas (minúsculo, sem acento, sem espaço). Ela nasce vazia, e pasta sem nenhum arquivo dentro não entra no Git: sem o `.gitkeep`, ela some ao clonar o cérebro em outra máquina, e a `/salvar` vai procurar por ela lá e não achar.
- `arquivo/`, com um `.gitkeep` dentro — vazia por enquanto, mas precisa existir e sobreviver ao primeiro commit, pelo mesmo motivo.
- `.claude/skills/` — vazia por enquanto; as skills do cérebro chegam aqui numa etapa futura desta mesma skill.

**Não crie** `projetos/`, `tarefas/` nem `clientes/` dentro de nenhuma área, e não crie uma pasta `sistema/` na raiz — essas nascem quando o primeiro item de cada tipo chegar (no caso de `sistema/`, na Etapa 2 deste produto, que é outra skill).

## E3 — Verificação

Este é um **gate**, não um relatório: enquanto sobrar algo, você não segue nem comenta com a pessoa.

Antes de seguir, confira se sobrou algum marcador no formato `{{ALGUMA_COISA}}` **na pasta inteira do cérebro** — não só no que você acabou de escrever. Numa retomada você pode não ter criado nenhum arquivo novo, e é justamente ali que mora o risco: um marcador cru deixado pela tentativa anterior passaria batido e acabaria publicado. Varra todos os arquivos de texto da pasta, inclusive os que já estavam lá antes de você chegar; o miolo do `.git/` não conta, é o histórico do git, não conteúdo do cérebro. Use a ferramenta de busca que preferir nesta máquina.

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

**Antes de propor nome nenhum, veja se esta pasta já está ligada a um repositório no GitHub** — se o repositório git daqui já tem um endereço de origem configurado. Numa retomada isso é comum: a tentativa anterior pode ter chegado até aqui. Se já houver essa ligação:

- **não crie outro repositório e não troque a ligação existente**, por nada. Apontar o cérebro para um repositório novo o desliga em silêncio da cópia que ele já tinha: nada se perde no computador, mas tudo que for salvo dali em diante vai para o lugar errado, e ninguém percebe — inclusive a conferência de privacidade lá embaixo estaria conferindo o repositório errado.
- Leia para onde a ligação aponta e **confirme com a pessoa, em uma linha, que é o repositório dela mesma**, mostrando o endereço. Com o sim dela, envie o que ainda não tiver subido e siga direto para a conferência de privacidade no fim desta etapa — é esse o repositório a conferir.
- Se alguma coisa estiver diferente do esperado — ela não reconhece o endereço, o repositório não existe mais, você não consegue acessá-lo, ou ele é de outra conta — **pare e explique o que encontrou**, em linguagem simples, e pergunte o que ela quer fazer. Não improvise um repositório novo para contornar.

Só quando **não houver** repositório ligado é que você cria um do zero, daqui em diante.

Proponha à pessoa o nome do repositório: o **slug do dono que você já calculou no E2** — o mesmo usado em `inbox/<slug-do-dono>/` — seguido de `-cerebro`. Nunca use o nome literal da pergunta 1 para isso: ele pode ter espaço e acento, e o GitHub não aceita isso em nome de repositório. Essa proposta é confirmada com a pessoa em uma linha — não é uma quarta pergunta da entrevista, é a confirmação de um valor que você já derivou.

**Só crie o repositório depois que a pessoa confirmar o nome.** Enquanto ela não responder, não crie nada no GitHub — criar antes é uma ação externa feita sem consentimento.

Se o nome confirmado já existir na conta dela (por exemplo, de uma tentativa anterior que não terminou), avise e proponha outro nome, em vez de falhar.

Com o nome confirmado, crie no GitHub um repositório **privado**, ligue a pasta a ele e envie tudo.

Depois de enviar, **consulte o GitHub para confirmar que o repositório está mesmo privado** — não confie no comando que você rodou, leia o estado real. Se por qualquer motivo ele estiver público, **torne-o privado imediatamente** — é isso que tira o conteúdo do ar, e você consegue fazer isso sem pedir nenhuma permissão nova. Se essa correção falhar por qualquer razão, **pare na hora** e avise a pessoa, em linguagem simples, que o cérebro dela ficou visível publicamente, que ela mesma precisa entrar na conta do GitHub e trocar o repositório para privado (ou apagá-lo), e explique em uma frase onde essa opção fica. Não siga para nenhuma etapa seguinte enquanto isso não estiver resolvido.

## E5 — Skills do dia a dia

Com o repositório no ar, instale as três skills que fazem o cérebro ser usado no dia a dia, não só
guardado. Esta skill trouxe as três junto de si, dentro da própria pasta dela: na subpasta
`skills-do-cerebro/`, uma pasta por skill (`skills-do-cerebro/salvar/SKILL.md`,
`skills-do-cerebro/ingestao/SKILL.md` e `skills-do-cerebro/perfil/SKILL.md`) — a mesma pasta de
onde você leu os `modelos/`. Elas viajam ali dentro justamente para chegarem juntas quando esta
skill é instalada; não há nada a baixar agora. Copie o conteúdo de cada `SKILL.md` para o destino
indicado abaixo.

1. **`/salvar` é global, e vai para um lugar só.** Antes de copiar, saiba onde ela **não** pode
   ir: **nunca dentro do cérebro.** Se `/salvar` for parar em `<cerebro>/.claude/skills/`, o
   `{{CEREBRO_PATH}}` daquela cópia fica cru — ninguém vai substituí-lo ali —, e o cérebro passa a
   carregar um placeholder que o gate do E3 já devia ter eliminado antes mesmo do repositório
   existir.

   O destino certo é `~/.claude/skills/salvar/SKILL.md` — a pasta de skills globais desta máquina,
   a mesma de onde qualquer skill roda não importa em que projeto a pessoa esteja. Copie
   `skills-do-cerebro/salvar/SKILL.md` para lá. É a única das três que precisa de ajuste: ela
   carrega o marcador `{{CEREBRO_PATH}}`, e você substitui pelo caminho absoluto do cérebro que
   acabou de criar. É global porque captura tem que funcionar de onde a pessoa estiver, não só de
   dentro do cérebro.

   **Antes de escrever nesse caminho, olhe se já existe uma `/salvar` instalada ali** e, se
   existir, leia qual caminho de cérebro ela carrega. Se for **outro** cérebro — não este que você
   acabou de montar —, **não sobrescreva**: essa máquina já captura para outro lugar, e trocar
   isso caladamente faria toda captura futura cair no cérebro errado, sem nenhum aviso. Diga para
   qual cérebro ela aponta hoje, para qual passaria a apontar, e pergunte o que a pessoa prefere.
   Só troque com o sim dela; se ela preferir manter o que tem, mantenha, siga para o item 2 e
   avise em uma linha que a captura continua indo para o cérebro antigo — e que, para guardar
   neste aqui, ela vai precisar dizer isso na hora de salvar. Se a `/salvar` que está lá já aponta
   para este mesmo cérebro, é a mesma instalação: pode sobrescrever sem perguntar.

2. **`/ingestao` e `/perfil` são do cérebro.** Copie `skills-do-cerebro/ingestao/SKILL.md` e
   `skills-do-cerebro/perfil/SKILL.md`, sem alterar nada, para
   `<cerebro>/.claude/skills/ingestao/SKILL.md` e `<cerebro>/.claude/skills/perfil/SKILL.md` —
   nenhuma das duas tem marcador para substituir. Elas só fazem sentido lendo o `CLAUDE.md`, o
   `USER.md` e a `inbox/` deste cérebro específico, e por isso viajam versionadas com o
   repositório: quando a pessoa clonar em outra máquina, já chegam prontas, sem precisar reinstalar
   nada.

   **Se alguma das duas já existir no destino, não copie por cima sem olhar** — numa retomada, ou
   num cérebro que já rodava, o arquivo que está lá pode ter sido editado pela pessoa, e a cópia
   silenciosa apagaria o que ela escreveu e ainda mandaria isso para o GitHub no passo seguinte.
   Compare o que está lá com o que você traz. Iguais, não há nada a fazer. Diferentes, **não
   sobrescreva calado**: diga em uma ou duas frases o que muda e pergunte se ela quer a versão
   nova. Só substitua com o sim dela; se ela preferir ficar com a versão dela, mantenha e siga.

**Verificação, antes de seguir para o E6:** o `{{CEREBRO_PATH}}` que você acabou de preencher é o
único marcador de toda a skill que sobrevive ao gate do E3 — ele nem existia até agora. Confira,
nas três skills que agora estão nos destinos (a global e as duas dentro do cérebro), tenha você
acabado de escrevê-las ou mantido a versão que já estava lá, se sobrou algum marcador no formato
`{{ALGUMA_COISA}}` em qualquer uma delas. Se encontrar algum, corrija e
confira de novo. Só siga para o E6 quando a busca vier vazia.

Com a verificação limpa, registre `/ingestao` e `/perfil` no controle de versão do cérebro, num
registro próprio, e **envie ao repositório** (a `/salvar`, por ser global, fica de fora — ela não
mora dentro do repositório). Se as duas já estavam lá e nada mudou — porque eram idênticas, ou
porque a pessoa preferiu manter a versão dela —, não há o que registrar: siga direto para o E6.

Não deixe essas duas skills penduradas até o E6: se a sessão parar
entre agora e o OK que o E6 pede, elas ficam presas só nesta máquina, sem nenhum sinal de que
falta enviá-las — e quem clonar o cérebro em outra máquina não as recebe.

## E6 — Primeiro ciclo ao vivo

O setup não termina no repositório publicado — termina com a pessoa vendo o ciclo inteiro
funcionar, uma vez, com material dela de verdade. Um cérebro que nasce sem nenhuma escrita nasce
com o hábito já morto.

1. Peça um item de verdade, em uma frase, mais ou menos assim: **"Me conta uma coisa que
   aconteceu essa semana — uma conversa com um fornecedor, um problema que apareceu, uma ideia que
   você teve. Qualquer coisa serve; é para você ver o cérebro funcionando com material seu."**
   Adapte a frase às áreas que ela nomeou no E1, e aceite o que vier — se ela responder curto, está
   ótimo.

   **Não use aqui a resposta da pergunta 2 da entrevista.** Ela descreve as frentes da pessoa
   inteira — foi dela que as áreas nasceram —, então encosta em todas e não pertence a nenhuma: a
   `/ingestao` corretamente propõe deixá-la na caixa de entrada, e o primeiro ciclo termina sem
   nenhuma nota gravada. Um fato do dia a dia cai numa área só e fecha o ciclo até o fim.

2. Rode a `/salvar` que você acabou de instalar, com o que ela contou, exatamente como ela
   escreveu — sem resumir, sem reescrever.
3. Mostre a ela o arquivo que apareceu dentro da `inbox/` — o caminho que a própria `/salvar`
   confirmou ao gravar.
4. Rode a `/ingestao`. Ela vai ler o item, apresentar o resumo em prosa e esperar o OK da pessoa
   antes de gravar qualquer coisa — este é o portão da `/ingestao`, espere a resposta de verdade,
   não presuma o OK para ir mais rápido.
5. Depois do OK e da gravação, mostre a nota no destino final onde a `/ingestao` a colocou, com o
   caminho completo dela. Se ela tiver ficado na caixa de entrada por falta de dono claro, peça
   outro item — mais concreto, ligado a uma área só — e rode o ciclo de novo: o E6 não termina sem
   uma nota gravada no acervo.
6. A própria `/ingestao` termina registrando e enviando o que gravou ao repositório. Confirme que
   isso aconteceu de verdade — se, por qualquer motivo, alguma coisa tiver ficado só nesta máquina,
   registre e envie você mesmo antes de fechar.
7. Feche com exatamente três linhas, nada além disso: o endereço do repositório que você publicou
   no E4; que `/salvar` guarda qualquer coisa em segundos, de qualquer pasta do computador; que
   `/ingestao` organiza o que se acumulou na caixa de entrada e `/perfil` melhora o que o cérebro
   sabe sobre ela — **essas duas só rodam com o Claude Code aberto dentro da pasta do cérebro**.
   Sem lista de próximos passos, sem tour pelo que mais o cérebro faz — cada linha a mais aqui é
   uma linha que a pessoa não vai ler.
