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
db // prints the current database
```

### Acessando um banco de dados
```bash
use <outro-banco-de-dados>
```

### Números de documentos na coleção
```bash
db.places.countDocumentos()
```

