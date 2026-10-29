# Banco H2 em Memória

H2 é um banco de dados relacional escrito em Java, muito usado em desenvolvimento e testes porque roda **em memória** (não precisa instalar nada) e sobe junto com a aplicação.

## Configuração usada no projeto

`application.properties`:
```properties
spring.application.name=auladao

spring.datasource.url=jdbc:h2:mem:empresa
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=adm
spring.datasource.password=password
spring.jpa.show-sql=true
```

- `jdbc:h2:mem:empresa` — banco chamado `empresa`, todo em memória RAM. **Os dados somem quando a aplicação para.**
- `spring.jpa.show-sql=true` — imprime no console cada SQL gerado (útil pra debugar, mesmo esse projeto não usando JPA de fato).

## `schema.sql` — inicialização automática
O Spring Boot roda esse arquivo automaticamente ao subir a aplicação, antes de qualquer código:

```sql
CREATE TABLE funcionario (codigo INT PRIMARY KEY, nome VARCHAR(100), cargo VARCHAR(100), ativo BOOLEAN);

INSERT INTO funcionario (codigo, nome, cargo, ativo) VALUES
(1, 'Maria Silva', 'Gerente', true),
(2, 'João Souza', 'Analista', true);
```

Isso significa que, toda vez que a aplicação reinicia, a tabela é recriada do zero com esses dois registros.

## Console H2
O `pom.xml` inclui a dependência `spring-boot-h2console`, que expõe uma interface web para inspecionar o banco enquanto a aplicação roda (útil para conferir se os dados do `schema.sql` foram carregados, ou testar queries manualmente).

## Por que H2 e não um banco "de verdade"?
Para fins de aula/aprendizado, evita a necessidade de instalar e configurar PostgreSQL/MySQL — o foco fica no código Java (DAO, JDBC, camadas), não em infraestrutura de banco.

## Ver também
- [[JDBC_Puro|JDBC puro]]
- [[Padrao_DAO|Padrão DAO]]
