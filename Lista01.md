## LISTA 01 – Exercícios -- Disciplina: Tec Impl BDs

### Alocação de Memória/Arquivo

1. Sobre sistema de alocação em disco, a alocação contígua permite trabalhar com 3 estratégias de alocação: first-fit, best-fit, worst-fit. A descrição correta para cada estratégia é:

    **Item A. &#9744;**

    **Best-fit:** o primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.

    **First-fit:** seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.

    **Worst-fit:** o maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.

    **Item B. &#9745;**

    **First-fit:** o primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.

    **Best-fit:** seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.

    **Worst-fit:** o maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.

    **Item C. &#9744;**

    **Best-fit:** o primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.

    **Worst-fit:** seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.

    **Fist-fit:** o maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.

    **Item D. &#9744;**

    **Worst-fit:** o primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.

    **First-fit:** seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.

    **Best-fit:** o maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.

2. Das principais estratégias de realocação de páginas que podem ser utilizadas pelo sistema operacional existe uma cuja implementação é bastante simples, pois necessita apenas da implementação do conceito de fila. Nesta estratégia as páginas mais antigas ficam no início da fila enquanto as mais
recentes no final. Estamos nos referindo à estratégia denominada:

    A. Aleatória &#9745;
    B. FIFO &#9744;
    C. LRU &#9744;
    D. NRU &#9744;
    E. LFU &#9744;

3. O algoritmo LRU (Least Recently Used) é utilizado em sistemas de bancos de dados como método de substituição de páginas. Considera o seguinte cenário: 4 páginas são alocadas na memória principal simultaneamente. Após a seguinte sequencia de requisição das páginas 4, 7, 5, 7, 6, 7, 10, 4, 8, 5, 8, 6, 8, 11, 4, 9, 5, 9, 6, 9, 12, 4, 7, 5, 7, qual será a taxa de não acerto? Justifique sua resposta.

Sequencias de paginas: 4, 7, 5, 7, 6, 7, 10, 4, 8, 5, 8, 6, 8, 11, 4, 9, 5, 9, 6, 9, 12, 4, 7, 5, 7

**Memória de 4 paginas**

|     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 4   | 7   | 5   | 7   | 6   | 7   | 10  | 4   | 8   | 5   | 8   | 6   | 8   | 11  | 4   | 9   | 5   | 9   | 6   | 9   | 12  | 4   | 7   | 5   | 7   |
| m   | m   | m   | h   | m   | h   | m   | h   | h   | h   | m   | h   | m   | h   | h   | h   | h   | m   | h   | m   | h   | h   | h   | h   | m   |

Lista de pagina chamadas: 4 7 5 7
-> hit 4 7 5
-> miss 7

Lista paginas na memória: 4 5 7 -> Memoria tem espaço ref > 6
-> hit 4 7 5 6
-> miss 7

Lista paginas na memória: 4 5 7 6 -> Memoria cheia ref > 7
-> hit 4 7 5 6
-> miss 7 7

Lista paginas na memória: 4 5 6 7 -> Memoria cheia ref > 10
-> hit 4 7 5 6
-> miss 7 7

Lista paginas na memória: 5 6 7 10 -> Memoria cheia ref > 4
-> hit 4 7 5 6 10
-> miss 7 7

Lista paginas na memória: 6 7 10 4 -> Memoria cheia ref > 8
-> hit 4 7 5 6 10 4
-> miss 7 7

Lista paginas na memória: 7 10 4 8 -> Memoria cheia ref > 5
-> hit 4 7 5 6 10 4 8
-> miss 7 7

Lista paginas na memória: 10 4 8 5 -> Memoria cheia ref > 8
-> hit 4 7 5 6 10 4 8 5
-> miss 7 7

Lista paginas na memória: 10 4 5 8 -> Memoria cheia ref > 6
-> hit 4 7 5 6 10 4 8 5
-> miss 7 7 8

Lista paginas na memória: 4 5 8 6 -> Memoria cheia ref > 8
-> hit 4 7 5 6 10 4 8 5 6
-> miss 7 7 8

Lista paginas na memória: 4 5 6 8 -> Memoria cheia ref > 11
-> hit 4 7 5 6 10 4 8 5 6
-> miss 7 7 8 8

Lista paginas na memória: 5 6 8 11 -> Memoria cheia ref > 4
-> hit 4 7 5 6 10 4 8 5 6 11
-> miss 7 7 8 8

Lista paginas na memória: 6 8 11 4 -> Memoria cheia ref > 9
-> hit 4 7 5 6 10 4 8 5 6 11 4
-> miss 7 7 8 8

Lista paginas na memória: 8 11 4 9 -> Memoria cheia ref > 5
-> hit 4 7 5 6 10 4 8 5 6 11 4 9
-> miss 7 7 8 8

Lista paginas na memória: 11 4 9 5 -> Memoria cheia ref > 9
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5
-> miss 7 7 8 8

Lista paginas na memória: 11 4 5 9 -> Memoria cheia ref > 6
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5
-> miss 7 7 8 8 9

Lista paginas na memória: 4 5 9 6 -> Memoria cheia ref > 9
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6
-> miss 7 7 8 8 9

Lista paginas na memória: 4 5 6 9 -> Memoria cheia ref > 12
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6
-> miss 7 7 8 8 9 9

Lista paginas na memória: 5 6 9 12 -> Memoria cheia ref > 4
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6 12
-> miss 7 7 8 8 9 9

Lista paginas na memória: 6 9 12 4 -> Memoria cheia ref > 7
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6 12 4
-> miss 7 7 8 8 9 9

Lista paginas na memória: 9 12 4 7 -> Memoria cheia ref > 5
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6 12 4 7
-> miss 7 7 8 8 9 9

Lista paginas na memória: 12 4 7 5 -> Memoria cheia ref > 7
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6 12 4 7 5
-> miss 7 7 8 8 9 9

Lista paginas na memória: 12 4 5 7 -> Memoria cheia
-> hit 4 7 5 6 10 4 8 5 6 11 4 9 5 6 12 4 7 5
-> miss 7 7 8 8 9 9 7

Taxa de acerto ${numeros de page Faul / numeros de paginas}$

**Total de pagefoul:** $18/25=0,72$ => aproximadamente 72%

4. Suponha que o esquema adotado para gerenciamento de memória de um determinado SGBD seja baseado na estratégia de working sets - W(t,Δ), com política de re-alocação de página do tipo LRU – Least Recently Used e Δ = 3. Nessas condições, um determinado processo apresentou a seguinte seqüência de referências a páginas: 24, 15, 18, 23, 24, 18, 17, 18, 24, 17, 17, 15, 24, 17, 24 e 18. Calcule a taxa de acerto, justificando a sua resposta.

5. Na estratégia de alocação indexada de espaço em disco, os ponteiros para os blocos de dados de um arquivo podem ser armazenados em um bloco de índices. No caso de arquivos com grande tamanho, o tamanho de um bloco de índices pode não ser suficiente para armazenar todos os índices. Explique,
justificando a sua resposta, uma abordagem para amenizar o problema citado anteriormente (blocos de índices não suficientes para armazenar todos os índices).

6. Discos magnéticos modernos armazenam mais setores nas trilhas externas do que nas internas. Dado que:

* a velocidade de rotação é constante.

* a velocidade de transferência de dados sequencial é maior nas trilhas externas.

* o tempo de procura e retardo rotacional não se modificam.

  Dados este cenário, explique (justificando a sua resposta) boas estratégias para alocação de arquivos de acordo com os seguintes padrões de acesso:

  A Frequente acesso randômico a pequenos arquivos;
  B Busca sequencial em um grande arquivo;
  C Acesso randômico a um grande arquivo através de um índice;
  D Leitura sequencial de um pequeno arquivo;
