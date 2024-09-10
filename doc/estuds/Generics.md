
# Generics em Java

## Introdução
Em Java, generics permitem criar classes, interfaces e métodos que podem trabalhar com tipos desconhecidos ou parâmetros genéricos. Eles fornecem uma forma de escrever código flexível e reutilizável, tornando-o independente de tipos específicos e permitindo que ele funcione com diferentes tipos de dados.

## Criando uma Classe Genérica
Para criar uma classe genérica, você usa parâmetros de tipo representados entre colchetes angulares `<T>`. Geralmente, usamos letras maiúsculas únicas, mas você pode usar qualquer identificador válido em Java.

Exemplo de uma classe genérica chamada `Caixa`, que armazena um valor de um tipo desconhecido:

```java
public class Caixa<T> {
    private T conteudo;

    public T getConteudo() {
        return conteudo;
    }

    public void setConteudo(T conteudo) {
        this.conteudo = conteudo;
    }
}
```

## Usando a Classe Genérica
Você pode instanciar uma classe genérica com diferentes tipos de dados:

```java
public class TestaCaixa {
    public static void main(String[] args) {
        Caixa<String> caixaDeTexto = new Caixa<>();
        caixaDeTexto.setConteudo("Guardando texto na minha caixa!");

        Caixa<Integer> caixaDeIdade = new Caixa<>();
        caixaDeIdade.setConteudo(30);

        Caixa<Double> caixaDeValor = new Caixa<>();
        caixaDeValor.setConteudo(150.50);
    }
}
```

Neste exemplo, o compilador garante que apenas valores do tipo `String`, `Integer` ou `Double` possam ser armazenados nos objetos respectivos.

## Criando um Método Genérico
Métodos também podem ser genéricos, permitindo que funcionem com diferentes tipos de dados. Aqui está um exemplo de um método genérico que soma valores na caixa:

```java
public <T> T somaConteudoNaCaixa(T valor) {
    if (this.conteudo instanceof Integer c && valor instanceof Integer i) {
        Integer resultado = c + i;
        return (T) resultado;
    } else if (this.conteudo instanceof Double c && valor instanceof Double d) {
        Double resultado = c + d;
        return (T) resultado;
    } else if (this.conteudo instanceof String c && valor instanceof String s) {
        String resultado = c + "\n" + s;
        return (T) resultado;
    }
    return null;
}
```

## Testando o Método Genérico
A classe `TestaCaixa` usando o método genérico:

```java
public static void main(String[] args) {
    Caixa<String> caixaDeTexto = new Caixa<>();
    caixaDeTexto.setConteudo("Guardando texto na minha caixa!");
    System.out.println(caixaDeTexto.somaConteudoNaCaixa("Mais uma linha"));

    Caixa<Integer> caixaDeIdade = new Caixa<>();
    caixaDeIdade.setConteudo(30);
    System.out.println(caixaDeIdade.somaConteudoNaCaixa(26));

    Caixa<Double> caixaDeValor = new Caixa<>();
    caixaDeValor.setConteudo(150.50);
    System.out.println(caixaDeValor.somaConteudoNaCaixa(350.50));
    System.out.println(caixaDeValor.somaConteudoNaCaixa("texto"));
}
```

A saída seria:
```
Guardando texto na minha caixa!
Mais uma linha
56
501.0
null
```

## Adicional: Curingas e Restrição de Tipos

### Uso de `extends` em Generics
Você pode restringir os tipos genéricos usando `extends` para definir uma hierarquia de tipos:
```java
public class Caixa<T extends Number> {
    private T conteudo;
}
```

### Curingas (`?`)
Curingas permitem maior flexibilidade em métodos genéricos:
```java
public static void imprimirCaixa(Caixa<? extends Number> caixa) {
    System.out.println(caixa.getConteudo());
}
```

### Limitações dos Generics
- Não é possível criar arrays de tipos genéricos diretamente.
- `instanceof` não funciona diretamente com tipos genéricos.

Esses conceitos são essenciais para entender e trabalhar com generics em Java.

