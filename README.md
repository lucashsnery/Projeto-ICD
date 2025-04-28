# Projeto-ICD

**Integrantes:** Lucas Marinho, Lucas Nery, Giulle e Gustavo  

**Tema:** Análise de dados sobre sentimentos e reações do público nas premiações do Oscar

**Abordagem da Coleta de Dados:** Processamento de Linguagem Natural (PLN), API, DataSet

---

## Conjunto dos dados

O conjunto de dados consiste em informações extraídas do Reddit sobre as reações do público em relação à premiação do Oscar, analisando o post anual do subreddit r/Oscars que reúne milhares de comentários e reações diversas sobre o tema que queremos analisar. Os dados dos posts incluem título, texto, autor, subreddit de origem, número de votos e análise de sentimento. Já os comentários vinculados aos posts contêm informações como texto, sentimento, votos e profundidade de aninhamento do comentário.

## Processo de coleta de dados

A coleta de dados foi feita por meio do API do Reddit, o Praw, utilizando o id do post específico, nós extraímos as informações do próprio post para fazer o dataset do post, e utilizando recursos do Praw extraímos os comentários do post e seus dados, foi necessário um esforço extra devido tanto às limitações do API, com limite de requisições, como também pelo estilo de aninhamento de comentários do reddit, que necessitou de uma função específica para iterar sobre todos os comentários, alongando o processo de coleta. Coletados os textos, é feita a análise do sentimento geral do comentário, utilizando o módulo VADER, que analisa palavra por palavra, além de expressões e gírias e consegue compor um número que a depender de seu resultado indica o teor do texto, isto é, negativo, neutro ou positivo.

## Colunas do Post

### Descrição das colunas

**Subreddit:** Nome do subreddit onde o post foi publicado.

**Title:** Título do post.

**Text:** Texto do post, caso o usuário tenha escrito algo além do título.

**Upvotes:** Número de votos positivos (upvotes) recebidos pelo post.

**Downvotes:** Número de votos negativos (downvotes) (nem sempre disponível na API do Reddit).

**Sentimento:** Classificação do sentimento do post com base na análise de sentimentos (positivo, negativo ou neutro).

**Author:** Nome do autor do post.

**Submission_id:** Identificador único do post no Reddit.

**Data:** Data e hora da publicação do post.

### Exemplo

|   Subreddit   |             Title              |                 Text                 | Upvotes | Downvotes | Sentimento |     Author      | Submission_id |        Data         |
|:-------------:|:------------------------------:|:------------------------------------:|:-------:|:----------:|:-----------:|:---------------:|:--------------:|:-------------------:|
|    Movies     | Oscars 2025: Quem deveria ganhar? | A premiação deste ano foi cheia de surpresas… |  1523   |    34     |  Positivo   | u/filmefanatico |    1j24nvr     | 2025-03-02 20:25:38 |

## Colunas dos comentários:

### Descrição das colunas

**Comentário:** Texto do comentário coletado.

**Sentimento:** Classificação do sentimento do comentário (positivo, negativo ou neutro).

**Upvotes:** Número de votos positivos do comentário.

**Depth:** Nível de aninhamento do comentário na árvore de respostas (0 = comentário principal, 1 = resposta a um comentário, etc.).

### Exemplo

|     Comentário                                           | Sentimento | Upvotes | Depth |
|:--------------------------------------------------------:|:----------:|:-------:|:-----:|
| Eu acho que o Oscar deveria ter ido para outro filme!    |  Negativo  |   230   |   1   |

## Acesso aos Dados:

[Clique aqui para acessar o conjunto de dados no Google Drive](https://drive.google.com/drive/folders/18oqFb6_7-i5956Uw1FGGG0uZs--yhyh-)
