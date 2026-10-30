# iFood Case: Otimização de campanhas

Análise exploratória e proposta inicial de priorização utilizando um modelo preditivo de propensão (Machine Learning), com foco na identificação de clientes estratégicos para otimizar a rentabilidade da campanha de marketing.

## Objetivo

Usar dados de perfil, compras e respostas a campanhas anteriores para identificar quais clientes devem ser priorizados na próxima campanha.

## Conteúdo

- `IfoodCase_Resolution.ipynb`: notebook com carregamento, validações, exploração, segmentação, diagnóstico financeiro, regressão logística e score de priorização.
- `ifood_case_data.csv`: base utilizada na análise.
- `ifood_case_enunciado.md`: enunciado original do case.

## Como executar

Abra o notebook no Jupyter ou clique aqui para ir Google Colab e execute as células em ordem. Os dados são carregados diretamente do GitHub.

## Premissas principais

- Custo por contato: 3 MU.
- Receita por conversão: 11 MU.
- Break-even: conversão superior a 27,27%.
- Clientes com ano de nascimento anterior a 1936 ou renda igual a 666.666 são sinalizados para auditoria e não entram no modelo principal.
- Sem grupo de controle explícito, os resultados representam propensão histórica, não necessariamente efeito causal da campanha.

## Resultado da análise

O notebook gera um score individual com probabilidade de resposta, lucro esperado, prioridade e faixa de contato. A base recomendada para contato é exportada como `clientes_priorizados_contato.csv` após a execução do notebook que permite download direto em csv.

## Próximos passos

Validar o score em uma divisão temporal, testar uma oferta ou canal alternativo e acompanhar a próxima campanha com grupo de controle aleatório para medir o lucro incremental.
