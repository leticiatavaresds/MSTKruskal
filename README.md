## 1.	Árvore Geradora Mínima
Dado um grafo não direcionado e ponderado, uma Árvore Geradora Mínima (Minimum Spanning Tree) é uma subárvore desse grafo que conecta todos os vértices e apresenta a menor soma dos pesos de todas as arestas possível, ou seja, é a árvore geradora do grafo com menor peso dentre todas as árvores geradoras possíveis onde o peso da árvore é a soma de todos os pesos de suas arestas.


## 2.	Algoritmo de Kruskal
O algoritmo de Kruskal é um algoritmo guloso para encontrar a Árvore Geradora Mínima que tem como entrada um grafo G(V,E) não direcionado e conexo. Seu funcionamento ocorre da seguinte maneira:
1.	Cria-se a Árvore Geradora Mínima vazia.
2.	Organiza-se todas as arestas do Grafo em ordem crescente de peso.
3.	Pega-se a aresta com o menor peso e a adiciona à Árvore Geradora. Se ao ser adicionada, a aresta gerar um ciclo, rejeita-se essa aresta.
4.	Continua-se adicionando as arestas em ordem crescente de peso até que todos os vértices sejam alcançados.
 

## 3.	Implementação do Algoritmo de Kruskal
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



### 3.1	Algoritmo de Kruskal utilizando Union-Find
Com a utilização do Union-Find, a Árvore Geradora Mínima é dada por um processo de unificação onde em cada iteração pega-se 
uma aresta da lista de arestas ordenadas do grafo e aplica-se o método Find que verifica se as extremidades da aresta pertencem 
à subárvores diferentes (aresta não gerou um ciclo), se sim, essas subárvores são combinadas pelo método Union, e a aresta é adicionada à resposta. 
Depois de iterar sobre todas as arestas, todos os vértices pertencerão à mesma subárvore e a Árvore Geradora Mínima será dada. 


### 3.2	Algoritmo de Kruskal utilizando Busca em Profundidade
Com a utilização da Busca e Profundidade, a Árvore Geradora Mínima é dada por um processo de adição e remoção de arestas. 
Em cada iteração pega-se uma aresta da lista de arestas ordenadas do grafo e a adiciona à Árvore Geradora Mínima (que se ininica vazia), 
verifica-se então se a Árvore permanece acíclica através de uma busca em profundidade na árvore, se sim, a aresta permanece, se não, é removida. 

## 4 - Arquivos de entrada na pasta myfiles

O seguintes exemplos se encontram na pasta myfiles:

ddesconexo - Exeplo de grafo direcionado e desconexo. O programa imprime o grafo subjacente correspondente, mas diz que não é 
conexo e não é possível encontrar a árvore geradora mínima.

dinvalido - Exeplo de grafo direcionado, mas com duas arestas paralelas de mesmo sentido com pesos diferentes. O programa imprime que
o aquivo está corrompido.

dinvalido2 - Exeplo de grafo direcionado, mas com duas arestas paralelas de sentidos contrários com pesos diferentes. O programa imprime que
o aquivo está corrompido.

dinvalido3 - Exeplo de grafo direcionado, mas com dois laços de sentidos contrários com pesos diferentes. O programa imprime que
o aquivo está corrompido.

dnormal - Exeplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

dnormal1 - Exeplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. 
Apresenta arestas paralelas de direções diferentes com pesos iguais. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

dnormal2 - Exeplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. 
Apresenta arestas paralelas de direções iguais com pesos iguais. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

dnormal3 - Exeplo de grafo direcionado, conexo e sem arestas paralelas com pesos diferentes. 
Apresenta laços paralelos com pesos iguais. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

gaparalela - Gafo não direcionado e conexo que apresenta arestas paralelas. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

gdesconexo - Grafo não diecionado e não conexo. O programa imprime que o grafo não é 
conexo e assim não é possível encontrar a árvore geradora mínima.

glaço - Gafo não direcionado e conexo que apresenta laço. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.

gnormal - Grafo não diecionado, conexo sem laços e arestas paralelas. O programa imprime o grafo subjacente correspondente
e sua árvore geradora mínima.


