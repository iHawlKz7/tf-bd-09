#  Projeto MongoDB - Catálogo E-commerce

## Objetivo

Praticar operações CRUD utilizando MongoDB com modelo de documentos flexível.

---

## 1. Criação do Banco e Inserção de Dados (CREATE)

```js
use loja_virtual
```

```js
db.createCollection("produtos")
```

```js
db.produtos.insertOne({
  nome: "Smartphone Galaxy A15",
  categoria: "Eletronicos",
  preco: 1299.90,
  marca: "Samsung",
  armazenamento: "128GB",
  cor: "Azul"
})
```

```js
db.produtos.insertMany([
  {
    nome: "MongoDB na Pratica",
    categoria: "Livros",
    preco: 79.90,
    autor: "Joao Silva",
    editora: "Tech Books",
    paginas: 320
  },
  {
    nome: "Camiseta Basica",
    categoria: "Roupas",
    preco: 49.90,
    tamanho: "M",
    cor: "Preta",
    material: "Algodao"
  }
])
```

**Explicação:**
A coleção foi criada manualmente utilizando `createCollection`. No MongoDB, ela também poderia ser criada automaticamente ao inserir dados, mostrando a flexibilidade do banco.

---

## 2. Consultas (READ)

```js
db.produtos.find()
```

```js
db.produtos.find({ preco: { $gt: 100 } })
```

```js
db.produtos.find({ categoria: "Eletronicos" })
```

```js
db.produtos.find({}, { nome: 1, preco: 1, _id: 0 })
```

**Explicação:**
As consultas permitem filtrar dados e retornar apenas informações específicas.

---

##3. Atualizações (UPDATE)

```js
db.produtos.updateOne(
  { nome: "Smartphone Galaxy A15" },
  { $set: { preco: 1199.90 } }
)
```

```js
db.produtos.updateMany(
  {},
  { $set: { estoque: 100 } }
)
```

```js
db.produtos.updateMany(
  { categoria: "Roupas" },
  { $set: { promocao: true } }
)
```

**Explicação:**
O operador `$set` permite atualizar ou adicionar novos campos.

---

## 4. Exclusão (DELETE)

```js
db.produtos.deleteOne({ nome: "Camiseta Basica" })
```

```js
db.produtos.deleteMany({ categoria: "Livros" })
```

**Explicação:**
Permite remover documentos específicos ou vários documentos com base em critérios.

---

## Conclusão

O MongoDB permite armazenar documentos com estruturas diferentes dentro da mesma coleção, sendo ideal para sistemas como e-commerce.

Todos os comandos foram executados com sucesso no ambiente MongoDB via Docker (WSL).
