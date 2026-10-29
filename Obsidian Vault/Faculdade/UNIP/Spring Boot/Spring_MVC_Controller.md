# Spring MVC — Controller Básico

## O código do projeto
```java
@Controller
public class FuncionarioController {
    FuncionarioService funcionarioService = null;

    public FuncionarioController() {
        funcionarioService = new FuncionarioService();
    }

    @RequestMapping("/listarFuncionarios")
    @ResponseBody
    public String listarFuncionarios() {
        String resposta = "";
        for (Funcionario funcionario : funcionarioService.listarFuncionarios()) {
            resposta += funcionario.toString() + "<br>";
        }
        return resposta;
    }

    @RequestMapping("/pesquisarFuncionario")
    @ResponseBody
    public String pesquisarFuncionario(@RequestParam("cod") int codigo) {
        String resposta = "";
        Funcionario fun = funcionarioService.pesquisarFuncionario(codigo);
        if (fun != null)
            resposta += fun.toString();
        return resposta;
    }
}
```

## As anotações

- **`@Controller`**: marca a classe como um controlador Spring MVC — o Spring escaneia e registra essa classe automaticamente, associando os métodos às rotas.
- **`@RequestMapping("/rota")`**: mapeia a URL para o método. `GET /listarFuncionarios` chama `listarFuncionarios()`.
- **`@ResponseBody`**: diz ao Spring "não procure uma página HTML (view) para essa resposta — devolva o valor de retorno diretamente no corpo da resposta HTTP". Sem essa anotação, `@Controller` tentaria resolver uma *view* (ex: um template Thymeleaf).
- **`@RequestParam("cod")`**: pega o parâmetro `cod` da query string. Chamando `/pesquisarFuncionario?cod=1`, o Spring injeta `1` no parâmetro `codigo`.

## `@Controller` + `@ResponseBody` vs `@RestController`
Essa combinação (`@Controller` em toda a classe + `@ResponseBody` em cada método) é equivalente a usar **`@RestController`** na classe inteira — `@RestController` é só um atalho que já aplica `@ResponseBody` a todos os métodos automaticamente. Em uma API REST "de verdade", normalmente se usa `@RestController` direto.

## Rotas HTTP "informais"
Repare que as rotas usam verbos no nome (`/listarFuncionarios`, `/pesquisarFuncionario`) em vez do padrão REST (`GET /funcionarios`, `GET /funcionarios/{codigo}`). Isso é comum em projetos didáticos simples — numa API REST convencional, o recurso (`/funcionarios`) fica no caminho e a ação é definida pelo verbo HTTP (`GET`, `POST`, etc.), não pelo nome da rota.

## Resposta em texto/HTML cru
O método devolve uma `String` com tags `<br>` concatenadas manualmente — funciona, mas não é o padrão de uma API real, onde normalmente se devolveria JSON (uma `List<Funcionario>` como retorno já seria serializada automaticamente pelo Spring como JSON, sem precisar montar a `String` na mão).

## Ver também
- [[Arquitetura_Em_Camadas|Arquitetura em camadas]]
- [[Projeto_AulaDAO|Projeto completo]]
