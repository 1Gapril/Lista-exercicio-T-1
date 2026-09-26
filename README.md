# Lista-exercicio-T-1

##Gabriel Ferreira 325140970##

# Atividades de Garantia da Qualidade de Software

## Exercício 1: A Mudança de Mentalidade (Código Primeiro vs. Teste Primeiro)

**Pergunta a)** Por que começar escrevendo o teste obriga o desenvolvedor a pensar como um "cliente" ou "usuário" da classe, em vez de pensar na implementação interna?

**Resposta:** Escrever o teste primeiro faz o desenvolvedor pensar no que o usuário quer que o programa faça, não em como o programa vai funcionar por dentro. Isso ajuda a focar no resultado que importa para o cliente.

**Pergunta b)** Em equipes que usam o fluxo tradicional, é muito comum encontrar a frase: "O código já está pronto, só falta fazer os testes". Explique por que, sob a ótica do TDD, essa frase é uma contradição e qual o risco de escrever testes depois do código de produção estar totalmente pronto.

**Resposta:** Dizer "o código está pronto, só falta testar" é errado no TDD porque os testes devem ser feitos antes do código. Fazer testes depois pode deixar passar erros, porque o teste pode só confirmar o que o código já faz, sem garantir que tudo está correto.

---

## Exercício 2: O Ritmo do TDD — O Ciclo Red-Green-Refactor

**Pergunta a)** Explique o que significa e o que deve ser feito pelo desenvolvedor em cada uma das três etapas: RED, GREEN, REFACTOR.

**Resposta:**
- **RED:** Escrever um teste que falha porque a funcionalidade ainda não foi implementada.
- **GREEN:** Escrever o código mínimo para fazer o teste passar, mesmo que seja simples ou com valor fixo.
- **REFACTOR:** Melhorar o código sem mudar seu comportamento, deixando-o mais limpo e eficiente.

**Pergunta b)** O que é o princípio da "Solução Mais Simples Possível" na fase GREEN? Por que, nessa fase, é permitido até mesmo retornar um valor fixo (hardcoded) para fazer o teste passar?

**Resposta:** Na fase GREEN, o objetivo é fazer o teste passar com o menor esforço possível, sem se preocupar com a perfeição do código. Retornar um valor fixo é permitido porque o foco é garantir que o teste passe, para depois melhorar o código na fase REFACTOR.

**Pergunta c)** Se durante a etapa REFACTOR você alterar o código e um dos testes que antes estava verde ficar vermelho, qual deve ser a sua atitude imediata?

**Resposta:** Você deve corrigir imediatamente o problema que fez o teste falhar, voltando a ter todos os testes passando antes de continuar.

---

## Exercício 3: As Três Leis do TDD

**Pergunta a)** Suponha que você precisa criar um método somar(a, b). Segundo a Lei 2, se você tentar escrever o teste chamando calculadora.somar(2, 3) e a classe Calculadora nem sequer existir no projeto, o teste compilou? Isso conta como um teste que falhou (RED)?

**Resposta:** Não, o teste não compila porque a classe Calculadora não existe. Isso não é considerado um teste que falhou, mas sim um erro de compilação.

**Pergunta b)** Qual é a vantagem prática de seguir loops tão curtos de desenvolvimento (que duram segundos ou poucos minutos) em vez de passar horas programando antes de rodar qualquer coisa?

**Resposta:** Loops curtos ajudam a detectar erros rapidamente, facilitam correções imediatas e mantêm o código sempre funcionando, evitando acúmulo de problemas difíceis de resolver depois.

---

## Exercício 4: O Teste como Documentação Viva

**Pergunta a)** Explique a frase: "No TDD, a suíte de testes unitários funciona como uma documentação executável e sempre atualizada do sistema".

**Resposta:** Os testes mostram exatamente como o sistema deve funcionar e são executados sempre que o código muda, garantindo que a documentação está sempre correta e atualizada.

**Pergunta b)** Por que a nomeação dos métodos de teste é crucial para essa documentação? Compare os dois nomes abaixo e diga qual expressa melhor a intenção do requisito de negócio:
* Opção A: @Test void teste1()
* Opção B: @Test void deveBloquearSaqueQuandoSaldoForInsuficiente()

**Resposta:** O nome do método deve ser claro e descrever o que está sendo testado. A Opção B é melhor porque explica claramente o comportamento esperado, facilitando o entendimento do requisito.

---

## Exercício 5: Baby Steps (Passos de Bebê)

**Pergunta a)** Em vez de tentar validar tudo de uma vez no primeiro teste, ordene e descreva como você dividiria esses requisitos em 3 etapas progressivas de testes (da mais simples para a mais complexa).

**Resposta:**
1. Testar se a senha tem pelo menos 8 caracteres.
2. Testar se a senha contém pelo menos um número.
3. Testar se a senha contém pelo menos um caractere especial.

**Pergunta b)** Qual é a vantagem de avançar em pequenos passos quando você encontra um erro (bug) no código?

**Resposta:** Avançar em pequenos passos facilita encontrar exatamente onde o erro ocorreu, tornando a correção mais rápida e segura.
