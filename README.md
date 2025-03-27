# Projeto-ICD

Integrantes: Lucas Marinho, Lucas Nery, Giulle e Gustavo

Tema: Análise de Dados aos sentimentos e reações do público nas premiações do Oscar

Abordagem da Coleta de Dados: Processamento de Linguagem Natural (PLN), API, DataSet

O conjunto de dados consiste em informações extraídas do Reddit sobre as reações do público em relação à premiação do Oscar, analisando o post anual do subreddit r/Oscars que reúne milhares de comentários e reações diversas sobre o tema que queremos analisar. Os dados dos posts incluem título, texto, autor, subreddit de origem, número de votos e análise de sentimento. Já os comentários vinculados aos posts contêm informações como texto, sentimento, votos e profundidade de aninhamento do comentário.

A coleta de dados foi feita por meio do API do Reddit, o Praw, utilizando o id do post específico, nós extraímos as informações do próprio post para fazer o dataset do post, e utilizando recursos do Praw nós extraímos os comentários do post e seus dados, foi necessário um esforço extra devido tanto às limitações do API que tem limite de requisições, como também pelo estilo de aninhamento de comentários do reddit, que necessitou de uma função específica para iterar sobre todos os comentários, alongando o processo de coleta. coletados os textos, é feita a análise do sentimento geral do comentário, utilizando o módulo VADER, que analisa palavra por palavra, além de expressões e gírias e consegue compor um número que a depender de seu resultado indica o teor do texto, isto é, negativo, neutro ou positivo.

# Colunas do post:

Subreddit: Nome do subreddit onde o post foi publicado.
Exemplo: Movies

Title: Título do post.
Exemplo: Oscars 2025: Quem deveria ganhar?

Text: Texto do post, caso o usuário tenha escrito algo além do título.
Exemplo: A premiação deste ano foi cheia de surpresas...

Upvotes: Número de votos positivos (upvotes) recebidos pelo post.
Exemplo: 1523

Downvotes: Número de votos negativos (downvotes) (nem sempre disponível na API do Reddit).
Exemplo: 34

Sentimento: Classificação do sentimento do post com base na análise de sentimentos (positivo, negativo ou neutro).
Exemplo: positivo

Author: Nome do autor do post.
Exemplo: u/filmefanatico

Submission_id: Identificador único do post no Reddit.
Exemplo: 1j24nvr

Data: Data e hora da publicação do post.
Exemplo: 2025-03-02 20:25:38

# Colunas dos comentários:

Comentário: Texto do comentário coletado.
Exemplo: Eu acho que o Oscar deveria ter ido para outro filme!

Sentimento: Classificação do sentimento do comentário (positivo, negativo ou neutro).
Exemplo: negativo

Upvotes: Número de votos positivos do comentário.
Exemplo: 230

Depth: Nível de aninhamento do comentário na árvore de respostas (0 = comentário principal, 1 = resposta a um comentário, etc.).
Exemplo: 1

Autor: Nome do autor do comentário.
Exemplo: u/cinema_love

Data: Data e hora da publicação do comentário.
Exemplo: 2025-03-03 14:12:10
