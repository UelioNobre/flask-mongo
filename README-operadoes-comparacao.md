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
---

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
---

### `$gt:` Maior que.

Todos os valores que sejam maiores de `500`

```bash
db.places.find({price: {'$gt': 500}}, {price: true}).sort({price: 1})
# [ 
#   { _id: 2, price: 746 }, 
#   { _id: 9, price: 5595 } 
#   ]
```
---

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
---

### `$gte:` Maior ou igual a.

Todos os valores que sejam maiores ou iguais a `380`

```bash
db.places.find({price: {'$gte': 380}}, {price: true}).sort({price: 1})
# [
#   { _id: 1, price: 380 },
#   { _id: 2, price: 746 },
#   { _id: 9, price: 5595 }
# ]
```
---

### `$lte:` Menor ou igual a.

Todos os valores que sejam menores ou iguais a `50`

```bash
db.places.find({price: {'$lte': 50}}, {price: true}).sort({price: 1})
# [
#   { _id: 11, price: 35 },
#   { _id: 8, price: 50 },
#   { _id: 3, price: 50 }
# ]
```
---

### `$in:` Pertence a um conjunto específico.

Todos os valores que tenham "fogão", nas `amenities`

```bash
db.places.find({'amenities': {$in: ["Stove"]}}, {'price': true})
# [ 
#   { _id: 12, price: 75 }, 
#   { _id: 11, price: 35 } 
# ]
```
---

### `$nin:` Não pertence a um conjunto específico.

Todos os valores que `não` tenham "fogão, TV e Shampoo", nas `amenities`

```bash
db.places.find({'amenities': {$nin: ["Stove", "TV", "Shampoo"]}}, # {'price': true})
# [
#   { _id: 1, price: 380 },
#   { _id: 9, price: 5595 },
#   { _id: 10, price: 351 }
# ]
```
---

### `$exists:` Verifica se um campo existe.
Todos os valores que tenham uma politica de cancelamento
```bash
db.places.find({'cancellation_policy': {$exists: false}}, {'cancellation_policy': true})
# [
#   { _id: 2, cancellation_policy: 'flexible' },
#   { _id: 4, cancellation_policy: 'flexible' },
#   { _id: 1, cancellation_policy: 'flexible' },
#   { _id: 8, cancellation_policy: 'moderate' },
#   { _id: 7, cancellation_policy: 'strict_14_with_grace_period' },
#   { _id: 6, cancellation_policy: 'strict_14_with_grace_period' },
#   { _id: 3, cancellation_policy: 'flexible' },
#   { _id: 11, cancellation_policy: 'super_strict_30' }
# ]
```
---

### `$type:` Compara o tipo de dado de um campo.

Todos os valores e a quantidade de noites minímas, que tenha o valor da chave `minimum_nights` seja uma `string`

```bash
db.places.find({minimum_nights: {$type: "string"}}, {price: true, minimum_nights: true})
# [ 
#   { _id: 11, minimum_nights: '2', price: 35 } 
# ]
```
---

### `$regex:` Realiza uma comparação usando expressões regulares.

Todos os valores e o nome dos anfitriões, que o nome deles terminam com a silaba `do`

```bash
db.places.find({'host.host_name': {$regex: /do$/}}, {price: true, 'host.host_name': true})
# [
#   { _id: 1, price: 380, host: { host_name: 'Ricardo' } },
#   { _id: 9, price: 5595, host: { host_name: 'Fernando' } }
# ]
```
---

### `$all` Realiza comparações em arrays

O operador `$all` retorna somente os documentos que tenham o critério informado no array. Olhando pela perspectiva de conjuntos, se `todos` os valores informados estiverem presentes, retorna o respectivo documento. Caso contrário, não.

```bash
db.places.find({amenities: {$all: ['Stove', 'Garage']}}, {amenities: true})
# [
#   {
#     _id: 11,
#     amenities: [
#       'TV',
#       'Stove',
#       'Refrigerator',
#       'Garage',
#       'Essentials',
#       'wardrobe',
#       'Microwave'
#     ]
#   }
# ]
```

O operador `$all` tem o efeito oposto do operador `$in` e `$nin`.

```bash
db.places.find({amenities: {$all: ['Stove', 'Elevator']}}, {amenities: true})

# Nessa caso, nenhum dado será retornado, pois não existe facilidades que tenham as duas opções: Fogão e Elevador juntos.
```
---

### $elemMatch
Seleciona documentos se pelo menos um elemento de um array atender a determinada condição. 

Útil para utilizar mais de um operador.

No exemplo abaixo, irá retornar todos os documentos que tenham as comodidades de `Stove` ou `Pool`.

```bash
db.places.find({ amenities: { $elemMatch: { $in: ['Stove', 'Pool'] } } }, { _id_: true })
# [ { _id: 2 }, { _id: 9 }, { _id: 12 }, { _id: 11 } ]
```

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
