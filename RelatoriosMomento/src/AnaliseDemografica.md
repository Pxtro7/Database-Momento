# Analise demográfica

Esse relatório traz informações básicas sobre os funcionários da empresa.

## Querys utilizadas:

- 1 - ``db.funcionarios.aggregate([
  {$match: {"dependentes.conjuge": {$exists: true, $ne: null}
  }
  },
  {
  $count: "totalConjuge"
  }
  ])``
  - **7 funcionários possuem cônjuge cadastrados.**
  

- 2 - `db.funcionarios.aggregate([
  {$match: {"dependentes.filhos": {$exists: true, $ne: null}
  }
  },
  {
  $count: "QuantidadeDePais"
  }
  ])`
  - **Contamos com 7 funcionarios que possuem filhos cadastrados.**


- 3 - `db.funcionarios.aggregate([
  {
  $group: {
  _id: null,
  funcionarioMaisAntigo: { $min: "$dataAdmissao" }
  }
  }
  ]) `|| `db.funcionarios.find({
  dataAdmissao: "1980-09-28"
  })
`
  - **Irene Adler é a funcionária mais antigo da empresa.**


- 4 - `db.funcionarios.aggregate([
  {
  $group: {
  _id: null,
  funcionarioMaisAntigo: { $max: "$dataAdmissao" }
  }
  }
  ])` || `db.funcionarios.find({
  dataAdmissao: "2025-10-15"
  })`
  - **Vinicius Patrocinio Leite é o funcionário mais novo da empresa**


- 5 - `db.funcionarios.aggregate([
  {
  $match: { dataAdmissao: { $exists: true } }
  },
  {
  $sort: { dataAdmissao: 1 }  
  },
  {
  $limit: 5
  },
  {
  $project: {
  _id: 0,
  nome: 1,
  dataAdmissao: 1
  }
  }
  ])`
  - **5 funcionarios mais antigos e suas datas:**
    -   nome: 'Irene Adler',
        dataAdmissao: '1980-09-28'
    -   nome: 'Jennifer Whalen',
        dataAdmissao: '1987-09-17'
    -   nome: 'Den Raphaely',
        dataAdmissao: '1994-12-07'
    -   nome: 'Payam Kaufling',
        dataAdmissao: '1995-05-01'
    -  nome: 'Normam Osborn',
       dataAdmissao: '1995-05-18'


- 6 - `db.funcionarios.aggregate([
  {
  $match: {
  dataAdmissao: { $exists: true }
  }
  },
  {
  $match: {
  dataAdmissao: { $gte: "1990-01-01", $lt: "1999-12-31" }
  }
  },
  {
  $count: "totalFuncionarios1990"
  }
  ])`
  - **temos 11 funcionarios que foram contratados nos anos 90**


- 7 - `db.funcionarios.aggregate([
  {
  $match: {
  dataAdmissao: { $exists: true },
  salario: { $exists: true }
  }
  },
  {
  $group: {
  _id: { ano: { $substr: ["$dataAdmissao", 0, 4] } }, 
  mediaSalarial: { $avg: "$salario" }
  }
  },
  {
  $sort: { "_id.ano": 1 }
  },
  {
  $project: {
  _id: 0,
  ano: "$_id.ano",
  mediaSalarial: 1
  }
  }
  ])
`

  - **Media salarial por ano:**
    -  mediaSalarial: $9.700,00 |
       ano: '1980'
    -   mediaSalarial: $23.000,00 |
        ano: '1987'
    -  mediaSalarial: $12.500,00 |
       ano: '1994'
    -   mediaSalarial: $13.840,00 |
        ano: '1995'
    -   mediaSalarial: $30.966,66 |
        ano: '1996'
    -   mediaSalarial: $15.275,00 |
        ano: '1997'
    -   mediaSalarial: $8.900,00 |
        ano: '1999'
    -   mediaSalarial: $4.100,00 |
        ano: '2000'
    -   mediaSalarial: $3.400,00 |
        ano: '2005'
    -   mediaSalarial: $3.500,00 |
        ano: '2008'
    -   mediaSalarial: $2.900,00 |
        ano: '2009'
    -   mediaSalarial: $10.000,00 |
        ano: '2025'





## Informações retiradas do banco:
- 8 dos 24 funcionários contem dependentes.
- A pessoa mais antiga da empresa está ha 35 anos na empresa.
- Aproximadamente metade dos funcionários estam a mais de 25 anos na empresa, o que faz com que a maioria entenda o funcionamento da Momento.
