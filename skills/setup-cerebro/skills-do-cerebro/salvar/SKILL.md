---
name: salvar
description: Guarda rapidamente qualquer coisa na inbox do segundo cérebro — ideia, recado, link, print, trecho de conversa. Use quando a pessoa disser "salva isso", "guarda no cérebro", "anota aí", "registra isso". NÃO use para organizar o que já está na inbox (isso é /ingestao) nem para responder sem gravar.
---

# /salvar

Deposita qualquer coisa na caixa de entrada do cérebro, na hora, sem organizar. Organizar é
trabalho da `/ingestao` — esta skill só guarda.

**Caminho do cérebro:** `{{CEREBRO_PATH}}`. Esta skill é global — roda de qualquer pasta, em
qualquer projeto — então não tente descobrir o caminho do cérebro pelo diretório atual: use
sempre este.

## O que fazer

1. **Ache a caixa de entrada pessoal.** Dentro de `{{CEREBRO_PATH}}/inbox/` existe uma subpasta
   com o nome do dono do cérebro — foi criada no setup. É ali que o item vai, nunca solto na
   raiz de `inbox/` nem dentro de `areas/`. Dois casos fora do comum:
   - **Mais de uma subpasta candidata**, sem ser óbvio qual usar → pergunte antes de gravar.
   - **Nenhuma subpasta lá dentro** → crie uma com o nome do dono do cérebro (minúsculo, sem
     acento, sem espaço) e siga normalmente, avisando em uma linha que criou a caixa de entrada
     pessoal. Não trave por causa disso, e não grave solto na raiz de `inbox/`.

2. **Monte o nome do arquivo.** Formato: `AAAA-MM-DD-HHMM-<slug>.md` — a data e a hora de agora,
   seguidas de um slug curto (minúsculo, sem acento, palavras separadas por hífen) que resuma o
   conteúdo em poucas palavras. O carimbo de hora no nome existe para que duas capturas do mesmo
   dia não se sobrescrevam; se ainda assim colidir com um arquivo já existente, acrescente um
   sufixo numérico ao slug.

3. **Escreva o arquivo**, com este frontmatter mínimo no topo:

   ```yaml
   ---
   tipo: triagem
   data: AAAA-MM-DD
   origem: <de onde isto veio — "conversa", "whatsapp", "e-mail", ou o que a pessoa disser>
   captado_em: AAAA-MM-DD HH:MM
   ---
   ```

   Depois do frontmatter, o conteúdo exatamente como a pessoa passou.

4. **Se o que a pessoa mandou for uma imagem ou um print**, transcreva em texto tudo que estiver
   visível e for relevante — preservando número, nome e data exatamente como aparecem na imagem —
   e grave essa transcrição como o conteúdo do arquivo. A imagem em si **não é gravada**: o
   `.gitignore` deste cérebro só deixa `.md` subir para o GitHub, então uma imagem guardada aqui
   nunca chegaria lá — ficaria só nesta máquina, parecendo salva sem estar. O texto, sim, sobe:
   na próxima vez que a pessoa rodar a `/ingestao`, é ela que leva tudo para o GitHub. Avise disso
   na confirmação (passo 6): diga que guardou o conteúdo em texto e que a imagem não fica salva no
   cérebro.

5. **Preserve o literal.** Número, valor, nome próprio e data entram tal como foram ditos — não
   interprete, não arredonde, não troque "talvez" por "vai", não resuma o que a pessoa quis
   guardar por inteiro.

6. **Confirme em uma frase** o que guardou e onde — por exemplo: "Guardado em
   `inbox/<dono>/2026-08-08-1432-ideia-promocao-fim-de-semana.md`." Se o item era imagem ou
   print, deixe explícito: "Guardei em texto o que estava no print, em
   `inbox/<dono>/2026-08-08-1440-tabela-preco-fornecedor.md` — a imagem em si não fica salva."

## O que NÃO fazer

- Não decida destino nem área — isso não é desta skill, é da `/ingestao`, mais tarde, com o lote
  inteiro na frente.
- Não crie nem edite nada em `areas/`, `contexto/` ou nos arquivos da raiz (`CLAUDE.md`,
  `MAPA.md`, `USER.md`).
- Não organize, não classifique, não resuma o conteúdo — só deposite.
