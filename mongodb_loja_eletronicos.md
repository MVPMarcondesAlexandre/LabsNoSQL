# Atividade Prática — Banco de Dados MongoDB (Loja Web de Produtos Eletrônicos)

## Cenário
Imagine que você está criando o banco de dados para uma **Loja Web de Produtos Eletrônicos**. Essa loja vende notebooks, smartphones, acessórios e outros equipamentos. O banco de dados será usado para armazenar informações sobre produtos, clientes, pedidos, fornecedores e avaliações.

Você deverá utilizar o **MongoDB** no **VS Code**, criando e manipulando os dados diretamente pelo **MongoDB Shell** ou pela **MongoDB for VS Code Extension**.

---

## 1. Criando o Banco de Dados no VS Code
1. Abra o **VS Code**.
2. Instale a extensão **MongoDB for VS Code** (na aba de extensões, pesquise por *MongoDB*).
3. Clique no ícone do **MongoDB** no painel lateral esquerdo.
4. Conecte-se ao servidor local ou ao Atlas (dependendo da instalação que você tiver).
5. No terminal integrado do VS Code, execute:
```javascript
use lojaEletronicos
```
Isso cria (ou seleciona) o banco de dados chamado `lojaEletronicos`.

---

## 2. Criar as Coleções e Inserir Documentos

### 2.1 Produtos
```javascript
db.produtos.insertMany([
  { nome: "Notebook Dell Inspiron", preco: 3500, estoque: 12, categoria: "Notebooks" },
  { nome: "Smartphone Samsung Galaxy S23", preco: 4200, estoque: 8, categoria: "Smartphones" },
  { nome: "Mouse Logitech MX Master 3", preco: 450, estoque: 20, categoria: "Acessórios" },
  { nome: "Teclado Mecânico Redragon", preco: 300, estoque: 15, categoria: "Acessórios" },
  { nome: "Monitor LG 27'' 4K", preco: 2200, estoque: 5, categoria: "Monitores" },
  { nome: "Headset HyperX Cloud II", preco: 600, estoque: 10, categoria: "Acessórios" },
  { nome: "HD Externo Seagate 2TB", preco: 500, estoque: 18, categoria: "Armazenamento" },
  { nome: "SSD Kingston 1TB", preco: 700, estoque: 14, categoria: "Armazenamento" },
  { nome: "Smartwatch Apple Watch SE", preco: 2500, estoque: 7, categoria: "Wearables" },
  { nome: "Câmera Logitech C920", preco: 400, estoque: 9, categoria: "Acessórios" }
])
```

### 2.2 Clientes
```javascript
db.clientes.insertMany([
  { nome: "João Silva", email: "joao@email.com", cidade: "Fortaleza", idade: 30 },
  { nome: "Maria Oliveira", email: "maria@email.com", cidade: "São Paulo", idade: 27 },
  { nome: "Carlos Souza", email: "carlos@email.com", cidade: "Rio de Janeiro", idade: 35 },
  { nome: "Ana Lima", email: "ana@email.com", cidade: "Belo Horizonte", idade: 40 },
  { nome: "Pedro Santos", email: "pedro@email.com", cidade: "Fortaleza", idade: 22 },
  { nome: "Fernanda Costa", email: "fernanda@email.com", cidade: "Recife", idade: 29 },
  { nome: "Rafael Gomes", email: "rafael@email.com", cidade: "Salvador", idade: 33 },
  { nome: "Juliana Rocha", email: "juliana@email.com", cidade: "Curitiba", idade: 26 },
  { nome: "Bruno Almeida", email: "bruno@email.com", cidade: "Porto Alegre", idade: 38 },
  { nome: "Carla Nunes", email: "carla@email.com", cidade: "Manaus", idade: 31 }
])
```

### 2.3 Pedidos
```javascript
db.pedidos.insertMany([
  { clienteId: 1, produtos: ["Notebook Dell Inspiron", "Mouse Logitech MX Master 3"], total: 3950, status: "Enviado" },
  { clienteId: 2, produtos: ["Smartphone Samsung Galaxy S23"], total: 4200, status: "Processando" },
  { clienteId: 3, produtos: ["Monitor LG 27'' 4K"], total: 2200, status: "Entregue" },
  { clienteId: 4, produtos: ["Teclado Mecânico Redragon", "Headset HyperX Cloud II"], total: 900, status: "Cancelado" },
  { clienteId: 5, produtos: ["SSD Kingston 1TB"], total: 700, status: "Enviado" },
  { clienteId: 6, produtos: ["Smartwatch Apple Watch SE"], total: 2500, status: "Processando" },
  { clienteId: 7, produtos: ["HD Externo Seagate 2TB", "Câmera Logitech C920"], total: 900, status: "Entregue" },
  { clienteId: 8, produtos: ["Notebook Dell Inspiron"], total: 3500, status: "Enviado" },
  { clienteId: 9, produtos: ["Headset HyperX Cloud II"], total: 600, status: "Processando" },
  { clienteId: 10, produtos: ["Teclado Mecânico Redragon"], total: 300, status: "Entregue" }
])
```

### 2.4 Fornecedores
```javascript
db.fornecedores.insertMany([
  { nome: "Dell Brasil", contato: "contato@dell.com", cidade: "São Paulo" },
  { nome: "Samsung Brasil", contato: "contato@samsung.com", cidade: "Campinas" },
  { nome: "Logitech", contato: "contato@logitech.com", cidade: "Joinville" },
  { nome: "Redragon", contato: "contato@redragon.com", cidade: "São Paulo" },
  { nome: "LG", contato: "contato@lg.com", cidade: "Taubaté" },
  { nome: "HyperX", contato: "contato@hyperx.com", cidade: "Rio de Janeiro" },
  { nome: "Seagate", contato: "contato@seagate.com", cidade: "Fortaleza" },
  { nome: "Kingston", contato: "contato@kingston.com", cidade: "Manaus" },
  { nome: "Apple Brasil", contato: "contato@apple.com", cidade: "São Paulo" },
  { nome: "Microsoft", contato: "contato@microsoft.com", cidade: "Brasília" }
])
```

### 2.5 Avaliações
```javascript
db.avaliacoes.insertMany([
  { produtoId: 1, clienteId: 1, nota: 5, comentario: "Excelente notebook, muito rápido." },
  { produtoId: 2, clienteId: 2, nota: 4, comentario: "Ótimo smartphone, mas caro." },
  { produtoId: 3, clienteId: 3, nota: 5, comentario: "Mouse muito confortável." },
  { produtoId: 4, clienteId: 4, nota: 4, comentario: "Teclado muito bom, mas barulhento." },
  { produtoId: 5, clienteId: 5, nota: 5, comentario: "Monitor excelente, cores vivas." },
  { produtoId: 6, clienteId: 6, nota: 3, comentario: "Bom headset, mas poderia ser mais barato." },
  { produtoId: 7, clienteId: 7, nota: 4, comentario: "Bom HD externo, rápido e confiável." },
  { produtoId: 8, clienteId: 8, nota: 5, comentario: "SSD muito rápido." },
  { produtoId: 9, clienteId: 9, nota: 5, comentario: "Smartwatch com muitas funções úteis." },
  { produtoId: 10, clienteId: 10, nota: 4, comentario: "Câmera boa para videochamadas." }
])
```

---

## 3. Consultas, Atualizações e Deleções
*(mantidos conforme documento anterior)*
