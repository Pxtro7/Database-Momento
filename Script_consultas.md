# Momento 

Bem-vindo à base de dados da empresa **Momento**!

A Momento é uma empresa inovadora do setor de tecnologia e vendas de produtos temáticos de super-heróis e cultura pop. Fundada em 1980, a empresa começou como uma pequena loja em Gotham City e hoje possui escritórios em diversos países, com departamentos especializados em Vendas, Tecnologia, Recursos Humanos, Marketing, Financeiro e Dados.

Nestes exercícios, você vai explorar o banco de dados MongoDB da empresa e responder perguntas que revelam insights importantes sobre o negócio. Prepare-se para usar queries básicas, agregações complexas, e operações avançadas do MongoDB!

---

## Nível 1: Conhecendo a Empresa

### Seu Primeiro Dia na Momento

Você acabou de ser contratado pela Momento! Vamos começar incluindo você no sistema.

**1.1** Inclua suas próprias informações no departamento de Tecnologia da empresa.

R:
```bson
insertOne({
  "nome": "Ana",
  "sobrenome": "Silva",
  "data_nascimento": "1990-01-01",
  "data_contratacao": "2020-01-01",
  "salario": 5000,
  "departamento": "Tecnologia",
  "cargo": "Desenvolvedora",
  "escritorio": "São Paulo"
})
```

**1.2** Agora que você faz parte da equipe, quantos funcionários temos ao total na empresa?

**1.3** Quantos funcionários trabalham especificamente no Departamento de Tecnologia?

**1.4** Liste todos os departamentos que existem na empresa. Quantos são?

**1.5** Quantos escritórios a Momento possui? Em quais países?

---

## Nível 2: Análise Financeira Básica

O CFO precisa de relatórios urgentes sobre os custos da empresa.

**2.1** Quantos funcionários trabalham no Departamento de Vendas?

**2.2** Qual é o custo total com salários do Departamento de Vendas?

**2.3** Qual é a média salarial da empresa, excluindo os cargos de CEO, CMO e CFO?

**2.4** Qual é a média salarial do Departamento de Tecnologia?

**2.5** Qual departamento possui a maior média salarial?

**2.6** Qual departamento possui o menor número de funcionários?

---

## Nível 3: Recursos Humanos

O RH está fazendo uma análise demográfica da empresa.

**3.1** Quantos funcionários da empresa Momento possuem cônjuges?

**3.2** Quantos funcionários possuem filhos registrados?

**3.3** Qual funcionário foi contratado há mais tempo na empresa?

**3.4** Qual funcionário foi contratado há menos tempo na empresa?

**3.5** Liste os 5 funcionários com mais tempo de casa, ordenados pela data de contratação.

**3.6** Quantos funcionários foram contratados na década de 1990 (entre 1990-1999)?

**3.7** Como a média salarial da Momento evoluiu ao longo dos anos? Agrupe por ano de contratação e calcule a média salarial.

---

## Nível 4: Operações e Escritórios

**4.1** Liste todos os escritórios e seus respectivos países.

**4.2** Qual é o custo total de suprimentos em cada escritório? Ordene do mais caro ao mais barato.

**4.3** Qual escritório possui a maior quantidade de diferentes tipos de suprimentos?

**4.4** Qual é o suprimento mais caro (considerando preço unitário) em toda a empresa?

**4.5** Calcule o valor total do inventário de suprimentos da empresa (quantidade × preço unitário de todos os itens em todos os escritórios).

---

## Nível 5: Produtos e Vendas

**5.1** Quais produtos foram vendidos pela Momento? Liste todos os produtos únicos.

**5.2** Qual é o produto mais vendido (maior quantidade total)?

**5.3** Qual é o produto menos vendido?

**5.4** Pensando na relação quantidade × valor unitário, qual produto gerou mais receita para a empresa?

**5.5** Qual é o produto mais caro (maior preço unitário) no catálogo?

**5.6** Qual foi o faturamento total da empresa em vendas?

**5.7** Quantas vendas foram realizadas no mês de junho de 2023?

**5.8** Qual vendedor realizou mais vendas (em quantidade de transações)?

**5.9** Qual vendedor gerou mais receita para a empresa?

---

## Nível 6: Operações de Atualização

A empresa está crescendo e mudanças precisam acontecer!

**6.1** Um novo departamento foi criado: **Inovações**. Ele será alocado no escritório "Wayne Offices". Adicione-o ao banco de dados.

**6.2** O departamento de Inovações está sem funcionários. Transfira 2 funcionários do departamento de Tecnologia para Inovações.

**6.3** A empresa decidiu dar um aumento de 10% para todos os funcionários do departamento de Tecnologia. Atualize os salários.

**6.4** O funcionário "Bruce Ernst" foi promovido a "Senior Web Developer" e recebeu um aumento para $5.000. Atualize suas informações.

**6.5** Adicione um novo suprimento ao escritório "Wayne Offices": 15 unidades de "Headsets" com preço unitário de $150 cada.

**6.6** Todos os funcionários contratados antes de 1990 estão aposentando. Remova-os do banco de dados (CUIDADO: execute um find antes para ver quantos serão afetados!).

---

## Dicas Gerais

- **Para iniciantes**: Comece sempre com um `find()` simples para entender os dados antes de criar agregações complexas.
- **Para intermediários**: Pratique o uso de `$match`, `$group`, `$project` e `$sort` em pipelines de agregação.
- **Para avançados**: Explore `$lookup`, `$unwind`, `$addFields` e operadores de array como `$filter`, `$map`.
- **Boa prática**: Sempre teste suas queries de UPDATE e DELETE com um `find()` primeiro!
- **Performance**: Use `explain()` para entender como suas queries estão sendo executadas.

---

**Objetivo de aprendizado**: Ao completar todos os níveis, você estará apto a trabalhar com MongoDB em ambientes de produção, realizar análises complexas de dados e otimizar queries para performance.

Bons estudos!