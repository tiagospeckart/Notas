---
title:  Modelo Relacional
created: Saturday 26th November 2022 18:58
Last modified: Saturday 26th November 2022 18:57
tags: banco de dados, BD
alias: Relational model, RM
---
# Modelo Relacional
## Comparação entre os modelos
### [[Modelo Entidade-Relacionamento]] -> conjuntos e relações
- Maior grau de abstração
- Mapeamento de operações matemáticas para facilitar a manipulação

### Modelo Relacional -> tabelas e restrições
- É mais próximo da implementação do [[Banco de dado]]
- Reflete como o Banco de dados deve estar organizado

# Tabelas (prática) ou Relações (teórica)

## Tabela
- Conjunto de [[Tuplas]] (linhas)
- Cada linha é composta por campos (atributos)
- Cada campo é identificado por um nome de campo (nome dos atributos)
- Conjunto de campos homônimos em todas as linhas é chamado de coluna

>[!NOTE] Notação de Tabela
>tabela(Coluna1, Coluna2, Coluna3)
>`empregado(CódigoEmpregado, Nome, CódigoDepartamento, Categoria)`

- As linhas de uma tabela não possuem ordenação. A recuperação pelo SGBD é arbitrária
- A não ser que o critério de busca especifique uma forma de ordenação
- Não se pode recuperar registros por uma determinada posição
- Os valores dos campos em uma tabela sempre serão atômicos e univalorados (pelo menos em 1 instância)
- Linguagens de manipulação de bases de dados permitem o acesso por quaisquer critérios envolvendo os campos de uma ou mais linhas
- Fazem uso de estruturas auxiliares (índices primários ou secundários)

## Chaves
Elemento que identifica uma linha ou estabelece relações entre linhas de várias tabelas
Pode ser uma junção de dados que se torna única, como RG + Estado emissor
### Chave primária
Identifica de forma única o registro
### Chave estrangeira
- Referência à outros registros, geralmente de outras tabelas
- Mas não necessariamente de outras tabelas, pois pode ser auto-relacionado
	- Exemplo: um Funcionário que é Chefe de outros Funcionários
### Chave alternativa
E quando tabelas possuem mais de um campo que identificam unicamente o registro?
- Código de empregado
- CPF
- E-mail

 A diferença da chave alternativa para a primária é que a chave primária será o elemento que será referenciado num relacionamento.
 Não são usadas em relações e referências, mas podem ser usadas nas buscas

# Notas
Há regras de integridade que também podemos definir:
- Campos podem ou não serem vazios
- Campos podem ter valores "default"
Observe bem as restrições de integridade ao inserir/alterar dados da tabela

Algumas restrições dependem também da aplicação (do sistema). Ex: um funcionário sem CNH do tipo B não pode ser cadastrado no departamento de transportes. E isso o [[Sistema de gerenciamento de banco de dados|SGBD]] não consegue restringir.

# Restrições
Quando da inclusão de uma linha na tabela que contém a chave estrangeira

Quando da alteração do valor da chave estrangeira

Quando da exclusão de uma linha da tabela que contém a chave primária referenciada pela chave estrangeira

Quando da alteração do valor da chave primária referenciada pela chave estranhgeira