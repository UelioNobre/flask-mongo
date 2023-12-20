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

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
