
-> Olá, seja bem vindo ao meu arquivo de estudo auto documentado
    -> me chamo Davi Brito. Atualmente estou estudando desenvolvimento FrontEnd, onde ja passei pelo modulo de javascript.

:. Antes de mais nada, gostaria de dizer que tudo que esta escrito aqui, não esta seguindo nenhuma orgem cronologica, onde irei apresentar tais conceitos da maneira a qual pude entender e que me ajudou a fixar!

sem enrolação, vamos direto ao ponto.

<h1>Variaveis:</h1>
<p>Bem o que falar das tão polemicas variaveis? <br>
- - - > A coisa mais relevante (inicialmente) que voce precisa entender sobre variaveis de um modo geral é que:

Variáveis são elementos fundamentais na programação e matemática, utilizadas para armazenar e manipular dados. Elas têm um nome associado que serve como referência para o valor que contêm. Em programação, as variáveis podem conter diferentes tipos de dados, como números, textos, booleanos, entre outros.

Existem algumas características essenciais das variáveis:

Declaração: Antes de usar uma variável, é necessário declará-la. Isso significa informar ao programa qual será o nome da variável e qual o tipo de dado ela irá armazenar.

Atribuição: Após a declaração, é possível atribuir um valor à variável. Isso é feito usando o operador de atribuição (geralmente o sinal de igual "=").

Tipo de Dado: Cada variável tem um tipo de dado associado, como inteiro (int), ponto flutuante (float), string (texto), booleano (true ou false), NULL, Undefined dentre outros.

Escopo: O escopo de uma variável refere-se à parte do programa onde ela é válida e pode ser utilizada. Algumas variáveis têm escopo global (válidas em todo o programa) e outras têm escopo local (válidas apenas em partes específicas do programa).

Manipulação: Variáveis podem ser utilizadas em operações matemáticas, lógicas e em diversas outras operações de processamento de dados.

Atualização: O valor de uma variável pode ser atualizado ao longo do programa, seja por meio de operações aritméticas ou atribuições diretas.

Reutilização: Uma variável pode ser reutilizada para armazenar diferentes valores ao longo da execução do programa.

Nomeclatura: É importante escolher nomes significativos e descritivos para as variáveis, seguindo as convenções de nomenclatura da linguagem de programação utilizada.

Variáveis são fundamentais para a criação de algoritmos e programas, permitindo o armazenamento temporário e manipulação de dados de forma eficiente. Elas facilitam o desenvolvimento de código modular e organizado, tornando o processo de programação mais eficaz e legível.
</p>

<h3>Para declarar variaveis na linguagem Javascript:</h3>

-> let <nome_da_variavel> = <Valor> | neste caso a entrada de valores no ato da declaração é opicional
                          |_____________ ESTE SINAL TEM A FUNÇÃO DE ATRIBUIÇÃO POREM EXISTEM OUTROS USOS PARA ESTE SINAL, VEREMOS MAIS A FRENTE!
                          |_
                            |-> ELE SENDO USADO ASSIM: == TEM SENTIDO DE COMPARAÇÃO


-> let <nome_da_variavel> = <Valor> | neste caso a entrada de valores no ato da declaração é obrigatorio por se tratar de uma variavel que nao tem seu valor alterado ao decorrer do programa.


- - - - - > ambas as formas de declarações de variaveis podem receber qualquer tipo de dado.
- - - - - > NOTA: O JAVASCRIPT TEM SUA ATRIBUIÇÃO DE TIPO DE DADO DINÂMICO, ou seja, independente do dado que voce passar para ele ele ira setar o tipo especifico de variavel de acordo com seu tipo primitivo! (mais a frente vamos entender melhor sobre este recurso, que aparentemente ajuda, porem em alguns casos acaba sendo desfavoravel)....

Ex: variaveis:

let numero = 123456

let texto = 'Um texto qualquer' |------> Este tipo de variavel recebe o nome de (String) então nao se assuste ao ler esse nome por ai.  String sempre vai se referir a algum tipo de texto e no javascript podemos declarar variaveis do tipo texto com aspas simples ou duplas '' ou "" ou ate com a crase ``

let teste = false |--------> este tipo de valor é chamado de Booleano (ja que representa verdadeiro ou falso (true or false) respectivamente);



