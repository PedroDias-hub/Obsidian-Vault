# Spring Boot (UNIP)

Notas baseadas no projeto de aula **auladao** (`com.unip.auladao`) — um cadastro simples de funcionários usado para ensinar o **padrão DAO** com JDBC puro dentro de uma aplicação Spring Boot, antes de introduzir o Spring Data JPA.

## Notas
1. [[Arquitetura_Em_Camadas|Arquitetura em camadas]] — visão geral do fluxo Controller → Service → DAO → Banco
2. [[Padrao_DAO|Padrão DAO]] — o que é, por que existe, como foi implementado
3. [[JDBC_Puro|JDBC puro]] — Connection, Statement, PreparedStatement, ResultSet
4. [[H2_Database|Banco H2 em memória]] — configuração, `schema.sql`, console H2
5. [[Spring_MVC_Controller|Spring MVC — Controller básico]] — `@Controller`, `@RequestMapping`, `@ResponseBody`
6. [[Projeto_AulaDAO|Projeto auladao — walkthrough completo]] — o código real, do início ao fim

## Contexto
Esse projeto é bem simples em termos de abstração: não usa injeção de dependência do Spring (`@Autowired`) nem Spring Data JPA — tudo é instanciado manualmente (`new FuncionarioDAOImpl()`). Isso é proposital: a aula isola o padrão DAO "na mão" antes de mostrar como o Spring automatiza isso.

Para comparar com uma abordagem mais moderna (JPA + DI), ver as anotações em [[Projeto_AulaDAO#Comparação com Spring Data JPA]].

## Ver também
- [[Spring Boot/README|UNIP]]
