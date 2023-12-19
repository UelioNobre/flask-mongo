# MongoDB - Find

Os operadores de comparação no MongoDB são utilizados para comparar valores em consultas de banco de dados.
Abaixo está um resumo dos operadores de comparação mais comuns no MongoDB:

Esses operadores podem ser usados em consultas para filtrar documentos com base em condições específicas. Por exemplo, você pode usar `$gt` para encontrar documentos com valores de campo maiores que um determinado número, ou `$in` para encontrar documentos cujo valor de campo esteja em um conjunto específico.

### Estrutura de uma comparação

```json
{"chave": { "operador": "valor" } }
```

- `chave`: A chave do documento
- `operador`: O operador de comparação
- `valor`: O valor da comparação
--- 

## Exemplos

Todos preços disponíveis ordenados de forma ascendente:

```bash
db.places.find({}, {'price': true}).sort({'price': 1})

# Todos os resultados
#[
#  { _id: 11, price: 35 },
#  { _id: 8, price: 50 },
#  { _id: 3, price: 50 },
#  { _id: 7, price: 75 },
#  { _id: 12, price: 75 },
#  { _id: 4, price: 150 },
#  { _id: 5, price: 185 },
#  { _id: 10, price: 351 },
#  { _id: 6, price: 353 },
#  { _id: 1, price: 380 },
#  { _id: 2, price: 746 },
#  { _id: 9, price: 5595 }
#]
```

### `$eq:` Equivale a (igual a).

```bash
db.places.find({price: {'$eq': 75}}, {price: true})

# [ 
#  { _id: 7, price: 75 }, 
#  { _id: 12, price: 75 }
# ]
```
--- 

### `$ne:` Não equivale a (diferente de).

Todos os valores que sejam diferentes de `75`
```bash
db.places.find({price: {'$ne': 75}}, {price: true})
# [
#   { _id: 2, price: 746 },
#   { _id: 4, price: 150 },
#   { _id: 1, price: 380 },
#   { _id: 5, price: 185 },
#   { _id: 8, price: 50 },
#   { _id: 6, price: 353 },
#   { _id: 9, price: 5595 },
#   { _id: 10, price: 351 },
#   { _id: 3, price: 50 },
#   { _id: 11, price: 35 }
# ]
```

### `$gt:` Maior que.

Todos os valores que sejam maiores de `500`

```bash
db.places.find({price: {'$gt': 500}}, {price: true}).sort({price: 1})
# [ 
#   { _id: 2, price: 746 }, 
#   { _id: 9, price: 5595 } 
#   ]
```

### `$lt:` Menor que.

Todos os valores que sejam menores de `75`

```bash
db.places.find({price: {'$lt': 75}}, {price: true}).sort({price: 1})
# [
#   { _id: 11, price: 35 },
#   { _id: 8, price: 50 },
#   { _id: 3, price: 50 }
# ]
```

- `$gte:` Maior ou igual a.

Todos os valores que sejam maiores ou iguais a `380`

```bash
db.places.find({price: {'$gte': 380}}, {price: true}).sort({price: 1})
# [
#   { _id: 1, price: 380 },
#   { _id: 2, price: 746 },
#   { _id: 9, price: 5595 }
# ]
```

- `$lte:` Menor ou igual a.
- `$in:` Pertence a um conjunto específico.
- `$nin:` Não pertence a um conjunto específico.
- `$exists:` Verifica se um campo existe.
- `$type:` Compara o tipo de dado de um campo.
- `$regex:` Realiza uma comparação usando expressões regulares.


[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
