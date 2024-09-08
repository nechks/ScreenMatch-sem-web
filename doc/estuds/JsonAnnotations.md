
# @JsonAlias e @JsonProperty em Jackson

## Visão Geral
`@JsonAlias` e `@JsonProperty` são anotações da biblioteca Jackson, amplamente utilizada em Java para processar JSON. Essas anotações facilitam o mapeamento de propriedades de classes Java para campos JSON, mas possuem funções diferentes. Vamos entender melhor cada uma delas.

## @JsonProperty
A anotação `@JsonProperty` é usada para definir o nome da propriedade JSON que está associada a um campo da classe Java.

- **Serialização**: Quando o objeto Java é convertido em JSON, o nome especificado em `@JsonProperty` será utilizado como chave no JSON gerado.
- **Desserialização**: Ao converter o JSON de volta para um objeto Java, a biblioteca buscará o nome especificado em `@JsonProperty` para mapear o valor JSON ao campo correspondente na classe Java.

Essa anotação é útil quando o nome da propriedade no JSON deve ser diferente do nome no código Java. Por exemplo, se você tiver uma propriedade `nomeCompleto` na sua classe Java, mas quiser que ela seja representada como `nome` no JSON, você pode fazer isso com `@JsonProperty("nome")`:

```java
public class Pessoa {
    @JsonProperty("nome")
    private String nomeCompleto;
}
```

## @JsonAlias
A anotação `@JsonAlias` permite definir um ou mais apelidos (aliases) para o nome da propriedade JSON associada ao campo Java, facilitando a desserialização.

- **Desserialização**: `@JsonAlias` é útil quando você está trabalhando com diferentes versões de um JSON ou deseja que uma propriedade possa ser referenciada por diferentes nomes no JSON. Isso garante maior flexibilidade na leitura dos dados.

Por exemplo, se um JSON usa o campo `nome` em vez de `nomeCompleto`, você pode usar `@JsonAlias({"nomeCompleto", "nome"})` para garantir que tanto `nomeCompleto` quanto `nome` serão aceitos ao desserializar:

```java
public class Pessoa {
    @JsonAlias({"nomeCompleto", "nome"})
    private String nomeCompleto;
}
```

## Quando Usar
- **Use `@JsonProperty`** quando precisar personalizar o nome da propriedade no JSON.
- **Use `@JsonAlias`** quando precisar garantir compatibilidade com diferentes versões ou nomenclaturas de JSON.

Essas duas anotações ajudam a simplificar a integração entre objetos Java e documentos JSON, permitindo maior controle e flexibilidade no mapeamento de dados.

