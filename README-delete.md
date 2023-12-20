# MongoDB - Delete

No mongo DB existe duas funções básicas para remoção de documentos:
- deleteOne
- deleteMany

Os parâmetros utilizados na projection, são semelhantes aos métodos `updateOne` e `updateMany`.

- `deleteOne` remove somente o documento definido no critério `projection`.
- `deleteMany` remove vários documentos definidos no critério `projection.`

---
<details>
<summary>Inserindo valores para utilizar o comando deleteOne e deleteMany</summary>

```bash
db.places.insert( {_id: 203, name: 'Mezanino', description: 'Mezanino 3x6' } )
db.places.insert( {_id: 204, name: 'Apartamento', description: 'Apartamento no centro' } )
db.places.insert( {_id: 205, name: 'Albergue', description: 'Albergue no centro' } )

# Visualiza todos os documentos criados no exemplo
db.places.find( { _id: { $gte: 100 } } )
```
</details>

---

### `deleteOne()`

A função `deleteOne` remove o primeiro registro difinido na `projection`.

```bash
db.places.deleteOne({_id: {$eq: 204}})
# { acknowledged: true, deletedCount: 1 }
```
---

### `deleteMany()`

A função `deleteMany` remove o primeiro registro difinido na `projection`.

```bash
db.places.deleteMany({_id: {$gte: 100}})
# { acknowledged: true, deletedCount: 5 }
```
---

### Truncate a coleção de documentos

Semelhante ao comando `TRUNCATE` de linguagens SQL, utilizar a função `deleteMany` com um objeto vazio na `query`, irá `truncar` a coleção. Em outras palavras, irá remover todos os documentos.

```bash
db.places.deleteMany({})
# Limpa toda a coleção
```

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
