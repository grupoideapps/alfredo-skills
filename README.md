# Alfredo Skills: 75 vídeos viram um consultor dentro do Claude

Skills e um agente para o Claude Code/Claude que respondem dúvidas de negócio (vendas, posicionamento, conteúdo, preço, margem, canais, foco, recorrência, eventos, time comercial e serviço B2B) a partir de 75 vídeos públicos do canal do **Alfredo Soares**.

Cada resposta aponta o vídeo e o minuto onde o tema aparece. Se a dúvida é sobre preço, você assiste ao trecho dele sobre preço. O repositório é uma porta de entrada para o canal.

**Canal do Alfredo Soares:** https://www.youtube.com/@canaldoalfredosoares

## O que é e o que não é

- É material de estudo: organização por tema e paráfrase das legendas automáticas de vídeos públicos.
- Não é fala oficial dele, não tem aval dele e não é afiliado a ele.
- A legenda automática erra nomes e números. Número citado por ele nos vídeos é "dito por ele, não verificado". Nunca use como referência de mercado.
- O que o agente responde sobre o seu caso é aplicação do raciocínio ao que você contou. O que não aparece nos vídeos, ele avisa.

## O que tem aqui

- `skills/alfredo-advisor`: roteadora. Classifica a pergunta e escolhe o tema.
- 8 skills de tema: `alfredo-canais-aquisicao`, `alfredo-margem-preco-caixa`, `alfredo-foco-crescimento`, `alfredo-receita-base-recorrencia`, `alfredo-eventos-experiencia`, `alfredo-marca-conteudo-founder`, `alfredo-gestao-vendas-pessoas`, `alfredo-servico-b2b`.
- `agents/alfredo.md`: o agente que usa as 9 skills, somente leitura.
- `skills/alfredo-advisor/references/links.md`: os 75 vídeos, com título e link.
- `METODO.md`: o passo a passo que usei para criar isso. Serve para qualquer canal do YouTube.

## Como instalar (Claude Code)

```bash
git clone https://github.com/grupoideapps/alfredo-skills.git
cp -r alfredo-skills/skills/* ~/.claude/skills/
cp alfredo-skills/agents/alfredo.md ~/.claude/agents/
```

Depois, no Claude Code, chame o agente: "alfredo, o que você acha da minha bio do Instagram?" ou peça uma resposta "no raciocínio do Alfredo" sobre preço, canal, posicionamento ou conteúdo.

## Quer fazer com outro canal?

Leia o `METODO.md`. O processo é o mesmo para qualquer criador com um bom acervo em vídeo.

## Feito por

Luan Bonadie, [omentor.ai](https://www.instagram.com/omentor.ai/). Se algum trecho estiver errado ou o Alfredo preferir que algo saia, abra uma issue ou fale comigo no Instagram.
