# Android Testing Euro Training

## Capítulo 1 - Para quê testar?

### Qualidade de software

Como medimos qualidade em software? Vamos comparar os snippets de código abaixo:

``` java
public static void main(String... args) {

    if (args == null || args.length == 0){
        throw new IllegalArgumentException("Missing param");
    }
    
    final MyApp app = new MyApp();
    app.setArgs(args);
    app.init();
}
```

``` java
public static void main(String... args) {

    final Validator argsVal = new MyAppArgumentsValidator(args);
    argsVal.validate();

    final MyApp app = new MyApp();
    app.setArgs(args);
    app.init();
}
```
  
Qual código tem mais qualidade? Não sei.

Qualidade de software é definida de duas formas:

- A qualidade funcional de um software reflete quão bem ele está em conformidade com um dado design, baseado nos requisitos funcionais ou especificações.
- A qualidade estrutural de um software se refere a como ele adere a requisitos não funcionais que suportam a entrega de requisitos funcionais, tais como estabilidade, manutenabilidade e etc.

#### Qualidade funcional

- Garantia de aderência a uma especificação funcional (caso de uso)
- BDD (Behaviour Driven Development) & SBE (Specification by Example)
  - Exercício dos casos de uso definidos por negócio
- Segurança: aderência a requisitos funcionais de segurança
    
#### Qualidade estrutural

- Garantia de aderência a requisitos não funcionais 
- Estrutura: arquitetura
  - Padrões de arquitetura: MVP, MVVM
  - Princípios e arquitetura: SOLID
- Linters: verificação de problemas conhecidos (tanto de execução como de estilo)
  - PMD, FindBugs, Checkstyle
- Estilo: padronização para manutenção
  - Favorecer a legibilidade do código
- Cobertura: exercício de todas as partes
  - Garantir que todos os passos do código sejam executados pelo menos uma vez 
- Performance: definição de metas de runtime
- Segurança: aderência a requisitos não funcionais de segurança
  - Bibliotecas atualizadas
  - Evitar práticas que exponham falhas

### Camadas de qualidade 

- Fluxo de desenvolvimento
  1. Máquina do desenvolvedor
  2. Binário para o QA
  3. Automatização de especificações
  4. Publicação do binário em Beta fechado
  5. Validação dos Stakeholders
  6. Produção

- Pelo menos 3 camadas de qualidade:
  - Validação do desenvolvedor
    - Testes unitários
    - Total controle sobre o código sendo executado
  - Validação do QA
    - Testes funcionais
    - Não possui controle sobre o código da aplicação, mas sim sobre o ambiente de execução
  - Validação do Stakeholder
    - Testes manuais
    - Trabalha como um usuário final interessado
- Em todas as camadas testes servem para *aferir os critérios definidos de qualidade* (seja estrutural ou funcional).

#### Problemas com testes manuais

- Tempo de execução
- Tempo de documentação
- Necessidade de seguir um script que precisará estar constantemente atualizado
- Propenso a erros de averiguação
- Propenso a erros humanos (esquecimento, má execução, etc)
- Falta de recursos para manipular o sistema com o intuito de gerar um determinado cenário
- Pouca rastreabilidade de quando bugs foram introduzidos

### Caminho feliz vs Realidade de produção

- Bases de código sem testes tendem a não validar cenários de exceção
- Produtos com testes manuais também
  - Muitas vezes é preciso manipular o sistema para conseguir gerar determinados cenários
- Bases de teste que não verificam condições excepcionais não estão aferindo todo o comportamento da base de código
  - Assume-se que os desenvolvedores possuem tratamento de erros nos produtos
- Sempre que se verificar um problem em produção deve-se *primeiro* reproduzir o ocorrido com um teste que falhe para em seguida efetuar a correção
  - Este é um teste de regressão: garantir que um erro não volte a ocorrer na base de código

### Confiabilidade

- A plataforma própria plataforma pode introduzir erros
  - O Android possui diversos leaks de memória conhecidos em suas versões. Ver, por exemplo, https://github.com/square/leakcanary/blob/master/leakcanary-android/src/main/java/com/squareup/leakcanary/AndroidExcludedRefs.java
- Todo o código executado no Android é essencialmente paralelo e concorrente. Isso é um grande fator de baixa previsibilidade para testes.
- As ferramentas de teste já melhoraram muito, mas uma suíte de testes extensa nunca vai garantir 100% de crash free. Também não é este o objetivo.

#### Objetivo da suíte de testes

- Tornar o produto o mais livre de bugs possível? Não. 
- **Tornar o produto o mais aderente possível aos critérios de qualidade estrutural e funcional.**

### Design de software (menção honrosa)

- Requisito de qualidade estrutural
  - Impacta em legibilidade, manutenção, performance e segurança
  - Podemos nos utilizar de princípios: SOLID, DRY, KISS, Principle of Least Knowledge, Single Responsibility principle, etc.
- Não é puramente arquitetura geral: MVC, MVP, MVVM.
- Deve ser analisado e testado em todas as partes do código, porém não como um todo.


## Exercícios

1. Qual a definição de teste?
2. Qual a diferença entre qualidade estrutura e funcional?
3. Qual o papel do desenvolvedor de aplicativo na qualidade do produto?
4. Quais as camadas de qualidade e quais suas funções?
5. O que pode-se dizer sobre a confiabilidade que uma suíte de testes em aplicativos móveis nos traz?
