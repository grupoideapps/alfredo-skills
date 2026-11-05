# Método: como transformar um canal do YouTube em skills e um agente

Passo a passo usado para criar este repositório. Funciona com qualquer canal público que você queira consultar. Respeite o canal: use para estudo, organize em paráfrase, aponte sempre para o vídeo e o minuto, e não republique a fala do autor.

## 1. Escolha o canal e liste os vídeos
Defina quantos vídeos entram (aqui foram 75). Guarde, para cada um: número, id do YouTube, título e duração. Esse índice vira o `links.md`.

## 2. Baixe só as legendas
Sem baixar o vídeo. Exemplo com `yt-dlp`:

```bash
yt-dlp --skip-download --write-auto-subs --sub-langs "pt-orig" \
  --convert-subs srt -o "%(playlist_index)02d-%(id)s" \
  "https://www.youtube.com/@canaldoalfredosoares/videos"
```

Converta cada legenda em texto com o minuto marcado `[hh:mm:ss]`. A legenda é automática: não tem revisão humana, então nomes próprios e números podem estar errados.

## 3. Extraia uma ficha por vídeo
Para cada vídeo, peça ao Claude uma ficha com:
- tipo do vídeo (entrevista, mentoria de um negócio, vlog, palestra);
- quanto do conteúdo é do autor e quanto é de convidado;
- os temas de negócio tratados;
- os frameworks e as ideias, cada uma com o minuto.

Marque quem fala: afirmação do autor, inferência sua, fala de convidado, ou falante incerto quando a legenda não separa as vozes.

## 4. Agrupe por tema
Leia as 75 fichas e deixe os temas emergirem. Aqui saíram 8: canais de aquisição, margem/preço/caixa, foco e crescimento, receita recorrente, eventos e experiência, marca e conteúdo do fundador, gestão de vendas e pessoas, serviço B2B.

## 5. Crie 1 skill por tema
Cada skill tem:
- **Quando usar** (com exemplos de pergunta do usuário);
- as perguntas que o autor faria antes de responder, em paráfrase;
- os frameworks, cada um com link para o vídeo e o minuto (`https://youtu.be/<id>?t=<segundos>`);
- um arquivo `references/fontes.md` com o banco de evidências e um `references/casos.md` com os casos citados.

Regra de ouro: nada de citação longa. Paráfrase, com o link do vídeo.

## 6. Crie 1 skill roteadora
Ela recebe a pergunta, classifica o tema (principal e, no máximo, um secundário) e aponta para a skill certa. Inclui o jeito de pensar do autor, o estilo de comunicação e as cautelas (números não verificados, fala de convidado, erros de legenda).

## 7. Crie o agente
Um subagente somente leitura que:
1. lê a roteadora e classifica a pergunta;
2. abre a skill do tema e busca a evidência no `fontes.md`;
3. responde em texto corrido, no raciocínio do autor;
4. fecha com as perguntas que ele faria e uma lista de **Fontes**, com o link do vídeo no minuto certo;
5. avisa quando o tema não aparece nos vídeos e marca como "não é dele" o que for opinião do agente.

## 8. Confira antes de publicar
- Rode uma checagem para garantir que nenhuma sequência longa de palavras repete a legenda original.
- Confira os links dos vídeos e dos minutos por amostragem.
- Deixe claro, no README, que não é fala oficial nem tem aval do autor.

## 9. Use
Instale as skills e o agente, e pergunte. A resposta vem com o vídeo e o minuto, e você assiste ao trecho para confirmar.
