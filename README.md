# Algoritmo de Kruskal em Java


![GitHub repo size](https://img.shields.io/github/repo-size/leticiatavaresds/MSTKruskal?color=a21360&style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/leticiatavaresds/MSTKruskal?color=a21360&style=for-the-badge)
![Made With](https://img.shields.io/badge/Made%20With-Java-lightgrey?color=a21360&style=for-the-badge)
![GitHub repo file count](https://img.shields.io/github/directory-file-count/leticiatavaresds/MSTKruskal?color=a21360&style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/leticiatavaresds/MSTKruskal?color=a21360&style=for-the-badge)

## Índice

- [Introdução](#introdução)
  - [Algoritmo de Kruskal](#algoritmo-de-kruskal)
- [Implementação do Algoritmo de Kruskal](#implementação-do-algoritmo-de-kruskal)
  - [Implementação por Union-Find](#implementação-por-union-find)
  - [Implementação por Busca em Profundidade](#implementação-por-busca-em-profundidade)
- [Execução](#execução)
- [Arquivos de Entrada](#arquivos-de-entrada)
- [Licença](#licença)

# Introdução

Dado um grafo não direcionado e ponderado, uma Árvore Geradora Mínima (Minimum Spanning Tree) é uma subárvore desse grafo que conecta todos os vértices e apresenta a menor soma dos pesos de todas as arestas possível, ou seja, é a árvore geradora do grafo com menor peso dentre todas as árvores geradoras possíveis onde o peso da árvore é a soma de todos os pesos de suas arestas.


## Algoritmo de Kruskal
O algoritmo de Kruskal é um algoritmo guloso para encontrar a Árvore Geradora Mínima que tem como entrada um grafo G(V,E) não direcionado e conexo. Seu funcionamento ocorre da seguinte maneira:
1.	Cria-se a Árvore Geradora Mínima vazia.
2.	Organiza-se todas as arestas do Grafo em ordem crescente de peso.
3.	Pega-se a aresta com o menor peso e a adiciona à Árvore Geradora. Se ao ser adicionada, a aresta gerar um ciclo, rejeita-se essa aresta.
4.	Continua-se adicionando as arestas em ordem crescente de peso até que todos os vértices sejam alcançados.
 
[⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>
#	Implementação do Algoritmo de Kruskal
Para esse trabalho, o algoritmo de Kruskal foi implementado de duas formas diferentes, que serão melhor descritas abaixo, 
para a etapa de verificar se uma aresta será adicionada à árvore ou não. 
Pois como essa etapa consiste em verificar se a árvore gerada pela adição da aresta permanece acíclica, há mais de uma maneira de fazer, 
sendo as utilizadas aqui a verificação por Union-Find e a verificação por uma Busca em Profundidade. 
Contudo, a etapa de ordenar as arestas em ordem crescente de peso é a mesma para ambos os pesos, dada pelo método abaixo.

Antes de começar a análise da presença das arestas na árvore, o código primeiro verifica se o grafo dado como entrada é não direcionado e conexo, se sim, continua-se normalmente. Porém, se for um grafo não direcionado e não conexo, o algoritmo para e imprime uma mensagem de entrada inválida. Já se for direcionado, encontra-se seu subjacente. Se o grafo subjacente obtido não for conexo ou apresentar arcos paralelos de pesos diferentes, o algotritmo para e imprime uma mensagem de entrada inválida, senão, continua-se normalmente obtendo se assim a árvore geradora mínima do subjacente do digrafo dado como entrada. Assim, após verificação se a entrada é válida, ou seja, é um grafo não direcionado e conexo ou um grafo direcionado conexo sem arestas paralelas com pesos diferentes, o código segue para a etapa de obtenção da Árvore Geradora Mínima utilizando find-union ou busca em profundidade. 

Para a verificação se um grafo é conexo utiliza-se aqui uma busca em profundidade. Já para verificar se é direcionado, analisa-se se para todo par de vértice (v,u), se v é vizinho de u, u é vizinho de v e se o número de arcos (v,u) é igual ao de arcos (u,v) e apresentam os mesmos pesos, pois, por exemplo, o grafo:
1 = 2 1 
2 = 1 3 
é um grafo direcionado.

## Implementação por Union-Find
Com a utilização do Union-Find, a Árvore Geradora Mínima é dada por um processo de unificação onde em cada iteração pega-se 
uma aresta da lista de arestas ordenadas do grafo e aplica-se o método Find que verifica se as extremidades da aresta pertencem 
à subárvores diferentes (aresta não gerou um ciclo), se sim, essas subárvores são combinadas pelo método Union, e a aresta é adicionada à resposta. 
Depois de iterar sobre todas as arestas, todos os vértices pertencerão à mesma subárvore e a Árvore Geradora Mínima será dada. 


## Implementação por Busca em Profundidade
Com a utilização da Busca e Profundidade, a Árvore Geradora Mínima é dada por um processo de adição e remoção de arestas. 
Em cada iteração pega-se uma aresta da lista de arestas ordenadas do grafo e a adiciona à Árvore Geradora Mínima (que se ininica vazia), 
verifica-se então se a Árvore permanece acíclica através de uma busca em profundidade na árvore, se sim, a aresta permanece, se não, é removida.
Se encontra comentado para que o programa não imprima o resultado duplicado, mas pode ser descomentado no método MST.

[⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>

# Execução 


1. Instale Java (preferencialmente a versão mais recente)
2. Faça o download da pasta do projeto ou clone o repositório.
3. Execute o projeto "src". Ao executar, a seguinte saída será impressa:

```
Selecione o que deseja fazer:   
 0 Sair 
 1 Entrada por arquivo de texto
 2 Print do Grafo
 3 Escrever em Arquivo
 4 Excluir vértice
 5 Árvore Geradora Mínima
 
```
4. Deve-se selecionar a opção 1, informanco o nome do arquivo txt que contém o grafo que obrigatoriamente deve estar contido no diretório "ArqsEntrada". Ao selecionar a opção e informarmos o nome do arquivo, temos a seguinte resposta

```
1

Informe o nome do arquivo txt sem escrever a extensão (arquivo deve estar na pasta ArqsEntrada):
dnormal2

Arquivo lido com sucesso. O que deseja fazer agora?

 0 Sair
 1 Entrada por arquivo de texto
 2 Print do Grafo
 3 Escrever em Arquivo
 4 Excluir vértice
 5 Árvore Geradora Mínima
```
5. Se o arquivo foi lido com sucesso, basta então selecionar a opçào 5 que o programa irá avaliar o grafo dado e tentará gerar sua Árvore Geradora Mínima. No exemplo de execução abaixo, o programa informa que o grafo dado é direcionado, dessa forma, para gerar sua Árvore Geradora Mínima, obtém-se primeiramente seu Grafo Subjacente.
```

 O Grafo é direcionado. Para encontrar a Árvore Geradora Mínima foi obtido o seguinte Grafo Subjacente: 
----------------------------------------------------
***************** Grafo Subjacente *****************
----------------------------------------------------

Id do vértice: 0, Vizinhança:  1 peso:10 2 peso:6 3 peso:5
Id do vértice: 1, Vizinhança:  0 peso:10 3 peso:15
Id do vértice: 2, Vizinhança:  0 peso:6 3 peso:4
Id do vértice: 3, Vizinhança:  0 peso:5 1 peso:15 2 peso:4

 Grafo, grau máximo 3
----------------------------------------------------


-------------------------------------------------------
**************** Árvore Geradora Mínima ***************
-------------------------------------------------------

Id do vértice: 0, Vizinhança:  1 peso:10 3 peso:5
Id do vértice: 1, Vizinhança:  0 peso:10
Id do vértice: 2, Vizinhança:  3 peso:4
Id do vértice: 3, Vizinhança:  0 peso:5 2 peso:4

Grau máximo da MST: 2
Soma dos pesos das arestas da MST: 19

----------------------------------------------------
 Deseja fazer mais alguma coisa?

 1 - Sim
 0 - Não, Sair.
 
 
 ```
 [⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>
 
 ## Arquivos de entrada 

Os seguintes exemplos se encontram na pasta [ArqsEntrada](https://github.com/leticiatavaresds/MSTKruskal/tree/master/src/ArqsEntrada):


| Nome Arquivo | Descrição                                                                                                                                               | Saída                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| ddesconexo.txt   | Exemplo de grafo direcionado e desconexo.                                                                                                               | Impressão do grafo subjacente correspondente. Informa que o grafo subjacente não é conexo e não é possível encontrar a árvore geradora mínima. |
| dinvalido.txt    | Exemplo de grafo direcionado contendo duas arestas paralelas de mesmo sentido com pesos diferentes.                                                     | Aviso de que o aquivo está corrompido.                                                                                    |
| dinvalido2.txt   | Exemplo de grafo direcionado contendo duas arestas paralelas de sentidos contrários com pesos diferentes.                                               | Aviso de que o aquivo está corrompido.                                                                                    |
| dinvalido3.txt   | Exemplo de grafo direcionado contendo dois laços de sentidos contrários com pesos diferentes.                                                           | Aviso de que o aquivo está corrompido.                                                                                    |
| dnormal.txt      | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes.                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal1.txt     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. Apresenta arestas paralelas de direções diferentes com pesos iguais. | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal2.txt     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. Apresenta arestas paralelas de direções iguais com pesos iguais.     | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal3.txt     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes.                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gaparalelas.txt   | Grafo não direcionado e conexo que apresenta arestas paralelas.                                                                                         | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gdesconexo.txt   | Grafo não diecionado e não conexo.                                                                                                                      | Informa que o grafo não é conexo e não é possível encontrar a árvore geradora mínima.                              |
| glaço.txt        | Grafo não direcionado e conexo que apresenta laço.                                                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gnormal.txt      | Grafo não diecionado, conexo, sem laços e sem arestas paralelas.                                                                                             | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |

[⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>

![image](https://user-images.githubusercontent.com/34246743/195705451-9565fa42-c176-4a9d-9444-71876ff9172a.png)


# Licença

The MIT License (MIT) 2022 - Letícia Tavares. Leia o arquivo [LICENSE.md](https://github.com/leticiatavaresds/MSTKruskal/blob/master/LICENSE.md) para mais detalhes.

[⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>
