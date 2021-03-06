# Programação Orientada a Objetos

##### Atualizado em 16-06-2021
###### A partir de: apontamentos das aulas teóricas

## Revisões / Bases

**Identificadores JAVA**

* Não podem começar por um dígito;
* Combinações de letras, dígitos e carateres `_` e `$`;
* Convenções: _classes_ começam com maiúscula; _subprogramas_ e _variáveis_ começam com minúscula; _constantes_ são escritas em maiúsculas.

**Tipos Primitivos:** boolean, char, byte, short, int, long, float, double.

**Declaração de variáveis**

`tipo variável1 [= valor1][, variável2 [= valor2]...];`

A declaração de constantes é semelhante à de variáveis, acrescida com a obrigatoriedade do atributo `final` e do valor da mesma: `final double PI = 3.14159273269`.

**Conversão Entre Tipos**

Os operadores aritméticos estão definidos para funcionar com operandos do mesmo tipo, logo, em expressões que contenham valores de vários tipos, o computador terá de fazer conversões de tipo automaticamente de modo a não haver perdas de informação. Nem todas as transformações são possíveis: é possível converter um valor para um tipo que ocupe mais espaço, mas não o inverso.

`byte > short > int > long > float > double`

A conversão de tipos com perda de informação é permitida usando o operador de coerção `cast` entre parêntesis antes da expressão a converter.

**Estruturas de Controlo Condicionais**

_Seleção simples:_ `if (condição) Instruções_Se_Condição_Verdadeira`

_Seleção em alternativa:_ `if (condição) ISCV else ISCF`

_Seleção múltipla:_ `switch (expressão) {case valor1: instruções1; [break;] ... case valorN: instruçõesN; [break;] default: InstruçõesCasoOmisso; [break]}`

O valor da expressão deve ser inteiro ou caratere, e a instrução `break` é necessária para que os ramos de instruções não sejam executados sequencialmente. Uma instrução `switch` pode ser substituída por `if-else`, mas não o contrário.

**Estruturas de Controlo Repetitivas**

_Ciclo for:_ `for (inicialização; condição_de_continuação; iteração) instruções;`

A `condição_de_continuação` é uma expressão booleana avaliada antes de cada iteração que determina a saída do ciclo assim que o seu valor seja `false`. O bloco `iteração` é executado após as `instruções` e serve para atualizar o valor da variável de controlo.

_Ciclo while:_ `while (condição_de_continuação) instruções;`

Enquanto a `condição_de_continuação` for verdadeira, as `instruções` são executadas.

_Ciclo do...while:_ `do {instruções;} while (condição_de_continuação);`

Usado quando as `instruções` devem ser executadas pelo menos uma vez. No final, a `condição_de_continuação` é testada e a iteração termina se o seu valor for `false`. 

---

<br/><br/>

## Aula 01 - Conceito de Objeto

**Objetos:** representação de uma entidade sob a forma de um identificador único, um conjunto de atributos privados (_estado_ do objeto) e um conjunto de operações (_comportamento_ do objeto). Destas operações, algumas são invocáveis do exterior (_operações públicas_ - _interface_ do objeto [_Application Programmer's Interface_, API]), outras são apenas internas ao objeto (_operações privadas_). Aos identificadores que guardam os valores dá-se o nome de _variáveis de instância_. Às operações que representam o comportamento do objeto dá-se o nome de _métodos de instância_.

**Mensagens:** os objetos interatuam entre si através de um mecanismo de envio de mensagens. O _recetor_ é o identificador do objeto que recebe a mensagem, a _mensagem_ é o identificador do método:
* `recetor.mensagem();` - envio de mensagem sem argumentos a um objeto, sem retorno de resultado pelo método correspondente;
* `recetor.mensagem(arg1, arg2, ..., argn);` - envio de uma mensagem com argumentos, sem retorno de resultado;
* `resultado = recetor.mensagem();` - envio de uma mensagem sem argumentos, com retorno de resultado;
* `resultado = recetor.mensagem();` - envio de uma mensagem com argumentos e com retorno de resultado.

Os argumentos e o resultado de uma mensagem têm de ser compatíveis com o tipo dos parâmetros e do valor devolvido pelo método correspondente.

**Instâncias vs Classes**

Uma **classe** é um objeto que contém a descrição da estrutura e comportamento de objetos do mesmo tipo e que cria objetos particulares que possuem igual estrutura e comportamento. Por **métodos de instanciação**, os objetos são _inicializados_, passando a existir e a poder receber mensagens de outros objetos.

Cada objeto tem as suas próprias variáveis de estado enquanto o código que implementa os métodos permanece armazenado na classe. Os objetos têm um comportamento comum, mas o seu estado é variável.

Quando um objeto é instanciado, a inicialização do seu estado é feita por invocação automática de um método de inicialização - **construtor da classe**.

---

<br/><br/>

## Aula 02 - Tecnologia Java e Tipos Referenciados

A tecnologia Java baseia-se na ideia de que qualquer programa deve poder ser executado sem ser alterado ou recompilado; o código-fonte é _compilado_ para uma representação intermédia, independente do sistema de execução e da arquitetura da máquina (_byte-code_), que depois é interpretado sobre o ambiente de cada máquina específica pela _Java Virtual Machine_ (JVM). A JVM recebe _byte-code_ e transforma-o em instruções executáveis na máquina onde o ambiente Java é instalado.

**Aplicações Java** são programas que, após serem compilados, apenas requerem uma JVM para serem interpretados e executados.

**_Applets_** são porções de código Java não executável por si próprio, requerendo a existência de um _browser_ que incorpore e execute a JVM.

Em Java os programas são constituídos por diversas **classes**, tipos de dados agrupados em pacotes (_packages_), que possuem **atributos** (variáveis) e **métodos** (funções). Um **construtor** é uma operação especial da classe, com o mesmo nome da classe, identificado pela sua lista de parâmetros, para criar objetos, mas sem declarar o tipo do resultado.

**Tipos referenciados** são entidades às quais se acede através de uma variável que contém o seu endereço; ou seja, o que é atribuído e manipulado são _referências_ (endereços).

**Arrays** são entidades referenciadas, mas não são objetos. São criados dinamicamente em tempo de execução e o seu espaço é automaticamente reaproveitado quando deixam de estar referenciados.

---

<br/><br/>

## Aula 03 - Classes e Instanciação de Objetos

Um **argumento** é um valor passado para uma função quando esta é chamada; um **parâmetro** é um valor passado para uma função quando esta é definida. Uma **classe** define a estrutura, propriedades e comportamento de um objeto; uma **instância** é a referência a um determinado objeto.

`class Contador { <instruções> }`

Por omissão, toda a classe possui um construtor, que atribui o valor `null` a todas as variáveis do objeto que sejam do tipo referenciado e arrays (inicializados de acordo com o seu tipo). Um construtor permite inicializar o estado (valores) das instâncias da classe.

Deve garantir-se que nenhum objeto faz acesso direto às variáveis de instância de outro objeto, de modo a garantir que se estão a definir objetos independentes e reutilizáveis). Um objeto genérico não deve ter instruções de _input_/_output_ no seu código.

_Assinatura de um método:_ constituída pelo identificador do método e pelo número, tipo e ordem dos seus parâmetros. `<tipo do resultado> <identificador> (pares tipo e nome do parâmetro)`.

Um valor do tipo _String_ é uma sequência de zero ou mais carateres entre aspas, com um valor imutável. O operador `+` permite a concatenação de _strings_ e cria implicitamente uma nova instância da classe String.

Métodos que façam **acesso de leitura** ao valor de uma variável X designam-se por _getters_ e devolvem um resultado do tipo da variável X (`getX`). Métodos que **alterem** o valor de uma variável X designam-se por _setters_, têm parâmetros de entrada e não devolvem qualquer resultado (`setX`).

A abordagem da comunicação por mensagens pode ser usada uniformemente para interação com outros objetos e invocação de métodos locais. Para que um objeto possa enviar uma mensagem a si próprio, tem de se autorreferenciar: `this` é um identificador especial que contém o endereço do próprio objeto em cujo contexto é utilizado.

Mecanismos de controlo de acesso especificam 'quem' tem acesso a cada entidade (classe, dados e métodos): `public`, `protected`, `private`.

Regras de acesso a classes:
* Uma classe é sempre acessível a todas as outras classes do mesmo _package_ independentemente do modificador de acesso;
* Se nenhum modificador de acesso é usado, a classe apenas pode ser acedida dentro do seu _package_;
* Quando uma classe é declarada como `public`, pode ser acedida por qualquer classe que tenha acesso ao seu _package_;
* Quando uma classe não é pública, é apenas acessível dentro do seu _package_.

Regras de acesso a variáveis e métodos:
* Variáveis e métodos auxiliares são privados; métodos de interface são públicos;
* Um método declarado como `public` é acessível de qualquer ponto de qualquer programa;
* Um método sem modificador de acesso é acessível a qualquer classe do mesmo _package_;
* Métodos ou variáveis declarados como `private` são apenas acessíveis dentro da própria classe;
* Métodos ou variáveis declarados como `protected` são acessíveis na própria classe, de outra classe dentro do mesmo _package_ e nas subclasses da classe.

---

<br/><br/>

## Aula 04 - Variáveis de Classe e Composição de Classes

**Variáveis de classe** representam a estrutura interna de uma dada classe e armazenam valores que identifiquem todos os objetos da classe. Podem ser usadas mesmo que nunca tenha sido instanciado um objeto da classe. Exemplo: `private static String texto;`.

**Variável de instância** Exemplo: `private int numero;`.

**Métodos de classe** implementam o comportamento da classe. São acessíveis às instâncias da classe, ou seja, um método de instância pode invocar um método de classe, mas não o contrário. Exemplo: `public static int metodoA()`.
 
Tanto as variáveis como os métodos de classe são invocados através de mensagens enviadas à classe e declaradas com o identificador `static`.

**Classes Não Instanciáveis** só têm variáveis e métodos de classe; não especificam a estrutura nem o comportamento de qualquer instância.

Em Java os parâmetros são passados por valor: é criada uma variável local com valor igual a uma cópia do argumento. Se o parâmetro é um tipo referenciado, equivale à passagem por referência - argumento.

---

<br/><br/>

## Aula 05 - Comparação de _Strings_

* Valores constantes do tipo _String_ têm a mesma referência;
* _Strings_ construídas em tempo de compilação são tratadas como valores constantes do tipo _String_;
* _Strings_ construídas em tempo de execução - só são criadas quando se executa o programa - têm referências distintas.

Logo, o método recomendado para comparar _strings_ é `s1.equals(s2)`, que compara o conteúdo e não apenas o endereço (como no `==`).

**Listas Dinâmicas**

A classe `ArrayList` no pacote `java.util` distingue-se dos _arrays_ porque pode (de)crescer de tamanho e pode armazenar objetos de diferentes tipos. Implementa uma abstração de dados que representam uma estrutura linear indexada a partir do índice 0 sem limite de dimensão. Alguns métodos da classe:

* `ArrayList()` -> construtor vazio, dimensão inicial zero;
* `boolean add(Object element)` -> adiciona o elemento especificado ao final da lista;
* `void add(int index, Object element)` -> insere o elemento especificado na posição do índice;
* `Object remove (int index)` -> remove o elemento da posição index;
* `boolean remove (Object element)` -> remove a primeira ocorrência do objeto dado como parâmetro;
* `Object set (int index, Object element)` -> substitui o elemento da posição index pelo elemento especificado;
* `Object get (int position)` -> devolve o elemento da posição index;
* `void clear()` -> remove todos os elementos da lista;
* `Object clone()` -> devolve uma cópia da lista;
* `boolean contains(Object element)` -> devolve _true_ se a lista contiver o elemento especificado;
* `boolean equals (Object element)` -> permite comparar duas listas;
* `int indexOf (Object element)` -> procura o índice da primeira ocorrência do elemento;
* `boolean isEmpty()` -> verifica se a lista está vazia;
* `int size()` -> devolve a dimensão atual da lista;
* `String toString()`.

A verificação de tipos pode ser feita durante a compilação, usando _tipos genéricos_ (tipo referenciado que usa na sua definição um ou mais tipos de dados como parâmetros). Seja o tipo `ArrayList<E>` em que E pode ser qualquer classe ou interface, a instanciação de um tipo genérico para um valor concreto de E dá origem a um _tipo parametrizado_.

---

<br/><br/>

## Aula 06 - Herança

Conceito em que uma classe pode herdar operações de uma superclasse (classe base) e as suas operações podem ser herdadas por subclasses (classes derivadas). O _mecanismo de herança_ permite definir uma nova classe em termos de uma classe existente, com modificações e/ou extensões de comportamento.

Todos os métodos e atributos da superclasse são herdados pela subclasse, à qual podem ser adicionados novos métodos e atributos no processo de especialização sucessiva. Dada uma hierarquia de classes, a instância de uma subclasse contém as variáveis de instância da superclasse e as variáveis de instância declaradas na classe derivada. O comportamento dessa instância está definido na sua classe e no conjunto das suas superclasses.

Quando um método é invocado, ou seja, quando é enviada uma mensagem a um objeto, torna-se necessário ligar a mensagem à implementação correspondente. Por exemplo:
* Uma _fila_ pode ser implementada a partir de uma _lista ligada_ desde que se imponham as restrições adequadas à manipulação dos seus elementos;
* Redefinem-se os métodos da _lista ligada_ para refletir a semântica da _fila_;
* Para execução, primeiro pesquisa-se a subclasse e só após a superclasse onde o método é encontrado.

A hierarquia é pesquisada na direção subclasse > superclasse, com início na classe do objeto que recebe a mensagem. É executado o método mais próximo.

**Tipos de ligação** - ligação do nome de um método a uma implementação:
* Em tempo de compilação - _ligação estática_:
  * Abordagem mais simples, em que o compilador constrói uma tabela de classes e métodos associados, produzindo um código com as ligações entre os métodos e correspondentes implementações;
  * _Vantagem:_ ligações erradas (chamadas a métodos não existentes) são detetadas em tempo de compilação;
  * _Desvantagem:_ para introduzir alterações na ligação é necessário recompilar todo o código;
* Em tempo de execução - _ligação dinâmica_:
  * A correspondência entre o método e a implementação é feita a cada invocação: a hierarquia é pesquisada e, se o método não existir, devolve `Método Desconhecido`;
  * _Vantagem:_ alterações na hierarquia não implicam necessidade de recompilação de todas as classes;
  * _Desvantagens:_ a pesquisa na hierarquia provoca alguma degradação no desempenho do sistema; necessidade de manipular mensagens `Método Desconhecido` em tempo de execução.

Declaração de B como subclasse de A: `public class B extends A`. Um objeto do tipo B também é do tipo A.

Cada classe possui uma só superclasse direta, e apenas esta é identificada na cláusula `extends`. A classe de topo da hierarquia é a classe **Object**; que é superclasse quando não é usada a cláusula `extends`.

A classe **Object** define o comportamento comum a todas as classes através de métodos genéricos que normalmente necessitam de ser redefinidos. Qualquer instância de qualquer classe pode responder às mensagens correspondentes aos métodos da classe.
* `public final Class getClass ()` - devolve a classe do objeto;
* `public String toString ()` - representação textual do objeto;
* `public boolean equals (Object obj)` - igualdade de referências;
* `protected Object clone ()` - clona um objeto.

Dadas uma classe A e uma subclasse B,
* B tem acesso direto a todas as variáveis e métodos de A que não sejam declaradas como `private`;
* B pode definir novas variáveis e métodos e redefinir variáveis e métodos herdados;
* Uma instância de B pode responder a mensagens que correspondam a todos os métodos públicos de B e A;
* Os atributos de uma instância de B são atributos definidos nas classes A e B.

**Princípio da substitutividade:** declarada uma variável como sendo de uma dada classe, é permitido atribuir-lhe um valor de sua classe ou de qualquer sua subclasse.

**Método `equals`** - compara a referência de um objeto que recebe como argumento com a referência do objeto recetor. Devolve `true` se as referências forem iguais, `false` caso contrário.

**Método `clone`** - cria e devolve a cópia do objeto recetor, tal que o objeto criado e o que recebe a mensagem:
* São diferentes: `y = x.clone (); // y != x;`;
* São instâncias da mesma classe: `x.clone().getClass() == x.getClass();`;
* Têm o mesmo valor nas variáveis de instância: `x.clone().equals(x) == true`.

---

<br/><br/>

## Aula 07 - Polimorfismo

Diz-se que o nome de um método foi sobrecarregado (_overloaded_) se dois métodos têm o mesmo nome mas assinaturas diferentes, que podem estar definidos na mesma classe e ser herdados por uma dada classe.

Uma classe pode redefinir um método herdado, e _a definição local sobrepõe-se à definição herdada_. Dois métodos sobrepõem-se se têm a mesma assinatura e o mesmo tipo de resultado.

Ao redefinir os métodos `clone`, `equals` ou `toString` da classe _Object_ estão-se a sobrepôr estes métodos. É possível aceder ao método da superclasse numa subclasse usando a referência `super` como prefixo: `super.m1()`.

Se uma variável _x_ é redefinida numa subclasse, essa declaração oculta (_hides_) a variável definida na superclasse.

Um construtor de uma dada classe pode invocar um construtor da mesma classe com a referência `this`. A invocação de um construtor através da referência `this`, se existir, tem de ser a primeira instrução do construtor com a exceção de quando exista a invocação do construtor da superclasse. Dada uma classe A e uma sua subclasse B, no construtor da subclasse, B, tem de se inicializar as variáveis definidas na subclasse B e na classe A. Todos os construtores de B devem invocar algum construtor de A através da referência `super`; se tal não for explícito, o compilador insere como primeira instrução o construtor da superclasse, `super()`, que garantirá a invocação do construtor por omissão de A.

**Princípio da substitutividade:** declarada uma variável como sendo de uma dada classe, é permitido atribuir-lhe um valor de sua classe ou de qualquer sua subclasse.

A declaração de uma variável é um processo _estático_ - determina o tipo estático da variável em tempo de compilação. O processo _dinâmico_ determina o tipo da variável em tempo de execução (verificado pelo interpretador). Uma variável diz-se _polimórfica_ se tiver mais do que um tipo. Um método ou um operador dizem-se _polimórficos_ se podem ser aplicados a vários tipos de valores.

**Polimorfismo de coerção** - uma variável inteira é tratada como real.

**Polimorfismo de sobrecarga** - o mesmo nome (de um método ou função) pode ser usado mais do que uma vez com diferentes tipos de parâmetros.

**Polimorfismo universal** - capacidade de uma única função (código único) poder ser usado com mais do que um tipo:
  * **Polimorfismo de inclusão** - uma função definida num determinado tipo pode também operar todos os seus subtipos (resultante do mecanismo de herança);
  * **Polimorfismo paramétrico** - uma única função pode ser aplicada a um conjunto de tipos sem qualquer relação entre si, existindo, explicitamente ou não, um parâmetro de tipo que determina o tipo de argumento para cada aplicação da função.

---

<br/><br/>

## Aula 08 - Exceções

Uma **exceção** ocorre quando um programa viola as restrições semânticas da linguagem e é um erro recuperável. Uma exceção diz-se lançada (_thrown_) no ponto onde ocorre e diz-se capturada (_caught_) no ponto para onde o controlo de execução é transferido. Cada exceção é representada por uma instância da classe - objeto que guarda a informação desde o ponto onde a exceção ocorre até ao ponto onde é capturada.

```
try {
  // conjunto de instruções onde há possibilidade de detetar a ocorrência de erros recuperáveis
} catch (<classe da exceção> <instância da exceção gerada>) {
  // instruções a executar caso ocorra uma exceção
  // podem haver vários catches para um único bloco try
} [ finally {
  // conjunto de instruções que serão executadas, ocorra ou não uma exceção no bloco try
} ]
```

Uma exceção pode ser lançada porque é detetada uma violação da semântica da linguagem ou porque é executada uma instrução _throw_ - geração explícita de uma exceção definida ou não pelo utilizador: `throw new <construtor da (sub)classe Exception>`.

Há dois tipos de exceções:
* _Exceções verificáveis pelo compilador:_
  * O compilador verifica se o programa trata as exceções que poderão ocorrer no código - `try (...) catch` ou `throws`;
* _Exceções não verificáveis pelo compilador:_
  * Objetos de classes e subclasses específicas:
    * `RunTimeException` - exceções cuja ocorrência é difícil de ser verificável pelo programador;
    * `Error` - erros não recuperáveis.

Um método que sobrepõe (_override_) outro não pode declarar / lançar mais exceções do que o método que é sobreposto. Cada exceção declarada numa subclasse tem de ser do mesmo tipo da exceção declarada na superclasse.

---

<br/><br/>

## Aula 09 - Classes Abstratas

_Classes abstratas_ são classes em que pelo menos um dos métodos de instância não é implementado, definindo uma linguagem comum a um subconjunto de classes herdeiras. Não é possível criar instâncias, embora se mantenham os mecanismos de herança e o princípio da substitutividade. Se uma subclasse de uma classe abstrata implementar todos os métodos, passa a ser uma classe concreta. Variáveis, construtores, métodos de classe e métodos privados não são abstratos.

Uma **interface** é uma especificação sintática de um conjunto de métodos e constantes, permitindo definir um comportamento comum a duas ou mais classes que não possuam qualquer relação hierárquica entre si. Interfaces são implícita e obrigatoriamente abstratas e os métodos nelas declarados são implícita e obrigatoriamente públicos e abstratos. As interfaces têm uma hierarquia própria (podendo uma interface ser subinterface de várias interfaces (_mecanismo de herança múltipla_)) e as constantes nelas declaradas são implícita e obrigatoriamente do tipo `public static final`.

Uma classe que implemente uma dada interface tem obrigatoriamente que implementar todos os métodos nela declarados.

Uma _classe abstrata_ pode ter métodos implementados; numa _interface_ todos os métodos são abstratos. A subclasse de uma _classe abstrata_ pode ser ou não uma classe abstrata; numa _subinterface_ todos os métodos são abstratos. Uma _classe abstrata_ pode ser usada para escrever _software_ genérico, em que cada subclasse vai sendo implementada num processo de especialização sucessiva; uma _interface_ especifica um comportamento comum a todas as classes que a implementam.

---

<br/><br/>

## Aula 10 - Ficheiros

Uma _stream_ é uma abstração que representa uma _fonte_ genérica de entrada de dados ou um _destino_ genérico para escrita de dados, definida independentemente do dispositivo físico concreto. Todas as classes que implementam _streams_ em `Java` são subclasses das classes abstratas: `InputStream` e `Output Stream` para ler/escrever bytes, `Reader` e `Writer` para ler/escrever carateres.

As classes `FileInputStream` e `FileOutputStream` definem objetos do tipo _stream_ que permitem ler e escrever sequências de bytes em ficheiros. A classe `DataOutputStream` permite fazer o output de tipos primitivos de dados, convertendo-os em sequências de bytes; fornece um acesso de alto nível, estando ligada a um objeto do tipo `FileOutputStream`, e não do tipo `File`.

Também se pode ler/escrever objetos de/num ficheiro, usando as classes `ObjectInputStream` e `ObjectOutputStream`. Uma `ObjectOutputStream` permite armazenar objetos através do método `writeObject ()`, que implementa um algoritmo de serialização que garante que todas as referências cruzadas existentes entre instâncias de diferentes classes serão repostas aquando do processo de leitura dessas mesmas instâncias. Para que se possam gravar instâncias de uma determinada classe numa `ObjectOutputStream`, é necessário que a classe implemente a interface `Serializable` e que todas as variáveis dessa classe sejam também serializáveis.