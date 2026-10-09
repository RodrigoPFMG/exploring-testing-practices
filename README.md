# Explorando Práticas de Teste

Neste exercício, vamos explorar práticas de teste em sistemas reais utilizando a ferramenta [TestMiner](https://andrehora.github.io/testminer).

O TestMiner permite visualizar e analisar testes de software em repositórios do GitHub, fornecendo dados sobre como os projetos organizam seus testes, como eles evoluem entre versões e quais bibliotecas de teste são utilizadas.
Explore a ferramenta antes de começar para se familiarizar com seu funcionamento.

Mais detalhes no GitHub da ferramenta: https://github.com/andrehora/testminer.

---

## Passo 1: Selecionar um repositório

Escolha um repositório real que possua testes de software.
Abaixo estão alguns links para ajudá-lo a encontrar projetos interessantes:

- Python: https://github.com/topics/python?l=python
- JavaScript: https://github.com/topics/javascript?l=javascript
- TypeScript: https://github.com/topics/typescript?l=typescript
- Java: https://github.com/topics/java?l=java

- Tópicos: [ai](https://andrehora.github.io/testminer/#topic:ai), [llm](https://andrehora.github.io/testminer/#topic:llm), [api](https://andrehora.github.io/testminer/#topic:api), [nodejs](https://andrehora.github.io/testminer/#topic:nodejs), [android](https://andrehora.github.io/testminer/#topic:android)

- Por organização: [Google](https://andrehora.github.io/testminer/#google), [Microsoft](https://andrehora.github.io/testminer/#microsoft), [Apple](https://andrehora.github.io/testminer/#apple), [Facebook](https://andrehora.github.io/testminer/#facebook), [Netflix](https://andrehora.github.io/testminer/#netflix), 
[GitHub](https://andrehora.github.io/testminer/#github), [Apache](https://andrehora.github.io/testminer/#apache), [HuggingFace](https://andrehora.github.io/testminer/#huggingface)

## Passo 2: Explorar o repositório selecionado

Busque o repositório escolhido no [TestMiner](https://andrehora.github.io/testminer) e analise os dados de teste gerados pela ferramenta.

## Passo 3: Explicar uma prática de teste

Escolha uma prática ou dado de teste relevante e explique com suas próprias palavras.

---

## Instruções de entrega

1. Faça um `fork` deste repositório (saiba mais sobre forks [aqui](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)).
2. Responda às questões abaixo diretamente neste arquivo `README.md` do seu fork. Pode adicionar imagens para enriquecer sua explicação.
3. No Moodle, submeta apenas a URL do seu fork.

---

## Respostas

Repositório: `https://github.com/apache/superset`

URL TestMiner: `https://andrehora.github.io/testminer/#apache/superset`

Explicação:

### Visão geral dos testes

Para realizar a análise, utilizei o TestMiner, que classifica os arquivos do projeto de acordo com sua função. O Superset possui 7445 arquivos de código, dos quais 2512 são testes. Além disso, foram identificados 286 test helpers, 55 fixtures, 5 testes E2E e apenas 1 benchmark. Também é possível observar que boa parte dos testes se concentra na pasta superset-frontend, que utiliza bibliotecas como jest e playwright. Neste trabalho, o foco foi o lado Python do projeto.

### Evolução dos testes

<img width="730" height="374" alt="Gráfico de evolução dos testes no TestMiner" src="https://github.com/user-attachments/assets/1e6746c9-e140-4ff8-aa04-b46b996cd647" />


Ao analisar o histórico de testes, as versões aparecem no gráfico na ordem 0.2.0, 3.1.2 e 2021.41.0. Porém, ao consultar as datas de cada uma, constatei que a ordem cronológica é diferente: a versão 0.2.0 é de setembro de 2015, a 2021.41.0 é de outubro de 2021 e a 3.1.2 é de abril de 2024. Dessa forma, é possível concluir que o número de testes cresceu ao longo do tempo, passando de 0 em 2015 para 532 em 2021 e 983 em 2024. Já os benchmarks permaneceram estáveis, com apenas 1 em 2021 e 1 em 2024, o que indica que o projeto priorizou testes funcionais em vez de medições de desempenho.

### Bibliotecas de teste em Python

Ao analisar as dependências de teste do projeto, observa-se que o Superset utiliza o pytest como base para escrever e executar seus testes. Em torno dele, o projeto adota outras bibliotecas que indicam práticas específicas.

A biblioteca freezegun permite fixar a data e a hora durante a execução de um teste. Isso é importante para códigos que dependem do tempo, pois, sem esse controle, o resultado poderia variar a cada execução. Assim, o uso dessa biblioteca indica uma preocupação com testes determinísticos.

Já o pytest-xdist permite executar os testes em paralelo, em diferentes processos. Como o projeto possui mais de 2500 testes, essa prática reduz o tempo total de execução e indica uma preocupação com a velocidade da suíte.

Por fim, é possível relacionar essas práticas ao crescimento observado no número de testes. À medida que a quantidade de testes aumenta, tornam-se mais relevantes tanto a previsibilidade dos resultados quanto o tempo necessário para executá-los.
