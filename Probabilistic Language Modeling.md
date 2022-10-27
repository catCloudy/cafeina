# 23/04 - NLP - Probabilistic Language Modeling

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/813bcf99-747e-4d98-b11b-e9a5075d334c/Untitled.png)

# How to compute P(W)

- **How to compute this joint probability**
    - P(word / history) → Probabilidade de word acontecer dado history
    - P (the / its water is so transparent that) → Probabilidade de the acontecer dado its water so transparent that
- **Use relative frequency counts**
    - Take a very large corpus
    - count the number of times we see "its water is so transparent that"
    - count the number of times this is followed by "the"
- P (the / its water is so transpaedent that) =  C (its water is so transparent taht the )/C(its water is so transparent that)
- **Intuition**
- Chain Rule of Probability

# Regra da cadeia

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5d3a3ef-487b-44da-a88d-47ad88296912/Untitled.png)

Baseado no teorema de Bayes

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cda6bf8c-b93a-4a6e-b814-decbf7a6ebf9/Untitled.png)

## Como estimar essas probabilidades

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e050599d-d270-473f-8399-8ffdb72a5150/Untitled.png)

## Cadeia de Markov → Andrei Markov

- Simplificando a suposição

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/daf08c0c-5a85-4b34-93e1-a66465b4f21d/Untitled.png)

- Ou talvez

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9b60f9b-7dfc-40e4-89cf-1fd237ac7c18/Untitled.png)

- Presume:
    - Um comportamento futuro de um sistema dinâmico apenas depende da história recente
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e233e804-5869-4a6c-94ce-9d1e11c61f6c/Untitled.png)
    

> Em vez de calcular a probabilidade de uma palavra dada sua história inteira, podemos aproximar a história apenas pelas últimas palavras.
> 

# Bigram Model

- Aproxima a probabilidade, qual aprobabilidade de uma palavra acontecer dado a anterior

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cda8c2bb-621d-4b1b-b7d8-0d4a801d26c5/Untitled.png)

- de uma palavra dada todas as palavras previas
- pela probabilidade condicional de uma palavra precedente

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cac3ef6-c9e0-46fa-99c7-260d66e38b72/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69e287d7-e981-461b-b15c-e8b67fca6aeb/Untitled.png)

# N-gram

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/02f67c61-b319-4236-8f83-d2928607513e/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/54cc6483-7869-419f-a441-6daaeb14b874/Untitled.png)

1. Unigram → Modelo de Markov de primeira ordem
2. Bigram, Digram →Modelo de Markov de segunda ordem
3. Trigram
4. 4-gram
5. 5-gram
- Sequência contígua de N elementos
- Comumente obtida (analizada) de um corpus
- Quanto mais aumenta o n-grama probabilidade de ocorrência das palavras aumenta

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e70fddfb-176c-45b0-8305-f697a3d6127c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cf33720-d5fd-45af-8859-ae375197b74b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce401d9c-a6e6-4cab-b2f9-0d1f979280a8/Untitled.png)

# Exemplo You Learn - Alanis Morissette

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cb6ac0f-1843-416a-b6ce-747a571f94ee/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e4c094b4-733d-4c15-b748-6fd84fd956f8/Untitled.png)

Em geral é um modelo insuficiente de linguagem

# Estimating bigram probabilities

The Maximum Likelihood Estimate

getting counts from a normalize corpus

normalizing to [0,1]

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/66b9d657-5715-4135-8f65-14dd5dcef02d/Untitled.png)

## Ler o capítulo 2 do livro do jurafsky

Quanto maior o número da matriz mais a matriz vai ser esparsa 

# Raw bigram probabilities

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8e3df56-4fff-46a1-b011-b213afddf778/Untitled.png)

# Language Modeling Toolkits

- SRILM
    - c++
    
    [STAR Laboratory: SRI Language Modeling Toolkit](http://www.speech.sri.com/projects/srilm/)
    
- KenLM
    
    [kenlm . code . Kenneth Heafield](https://kheafield.com/code/kenlm/)
    
- Google N-gram Release, August 2006

[All Our N-gram are Belong to You](https://ai.googleblog.com/2006/08/all-our-n-gram-are-belong-to-you.html)

[https://books.google.com/ngrams](https://books.google.com/ngrams)

## N-Grams Modelos em Português

[https://www.ngrams.info/](https://www.ngrams.info/)

# Train and Test Corpora

- Modelo de Linguagem
    - Trained in a large corpus of text to estimate good parameters values
    - evaluetad based on its ability to predict a high probability for a disjoint (held-out) test corpus
- Idealmente
- Talvez precise adaptar um modelo geral para um modelo de contagem pequeno dos novos dados adicion

Frases que estavam no conjunto de treinamento não devem ser incluídas no conjunto de testes

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/871602c0-4a8b-419a-824d-61e6f3db30df/Untitled.png)

# Palavras desconhecidas

Como lidar com palavras que não apareceram nos dados de treinamento

out of vocabulary (OOV) words

Incluem um explícito símbolo para uma palavra desconhec

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d7a61175-49d4-4c70-9813-2123cb0cb4b1/Untitled.png)

# Avaliar a qualidade do modelo

1. Extrinsico → mais complicada de fazer
    1. Avalia o usuo do modelo no final da aplicação()
    2. realistica
    3. cara
2. Intrísico → calcular uma medida que representa a habilidade do modelo
    1. avalia a abalidade do modelo no test do corpus
    2. menos realista
    3. cheaper
3. Verificar se pelo menos uma avaliação intríseca se correlaciona com um uma extrínsica

# Verificar quão bom o meu modelo é

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a7ae760-c276-403a-9def-a508bc8fd73f/Untitled.png)

# Não usar o dado de treinamento no test set

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5943b8ab-45c1-4de4-9f66-a1096834d673/Untitled.png)

# Avaliação de Extrinsica N-gram Models

 

- Melhor avaliação para comparar modelos A e B
    - colocar cada modelo em uma tarefa
    - spelling corrector, speech recognizer, MR system
- Rodar a tarefa, pegar a acurácia para A  e para B

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4c39561b-cf2a-401f-bce1-0435f4667494/Untitled.png)

- Comparar a acurácia de A e B

# Métrica PP - Perplexity

Não conhecia os dados e mesmo assim o modelo se comportou bem

QUanto menor a perplexidade melhor

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/92fb004e-d073-4d10-b14c-4cc21fe90b55/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b4b65520-fe0c-40d1-8247-9c60a6676b23/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a211ac1-afeb-4955-9190-614de860f465/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14a0621b-71e9-4667-9b61-805f9789a9a1/Untitled.png)

Quanto maior o contexto maiores serão as frases e mais coerentes

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/84df7b8c-d731-4f38-8b07-8fd2eec18883/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d2060ea0-0155-46d4-907b-f96087318cb2/Untitled.png)

# Corpus Dependency

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d9ab309e-8f31-4e64-a1bd-b3c962bcd8ef/Untitled.png)

Os modelos representam as características do Corpus

# Perigos do Overfiting

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45139067-ed50-464e-90ee-95ea7af09eed/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8fb587a-3beb-4fca-af68-e1390fabd05c/Untitled.png)

# Lidar com zeros é chamado de suavizção
