---
title:  SQL cheatsheet
created: Wednesday 30th November 2022
aliases: SQL
tags: BD, SQL
---
# Queries
Exemplos baseados no banco de dados *ecommerce* da aula de SQL da Gama Academy. 

## Inserção (Create)
No exemplo abaixo, *codigo* é *auto-increment*
### Especificando a ordem de inserções
```SQL
INSERT INTO departamento(codigo, nome, descricao) VALUES
	(1, 'Tecnologia', 'Produtos para computadores');
```

### Respeitando a ordem da tabela
```SQL
INSERT INTO departamento VALUES (
	null /* permite o sistema decidir o valor */, 
	'Eletronicos', 
	'bzzzzzz'
	);
```

### Ordem tabela + múltiplas tuplas
```SQL
INSERT INTO departamento VALUES
	(null, 'Games', 'Para jogadores'),
	(null, 'Acessorios', 'Cabos e conectores'),
	(null, 'Alimentacao', 'Nutrientes');
```

## Seleção (Read)
### Todas as colunas
```SQL
SELECT * FROM produto;
```

### Algumas colunas
```SQL
SELECT id, nome, cpf, senha FROM cliente;
```

### Por palavra chave
```SQL
SELECT * FROM produto WHERE nome LIKE "%USB%";
```

### Soma de valores
```SQL
SELECT sum(valor_final) FROM pedido;
```

### Contagem de itens
```SQL
SELECT count(id) FROM cliente;
```
### Mudando o título da coluna
```SQL
SELECT count(id) AS 'total de clientes' FROM cliente;
```

### Critério
```SQL
SELECT * FROM cliente WHERE id = 1;
```

### Ordenamento
```SQL
SELECT * FROM cliente ORDER BY nome ASC;
```

## Alteração (Update)
### Mudando nome
```SQL
UPDATE departamento SET nome="Informatica e Tecnologia" WHERE codigo=1;
```


```SQL
ALTER TABLE produto DROP COLUMN produtocol;
```

## Remoção (Delete)
### Por chave primária
```SQL
DELETE FROM produto WHERE codigo = 1;
```
Atentar para dependências de outras tabelas, e deletar elas de acordo se for necessário

# Junção
## Inner
Junta elementos que tem em comum
###  Junção simples como produto cartesiano
```SQL
SELECT * FROM produto inner JOIN departamento
	ON produto.departamento_codigo = departamento.codigo;
-- syntax: table.column
```

### 3 ou mais tabelas
```SQL
-- passo 1  a partir dos pedidos, faço a junção com os itens de pedido
-- passo 2: fazer a junçao com produto
-- passo 3: fazer a junção com cliente
select * from 
     pedido inner join item_pedido 
		on pedido.numero = item_pedido.pedido_numero
	inner join produto on produto.codigo = item_pedido.produto_codigo
    inner join cliente on pedido.cliente_id = cliente.id;
    
-- a mesma consulta anterior, porém buscando todos os dados do pedido + nome
-- do cliente + o nome do produto comprado

select pedido.numero, pedido.data_pedido, pedido.valor_bruto,
       pedido.desconto, pedido.valor_final, cliente.nome,
       produto.nome from 
     pedido inner join item_pedido 
		on pedido.numero = item_pedido.pedido_numero
	inner join produto on produto.codigo = item_pedido.produto_codigo
    inner join cliente on pedido.cliente_id = cliente.id
    order by pedido.numero;

-- quero totais de pedidos por cliente (inclusive com o nome deles)
select cliente.nome, pedido.cliente_id, sum(pedido.valor_final)
    from pedido inner join cliente on pedido.cliente_id = cliente.id
    group by pedido.cliente_id;
```

## Outer
```sql
-- hipótese 1: buscando todos os produtos a partir dos departamentos
select * from departamento inner join produto on
	departamento.codigo = produto.departamento_codigo;
    
-- inserindo um novo departamento
insert into departamento values (null, "Moveis", "Moveis para escritórios e gamers de todas as idades");

select * from departamento;

-- solução para isso: usar uma junçao externa (outer join)
select * from departamento left outer join produto
	on departamento.codigo = produto.departamento_codigo;
    
-- agora usando right outer join
select * from produto right outer join departamento
	on departamento.codigo = produto.departamento_codigo;
```

# Subqueries
São as especificações do `WHERE` em uma consulta.

```sql
-- gostaria de buscar todos os pedidos que possuem o produto mais caro neles

-- como saber qual o produto mais caro?
select * from produto order by preco desc limit 1;
select * from produto having max(preco);
select * from produto where preco = (select max(preco) from produto);

-- mas na verdade eu quero os pedidos que contem este produto
select * from pedido inner join item_pedido
	on item_pedido.pedido_numero = pedido.numero
	where item_pedido.produto_codigo = 
     (select codigo from produto having max(preco));
     
-- caso eu queira o(s) cliente(s) que compraram este produto mais caro 
-- basta fazer na consulta externa uma junção com cliente e recuperar seu nome

select * from cliente inner join pedido on cliente.id = pedido.cliente_id
		inner join item_pedido on item_pedido.pedido_numero = pedido.numero
        where item_pedido.produto_codigo = 
        (select codigo from produto having max(preco));
```