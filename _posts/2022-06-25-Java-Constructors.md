# Java: Constructors

Olá, Augusto aqui. Em java, um constructor é um método especial utilizado para inicializar objetos, sendo executado automaticamente quando um objeto é criado. Todo constructor deve possuir o mesmo nome de sua classe e não deve ter tipo de retorno. Segue exemplo:

```java
// Pessoa.java
class Pessoa {
  Pessoa() {
    System.out.println("Constructor sendo executado!");
  }
}

// Main.java 
class Main {
  public static void main(String[] args) {
    Pessoa pessoa = new Pessoa(); // Constructor sendo executado!
  }
}
```

Existem 2 tipos de constructors: 
1. No-Arg Constructor
2. Parameterized Constructor

## No-Arg Constructor

Um No-Arg Constructor é um constructor que não possui parâmetros, eles podem ser usados para definir valores padrões para as propriedades do objeto. Segue exemplo:

```java
// Banana.java
class Banana {
  String cor;

  Banana() {
    this.cor = "verde";
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Banana banana = new Banana();

    System.out.println(banana.cor); // verde
  }
}
```

## Parameterized Constructor

Um Parameterized Constructor é um constructor que possui parâmetros, eles podem ser usados para definir valores específicos para as propriedades do objeto. Segue exemplo:

```java
// Pessoa.java
class Pessoa {
  String nome;

  Pessoa(String nome) {
    this.nome = nome;
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Pessoa pessoa1 = new Pessoa("Ana");
    Pessoa pessoa2 = new Pessoa("Rafael");

    System.out.println(pessoa1.nome); // Ana
    System.out.println(pessoa2.nome); // Rafael
  }
}
```

## Default Constructor

Quando não definimos um constructor de uma classe, o compilador irá criar um No-Arg Constructor por padrão, este constructor irá inicializar as propriedades do objeto para um valor padrão de acordo com a tabela abaixo:

| **Tipo** | **Valor** |
|:--------:|:---------:|
|  boolean |   false   |
|   byte   |     0     |
|   short  |     0     |
|    int   |     0     |
|   long   |     0L    |
|   char   |   \u0000  |
|   float  |    0.0F   |
|  double  |    0.0D   |
|  Object  |    null   |

Segue exemplo:

```java
// Lampada.java
class Lampada {
  boolean ligada;
}

// Main.java
class Main {
  public static void main(String[] args) {
    Lampada lampada = new Lampada();

    System.out.println(lampada.ligada); // false
  }
}
```

### Extra: Constructor Overloading e Private Constructors

Constructor são métodos, e por isso também se beneficiam de Method Overloading, com isso, podemos ter vários constructors para uma mesma classe:

```java
// Pessoa.java
class Pessoa {
  String nome;

  Pessoa() {
    this.nome = "Desconhecido";
  }

  Pessoa(String nome) {
    this.nome = nome;
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Pessoa pessoa1 = new Pessoa();
    Pessoa pessoa2 = new Pessoa("Angela");

    System.out.println(pessoa1.nome); // Desconhecido
    System.out.println(pessoa2.nome); // Angela
  }
}
```

Além disso, podemos impedir que um objeto de uma classe seja criado se declararmos um constructor como `private`:

```java
// Banco.java
class Banco {
  private Banco() {}
}

// Main.java
class Main {
  public static void main(String[] args) {
    Banco banco = new Banco(); // erro, o constructor é privado
  }
}
```

## Conclusão

Os constructors nos dão flexibilidade no momento de criar objetos, permitindo que além de inicializar o valor de um propriedade, também chamamos outros métodos ou criemos lógica dentro deles. Enfim, chegamos ao fim do post, te espero na próxima.
