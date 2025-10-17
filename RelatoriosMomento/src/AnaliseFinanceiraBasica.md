# Conhecendo a empresa

Esse relatorio tras informações basicas sobre o financeiro da empresa.

## Querys utilizadas:

- 1 - `db.funcionarios.find({departamento: ObjectId('85992103f9b3e0b3b3c1fe71')}).count()`
  - **O departamento de vendas com 10 funcionários.**


- 2 - `db.funcionarios.aggregate([
  {
  $lookup:{
  from: "departamentos",
  localField: "departamento",
  foreignField: "_id",
  as: "info_departamento"
  }
  },
  {
  $match:{
  "info_departamento.nome" : "Vendas"
  }
  },
  {
  $group: {
  _id: null,
  total:{
  $sum: "$salario"
  }
  }
  }])`
  - **O valor somado da folha salarial do departamento de vendas é $95.100,00.**


- 3 - `db.funcionarios.aggregate([
  {
  $match: {
  cargo: {$nin: ["CEO", "CMO", "CFO"]}
  }
  },
  {
  $group:{
  _id: null,
  mediaSalario: {$avg: "$salario"}
  }
  }
  ])`
  - **A média salarial da empresa com exceção de cargos de diretória é de $9.768.69**



- 4 - `db.funcionarios.aggregate([
  {
  $lookup:{
  from: "departamentos",
  localField: "departamento",
  foreignField: "_id",
  as: "info_departamento"
  }
  },
  {
  $match:{
  "info_departamento.nome" : "Tecnologia"
  }
  },
  {
  $group: {
  _id: null,
  total:{
  $avg: "$salario"
  }
  }
  }])`
  - **A média salarial do departamento de tecnologia é $5.466,66.**


- 5 - `db.funcionarios.aggregate([
  {
  $lookup: {
  from: "departamentos",
  localField: "departamento",
  foreignField: "_id",
  as: "info_departamento"
  }
  },
  {
  $unwind: "$info_departamento"
  },
  {
  $match: {
  "info_departamento.nome": { $in: ["Vendas", "Recursos Humanos", "Tecnologia", "Dados", "Executivo", "Financeiro", "Marketing"] }
  }
  },
  {
  $group: {
  _id: "$info_departamento.nome",
  mediaSalarios: { $avg: "$salario" },
  totalFuncionarios: { $sum: 1 }
  }
  },
  {
  $sort: { totalSalarios: -1 }
  }
  ])`
  - **O departamento executivo é o departamento com maior média salarial.**


- 6 - `db.funcionarios.aggregate([
  {
  $lookup: {
  from: "departamentos",
  localField: "departamento",
  foreignField: "_id",
  as: "info_departamento"
  }
  },
  {
  $unwind: "$info_departamento"
  },
  {
  $match: {
  "info_departamento.nome": { $in: ["Vendas", "Recursos Humanos", "Tecnologia", "Dados", "Executivo", "Financeiro", "Marketing"] }
  }
  },
  {
  $group: {
  _id: "$info_departamento.nome",
  totalFuncionarios: { $sum: 1 }
  }
  },
  {
  $sort: { totalSalarios: -1 }
  }
  ])`
  -  **O departmento executivo conta coom apenas 1 funcionário.**







## Informações retiradas do banco:

- O departamento de vendas é onde a maioria dos funcionários se encontram.
- O departamento de tecnologia é o departamento que tem menor custo para empresa com um custo de $32.800,00 mensal.
- O departamento de recursos humanos é o departamento que tem maior custo para empresa com um custo de $96.780,00 mensal.