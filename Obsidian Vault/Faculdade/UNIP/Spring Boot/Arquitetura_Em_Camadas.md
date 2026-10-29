# Arquitetura em Camadas

O projeto `auladao` segue uma separação clássica de responsabilidades em 4 camadas:

```
Controller  →  Service  →  DAO  →  Connection/Banco de dados
(HTTP)         (regras)     (SQL)     (H2)
```

## As camadas no projeto

| Camada | Classe | Pacote | Responsabilidade |
|---|---|---|---|
| Model | `Funcionario` | `model` | Representa a entidade (POJO puro, sem lógica de banco) |
| DAO | `FuncionarioDAO` / `FuncionarioDAOImpl` | `model.db` | Executa SQL e converte `ResultSet` em objetos |
| Service | `FuncionarioService` | `model` | Regras de negócio; ponto único que o Controller consulta |
| Controller | `FuncionarioController` | `controller` | Recebe requisições HTTP e devolve respostas |

## Por que separar assim?
- **Controller** não sabe nada de SQL — só conhece o `Service`.
- **Service** não sabe nada de SQL — só conhece o `DAO` (via interface).
- **DAO** é o único lugar que sabe como os dados são armazenados (H2, JDBC).

Isso significa que trocar o banco de dados, ou até trocar SQL por outra forma de persistência, exige mexer só na camada de DAO, sem tocar em Service ou Controller.

## Ponto de atenção: instanciação manual
Nesse projeto, cada camada instancia a próxima "na mão" no construtor:

```java
// FuncionarioService.java
public FuncionarioService() {
    funcionarioDAO = new FuncionarioDAOImpl();
}
```

```java
// FuncionarioController.java
public FuncionarioController() {
    funcionarioService = new FuncionarioService();
}
```

Isso funciona, mas é o oposto da **injeção de dependência** que o Spring oferece (`@Autowired`, `@Service`, `@Repository`). Numa aplicação Spring "idiomática", o Spring criaria e injetaria essas dependências automaticamente — ver [[Projeto_AulaDAO#Comparação com Spring Data JPA]].

## Ver também
- [[Padrao_DAO|Padrão DAO]]
- [[Spring_MVC_Controller|Spring MVC — Controller básico]]
- [[Spring Boot/README|Spring Boot (UNIP)]]
