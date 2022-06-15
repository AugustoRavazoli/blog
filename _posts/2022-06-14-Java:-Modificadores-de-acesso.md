## Modificadores de acesso

Olá, Augusto aqui. Em Java, os modificadores de acesso são palavras-chaves(keywords)
que modificam o acesso a classes, métodos e propriedades.
Existem 4 modificadores de acesso ao todo,
são eles: `public`, `private`, `protected` e `default`.
Classes só podem receber `public` ou `default`, enquanto
métodos, propriedades e construtores podem receber qualquer modificador.

### Default

Quando não declaramos um modificador `public`, `private` ou `protected`,
o compilador aplica o modificador `default` por padrão.
Este modificador torna o elemento apenas acessível ao package que ele pertence.
Segue exemplo:

```java
// src/meupacote/Celular.java
package meupacote;

class Celular {
  void ligar() {
    System.out.println("Ligando...");
  }
}

// src/principal/Main.java
class Main {
  public static void main(String[] args) {
    // erro, a classe Celular é apenas visivel no package "meupacote"
    Celular meuCelular = new Celular();
  }
}
```

### Public

O modificador `public`, torna o elemento vísivel a todas as outras classes.
Segue exemplo:

```java
// Carro.java
public class Carro {
  public void mover() {
    System.out.println("O carro está movendo");
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Carro meuCarro = new Carro(); // acessando a classe Carro
    meuCarro.mover(); // acessando o método mover
  }
}
```

### Private

O modificador `private`, torna o elemento vísivel apenas a classe a qual ele pertence.
Segue exemplo:

```java
// Carro.java
class Carro {
  private void ligar() {
    System.out.println("O carro está ligando");
  }

  void mover() {
    ligar(); // acessando o método privado ligar
    System.out.println("O carro está movendo");
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Carro meuCarro = new Carro(); // funciona corretamente

    meuCarro.ligar(); // erro, o método ligar é privado
    meuCarro.mover(); // functiona corretamente
  }
}
```

### Protected

O modificador `protected`, torna o elemento vísivel apenas a classe no qual pertece,
suas classes filhas ou no mesmo package.
Segue exemplo:

```java
// Veiculo.java
class Veiculo {
  protected void mover() {
    System.out.println("O veículo está se movendo");
  }
}

// Carro.java
class Carro extends Veiculo {
  void buzinar() {
    System.out.println("Bi! Bi!");
  }
}

// Main.java
class Main {
  public static void main(String[] args) {
    Carro meuCarro = new Carro();

    meuCarro.mover(); // acessando o método mover
    meuCarro.buzinar();
  }
}
```

## Conclusão

Os modificadores de acesso juntamente com os getters e setters permitem que
ocultemos detalhes de implementação ou informações valiosas e apresentemos
apenas o necessário para o usuário, esse é o conceito de encapsulamento em
orientação a objetos. Enfim, chegamos ao fim do post, te espero na próxima.
