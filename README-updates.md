# MongoDB - Updates

No mongo DB existe duas funções básicas para inserção de documentos:
- updateOne
- updateMany

### `updateOne()`

No comando `update`, o que tem de diferente é a utilização das chaves `$set` e `$unset`.

- A chave `$set` é utilizado para atualizar um/vários campos de um documento.
- A chave `$unset` remove chaves criadas pelo comando `$set` ou chaves existentes.

Exemplo atualizando um documento `$set`

```bash
db.places.updateOne({_id: {$eq: 101}}, {$set:{status: true}})
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

Exemplo removendo uma chave do documento com `$unset`

```bash
db.places.updateOne({_id: {$eq: 101}}, {$unset:{status: true}})
# {
#   acknowledged: true,
#   insertedId: null,
#   matchedCount: 1,
#   modifiedCount: 1,
#   upsertedCount: 0
# }
```
---

### `updateMany()`

O comando `updateMany` por outro lado, atualiza vários documentos de uma só vez. Este comando altera valores existentes, assim como pode criar novas chaves usando o operador `$set` ou pode remover chaves existentes com o operador `$unset`.

Exemplo inserindo uma nova chave com `$set` em vários documentos.

```bash
db.places.updateMany({_id: {$gte: 101}}, {$set:{status: true}})
# {
#   acknowledged: true,
#   insertedId: null,
#   matchedCount: 3,
#   modifiedCount: 3,
#   upsertedCount: 0
# }
```


Exemplo removendo várias chaves com o operador `$unset`

```bash
db.places.updateMany({_id: {$gte: 101}}, {$unset:{status: true}})
# {
#   acknowledged: true,
#   insertedId: null,
#   matchedCount: 3,
#   modifiedCount: 3,
#   upsertedCount: 0
# }
```
---

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
