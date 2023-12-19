# MongoDB

### Copiar dados para uma máquina virtual Docker

O arquivo `.json` importado, é resultado da saída do [mongoexport](https://www.mongodb.com/docs/database-tools/mongoexport/)
```bash
docker cp nome-do-arquivo.json <nome-do-container-ou-id>:/tmp/nome-arquivo.json
```

### Importação do arquivo para o mongo, usando mongoimport
```bash
docker exec mongodb_v6 mongoimport -d trybnb -c places --file /tmp/trybnb.json --jsonArray
```