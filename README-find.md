# MongoDB - Find

O comando `find` tem a seguinte estrutura:

```bash
db.<colecao>.find(<query>, <projection>)
```

O parametro `query`, é semelhante com a palavra `WHERE` de algum banco de dados relacionais. Ou seja, um filtro para especificar um parametro de busca.

O parametro `projection`, é semelhando a palavra `SELECT`. É neste parametro que se especifica as propriedades do documento que sejam retornadas.

## Parâmentro `query`

### Buscando o documento pelo `id`
```
db.places.find({ '_id': 7 })
```

### Busca por um documento, em um campo aninhado
```bash
# Retorna todos os documentos, na chave "address", que tenha a chave "country_code" com valor "BR"
db.places.find({'address.country_code': 'BR'})
```

Acessar utilizando objetos aninhados, causa um erro:
```bash
db.places.find({'address': {'country_code'}}: 'BR'}
# Uncaught:
# SyntaxError: Unexpected token (1:42)

> 1 | db.places.find({'address': {'country_code'}}: 'BR'}
    |                                           ^
  2 |
```

### Conta quantos documentos há em uma consulta
```bash 
 db.places.find({'address.country_code': 'BR'}).count()
 ```


## Parâmentro `projection`

Retornando campos expecificos 

```bash
# Retorna os campos _id e name
db.places.find({ 'address.country_code': 'BR' }, {'name': true})

# Retorna os campos _id, name e os dados do host
db.places.find({ '_id': 7 }, { 'name': true, 'host': true })
```

Omitindo campos na consulta
```bash
# Um documento específico
db.places.find({ '_id': 7 }, { 'house_rules': false, 'reviews': false, 'review_scores': false, 'host': false, 'address': false, 'amenities': false, 'description': false})
```

```bash
# Todos os documentos
db.places.find({}, { 'house_rules': false, 'reviews': false, 'review_scores': false, 'host': false, 'address': false, 'amenities': false, 'description': false})
```

Inserir valores true/false na projeção, irá causar um erro. Use somente `true` ou somente `false` na especificação dos campos.
```bash
db.places.find({}, { 'house_rules': false, 'reviews': true})
# Causará um erro
# MongoServerError: Cannot do inclusion on field reviews in exclusion projection
```

## Ordenando resultados

Em ordem ascendente

```bash
db.places.find({}, {'name': true}).sort({'name': 1})
```

Em ordem decrescente
```bash
db.places.find({}, {'name': true}).sort({'name': -1})
```
--- 


## Exercícios
- Realize uma busca por todos os imóveis que se localizam no Brasil ordenados, de forma crescente, pelo atributo _id:

```bash
db.places.find({ 'address.country': 'Brazil'}).sort({'_id': 1})
# 6 resultados
```

- Realize uma busca por todos os imóveis que se localizam na Turquia que retorne a quantidade de imóveis.
Mais comandos mongodb:

```bash
db.places.find({ 'address.country': 'Turkey' }).count()
# 1
```

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
