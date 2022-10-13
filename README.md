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
- [Arquivos de Entrada](#arquivos-de-entrada)

# Introdução

Dado um grafo não direcionado e ponderado, uma Árvore Geradora Mínima (Minimum Spanning Tree) é uma subárvore desse grafo que conecta todos os vértices e apresenta a menor soma dos pesos de todas as arestas possível, ou seja, é a árvore geradora do grafo com menor peso dentre todas as árvores geradoras possíveis onde o peso da árvore é a soma de todos os pesos de suas arestas.


## Algoritmo de Kruskal
O algoritmo de Kruskal é um algoritmo guloso para encontrar a Árvore Geradora Mínima que tem como entrada um grafo G(V,E) não direcionado e conexo. Seu funcionamento ocorre da seguinte maneira:
1.	Cria-se a Árvore Geradora Mínima vazia.
2.	Organiza-se todas as arestas do Grafo em ordem crescente de peso.
3.	Pega-se a aresta com o menor peso e a adiciona à Árvore Geradora. Se ao ser adicionada, a aresta gerar um ciclo, rejeita-se essa aresta.
4.	Continua-se adicionando as arestas em ordem crescente de peso até que todos os vértices sejam alcançados.
 

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

## Arquivos de entrada 

Os seguintes exemplos se encontram na pasta [myfiles](https://github.com/leticiatavaresds/MSTKruskal/tree/master/myfiles):

| Nome Arquivo | Descrição                                                                                                                                               | Saída                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| ddesconexo   | Exemplo de grafo direcionado e desconexo.                                                                                                               | Impressão do grafo subjacente correspondente. Informa que o grafo subjacente não é conexo e não é possível encontrar a árvore geradora mínima. |
| dinvalido    | Exemplo de grafo direcionado contendo duas arestas paralelas de mesmo sentido com pesos diferentes.                                                     | Aviso de que o aquivo está corrompido.                                                                                    |
| dinvalido2   | Exemplo de grafo direcionado contendo duas arestas paralelas de sentidos contrários com pesos diferentes.                                               | Aviso de que o aquivo está corrompido.                                                                                    |
| dinvalido3   | Exemplo de grafo direcionado contendo dois laços de sentidos contrários com pesos diferentes.                                                           | Aviso de que o aquivo está corrompido.                                                                                    |
| dnormal      | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes.                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal1     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. Apresenta arestas paralelas de direções diferentes com pesos iguais. | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal2     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. Apresenta arestas paralelas de direções iguais com pesos iguais.     | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| dnormal3     | Exemplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes.                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gaparalela   | Grafo não direcionado e conexo que apresenta arestas paralelas.                                                                                         | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gdesconexo   | Grafo não diecionado e não conexo.                                                                                                                      | Informa que o grafo não é conexo e não é possível encontrar a árvore geradora mínima.                              |
| glaço        | Grafo não direcionado e conexo que apresenta laço.                                                                                                      | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |
| gnormal      | Grafo não diecionado, conexo, sem laços e sem arestas paralelas.                                                                                             | Impressão do grafo subjacente correspondente e de sua árvore geradora mínima.                                                  |

[⬆ Voltar ao topo](#algoritmo-de-kruskal-em-java)<br>
