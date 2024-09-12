# Comun Tables Expression

Exemplo:
```sql
WITH "goals_created_up_to_week" AS (
    SELECT "id", "title", "desired_weekly_frequency", "created_at"
    FROM "goals"
    WHERE "goals"."created_at" <= $1
),
"goal_completion_counts" AS (
    SELECT "goal_id", COUNT("id") AS "completionCount"
    FROM "goal_completions"
    WHERE ("goal_completions"."created_at" >= $2 AND "goal_completions"."created_at" <= $3)
    GROUP BY "goal_completions"."goal_id"
)
SELECT
    "goals_created_up_to_week"."id",
    "goals_created_up_to_week"."title",
    "goals_created_up_to_week"."desired_weekly_frequency",
    COALESCE("completionCount", 0)
FROM "goals_created_up_to_week"
LEFT JOIN "goal_completion_counts"
ON "goal_completion_counts"."goal_id" = "goals_created_up_to_week"."id"
```

### Explicação linha a linha:

#### 1. `WITH "goals_created_up_to_week" AS (`
Aqui, estamos criando uma Common Table Expression (CTE) chamada `goals_created_up_to_week`. Uma CTE é uma tabela temporária que só existe durante a execução da query. Esta CTE vai armazenar os dados dos objetivos que foram criados até uma determinada semana.

#### 2. `SELECT "id", "title", "desired_weekly_frequency", "created_at"`
Selecionamos as colunas `id`, `title`, `desired_weekly_frequency` (frequência semanal desejada), e `created_at` (data de criação) da tabela `goals`.

#### 3. `FROM "goals"`
Especifica que os dados estão sendo obtidos da tabela `goals`.

#### 4. `WHERE "goals"."created_at" <= $1`
Filtra as metas que foram criadas até a data indicada pela variável `$1` (um valor que será passado na execução da query).

#### 5. `),`
Fecha a primeira CTE, chamada `goals_created_up_to_week`.

#### 6. `"goal_completion_counts" AS (`
Iniciamos uma segunda CTE chamada `goal_completion_counts`, que será usada para calcular a contagem de realizações (completions) para cada meta.

#### 7. `SELECT "goal_id", COUNT("id") AS "completionCount"`
Selecionamos a coluna `goal_id` da tabela `goal_completions` e contamos o número de realizações (`id`) para cada `goal_id`. Esta contagem é armazenada em uma coluna nomeada `completionCount`.

#### 8. `FROM "goal_completions"`
Especifica que os dados estão sendo obtidos da tabela `goal_completions`.

#### 9. `WHERE ("goal_completions"."created_at" >= $2 AND "goal_completions"."created_at" <= $3)`
Filtra as realizações de metas que ocorreram entre duas datas: uma data inicial (`$2`) e uma data final (`$3`).

#### 10. `GROUP BY "goal_completions"."goal_id"`
Agrupa os resultados por `goal_id` para que possamos contar as realizações por meta.

#### 11. `)`
Fecha a segunda CTE, chamada `goal_completion_counts`.

#### 12. `SELECT`
Iniciamos a parte final da query, onde vamos selecionar e combinar os dados das duas CTEs.

#### 13. `"goals_created_up_to_week"."id",`
Seleciona o `id` da CTE `goals_created_up_to_week`.

#### 14. `"goals_created_up_to_week"."title",`
Seleciona o `title` (título) da CTE `goals_created_up_to_week`.

#### 15. `"goals_created_up_to_week"."desired_weekly_frequency",`
Seleciona a `desired_weekly_frequency` (frequência semanal desejada) da CTE `goals_created_up_to_week`.

#### 16. `COALESCE("completionCount", 0)`
Esta linha utiliza a função `COALESCE` para garantir que, se uma meta não tiver realizações, o valor retornado para `completionCount` seja `0` em vez de `NULL`.

#### 17. `FROM "goals_created_up_to_week"`
Especifica que os dados estão sendo obtidos da CTE `goals_created_up_to_week`.

#### 18. `LEFT JOIN "goal_completion_counts"`
Faz um `LEFT JOIN` com a CTE `goal_completion_counts`, que contém as contagens de realizações de metas. O `LEFT JOIN` garante que todas as metas sejam incluídas, mesmo se não houver realizações associadas.

#### 19. `ON "goal_completion_counts"."goal_id" = "goals_created_up_to_week"."id"`
Especifica que a junção deve ser feita onde o `goal_id` na CTE `goal_completion_counts` corresponde ao `id` na CTE `goals_created_up_to_week`.

---

### Resumo do que a query faz:
1. Obtém todas as metas que foram criadas até uma determinada data (`$1`).
2. Conta quantas vezes cada meta foi completada dentro de um intervalo de tempo específico (`$2` a `$3`).
3. Combina essas duas informações e retorna o `id`, `title`, `desired_weekly_frequency`, e a contagem de completions (ou 0 se não houver completions).

Esse formato de query é útil para gerar relatórios ou dashboards que mostram o progresso das metas ao longo do tempo.

---

Este tipo de query, que utiliza **Common Table Expressions (CTEs)**, é indicado em situações específicas e possui tanto vantagens quanto desvantagens, dependendo do cenário de uso.

### Quando é indicado usar este tipo de query:

1. **Leitura clara e manutenção**:
   - Se você está lidando com uma query complexa e precisa dividir a lógica em partes mais compreensíveis, as CTEs permitem organizar o código SQL de forma mais legível. Cada CTE atua como uma tabela temporária, o que torna a query mais modular e fácil de entender.
   
2. **Reutilização de subconsultas**:
   - Quando há a necessidade de reutilizar o mesmo conjunto de dados várias vezes na query. Usar CTEs permite que você calcule uma vez e referencie a mesma tabela temporária em diferentes partes da consulta, ao invés de duplicar a lógica.
   
3. **Cálculos intermediários**:
   - Quando a query exige cálculos intermediários, como agregações ou contagens baseadas em dados temporários, as CTEs ajudam a criar esses blocos de lógica antes de executar a consulta final.

4. **Hierarquias e dados recursivos**:
   - CTEs recursivas (não aplicável no seu exemplo específico) são extremamente úteis para trabalhar com estruturas de dados hierárquicas, como árvores ou gráficos, onde uma consulta simples pode não ser suficiente.

5. **Consultas complexas envolvendo agregações**:
   - Quando você está lidando com várias operações de agregação que precisam ser combinadas (como a contagem de completions para cada meta), CTEs são uma boa escolha para organizar a query em etapas.

### Quando **não** é indicado usar este tipo de query:

1. **Desempenho em consultas frequentes**:
   - CTEs podem não ser eficientes em termos de desempenho, especialmente se as subconsultas forem grandes e a query for executada frequentemente. Em alguns bancos de dados, CTEs não são materializadas (armazenadas temporariamente) e são reexecutadas toda vez que são referenciadas, o que pode resultar em sobrecarga.
   
2. **Consultas simples**:
   - Se a consulta é simples o suficiente para ser resolvida com uma ou duas junções (`JOINs`), o uso de CTEs pode ser um exagero e complicar desnecessariamente a query. Nesse caso, é mais eficiente e direto usar `JOINs` regulares.

3. **Cenários de tempo real e alta performance**:
   - Se o seu sistema requer respostas em tempo real e precisa de alta performance (como em um sistema crítico de alta concorrência), CTEs podem introduzir uma latência indesejada. Nestes casos, seria mais indicado usar índices ou otimizações específicas no banco de dados.

4. **Consulta com grande volume de dados**:
   - Se as subconsultas nas CTEs resultam em grandes volumes de dados, a query pode se tornar lenta, principalmente se não houver índices apropriados. Dependendo do banco de dados, `CTEs` podem ser menos otimizadas em comparação com junções normais.

5. **Sistemas que suportam *materialized views* ou cache**:
   - Se você tem acesso a *materialized views* (visões materializadas) ou tabelas temporárias, pode ser mais vantajoso pré-computar os resultados complexos e armazená-los em uma *view* materializada do que usar CTEs repetidamente.

### Conclusão:
Este tipo de query é ideal quando você precisa de organização e clareza em consultas complexas, onde cálculos intermediários são necessários. No entanto, não é recomendado para cenários onde o desempenho é crítico, ou se a consulta pode ser simplificada com junções ou agregações diretas.