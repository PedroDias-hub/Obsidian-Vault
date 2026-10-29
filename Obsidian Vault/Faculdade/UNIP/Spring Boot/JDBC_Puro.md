# JDBC Puro

JDBC (Java Database Connectivity) é a API padrão do Java para conversar com bancos relacionais. O Spring Data JPA é construído por cima dela — mas aqui o projeto usa JDBC diretamente, sem nenhuma camada de abstração.

## As peças principais

### `Connection`
Representa a conexão aberta com o banco. Criada a partir de uma `DriverManager`:

```java
public class ConnectionFactory {
    private static String url = "jdbc:h2:mem:empresa";
    private static String usuario = "adm";
    private static String senha = "password";

    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(url, usuario, senha);
    }
}
```

### `Statement` vs `PreparedStatement`
- **`Statement`**: executa SQL "cru", sem parâmetros. Só é seguro quando a query não tem nenhum dado vindo de fora.
- **`PreparedStatement`**: SQL com placeholders (`?`), preenchidos depois com `setInt`, `setString`, etc. **Sempre** que houver dado externo na query, use `PreparedStatement` — evita SQL injection e cuida da tipagem/escaping automaticamente.

```java
PreparedStatement ps = connection.prepareStatement("select * from funcionario where codigo = ?");
ps.setInt(1, codigo);
ResultSet rs = ps.executeQuery();
```

### `ResultSet`
O "cursor" sobre as linhas retornadas pela query. `rs.next()` avança uma linha e retorna `false` quando acabou:

```java
while (resultSet.next()) {
    int codigo = resultSet.getInt("codigo");
    String nome = resultSet.getString("nome");
    boolean ativo = resultSet.getBoolean("ativo");
}
```

### Fechar os recursos
`Connection`, `Statement`/`PreparedStatement` e `ResultSet` precisam ser fechados manualmente depois de usados, ou a conexão fica "vazando":

```java
resultSet.close();
statement.close();
connection.close();
```

> [!tip] Melhoria possível
> O projeto fecha tudo manualmente dentro do `try`. Uma versão mais robusta usaria **try-with-resources**, que fecha tudo automaticamente mesmo se der exceção:
> ```java
> try (Connection connection = ConnectionFactory.getConnection();
>      Statement statement = connection.createStatement();
>      ResultSet resultSet = statement.executeQuery("select * from funcionario")) {
>     while (resultSet.next()) { /* ... */ }
> } catch (SQLException e) {
>     // tratar erro
> }
> ```

## Tratamento de exceção
JDBC lança `SQLException` (checked exception) em praticamente tudo. O projeto captura e loga:

```java
catch (SQLException e) {
    System.err.println("Erro ao recuperar os funcionários do banco de dados: " + e.getMessage());
    e.printStackTrace();
}
```

## Ver também
- [[Padrao_DAO|Padrão DAO]]
- [[H2_Database|Banco H2 em memória]]
