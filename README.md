Relatório Técnico: Implementação do Algoritmo de Prim para a Geração de Árvores Geradoras Mínimas
Autor: Leo Thirso
Disciplina: Teoria dos Grafos
Professor: Florencio Mendes Oliveira Filho

1. Introdução
Este relatório detalha o desenvolvimento de uma aplicação computacional para a determinação da Árvore Geradora Mínima (MST - Minimum Spanning Tree) em grafos ponderados e não direcionados. O projeto, realizado no âmbito da disciplina de Teoria dos Grafos, aplica o clássico algoritmo de Prim a um conjunto de grafos definidos por matrizes de adjacência. O objetivo central é não apenas calcular a MST e seu custo, mas também fornecer uma visualização clara que facilite a análise comparativa entre o grafo original e sua respectiva árvore mínima.

2. Metodologia e Ferramentas Utilizadas
A solução foi implementada na linguagem Python, aproveitando o poder de bibliotecas especializadas que abstraem tarefas complexas e permitem focar na lógica do problema.

2.1. Ferramentas de Software

Pandas: Utilizada para a leitura e manipulação eficiente dos dados de entrada, que foram fornecidos como matrizes de adjacência em arquivos no formato Excel (.xlsx).
NetworkX: Biblioteca fundamental para a modelagem, manipulação e estudo de grafos. Foi empregada para construir as estruturas de grafo a partir das matrizes e, crucialmente, para executar o algoritmo de Prim.
Matplotlib: Empregada para a renderização gráfica dos resultados, permitindo a criação de visualizações comparativas e informativas.
Glob e OS: Bibliotecas auxiliares utilizadas para a localização e gerenciamento automatizado dos arquivos de dados no sistema de arquivos.
2.2. Processamento e Modelagem do Grafo

O núcleo lógico do projeto reside na função processar_matriz_com_prim. Esta função é responsável por converter a representação tabular de um grafo (matriz) em uma estrutura de dados manipulável pelo NetworkX. As etapas são:

Limpeza e Preparação da Matriz: O DataFrame lido do arquivo Excel passa por um pré-processamento. A primeira coluna, geralmente um índice redundante, é removida. Os índices de linhas e colunas são então normalizados para valores inteiros, que servirão como identificadores únicos para os vértices (nós) do grafo.
Construção do Grafo: Um grafo não direcionado vazio é instanciado. O programa itera sobre a matriz de adjacência, adicionando uma aresta ponderada entre dois vértices sempre que um peso válido (não nulo) é encontrado. Para garantir a eficiência e evitar a duplicidade de arestas em um grafo não direcionado, a iteração considera apenas a triangular superior da matriz (onde índice da linha < índice da coluna).
2.3. Aplicação do Algoritmo de Prim

Com o grafo original (G) devidamente construído, a Árvore Geradora Mínima é calculada através da função networkx.minimum_spanning_tree(G, algorithm='prim'). Esta função encapsula toda a complexidade da implementação do algoritmo, retornando um novo objeto de grafo (mst) que contém apenas as arestas da árvore mínima. Subsequentemente, o custo total da MST é calculado pela soma dos pesos de todas as arestas contidas neste novo grafo.

3. Resultados e Análise Visual
Para apresentar os resultados de forma clara, um script principal orquestra a execução para todos os arquivos de dados encontrados. Para cada arquivo, a função de processamento é chamada, e os resultados (grafo original, MST e custo) são passados para uma função de visualização dedicada, a visualizar_comparacao_mst.

Esta função gera uma figura contendo dois subplots lado a lado:

Grafo Original (Esquerda): Exibe a topologia completa do grafo, com todos os seus vértices e arestas, oferecendo um panorama geral das conexões possíveis.
Árvore Geradora Mínima (Direita): Apresenta a MST, destacando suas arestas com uma cor distinta (vermelho) para fácil identificação. Os pesos de cada aresta da MST são exibidos, e o custo total da árvore é informado no título do subplot.
O layout dos nós é gerado de forma consistente para ambos os subplots por meio do algoritmo spring_layout, garantindo que a comparação visual seja direta e intuitiva. O título principal da figura identifica o arquivo de origem, assegurando a rastreabilidade da análise.

4. Conclusão
O objetivo proposto foi alcançado com sucesso. A aplicação desenvolvida é capaz de processar múltiplas matrizes de adjacência, calcular a Árvore Geradora Mínima e seu custo utilizando o algoritmo de Prim, e apresentar os resultados de maneira visualmente eficaz. A separação da lógica de processamento e de visualização em funções modulares resultou em um código limpo, legível e de fácil manutenção. O produto final não só resolve o problema computacional, mas também serve como uma valiosa ferramenta didática para a compreensão prática do funcionamento e do impacto do algoritmo de Prim na otimização de redes.
