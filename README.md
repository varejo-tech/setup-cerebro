# Segundo Cérebro — VarejoTech

Um lugar onde o que você sabe sobre o seu negócio fica guardado, organizado e
nunca se perde. E um assistente de IA que sabe achar qualquer coisa ali
dentro, na hora que você precisar.

## O que você precisa antes de começar

- **Claude Code instalado** no seu computador.
- **Uma conta no GitHub.** Se você não tem, crie uma de graça em
  [github.com/signup](https://github.com/signup) — leva poucos minutos.
  Resolva isso antes de começar, porque o setup vai pedir essa conta lá pelo
  meio do caminho.
- **Uma pasta nova e vazia**, só para o cérebro. Não use uma pasta que já
  tenha algum arquivo dentro.

## Como instalar

**1. Crie a pasta e abra o Claude Code dentro dela.**

- No Mac: crie a pasta pelo Finder, clique nela com o botão direito e
  procure "Novo Terminal na Pasta" (ou abra o Terminal e navegue até lá).
  Depois digite `claude` e aperte Enter.
- No Windows: crie a pasta pelo Explorador de Arquivos, clique com o botão
  direito **dentro** dela e escolha "Abrir no Terminal" (ou "Git Bash
  aqui"). Depois digite `claude` e aperte Enter.

Se travar nesse passo, é normal — peça ajuda a alguém que manje um pouco de
computador em vez de desistir sozinho.

**2. Cole o texto abaixo** na conversa que abriu:

```
Instale a skill de setup do segundo cérebro a partir de
https://github.com/varejo-tech/setup-cerebro — clone o repositório
numa pasta temporária, copie skills/setup-cerebro para
~/.claude/skills/ e me confirme quando terminar. Depois vou rodar
/setup-cerebro.
```

**3.** Quando o agente confirmar, rode `/setup-cerebro`. Ele faz três
perguntas rápidas e monta tudo sozinho: a estrutura do cérebro, o
repositório privado no GitHub (um espaço só seu, guardado lá, com
histórico de tudo que for salvo) e os comandos do dia a dia.

**Quanto tempo leva:** cerca de 15 minutos, se você já tem o Git e a conta
no GitHub prontos. Se não tiver, sem problema — o próprio setup instala o
que falta e te orienta na hora, só que leva mais tempo.

**Um aviso sobre o GitHub:** em algum ponto do processo vai aparecer um
código na tela e o navegador vai abrir sozinho. É o `gh auth login` pedindo
para confirmar que é você mesmo — cole o código lá, autorize, e volte para o
Claude Code. É normal, faz parte do processo.

## Como usar depois

- **`/salvar`** — guarda qualquer coisa no cérebro em segundos: uma ideia,
  um recado, um print. Funciona de qualquer pasta do seu computador.
- **`/ingestao`** — organiza o que se acumulou na caixa de entrada, e só
  grava depois do seu OK.
- **`/perfil`** — aprofunda o que o cérebro sabe sobre você, para o agente
  trabalhar melhor com você.

## Já tenho notas antigas — e agora?

O cérebro nasce vazio, numa pasta nova. Nada do que você já tem — arquivo,
planilha, nota antiga — é lido, alterado ou apagado por este setup.

O que já existe entra depois, aos poucos, pela caixa de entrada (`inbox/`)
do cérebro novo. Leve os assuntos em blocos — por exemplo, tudo sobre um
fornecedor de uma vez, não um arquivo isolado por vez — e rode `/ingestao`.
O agente lê, organiza e guarda cada coisa no lugar certo, sem tocar no que
já é seu.
