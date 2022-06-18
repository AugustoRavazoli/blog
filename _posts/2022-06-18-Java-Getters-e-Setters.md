# Java: Getters e Setters

Olá, Augusto aqui. Em Java, Getters e Setters são métodos públicos criadas pelo programador para
acessarem e modificarem o valor de uma propriedade privada, respectivamente. 
Por convenção, se utiliza as palavras "get" e "set" seguidos pelo nome da propriedade.

## Getter  

Um método Getter retorna o valor de uma propriedade do objeto. Quando uma propriedade possui
apenas o método Getter, dizemos que ela é "read-only", ou seja, pode ser lida, mas não 
modificada. Segue exemplo:

```java
// Carro.java
public class Carro {
  private String motor;

  public Carro() {
    this.motor = "V8";
  }

  public String getMotor() {
    return this.motor;
  }
}

// Main.java
public class Main {
  public static void main(String[] args) {
    Carro meuCarro = new Carro();

    System.out.println(meuCarro.motor); // erro, a propriedade motor é privado
    meuCarro.motor = "V6"; // erro, a propriedade motor é privado
    System.out.println(meuCarro.getMotor()); // V8
  }
}
```

## Setter

Um método Setter modifica o valor de uma propriedade do objeto. Quando uma propriedade possui
apenas o método Setter, dizemos que ela é "write-only", ou seja, pode ser modificada, mas não 
lida. Ao usar um método Setter, podemos colocar condições para que aquele valor seja modificado, 
como no exemplo abaixo em que o valor da gasolina tem que ser menor que a capacidade do tanque:

```java
// Carro.java
public class Carro {
  private static final int CAPACIDADE_DO_TANQUE_EM_LITROS = 75;
  private int gasolinaEmLitros;

  public void setGasolinaEmLitros(int gasolinaEmLitros) {
    if (gasolinaEmLitros < CAPACIDADE_DO_TANQUE_EM_LITROS) {
      this.gasolinaEmLitros = gasolinaEmLitros;
    } else {
      System.out.println("Nâo cabe tudo isso no tanque!");
    }
  }
}

// Main.java
public class Main {
  public static void main(String[] args) {
    Carro meuCarro = new Carro();

    System.out.println(meuCarro.gasolinaEmLitros); // erro
    meuCarro.gasolinaEmLitros = 20; // erro
    meuCarro.setGasolinaEmLitros(20); // correto
    meuCarro.setGasolinaEmLitros(90); // Nâo cabe tudo isso no tanque!
  }
}
```

## Conclusão

Getters e Setters permitem que controlemos os acessos a propriedades privadas, permitindo que
elas sejam ready-only, write-only ou que coloquemos condições nesses acessos. Enfim, 
chegamos ao fim do post, te espero na próxima.