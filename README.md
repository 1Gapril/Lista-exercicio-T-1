# Lista de Exercícios - TDD (Test-Driven Development)

**Aluno:** Gabriel Ferreira
**RA:** 325140970
**Disciplina:** Garantia da Qualidade de Software / Gestão e Qualidade de Software
**Professor:** Daniel Henrique Matos de Paiva

---

## Exercício 1: A Mudança de Mentalidade (Código Primeiro vs. Teste Primeiro)

**a) Por que começar escrevendo o teste obriga o desenvolvedor a pensar como um "cliente" ou "usuário" da classe, em vez de pensar na implementação interna?**

**Resposta:** Escrever o teste primeiro força o desenvolvedor a pensar no comportamento esperado, nas entradas e nas saídas do sistema (o que o programa deve fazer), antes de se preocupar com a lógica interna (como o programa vai fazer). Isso ajuda a focar estritamente no resultado e no valor entregue ao cliente, guiando o design do código a partir do seu uso real.

**b) Em equipes que usam o fluxo tradicional, é muito comum encontrar a frase: "O código já está pronto, só falta fazer os testes". Explique por que, sob a ótica do TDD, essa frase é uma contradição e qual o risco de escrever testes depois do código de produção estar totalmente pronto.**

**Resposta:** Sob a ótica do TDD, essa frase é uma contradição porque o teste é a ferramenta que guia a construção do código, não uma etapa de verificação posterior. O risco de escrever testes no final é que o desenvolvedor pode criar testes viciados (que apenas confirmam o que o código já faz, mesmo que esteja errado) e se deparar com um código altamente acoplado e difícil de testar, o que muitas vezes leva a equipe a abandonar a criação dos testes.

---

## Exercício 2: O Ritmo do TDD — O Ciclo Red-Green-Refactor

**a) Explique o que significa e o que deve ser feito pelo desenvolvedor em cada uma das três etapas:**

**Resposta:**
*   **RED:** Escrever um teste para uma nova funcionalidade ou melhoria. Como a funcionalidade ainda não existe, o teste obrigatoriamente deve falhar (inclusive por erro de compilação).
*   **GREEN:** Escrever o código de produção mínimo e mais simples possível, apenas para fazer o teste passar. O foco aqui é fazer o teste ficar verde, sem se preocupar com a elegância do código neste momento.
*   **REFACTOR:** Analisar o código recém-criado e melhorá-lo (remover duplicações, melhorar nomes de variáveis, aplicar padrões), garantindo que os testes continuem passando (verdes) após as alterações.

**b) O que é o princípio da "Solução Mais Simples Possível" na fase GREEN? Por que, nessa fase, é permitido até mesmo retornar um valor fixo (hardcoded) para fazer o teste passar?**

**Resposta:** O princípio determina que não se deve antecipar complexidades. Na fase GREEN, o único objetivo é mudar o estado do teste de falhando para passando. Retornar um valor fixo (*hardcoded*) é permitido e encorajado porque comprova que a conexão entre o teste e o código funciona. A generalização e a lógica real do método serão exigidas naturalmente pela criação dos próximos testes e resolvidas na fase de refatoração.

**c) Se durante a etapa REFACTOR você alterar o código e um dos testes que antes estava verde ficar vermelho, qual deve ser a sua atitude imediata?**

**Resposta:** A atitude imediata deve ser interromper a refatoração e corrigir o problema que quebrou o teste (frequentemente desfazendo a última alteração com um "Ctrl+Z"). No TDD, você só deve continuar refatorando ou criando novas lógicas quando a suíte de testes estiver 100% verde.

---

## Exercício 3: As Três Leis do TDD

**a) Suponha que você precisa criar um método somar(a, b). Segundo a Lei 2, se você tentar escrever o teste chamando calculadora.somar(2, 3) e a classe Calculadora nem sequer existir no projeto, o teste compilou? Isso conta como um teste que falhou (RED)?**

**Resposta:** O teste não compilará, pois a classe não existe. No entanto, segundo as regras do TDD, **isso conta sim como um teste que falhou (estado RED)**. Erros de compilação são considerados falhas. O próximo passo (GREEN) seria justamente criar a classe `Calculadora` e o método `somar` (mesmo que vazios) apenas para fazer o código compilar e avançar no ciclo.

**b) Qual é a vantagem prática de seguir loops tão curtos de desenvolvimento (que duram segundos ou poucos minutos) em vez de passar horas programando antes de rodar qualquer coisa?**

**Resposta:** Loops curtos fornecem um *feedback* constante e imediato. Se algo quebrar, você sabe exatamente qual foi a última pequena alteração que causou o problema, tornando a correção trivial. Isso evita o acúmulo de erros sistêmicos que levariam horas para serem depurados no fluxo tradicional.

---

## Exercício 4: O Teste como Documentação Viva

**a) Explique a frase: "No TDD, a suíte de testes unitários funciona como uma documentação executável e sempre atualizada do sistema".**

**Resposta:** Documentações tradicionais (em texto) ficam facilmente defasadas conforme o software evolui. Os testes unitários, por outro lado, descrevem exatamente o comportamento esperado do sistema por meio de código. Como eles são executados continuamente (documentação executável), se o código mudar e o comportamento documentado no teste não for mais realidade, o teste falha, forçando a equipe a manter essa "documentação" sempre atualizada.

**b) Por que a nomeação dos métodos de teste é crucial para essa documentação? Compare os dois nomes abaixo e diga qual expressa melhor a intenção do requisito de negócio:**

**Resposta:** O nome do método de teste serve como o "título" do requisito documentado. A **Opção B** (`deveBloquearSaqueQuandoSaldoForInsuficiente()`) expressa muito melhor a intenção do negócio, pois descreve claramente o cenário, a ação e o resultado esperado. A Opção A (`teste1()`) não comunica nada sobre o comportamento do sistema, inutilizando o teste como forma de documentação.

---

## Exercício 5: Baby Steps (Passos de Bebê)

**a) Em vez de tentar validar tudo de uma vez no primeiro teste, ordene e descreva como você dividiria esses requisitos em 3 etapas progressivas de testes (da mais simples para a mais complexa).**

**Resposta:**
1.  **Etapa 1:** Criar um teste validando apenas o tamanho. (Ex: Passar uma senha com 8 letras e garantir que seja aceita; passar uma com 7 letras e garantir que falhe).
2.  **Etapa 2:** Adicionar um teste validando a necessidade de números. (Ex: Passar uma senha com 8 letras, mas sem número, garantindo que falhe).
3.  **Etapa 3:** Adicionar um teste validando a necessidade de caracteres especiais. (Ex: Passar uma senha com 8 letras e um número, mas sem caractere especial, garantindo que falhe).

**b) Qual é a vantagem de avançar em pequenos passos quando você encontra um erro (bug) no código?**

**Resposta:** Ao avançar em pequenos passos, o escopo de código modificado desde a última vez que tudo funcionava (estado verde) é mínimo. Quando um *bug* surge, é muito mais rápido e seguro isolar e corrigir a falha, pois a causa do erro estará restrita às poucas linhas de código escritas no último "passo de bebê".
