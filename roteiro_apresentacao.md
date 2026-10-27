# Roteiro de apresentação: iFood Case

## Objetivo da apresentação

Mostrar como a campanha piloto gerou prejuízo, quais clientes apresentam maior propensão histórica de resposta e como uma estratégia de priorização pode melhorar o resultado financeiro da próxima campanha.

Tempo recomendado: 5 a 7 minutos.

Mensagem central:

> A solução não é contactar mais clientes, mas concentrar o contato nos clientes com maior probabilidade de resposta e lucro esperado positivo.

---

## Slide 1 — Contexto e objetivo

### Título

**Como melhorar a rentabilidade da próxima campanha?**

### Conteúdo

- A campanha piloto impactou 2.240 clientes.
- O objetivo é definir quais clientes devem receber a próxima oferta.
- A decisão precisa considerar não apenas propensão de compra, mas também retorno financeiro.

### Fala sugerida

“O desafio não era simplesmente encontrar quem provavelmente compraria. Era identificar quem valeria a pena contactar considerando o custo da campanha e a receita esperada por conversão.”

---

## Slide 2 — Diagnóstico financeiro da campanha piloto

### Indicadores

| Métrica | Resultado |
|---|---:|
| Clientes contactados | 2.240 |
| Conversões | 334 |
| Taxa de conversão | 14,91% |
| Custo por contato | 3 MU |
| Receita por conversão | 11 MU |
| Resultado da campanha | -3.046 MU |
| Break-even | 27,27% |

### Mensagem principal

A campanha converteu 14,91%, mas precisava superar 27,27% para empatar.

### Fala sugerida

“O primeiro diagnóstico foi financeiro. A campanha perdeu 3.046 MU porque a conversão ficou muito abaixo do ponto de equilíbrio. Isso indica que contactar a base inteira não é uma estratégia eficiente sob essas premissas.”

---

## Slide 3 — Qualidade dos dados e principais sinais

### Conteúdo

- Não foram encontradas linhas ou IDs duplicados.
- Foram identificados 24 registros com renda ausente.
- Quatro clientes foram sinalizados para auditoria:
  - três com ano de nascimento anterior a 1936;
  - um com renda igual a 666.666.
- Os quatro representam apenas 0,18% da base.
- A análise principal utilizou 2.236 clientes elegíveis.

### Principal insight comportamental

| Campanhas anteriores aceitas | Taxa de resposta atual |
|---:|---:|
| 0 | 8,23% |
| 1 | 31,17% |
| 2 | 50,60% |
| 3 | 79,55% |
| 4 | 90,91% |

### Fala sugerida

“O histórico de aceitação de campanhas foi o sinal mais evidente. Clientes sem histórico positivo ficaram abaixo do break-even, enquanto clientes que já haviam aceitado campanhas anteriores apresentaram taxas de resposta significativamente maiores.”

---

## Slide 4 — Modelo de propensão

### Conteúdo

- Foi utilizada uma regressão logística.
- O modelo combina perfil, histórico de compras, engajamento e campanhas anteriores.
- ROC-AUC: 0,893.
- PR-AUC: 0,618.

### Interpretação

O modelo consegue ordenar razoavelmente bem os clientes entre maior e menor propensão histórica de resposta.

### Fala sugerida

“Escolhi uma regressão logística porque ela é interpretável e gera probabilidades. Os indicadores mostram uma boa capacidade de ordenação para uma primeira versão, mas não representam causalidade: sem grupo de controle, não sabemos quantas compras aconteceriam sem a campanha.”

---

## Slide 5 — Da probabilidade para o lucro esperado

### Fórmula

```text
Lucro esperado = Probabilidade de resposta × 11 - 3
```

### Regra de decisão

Contactar clientes com probabilidade estimada superior a 27,27%, pois esse é o ponto de equilíbrio da campanha.

### Faixas de prioridade

| Faixa | Clientes | Lucro esperado |
|---|---:|---:|
| Alta prioridade | 200 | +1.014 MU |
| Prioridade de teste | 168 | +200 MU |
| Não priorizar | 1.868 | -4.248 MU |

### Fala sugerida

“O modelo transforma uma probabilidade em uma decisão financeira. Não basta o cliente ter alguma chance de comprar; ele precisa ter uma chance suficiente para compensar o custo do contato.”

---

## Slide 6 — O que a estratégia recupera?

### Resultado acumulado da alta prioridade

```text
Prejuízo da campanha piloto:       -3.046 MU
Lucro esperado da alta prioridade: +1.014 MU
Resultado acumulado:               -2.032 MU
```

### Interpretação

- A alta prioridade gera lucro esperado positivo.
- Esse lucro recupera aproximadamente 33,29% do prejuízo anterior.
- A nova campanha melhora o resultado, mas não recupera todo o prejuízo em uma única rodada.
- Os 368 clientes com lucro esperado positivo geram aproximadamente +1.214 MU de lucro esperado.

### Mensagem principal

O modelo reduz o desperdício, mas não cria valor econômico sozinho. Para recuperar todo o gap, será necessário testar uma oferta, canal ou abordagem capaz de aumentar conversão, receita por conversão ou reduzir custo de contato.

### Fala sugerida

“É importante separar o lucro da nova campanha do resultado acumulado. A alta prioridade é positiva isoladamente, mas ainda não compensa integralmente o prejuízo histórico. Isso mostra o limite da segmentação e abre espaço para um teste de oferta ou canal.”

---

## Slide 7 — Recomendação e próximos passos

### Recomendação

1. Priorizar os clientes com lucro esperado positivo.
2. Usar a base `clientes_priorizados_contato.csv` como lista operacional.
3. Separar uma amostra aleatória para controle.
4. Testar uma abordagem diferenciada nos clientes de alta prioridade.
5. Medir lucro incremental, e não apenas conversão.

### Indicadores da próxima campanha

- taxa de conversão;
- custo por conversão;
- receita e margem por cliente;
- lucro incremental contra o grupo de controle;
- cobertura do prejuízo piloto;
- desempenho por faixa de score.

### Fala sugerida

“Minha recomendação é usar o modelo como mecanismo de priorização e validar a próxima campanha com experimento controlado. Assim conseguimos saber se estamos apenas identificando clientes que já comprariam ou se a campanha realmente está gerando compras incrementais.”

---

## Materiais para o Gamma

Usar no deck:

- gráfico da campanha piloto versus break-even;
- gráfico de resposta por campanhas anteriores;
- gráfico de taxa de resposta por recência;
- distribuição das probabilidades previstas;
- lucro esperado acumulado por prioridade;
- tabela de faixas de prioridade;
- tabela de resultado acumulado.

Evitar colocar a lista completa de IDs nos slides. O arquivo `clientes_priorizados_contato.csv` deve ser tratado como material operacional complementar ou apêndice.

## Observações metodológicas

- A base não apresenta grupo de controle explícito.
- O modelo estima propensão histórica, não efeito causal.
- A validação atual é aleatória; uma versão futura deve preferir validação temporal.
- O corte de 1936 é uma premissa de elegibilidade e deve ser validado pelo negócio.
- A receita de 11 MU deve ser substituída por margem ou contribuição caso represente receita bruta.
