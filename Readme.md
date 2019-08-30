## Sistema de Bando de Dados 2
### Prof. Aguiar

> Nota de aula

## Teste

### Arquitertura de Três Camadas

O objetivo dessa arquitetura e separar as aplicações do usuário do banco de dados fisicos. Nessa arquitetura os esquemas são divididos em três níveis.

1. O Nível interno

    Descreve a estrutura do armazenamento físico do banco de dados, usa um modelo de dados físico e descreve os detalhes completos do armazenamento de dados e os caminhos de acesso.

2. O Nível conceitual

    Descreve a estrutura do banco de dados inteiro para o usuário, ele oculta os detalhes das estruturas de armazenamento físico e concentra-se na descrição das entidades.

3. O Nível externo

   Inclui uma serie de visões externos ou visões do usuário. Cada esquema externo descreve a parte do banco de dados em que um grupo de usuário em particular está interessado.

> A visualização em cada um dos níveis acima é descrita por um esquema, que é um esboço ou plano que descreve os registros, atributos e relacionamentos existentes na exibição.
> O termo visão, esquema são usados de forma intercambiável.
> Uma linguagem de definição de dados (DDL), é usada para definir os esquemas conceituais e externos.
> Os comandos da linguagem de consulta estruturada (SQL) são usados para descrever os aspectos do esquema físico (ou interno).
> As informações sobre os esquemas interno, conceitual e externo são armazenadas no catálogo do sistema.

#### Nível interno

Nível interno é a representação física do banco de dados no computador e essa visualização é encontrada no nível mais baixo de abstração do banco de dados.

Este nível indica como os dados serão armazenados no banco de dados e descreve as estruturas de dados, as estruturas de arquivos e os métodos de acesso a serem usados ​​pelo banco de dados.

Ele descreve a maneira como o SGDB e o sistema operacional recebem os dados no banco de dados. Logo abaixo do nível interno, há uma organização de dados no nível físico cuja implementação é coberta pelo nível interno para obter desempenho rotineiro e utilização do espaço de armazenamento.

O esquema interno define o nível interno (ou visualização). O esquema interno contém a definição do registro armazenado, o método de representação dos campos de dados (ou atributos), esquemas de indexação e hash e os métodos de acesso utilizados.

O nível interno fornece cobertura para as estruturas de dados e organizações de arquivos usadas para armazenar dados em dispositivos de armazenamento.

> Essencialmente, o esquema interno resume como as relações descritas no esquema conceitual são realmente armazenadas em dispositivos de armazenamento secundário, como discos e fitas. Ele faz interface com os métodos de acesso do sistema operacional (também chamados de técnicas de gerenciamento de arquivos para armazenar e recuperar registros de dados) para colocar os dados nos dispositivos de armazenamento, criar os índices, recuperar os dados e assim por diante. O nível interno preocupa-se com as seguintes atividades:

* Alocação de espaço de armazenamento para dados e armazenamento.
* Registro e descrições para armazenamento com tamanhos armazenados para itens de dados.
* Gravar posicionamento.
* Técnicas de compactação e criptografia de dados.

#### Nível Conceitual

O nível conceitual é o nível intermediário na arquitetura de três camadas. Nesse nível de abstração do banco de dados, todas as entidades e relacionamentos entre eles são incluídos. O nível conceitual fornece a visão da comunidade do banco de dados e descreve quais dados são armazenados no banco de dados e os relacionamentos entre os dados. Ele contém a estrutura lógica de todo o banco de dados, conforme visto pelo DBA. Uma visão conceitual representa todo o banco de dados de uma organização. É uma visão completa dos requisitos de dados da organização, independente de quaisquer considerações de armazenamento. O esquema conceitual define a visão conceitual. **Também é chamado de esquema lógico** . Existe apenas um esquema conceitual por banco de dados. O nível conceitual está relacionado às seguintes atividades:

* Todas as entidades, seus atributos e seus relacionamentos.
* Restrição nos dados.
* Informações semânticas sobre os dados.
* Verifica para manter a consistência e a integridade dos dados.
* Informação segura

O nível conceitual suporta cada visão externa, na medida em que quaisquer dados disponíveis para um usuário devem estar contidos ou derivados do nível conceitual.

No entanto, este nível não deve conter nenhum detalhe dependente de armazenamento. Por exemplo, a descrição de uma entidade deve conter apenas tipos de dados de atributos (por exemplo, número inteiro, real, caractere etc.) e seu comprimento (como o número máximo de dígitos ou caracteres), mas nenhuma consideração de armazenamento, como o número de bytes ocupados.

A escolha das relações e a escolha do campo (ou item de dados) para cada relação nem sempre é óbvia. O processo de obtenção de um bom esquema conceitual é chamado de **design conceitual de banco de dados**. O esquema conceitual é escrito usando a linguagem de definição de dados conceituais **"DDL conceitual"**.

#### Nível Externo

O nível externo é a visão do usuário do banco de dados. Esse nível está no nível mais alto de abstração de dados, onde apenas as partes do banco de dados relacionadas a um usuário ou programa de aplicativo estão incluídas.

Em outras palavras, esse nível descreve a parte do banco de dados relevante para o usuário. Cada usuário tem uma visão do "mundo real" representado de uma forma familiar para esse ele. 

A visão externa inclui apenas as entidades, atributos e relacionamentos no “mundo real” em que o usuário está interessado. Outras entidades, atributos e relacionamentos que não são de interesse do usuário, podem ser representados no banco de dados, mas o usuário não tenha conhecimento deles.

No nível externo, as diferentes visualizações podem ter diferentes representações dos mesmos dados. Por exemplo, um usuário pode visualizar dados no formulário como dia, mês, ano, enquanto outro pode visualizar como ano, mês, dia. Algumas visualizações podem incluir dados derivados ou calculados, ou seja, os dados não são armazenados no banco de dados, mas são criados quando necessário. Por exemplo, a idade média de um funcionário em uma organização pode ser derivada ou calculada a partir da idade individual de todos os funcionários armazenados no banco de dados. As visualizações externas podem incluir dados combinados ou derivados de várias entidades.

Um esquema externo descreve cada visualização externa. O esquema externo consiste na definição dos registros lógicos e nos relacionamentos na visualização externa. Ele também contém o método de derivar os objetos (por exemplo, entidades, atributos e relacionamentos) na visão externa do objeto na visão conceitual. Esquemas externos permitem que o acesso a dados seja personalizado no nível de usuários individuais ou grupos de usuários.

Qualquer banco de dados fornecido possui exatamente um esquema interno ou físico e um esquema conceitual porque possui apenas um conjunto de relações armazenadas. Mas, pode ter vários esquemas externos, cada um adaptado a um grupo específico de usuários. O esquema externo é gravado usando a linguagem de definição de dados externa **"DDL externa"**.

#### Vantagens da arquitetura de três camadas

O principal objetivo da arquitetura do banco de dados de três camadas é isolar a visualização de cada usuário do banco de dados da maneira como o banco de dados é fisicamente armazenado ou representado. 

As principais vantagens de uma arquitetura de banco de dados de três camadas:

* Cada usuário pode acessar os mesmos dados, mas ter uma visualização personalizada diferente dos dados conforme suas próprias necessidades. Cada usuário pode alterar a maneira como visualiza os dados e essa alteração não afeta outros usuários do mesmo banco de dados.

* O usuário não está preocupado com os detalhes físicos do armazenamento de dados. A interação do usuário com o banco de dados é independente da organização de armazenamento físico de dados.

* A estrutura interna do banco de dados não é afetada por alterações na organização do armazenamento físico, como a mudança para um novo dispositivo de armazenamento.

* O administrador do banco de dados (DBA) pode alterar as estruturas de armazenamento do banco de dados sem afetar a exibição do usuário.

* O DBA pode alterar a estrutura conceitual do banco de dados sem afetar todos os usuários.


