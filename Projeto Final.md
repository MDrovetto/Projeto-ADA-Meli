  Marketplace Priority Sorter (MPS)
O VelozMart processa 10.000 pedidos diários com picos de 50.000 em datas festivas (Black Friday). Cada pedido tem:

priorityScore (0-100)
dispatchWindow (minutos restantes)
sizeCategory (P/M/G)
O algoritmo escolhido foi o Merge Sort, devido à sua estabilidade, especialmente em relação ao armazenamento de pedidos. Assim, conseguimos manter a ordem de chegada dos pedidos mesmo que tenham a mesma prioridade.

Pedidos são acumulados até o horário de saída da Central. Antes de cada expedição, o sistema pode ordenar todos os pedidos do lote de uma vez. Toda vez que um pedido é finalizado o sistema atualiza, disparando uma nova ordenação se necessário.

Algoritmo (Pseudocódigo)
Code
Função ordenarPedidos(lista):
  - Se a lista tiver 0 ou 1 pedido:
    - Já está ordenada, então devolve do jeito que está.
  - Se tiver mais de 1 pedido:
    - Divide a lista em duas partes.
    - Ordena cada parte separadamente.
    - Junta as duas partes usando os critérios de prioridade.

Função juntarListas(parteA, parteB):
  - Cria uma nova lista vazia para colocar os pedidos em ordem.
  - Compara sempre o primeiro pedido de cada parte:
    - Coloca o mais importante na nova lista.
    - Tira esse pedido da parte de onde ele veio.
  - Repete até que todas as partes estejam vazias.
  - Depois, devolve a lista final com todos os pedidos em ordem.
Merge Sort

Vantagens do Merge Sort
Mantém a ordem de chegada dos pedidos com a mesma prioridade.
Desempenho garantido de O(n log n) em todos os casos, inclusive em picos como a Black Friday, o que evita lentidão inesperada.
É simples montar uma função de comparação com peso para priorityScore, dispatchWindow e sizeCategory.
Desvantagens do Merge Sort
Sempre que chega um novo pedido ou o tempo muda, o algoritmo precisa reordenar toda a lista, o que pode ser custoso se ocorrer com muita frequência como no caso de deliverys como iFood, 99.
Próximos Passos - Implementar melhorias do sistema
Melhorar o peso dos critérios de prioridade usando o histórico de pedidos para melhorar a performance e reduzir o atraso.
Realizar testes A/B com uma parte dos pedidos utilizando outros algoritmos como priority queue para entender vantagens e desvantagens em cenário real.
Implementar métricas para acompanhar gargalos em tempo real e realizar alterações quando necessário.
