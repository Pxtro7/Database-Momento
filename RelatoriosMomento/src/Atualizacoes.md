# Operações de Atualização

Esse relatório traz informações sobre as mudanças da empresa

## Querys utilizadas:

- 1 - `db.departamentos.insertOne({
  "nome": "Inovações",
  "escritorio": ObjectId('5f8b3f3f9b3e0b3b3c1e3e3e')
  })`
  - **Inserção de um departamento novo.**


- 2 - `db.funcionarios.updateOne({"nome": "Vinicius"},{$set: {"departamento": ObjectId('5f8b3f3f9b3e0b3b3c1e3e3e')}})` || `db.funcionarios.updateOne({"nome": "David Austin"},{$set: {"departamento": ObjectId('5f8b3f3f9b3e0b3b3c1e3e3e')}})`
  - **Dois funcionários do setor de tecnologia foram para o departamento de inovação**


- 3 - `db.funcionarios.updateMany(
  {
  "departamento": ObjectId("85992103f9b3e0b3b3c1fe74")
  },
  {
  $mul: { "salario": 1.10 }
  }
  )`
  - **Alteração em massa no valor de salário dos funcionários do departamento de tecnologia.**


- 4 - `db.funcionarios.updateOne(
  { _id: ObjectId("5f8b3f3f9b3e0b3b3c1e3e45") },
  {
  $set: {
  cargo: "Senior Web Developer",
  salario: 5000,
  }
  }
  )`
  - **Promoção de um funcionário.**


- 5 - `db.escritorios.updateOne(
  {
  "nome": "Wayne Offices"
  },
  {
  $push: {
  "suprimentos": {
  "produto": "Headsets",
  "quantidade": 15,
  "precoUnitario": 150
  }
  }
  }
  )`
  - **Compra de suprimentos para o escritório Wayne Offices.** 


- 6 - `db.funcionarios.find({
  "dataAdmissao": { $lt: "1990-01-01" }
  })` || `db.funcionarios.deleteMany({
  "dataAdmissao": { $lt: "1990-01-01" }
  })`
  - **Exclusão de funcionários do banco de dados.**




## Informações retiradas do banco:
- Novo departamento de Inovações está localizado no escritório Wayne Offices. 
- O funcionário Vinicius Patrocinio Leite e David Austin agora fazem parte do departamento de inovação.
- Aumento em 10% na folha salarial do departamento de tecnologia.
- O funcionário Bruce Ernst foi promovido a Senior Web Developer e recebeu um aumento para $5.000
- As funcionárias Irene Adler e Jennifer Whalen se aposentaram e não fazem mais parte do quadro de funcionários da Momento. **AGRADECEMOS PELOS SERVIÇOS PRESTADOS!**