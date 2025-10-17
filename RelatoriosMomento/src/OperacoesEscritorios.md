# Escritorios

Esse relatório traz informações sobre os escritórios da empresa.

## Querys utilizadas:

- 1 - `db.escritorios.aggregate([
  {
  $group: {
  _id: { nome: "$nome", pais: "$pais" }
  }
  },
  {
  $project: {
  _id: 0,
  nome: "$_id.nome",
  pais: "$_id.pais"
  }
  }
  ])`
  - **A Momento conta com 4 escritórios:**
    -   nome: Stark Industries |
        pais: England
    -   nome: Umbrella Corp |
        pais: Equador
    -   nome: Wayne Offices |
        pais: United States of America
    -   nome: Winterfell Offices |
        pais: Ireland


- 2 - `db.escritorios.aggregate([
  { $unwind: "$suprimentos" },
  { $addFields: {
  custoItem: { $multiply: ["$suprimentos.quantidade", "$suprimentos.precoUnitario"] }
  }
  },
  { $group: {
  _id: "$nome",
  custoTotal: { $sum: "$custoItem" }
  }
  },
  { $project: {
  _id: 0,
  escritorio: "$_id",
  custoTotal: 1
  }
  }
  ])`
  - **Custo dos suprimentos dos escritórios:**
    - custoTotal: $376.486.500,00  
      escritório: Umbrella Corp
    - custoTotal: $149.628,75  
      escritório: Wayne Offices
    - custoTotal: $149.142,50  
      escritório: Winterfell Offices
    - custoTotal: $189.792,50  
      escritório: Stark Industries


- 3 -  `db.escritorios.aggregate([
  {
  $project: {
  _id: 0,
  nome_escritorio: "$nome",
  quantidade_itens: { $size: "$suprimentos" }
  }
  },
  {
  $sort: {
  quantidade_itens: -1
  }
  },
  {
  $limit: 1
  }
  ])`
  - **Os escritórios que tem mais suprimentos diversos são Wayne Offices e Winterfell Offices, contando com 5 cada.**


- 4 - `db.escritorios.aggregate([
  {
  $unwind: "$suprimentos"
  },
  {
  $project: {
  _id: 0,
  nome_escritorio: "$nome",
  item: "$suprimentos.produto",
  preco: "$suprimentos.precoUnitario"
  }
  },
  {$sort: {preco: -1}}
  ])`
  - **Suprimentos mais caros são livros didáticos e computadores**


- 5 - `db.escritorios.aggregate([
  {
    $unwind: "$suprimentos"
  },
  {
    $group: {
      _id: {
        escritorio: "$nome",
        produto: "$suprimentos.produto"
      },
      valor_total: {
        $sum: {
          $multiply: [ 
            "$suprimentos.quantidade", 
            "$suprimentos.precoUnitario" 
          ]
        }
      }
    }
  },
  {
    $project: {
      _id: 0,
      escritorio: "$_id.escritorio",
      produto: "$_id.produto",
      valor_total_produto: "$valor_total"
    }
  },
  {
    $sort: {
      escritorio: 1,
      valor_total_produto: -1
    }
  }
])`



## Informações retiradas do banco:

- Winterfell Offices e Wayne Offices são escritórios que custam mais.
- Instrumentos de conhecimento são os suprimentos mais valiosos
- Umbrella Corp é o escritório com maior gasto.
  - O produto com maior gasto está na Umbrella Corp.
  - Folhas de Sulfito é o produto com mais gasto.