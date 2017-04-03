# Android Testing Euro Training

![Euro Training](https://media.giphy.com/media/tBYOOzPcku9s4/giphy.gif "Euro Training")

# Agenda

0. Setup do ambiente para o treinamento

  - Android SDK
  - Android Studio
    - Run configurations
  - PATH e ANDROID_HOME (adb, emulator e etc)
  - GIT
  - Clone do repo

1. [Para que testar?](chapter_1/CHAPTER.md)

  - Qualidade de software
    - Garantias de qualidade
    - Camadas de qualidade
    - Medidas de qualidade
  - Caminho feliz vs Realidade de produção
  - Confiabilidade
    - Especificamente no Android
  - Design de software

2. Conceitos básicos de testes

  - Tipos de teste
    - unitários vs funcionais
    - locais vs instrumentados
    - Outros tipos (integrados, stress, segurança, etc)
  - Fases de um teste
      - Preparação
      - Execução
      - Asserção
  - Aferindo execuções: asserções
    - JUnit e Hamcrest
    - Espresso e Hamcrest
    - AssertJ
  - Ordem de testes
  - Taggeamento de testes
    - Smoke tests
  - O que faz um teste falhar?
    - Sempre faça um teste falhar primeiro
  - Estilos de teste
    - Gherkin (BDD e SBE)
    - Triple AAA
    - Robots e Results
  - Características de uma suíte de testes
    - FIRST (Fast, Isolated/Independent, Repeatable, Self-Validating, Thorough and Timely)
  - Devo testar meu código de testes?
    - Não.
    - Sim.
  - Escopo do código de teste: NUNCA EM CÓDIGO DE APLICAÇÃO!
    - Vale até reflection...
  - Atomicidade dos testes

3. JUnit

  - Rápida história do JUnit
    - JUnit 3 (padrão Android): `junit.framework.TestCase`
    - JUnit 4 (padrão support Android): `org.junit.Test`
    - JUnit 5 (já é possível no Android): `org.junit.jupiter.api.Test`
  - Ciclo de vida de um teste
    - `@Before`
    - `@After`
    - `@BeforeClass`
    - `@AfterClass`
  - Execução de um teste
    - O famoso `TestRunner`
    - `@RunWith`
    - O que é um `Statement`?
    - `@Rule` e `@RuleChain`
  - Asserções: `org.junit.Assert`
    - Conflitos com o Hamcrest na história do JUnit
  - Aferindo exceções `org.junit.rules.ExpectedException`
  - JUnit listeners

4. Hamcrest

  - Escrevendo asserções narrativas
  - "Me garanta que..." `org.hamcrest.MatcherAssert.assertThat()`
  - `org.hamcrest.Matcher`
    - `void describeMismatch(Object item, Description mismatchDescription)`
    - "N.B. Well designed matchers should be immutable."
  - hamcrest-library
    - `org.hamcrest.Matchers`
  - Custom Matchers

5. Robolectric

  - Rápida história do Robolectric
    - Born as a hack
    - Shadows everywhere
    - Baixa confiabilidade
    - Crescimento dentro da comunidade
    - Dias de hoje
  - Arquitetura
    - As close as possible to Android (usando o fonte do Android)
    - Atenção! O download do fonte é dinâmico!
    - Fakes
  - `org.robolectric.RobolectricTestRunner`
    - `@Config`
    - `robolectric.properties`
  - O contexto principal: `org.robolectric.RuntimeEnvironment.application`
  - Como faço uma aplicação de teste para o Robolectric?
    - Usando o sufixo 'Test'
  - Ciclo de vida das Activities (e Fragments e Views)
    - 'X'Controller: ActivityController, FragmentController, etc
    - Robolectric.build'X': buildActivity, buildFragment, buildService, etc
    - Diferença entre build'X' e setup'X'
  - O que eu devo testar com Robolectric?
    - Lembre-se: não é o Android!
    - Lógica entre callbacks de ciclo de vida
      - Pré e pós asserção
  - Testando Views customizadas (`buildAttributeSet`)
  - Pitfalls
    - Dependências nativas (Realm :D)
    - Documentação =/

6. `com.android.support.test`

  - Componentes
    - `runner`
    - `rules`
    - `uiautomator`
    - `janktesthelper`
    - `espresso` (tem seu próprio grupo de depndências)
  - Testes no Android e o dilema do device ou emulador
    - Onde o teste é executado?
    - Arquitetura de testes instrumentados

7. `AndroidJUnitRunner`

  - 

=> Pesquisa sobre o curso

  - Conteúdo?
  - Formato?
  - Exercícios?
