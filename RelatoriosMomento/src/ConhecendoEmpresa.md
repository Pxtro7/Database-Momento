# Conhecendo a empresa

Esse relatório traz informações básicas sobre a empresa

## Querys utilizadas:

- 1 - `db.funcionarios.insertOne({
  "nome": "Vinicius",
  "sobrenome": "Patrocinio Leite",
  "data_nascimento": "2004-06-19",
  "dataAdmissao": "2025-10-15",
  "salario": 10000,
  "departamento": "Tecnologia",
  "cargo": "Desenvolvedora",
  "escritorio": "São Paulo"
  })`
  - **Foi adicionado um novo funcionario no banco de dados da empresa.**

- 2 - `db.funcionarios.countDocuments()`
  - **A empresa conta com 24 funcionarios;**


- 3 - `db.departamentos.find({nome: "tecnologia})`
  ||  `db.funcionarios.find({departamento: ObjectId('85992103f9b3e0b3b3c1fe74')}).count()`
  - **Contem 6 funcionarios no departamento de tecnologia;**


- 4 - `db.departamentos.distinct("nome")`
  ||  `db.departamentos.count()`
  - **Temos 7 departamentos na empresa: dados, executivo, financeiro, marketing, recursos humanos, tecnologia e vendas**


- 5 - `db.escritorios.countDocuments()` || `db.escritorios.distinct("pais")`
  - **A empresa conta com 4 escritórios com um em cada pais ENG, IRE, USA, EQU** 







## Informações retiradas do banco:

- A empresa momento conta com 24 funcionários.
- Um quarto da empresa é do setor da tecnologia.
- A empresa está dividida em 2 continentes sendo eles Europa e America com 2 escritórios cada.