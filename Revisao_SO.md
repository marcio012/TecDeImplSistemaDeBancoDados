## Sistema de Bando de Dados 2
### Prof. Aguiar

## Notas de Aulas

### Revisão de SO

#### Alocação de memória

* Alocação Contígua Simples
  * implementado nos primeiros sistemas operacionais

  * a memória principal é dividida em duas partes, uma para o sistema operacional e a outra para o programa do usuário.

  * não permite a utilização eficiente dos recursos do sistema, pois apenas um usuário pode dispor destes recursos.

  * todos os programas estão limitados ao tamanho da memória principal disponível para o usuário.

* Segmentação de Programas

  * dividir o programa em módulos.

  * execução independente de cada módulo, utilizando a mesma área de memória (overlay).

  * a grande vantagem da utilização desta técnica consiste em se poder executar programas maiores do que a memória física disponível.

* Alocação Particionada Estática

  * alocação particionada estática absoluta - todas as referências a endereços no programa são posições físicas na memória, ou seja, o programa só poderia ser  carregado a partir do endereço de memória especificado no seu próprio código.

  * alocação particionada estática relocável - todas as referências a endereços no programa são relativas ao início do código e não a endereços fixos na memória.

  * problema decorrente do esquema de alocação fixa de partições, é chamado fragmentação interna.

* Alocação Particionada Dinâmica
  
  * foi eliminado o conceito de partições de tamanho fixo.
  
  * programas utilizam apenas o espaço de que necessitam.

  * outro tipo de problema: fragmentação externa.
  
  * reunião de todos os blocos livres adjacentes.

  * realocação de todas as partições ainda ocupadas para a parte inicial da memória.

#### Estratégias de Alocação de Partição

* **Best-fit:** é escolhida a melhor partição, ou seja, aquela que deixa o menor espaço sem utilização. Uma grande desvantagem desta estratégia é que, como são alocados primeiramente as partições menores, deixando pequenos blocos, a fragmentação aparece mais rapidamente.

* **First-fit:** esta estratégia aloca o programa na primeira partição que o couber, independente do espaço livre que vai deixar. Das três estratégias, esta é a mais rápida, consumindo menos recursos do sistema.
  
* **Worst-fit:** aloca o programa na pior partição, ou seja, aquela que deixa o maior espaço livre. Esta técnica, apesar de aproveitar primeiro as partições maiores, acaba deixando espaços livres grandes o suficiente para que outros programas utilizem esses espaços, permitindo que um número maior de processos se utilizem da memória, diminuindo ou retardando a fragmentação.

#### Técnicas de Gerenciamento de Memória

**Swapping**

* o sistema operacional “descarrega” um processo da memória para uma área especial em disco, chamada arquivo de swap.

 -o problema dessa técnica é que pode provocar um número excessivo de acesso à memória secundária (disco), levando o sistema a uma queda de desempenho.

**Memória Virtual**

* a utilização da técnica de overlay para contornar o problema do tamanho dos programas é de difícil implementação na prática e nem sempre uma solução garantida e eficiente.

* o conceito de memória virtual baseia-se em não vincular o endereçamento feito pelo programa aos endereços físicos da memória principal.

* vantagem desta técnica é permitir um número maior de processos compartilhando a memória principal, já que apenas partes de cada processo estarão residentes. Isto leva a uma utilização mais eficiente do processador, além de minimizar (ou quase eliminar) o problema da fragmentação.
