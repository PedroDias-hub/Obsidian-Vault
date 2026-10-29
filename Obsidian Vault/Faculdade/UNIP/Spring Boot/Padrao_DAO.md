# Padrão DAO (Data Access Object)

## O que é
DAO é um padrão de projeto que **isola toda a lógica de acesso a dados** (SQL, conexões, `ResultSet`) atrás de uma interface. O resto da aplicação (Service, Controller) conversa só com a interface — nunca com SQL diretamente.

## Estrutura no projeto

### 1. A interface — define o contrato
```java
public interface FuncionarioDAO {
    public List<Funcionario> listarFuncionarios();
    public Funcionario pesquisarFuncionario(int codigo);
}
```

### 2. A implementação — faz o trabalho sujo (SQL)
```java
public class FuncionarioDAOImpl implements FuncionarioDAO {

    @Override
    public List<Funcionario> listarFuncionarios() {
        List<Funcionario> lista = new ArrayList<>();
        try {
            Connection connection = ConnectionFactory.getConnection();
            Statement statement = connection.createStatement();
            ResultSet resultSet = statement.executeQuery("select * from funcionario");
            while (resultSet.next()) {
                lista.add(new Funcionario(resultSet.getInt("codigo"),
                    resultSet.getString("nome"), resultSet.getString("cargo"),
                    resultSet.getBoolean("ativo")));
            }
            resultSet.close();
            statement.close();
            connection.close();
        } catch (SQLException e) {
            System.err.println("Erro ao recuperar os funcionários: " + e.getMessage());
        }
        return lista;
    }
    // ...
}
```

## Por que usar uma interface?
- O `FuncionarioService` depende de `FuncionarioDAO` (a interface), não de `FuncionarioDAOImpl` (a implementação).
- Se amanhã você trocar de H2 para PostgreSQL, ou de JDBC puro para outra estratégia, basta criar uma nova classe que implementa `FuncionarioDAO` — nada no Service ou no Controller muda.
- Isso é o princípio da **inversão de dependência** (o "D" de SOLID) aplicado na prática.

## `listarFuncionarios()` vs `pesquisarFuncionario(int codigo)`
- `listarFuncionarios()` usa `Statement` simples — não recebe parâmetros externos, então não há risco de SQL injection.
- `pesquisarFuncionario(int codigo)` usa `PreparedStatement` com `?` — necessário sempre que um valor externo (vindo do usuário) entra na query, para evitar SQL injection e problemas de tipagem:

```java
PreparedStatement preparedStatement = connection.prepareStatement(
    "select * from funcionario where codigo = ?");
preparedStatement.setInt(1, codigo);
```

## DAO x Repository (Spring Data JPA)
O `FuncionarioDAO` daqui é o "avô" manual do que o Spring Data JPA automatiza com `@Repository` e interfaces como `JpaRepository<Funcionario, Integer>`: lá, você nem escreve a implementação — o Spring gera na hora de rodar. Entender o DAO na mão ajuda a entender **o que o JPA está economizando** de código.

## Ver também
- [[Arquitetura_Em_Camadas|Arquitetura em camadas]]
- [[JDBC_Puro|JDBC puro]]
- [[Projeto_AulaDAO|Projeto completo]]
