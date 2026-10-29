# Projeto auladao — Walkthrough Completo

Projeto: `com.unip.auladao` · Spring Boot 4.1.1 · Java 21 · H2 em memória.

## Estrutura de pacotes
```
com.unip.auladao
├── AuladaoApplication.java          (classe main)
├── controller/
│   └── FuncionarioController.java   (recebe HTTP)
├── model/
│   ├── Funcionario.java             (entidade/POJO)
│   ├── FuncionarioService.java      (regra de negócio)
│   └── db/
│       ├── ConnectionFactory.java   (abre conexão JDBC)
│       ├── FuncionarioDAO.java      (interface)
│       └── FuncionarioDAOImpl.java  (implementação com SQL)
```

## O caminho de uma requisição
Exemplo: o navegador acessa `GET /pesquisarFuncionario?cod=1`

1. **`FuncionarioController.pesquisarFuncionario(1)`** recebe a requisição — [[Spring_MVC_Controller|detalhes]]
2. Chama **`funcionarioService.pesquisarFuncionario(1)`**
3. **`FuncionarioService`** repassa para **`funcionarioDAO.pesquisarFuncionario(1)`** — [[Padrao_DAO|detalhes]]
4. **`FuncionarioDAOImpl`** abre conexão via `ConnectionFactory`, monta um `PreparedStatement` e executa o SQL — [[JDBC_Puro|detalhes]]
5. O `ResultSet` é convertido num objeto `Funcionario`
6. O objeto sobe de volta: DAO → Service → Controller
7. O Controller chama `.toString()` no objeto e devolve como texto puro na resposta HTTP

## `Funcionario` — o modelo
Um POJO simples: atributos privados + getters/setters + `toString()`. Sem nenhuma anotação de banco (sem `@Entity`, sem `@Id`) — porque quem sabe mapear os campos para colunas é o `FuncionarioDAOImpl`, na mão, linha por linha:

```java
new Funcionario(resultSet.getInt("codigo"), resultSet.getString("nome"),
                 resultSet.getString("cargo"), resultSet.getBoolean("ativo"))
```

## Comparação com Spring Data JPA
Como você já mexe com JPA no seu projeto de task manager, vale ver lado a lado o que o Spring automatiza:

| Neste projeto (DAO manual) | Com Spring Data JPA |
|---|---|
| `Funcionario` é um POJO puro | `Funcionario` vira `@Entity`, com `@Id` no campo `codigo` |
| `FuncionarioDAO` + `FuncionarioDAOImpl` escritos à mão | Basta `interface FuncionarioRepository extends JpaRepository<Funcionario, Integer>` — sem implementação |
| SQL escrito manualmente (`select * from funcionario where codigo = ?`) | Gerado automaticamente a partir do nome do método (`findByCodigo`) ou de `@Query` |
| `ConnectionFactory.getConnection()` chamado a cada operação | Gerenciado pelo Spring via `DataSource`/connection pool |
| Dependências instanciadas com `new` no construtor | Injeção de dependência com `@Autowired` (ou construtor + `@Service`/`@Repository`) |
| Controller monta `String` manualmente | Retornar a entidade/lista direto vira JSON automaticamente |

Nenhuma abordagem está "errada" — o projeto `auladao` existe justamente para mostrar o que está por baixo do capô antes de confiar no JPA para fazer isso por você.

## Ver também
- [[Spring Boot/README|Spring Boot (UNIP)]]
- [[Arquitetura_Em_Camadas|Arquitetura em camadas]]
- [[Padrao_DAO|Padrão DAO]]
- [[JDBC_Puro|JDBC puro]]
- [[H2_Database|Banco H2 em memória]]
- [[Spring_MVC_Controller|Spring MVC — Controller básico]]
