# Produtos e vendas

Esse relatório traz informações básicas sobre as vendas da empresa

## Querys utilizadas:

- 1 - `db.vendas.aggregate([
  {
  $group: {
  _id: "$produto"
  }
  },
  {
  $project: {
  _id: 0,
  nome: "$_id"
  }
  }
  ])`
  - **Essa query retorna os produtos que os escritórios comercializam.**


- 2 - `db.vendas.aggregate([
  {
  $group: {
  _id: "$produto",
  maior_quantidade: { $max: "$quantidade" }
  }
  },
  {
  $sort: {
  maior_quantidade: -1
  }
  },
  {
  $project: {
  _id: 0,
  produto: "$_id",
  maior_quantidade: "$maior_quantidade"
  }
  }
  ])`
  - **O produto mais vendido conta com 10 vendas.**


- 3 - `db.vendas.aggregate([
  {
  $group: {
  _id: "$produto",
  maior_quantidade: { $max: "$quantidade" }
  }
  },
  {
  $sort: {
  maior_quantidade: 1
  }
  },
  {
  $project: {
  _id: 0,
  produto: "$_id",
  maior_quantidade: "$maior_quantidade"
  }
  }
  ])`
  - **Os produtos menos vendidos conta com 1 venda**


- 4 - `db.vendas.aggregate([
  {
    $project: {
      _id: 0,
      produto: "$produto",
      quantidade_vendida: "$quantidade",
      valor_produto: "$precoUnitario",
      valor_vendido: { $multiply: ["$quantidade", "$precoUnitario"] }
    }
  },
  {
    $sort: {valor_vendido: -1}
  }
])`
  - **O produto mais que gerou mais receita gerou cerca de R$7.722,32**
  

- 5 - `db.vendas.aggregate([
  {
    $project: {
      _id: 0,
      produto: "$produto",
      valor_produto: "$precoUnitario",
    }
  },
  {
    $sort: {valor_produto: -1}
  }
])`
   - **Produtos de maior valor do catálogo é Sabre de Luz (Mace Windu)**


- 6 - `db.vendas.aggregate([
  {
  $group: {
  _id: null,
  faturamento: { $sum: { $multiply: ["$quantidade", "$precoUnitario"] }}
  }
  },
  {
  $project: {
  _id: 0,
  faturamento: "$faturamento"
  }
  }
  ])`
  - **Faturamento: $27.076,00**


- 7 - `db.vendas.aggregate([
  {
  $match: {
  "dataVenda": {
  $gte: "2023-06-01",
  $lt: "2023-07-01"
  }
  }
  },
  {
  $count: "vendas_em_junho_2023"
  }
  ])`
  - **Foram feitas 9 vendas no mes de junho**


- 8 - `db.vendas.aggregate([
  {
  $group: {
  _id: "$vendedor",
  total_vendas: { $sum: 1 }
  }
  },
  {
  $sort: {
  total_vendas: -1
  }
  },
  {
  $limit: 1
  },
  {
  $lookup: {
  from: "funcionarios",
  localField: "_id",
  foreignField: "_id",
  as: "info_vendedor"
  }
  },
  {
  $unwind: "$info_vendedor"
  },
  {
  $project: {
  _id: 0,
  nome_vendedor: "$info_vendedor.nome",
  quantidade_de_transacoes: "$total_vendas"
  }
  }
  ])`
  - O vendedor lidera o ranking de vendas com 3 vendas.


- 9 - `db.vendas.aggregate([
  {
  $group: {
  _id: "$vendedor",
  receita_total: {
  $sum: {
  $multiply: [ "$quantidade", "$precoUnitario" ]
  }
  }
  }
  },
  {
  $sort: {
  receita_total: -1
  }
  },
  {
  $limit: 1
  },
  {
  $lookup: {
  from: "funcionarios",
  localField: "_id",
  foreignField: "_id",
  as: "info_vendedor"
  }
  },
  {
  $unwind: "$info_vendedor"
  },
  {
  $project: {
  _id: 0,
  nome_vendedor: "$info_vendedor.nome",
  receita_gerada: "$receita_total"
  }
  }
  ])`
  - **O vendedor lidera o ranking de receitas com R$13.256,17.**






## Informações retiradas do banco:

- A Momento comercializa 14 produtos diferentes.
- O produto mais vendido é o Uniforme de Moléculas Instáveis.
- O produto menos vendido é o Uniforme do Superman.
- O produto que gerou mais receita foi o Sabre de Luz (Mace Windu).
- O faturamento da Momento foi de $27.076,00.
- Michael Hartstein é o vendedor com mais vendas.
- Michael Hartstein é o vendedor que gerou mais receita.

