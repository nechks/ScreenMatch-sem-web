
# Coleções em Java

## Introdução
As coleções são estruturas de dados fundamentais no Java, que nos permitem armazenar e manipular conjuntos de elementos de forma eficiente. Elas são implementadas pela API de coleções do Java, que faz parte do pacote `java.util`. As coleções fornecem uma variedade de classes e interfaces para armazenar e organizar dados de diferentes maneiras, atendendo a diferentes necessidades e cenários.

## Hierarquia das Coleções
A interface `Collection` é a raiz da hierarquia de todas as coleções (exceto `Map`), e interfaces como `List`, `Set`, e `Queue` são subinterfaces dela.

As principais interfaces de coleções são:

- **`List`**: Uma coleção ordenada que permite elementos duplicados. Os elementos são acessados por índices.
- **`Set`**: Uma coleção que não permite elementos duplicados e normalmente não possui ordem definida.
- **`Queue`**: Uma coleção que representa uma fila, onde os elementos são adicionados no final e removidos do início.
- **`Map`**: Uma coleção de pares chave-valor, onde cada chave é única e mapeada para um valor correspondente.

## Usando a Interface `List`
A interface `List` define uma sequência ordenada de elementos, onde cada elemento possui uma posição específica. Uma das principais razões para usarmos `List` é a flexibilidade que ele oferece: podemos adicionar, remover e acessar elementos facilmente. Além disso, `List` permite a duplicação de elementos.

### Exemplo de `List`:
```java
import java.util.List;
import java.util.ArrayList;

public class ExemploList {
    public static void main(String[] args) {
        List<Integer> numeros = new ArrayList<>();
        numeros.add(10);
        numeros.add(20);
        numeros.add(30);
        System.out.println("Primeiro elemento: " + numeros.get(0)); // Saída: 10
        System.out.println("Segundo elemento: " + numeros.get(1)); // Saída: 20
        System.out.println("Terceiro elemento: " + numeros.get(2)); // Saída: 30

        for (Integer numero : numeros) {
            System.out.println(numero);
        }

        numeros.remove(1); // Remove o elemento de índice 1 (20)
        System.out.println("Tamanho do List: " + numeros.size()); // Saída: 2
    }
}
```

## Coleções Imutáveis
O Java 9 introduziu coleções imutáveis, cujo conteúdo não pode ser modificado após a criação. Elas podem ser criadas usando `List.of()`, `Set.of()`, e `Map.of()`.

```java
List<String> listaImutavel = List.of("A", "B", "C");
Set<Integer> setImutavel = Set.of(1, 2, 3);
```

## Métodos Úteis em `List` e Outras Coleções
Métodos como `contains()`, `sort()`, e `isEmpty()` são úteis para manipulação das coleções.

```java
List<String> nomes = new ArrayList<>();
nomes.add("Alice");
nomes.add("Bob");

if (nomes.contains("Alice")) {
    System.out.println("Alice está na lista.");
}
Collections.sort(nomes);
System.out.println(nomes); // Saída: [Alice, Bob]
```

## Comparação entre `ArrayList` e `LinkedList`
- **`ArrayList`**: Baseado em array, é mais rápido para acessar elementos por índice, mas menos eficiente para inserções e remoções.
- **`LinkedList`**: Baseado em uma lista duplamente ligada, é mais eficiente para inserções e remoções, mas o acesso por índice é mais lento.

## Usando `Set` e `Map`
- **`Set`**: Garante que não haja elementos duplicados.
```java
Set<String> nomesUnicos = new HashSet<>();
nomesUnicos.add("Ana");
System.out.println(nomesUnicos); // Saída: [Ana]
```

- **`Map`**: Usa pares chave-valor para associar dados.
```java
Map<String, Integer> idadePorNome = new HashMap<>();
idadePorNome.put("João", 30);
idadePorNome.put("Maria", 25);
System.out.println("Idade de João: " + idadePorNome.get("João")); // Saída: 30
```

## Coleções Sincronizadas
Em ambientes com múltiplas threads, pode ser necessário usar coleções sincronizadas:

```java
List<String> listaSincronizada = Collections.synchronizedList(new ArrayList<>());
Map<String, Integer> mapaSincronizado = Collections.synchronizedMap(new HashMap<>());
```

## Conclusão
As coleções em Java são essenciais para manipular grandes volumes de dados de forma eficiente e flexível. Seja usando `List`, `Set`, `Map` ou outras estruturas, o domínio dessas APIs ajuda a otimizar o código e melhorar a performance.
