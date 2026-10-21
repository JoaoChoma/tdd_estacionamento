# TDD — Estacionamento (Java 17 + Maven + JUnit 5)

1. Projeto de referência **com implementação concluída** para orientar a demonstração do conteúdo.

2. A ideia é começar com um projeto Maven vazio e escrever os testes antes de criar `Estacionamento`. 

3. Use esse repositório para orientar o que você implementou.

---

Abra a pasta do projeto no IntelliJ IDEA como projeto Maven. É necessário Java 17 e Maven (ou usar o Maven integrado da IDE).

## Requisitos e testes

| Regra | Comportamento | Testes |
|---|---|---|
| RN01 | Criar estacionamento com capacidade máxima informada | `deveArmazenarCapacidadeMaxima`, `deveArmazenarOutraCapacidadeMaxima` |
| RN02 | Iniciar com ocupação zero | `deveIniciarComZeroVeiculos` |
| RN03 | Cada entrada aumenta a ocupação em uma unidade | `deveAdicionarUmVeiculo`, `deveAcumularEntradas` |
| RN04 | Impedir entrada acima da capacidade | `naoDevePermitirEntradaQuandoLotado` |

## Roteiro de demonstração (RED → GREEN → REFACTOR)

1. **RN02:** escreva `deveIniciarComZeroVeiculos()` antes de existir a classe. Use `Alt+Enter` para gerar classe, construtor e `getOcupacao()`. Com método lançando `UnsupportedOperationException`, observe RED. Retorne `0` para GREEN.
2. **RN01:** escreva `deveArmazenarCapacidadeMaxima()`. Gere `getCapacidadeMaxima()` e retorne provisoriamente `0` (RED). Retorne `10` (GREEN apenas para esse cenário). Adicione teste com `25` (RED); armazene o argumento em um campo e retorne o campo (GREEN). Renomeie parâmetro `i` para `capacidadeMaxima` com `Shift+F6` (REFACTOR).
3. **RN03:** escreva teste que chama `adicionarVeiculo()`. Gere método vazio (RED: ocupação continua zero). Crie campo `ocupacao`, incremente com `ocupacao++` e retorne o campo em `getOcupacao()` (GREEN). Teste duas entradas.
4. **RN04:** escreva teste de estacionamento lotado. Preencha 3 vagas, tente quarta entrada e verifique `assertThrows(IllegalStateException.class, ...)` **e** ocupação preservada em 3 (RED). Valide antes de incrementar (GREEN). Opcional: extrair validação em método privado (REFACTOR).

### Implemente os casos de teste e na sequência implemente o código do produto. 

## Estrutura

```text
pom.xml
src/main/java/br/uem/tdd/Estacionamento.java
src/test/java/br/uem/tdd/EstacionamentoTest.java
```

## Atenção

`O exemplo cobre apenas criação, ocupação, entrada e lotação. Saída de veículos e validação de capacidade não fazem parte desta versão.`
