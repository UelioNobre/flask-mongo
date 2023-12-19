# MongoDB - Find

Os operadores de comparação no MongoDB são utilizados para comparar valores em consultas de banco de dados.
Abaixo está um resumo dos operadores de comparação mais comuns no MongoDB:

- `$eq:` Equivale a (igual a).
- `$ne:` Não equivale a (diferente de).
- `$gt:` Maior que.
- `$lt:` Menor que.
- `$gte:` Maior ou igual a.
- `$lte:` Menor ou igual a.
- `$in:` Pertence a um conjunto específico.
- `$nin:` Não pertence a um conjunto específico.
- `$exists:` Verifica se um campo existe.
- `$type:` Compara o tipo de dado de um campo.
- `$regex:` Realiza uma comparação usando expressões regulares.

Esses operadores podem ser usados em consultas para filtrar documentos com base em condições específicas. Por exemplo, você pode usar `$gt` para encontrar documentos com valores de campo maiores que um determinado número, ou `$in` para encontrar documentos cujo valor de campo esteja em um conjunto específico.

### Estrutura de uma comparação

```json
{"chave": { "operador": "valor" } }
```

- `chave`: A chave do documento
- `operador`: O operador de comparação
- `valor`: O valor da comparação
--- 


[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
