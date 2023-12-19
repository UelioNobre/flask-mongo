# MongoDB

### Usando uma maquina docker com mongodb
```bash
docker run --name mongodb_v6 -d -p 27017:27017 mongo:6.0
```

### Executando uma maquina docker com mongosh
```bash
docker exec -it mongodb_v6 mongosh
```

### Copiar dados para uma máquina virtual Docker
O arquivo `.json` importado, é resultado da saída do [mongoexport](https://www.mongodb.com/docs/database-tools/mongoexport/)
```bash
docker cp nome-do-arquivo.json <nome-do-container-ou-id>:/tmp/nome-arquivo.json
```

### Importação do arquivo para o mongo, usando mongoimport, no mongosh
```bash
docker exec mongodb_v6 mongoimport -d trybnb -c places --file /tmp/trybnb.json --jsonArray
```

## Comando mongo para manipulacão do banco de dados

### Exibe os bancos de dados existentes
```bash
show dbs

# prints the current database
db 
```

### Acessando um banco de dados
```bash
use <outro-banco-de-dados>
```

### Exibe as coleções disponiveis no banco
```bash
show collections
```

### Números de documentos na coleção
```bash
db.places.countDocumentos()
```

## Documentos baseados em critérios

O comando `find` tem a seguinte estrutura:
```bash
db.<colecao>.find(<query>, <projection>)
```

O parametro `query`, é semelhante com a palavra `WHERE` de algum banco de dados relacionais. Ou seja, um filtro para especificar um parametro de busca.

O parametro `projection`, é semelhando a palavra `SELECT`. É neste parametro que se especifica as propriedades do documento que sejam retornadas.


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


## Paramentro `projection`

Retornando campos expecificos 

```bash
# Retorna os campos _id e name
db.places.find({ 'address.country_code': 'BR' }, {'name': true})

# Retorna os campos _id, name e os dados do host
db.places.find({ '_id': 7 }, { 'name': true, 'host': true })
```
--- 
Mais comandos mongodb:
[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)