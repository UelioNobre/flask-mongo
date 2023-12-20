# MongoDB - Inserts

No mongo DB existe duas funções básicas para inserção de documentos:
- insertOne
- insertMany

### `insertOne()`

O comando `insertOne` é bem simples. Onde há a marcação `<data-as-bson>` é onde será inserido os dados para cadastro.

-  insertOne(&lt;`data-as-bson`&gt;)


<details>
<summary>Exemplo</summary>

```bash
db.places.insertOne({_id: 101, name: 'Edicula Santa Helena', description: 'Edicula com piscina, churrasqueira, quarto e banheiro' })

# { acknowledged: true, insertedId: 101 }
```
</details>
---

### `insertMany()`

O comando `insertMany` é semelhante ao `insertOne`, exceto pela característica de inserir vários documentos de uma só vez, como sua assinatura sugere. Os dados são informados em formato de `array`.

-  insertMany(&lt;`array-as-bson`&gt;)


<details>
<summary>Exemplo</summary>

```bash
db.places.insertMany([{_id: 201, name: 'Cháchara', description: 'Chácara na serra'}, {_id: 202, name: 'Sítio', description: 'Sítio na Chapada'}])

# { acknowledged: true, insertedIds: { '0': 201, '1': 202 } }
```

</details>

---

[Cheat Sheet MongoDB](https://www.mongodb.com/developer/products/mongodb/cheat-sheet/)
