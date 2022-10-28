--LETRA A: Crie uma consulta por meio do comando SELECT que exiba informações das categorias de produto e respectivos produtos de cada categoria. Exiba as seguintes informações: código e nome da categoria, código e descrição do produto, valor unitário, tipo de embalagem e percentual do lucro de cada produto. Caso exista alguma categoria sem produto, favor exibir a categoria e deixar os dados do produto em branco. Classifique a consulta em ordem de categoria e nome de produto de forma ascendente.
SELECT T_MC_PRODUTO.CD_CATEGORIA,
       T_MC_CATEGORIA_PROD.DS_CATEGORIA,
       T_MC_PRODUTO.CD_PRODUTO,
       T_MC_PRODUTO.DS_PRODUTO,
       T_MC_PRODUTO.VL_UNITARIO,
       T_MC_PRODUTO.TP_EMBALAGEM,
       T_MC_PRODUTO.VL_PERC_LUCRO
FROM T_MC_PRODUTO
INNER JOIN T_MC_CATEGORIA_PROD ON T_MC_CATEGORIA_PROD.CD_CATEGORIA = T_MC_PRODUTO.CD_CATEGORIA;

--LETRA B: Crie uma consulta por meio do comando SELECT que exiba a quantidade de clientes agrupados por Estado, cidade e bairro. Classifique a consulta por nome do Estado, nome da cidade e nome do bairro. Caso não existam clientes cadastrados para algum bairro, exiba o valor zero para o bairro.
SELECT T_MC_ESTADO.NM_ESTADO AS "Nome do estado",
       T_MC_CIDADE.NM_CIDADE AS "Nome da cidade",
       T_MC_BAIRRO.NM_BAIRRO AS "Nome do bairro",
       COUNT(T_MC_END_CLI.NR_CLIENTE) AS "Contagem de clientes"
FROM T_MC_BAIRRO
LEFT JOIN T_MC_LOGRADOURO ON T_MC_BAIRRO.CD_BAIRRO = T_MC_LOGRADOURO.CD_BAIRRO
LEFT JOIN T_MC_END_CLI ON T_MC_END_CLI.CD_LOGRADOURO_CLI = T_MC_LOGRADOURO.CD_LOGRADOURO
LEFT JOIN T_MC_CIDADE ON T_MC_CIDADE.CD_CIDADE = T_MC_BAIRRO.CD_CIDADE
LEFT JOIN T_MC_ESTADO ON T_MC_CIDADE.SG_ESTADO = T_MC_ESTADO.SG_ESTADO
GROUP BY T_MC_BAIRRO.NM_BAIRRO, T_MC_CIDADE.NM_CIDADE, T_MC_ESTADO.NM_ESTADO
ORDER BY T_MC_ESTADO.NM_ESTADO, T_MC_CIDADE.NM_CIDADE, T_MC_BAIRRO.NM_BAIRRO;

--LETRA C: Crie uma instrução SQL que exiba o TOP 10 vídeos de produtos assistidos pelo cliente. Exiba o código do produto, nome do produto, ano e mês de visualização e a quantidade total de visualizações que o produto teve durante o ano e mês.
SELECT T_MC_SGV_VISUALIZACAO_VIDEO.CD_PRODUTO AS "Codigo do produto",
       MAX(T_MC_PRODUTO.DS_PRODUTO) AS "Produto",
       TO_CHAR(T_MC_SGV_VISUALIZACAO_VIDEO.DT_VISUALIZACAO,'mm-yyyy') AS "Mês da visualizacao",
       COUNT(DISTINCT T_MC_SGV_VISUALIZACAO_VIDEO.CD_VISUALIZACAO_VIDEO) AS "Visualizacoes"
FROM T_MC_SGV_VISUALIZACAO_VIDEO
LEFT JOIN T_MC_PRODUTO ON T_MC_PRODUTO.CD_PRODUTO = T_MC_SGV_VISUALIZACAO_VIDEO.CD_PRODUTO
WHERE ROWNUM <=10
GROUP BY T_MC_SGV_VISUALIZACAO_VIDEO.CD_PRODUTO, TO_CHAR(T_MC_SGV_VISUALIZACAO_VIDEO.DT_VISUALIZACAO,'mm-yyyy')
ORDER BY "Visualizacoes" DESC;

--LETRA D: Crie uma instrução SQL que exiba os dados dos clientes pessoa física. Exiba as seguintes informações: código e nome do cliente, e-mail, telefone, login, data de nascimento, sexo biológico e CPF.
SELECT T_MC_CLIENTE.NR_CLIENTE   "Código do Cliente",  
    T_MC_CLIENTE.NM_CLIENTE   "Nome do Cliente",
    T_MC_CLIENTE.DS_EMAIL    "Email do Cliente",
    T_MC_CLIENTE.NR_TELEFONE     "Número do Telefone",
    T_MC_CLIENTE.NM_LOGIN       "Login",
    T_MC_CLI_FISICA.DT_NASCIMENTO   "Data de Nascimento",
    T_MC_CLI_FISICA.FL_SEXO_BIOLOGICO   "Sexo Biológico",
    T_MC_CLI_FISICA.NR_CPF      "CPF"
FROM T_MC_CLIENTE,
    T_MC_CLI_FISICA
WHERE T_MC_CLIENTE.NR_CLIENTE = T_MC_CLI_FISICA.NR_CLIENTE
ORDER BY T_MC_CLIENTE.NM_CLIENTE;

--LETRA E: Crie uma instrução SQL que exiba os dados dos clientes pessoa jurídica. Exiba as seguintes informações: código e nome do cliente, e-mail, telefone, login, data de fundação e CNPJ.
SELECT T_MC_CLIENTE.NR_CLIENTE   "Código do Cliente",  
    T_MC_CLIENTE.NM_CLIENTE   "Nome do Cliente",
    T_MC_CLIENTE.DS_EMAIL    "Email do Cliente",
    T_MC_CLIENTE.NR_TELEFONE     "Número do Telefone",
    T_MC_CLIENTE.NM_LOGIN       "Login",
    T_MC_CLI_JURIDICA.DT_FUNDACAO   "Data de Fundação",
    T_MC_CLI_JURIDICA.NR_CNPJ   "Número do CNPJ"
FROM T_MC_CLIENTE,
    T_MC_CLI_JURIDICA
WHERE T_MC_CLIENTE.NR_CLIENTE = T_MC_CLI_JURIDICA.NR_CLIENTE
ORDER BY T_MC_CLIENTE.NM_CLIENTE;

--LETRA F: Exiba qual é o dia da semana em que os vídeos são mais acessados. Exiba o dia da semana por extenso e a quantidade de vídeos acessados. Classifique a saída de dados por quantidade de vídeos mais acessados, ou seja, por ordem descendente.
SELECT TO_CHAR(T_MC_SGV_VISUALIZACAO_VIDEO.DT_VISUALIZACAO,'DAY') AS "Dia da semana",
       COUNT(T_MC_SGV_VISUALIZACAO_VIDEO.CD_VISUALIZACAO_VIDEO) AS "Vídeos acessados"
FROM T_MC_SGV_VISUALIZACAO_VIDEO
GROUP BY TO_CHAR(T_MC_SGV_VISUALIZACAO_VIDEO.DT_VISUALIZACAO,'DAY')
ORDER BY "Vídeos acessados" DESC

--LETRA G: Exiba por ano e por mês a quantidade de chamados abertos no SAC até o momento. Exiba o ano e mês da abertura do SAC e a quantidade de ocorrências abertas pelo cliente por ano e mês. Classifique a consulta em ordem de ano e mês.
SELECT TO_CHAR(T_MC_SGV_SAC.DT_ABERTURA_SAC,'mm-yyyy') "Mês abertura SAC",
       T_MC_SGV_SAC.NR_CLIENTE AS "Número do Cliente",
       MAX(T_MC_CLIENTE.NM_CLIENTE) AS "Nome do Cliente",
       COUNT(T_MC_SGV_SAC.NR_SAC) AS "Ocorrências abertas"
FROM T_MC_SGV_SAC
LEFT JOIN T_MC_CLIENTE ON T_MC_CLIENTE.NR_CLIENTE = T_MC_SGV_SAC.NR_CLIENTE
GROUP BY TO_CHAR(T_MC_SGV_SAC.DT_ABERTURA_SAC,'mm-yyyy'), T_MC_SGV_SAC.NR_CLIENTE
ORDER BY "Mês abertura SAC"

--LETRA H: Exiba o chamado no SAC que teve o maior tempo de atendimento total em número de horas (*utilize a técnica de subquery). Fica a seu critério informar as colunas que julgar necessárias. Não utilize *, selecione algumas colunas relevantes.
SELECT T_MC_PRODUTO.DS_PRODUTO AS "Produto sobre o qual é o chamado",
       T_MC_CLIENTE.NM_CLIENTE AS "Nome do cliente",
       T_MC_FUNCIONARIO.NM_FUNCIONARIO AS "Nome do atendente",
       T_MC_SGV_SAC.TP_SAC AS "Tipo de chamado",
       T_MC_SGV_SAC.NR_INDICE_SATISFACAO AS "Índice de satisfação"
FROM T_MC_SGV_SAC
LEFT JOIN T_MC_PRODUTO ON T_MC_PRODUTO.CD_PRODUTO = T_MC_SGV_SAC.CD_PRODUTO
LEFT JOIN T_MC_CLIENTE ON T_MC_CLIENTE.NR_CLIENTE = T_MC_SGV_SAC.NR_CLIENTE
LEFT JOIN T_MC_FUNCIONARIO ON T_MC_FUNCIONARIO.CD_FUNCIONARIO = T_MC_SGV_SAC.CD_FUNCIONARIO
WHERE T_MC_SGV_SAC.NR_TEMPO_TOTAL_SAC = (SELECT MAX(T_MC_SGV_SAC.NR_TEMPO_TOTAL_SAC) FROM T_MC_SGV_SAC);

--LETRA I: Exiba a quantidade média do índice de satisfação informada pelo cliente para cada funcionário. Exiba o código e nome do funcionário, o nome do departamento onde ele trabalha, seu cargo e também exiba o valor do índice médio geral de satisfação aplicado em cada chamado pelo cliente. Os funcionários que não têm status A(tivo) não devem ser exibidos.
SELECT T_MC_FUNCIONARIO.CD_FUNCIONARIO,
       MAX(T_MC_FUNCIONARIO.NM_FUNCIONARIO),
       MAX(T_MC_DEPTO.NM_DEPTO),
       MAX(T_MC_FUNCIONARIO.DS_CARGO),
       AVG(T_MC_SGV_SAC.NR_INDICE_SATISFACAO) AS "Média do índice de satisfação"
FROM T_MC_FUNCIONARIO
LEFT JOIN T_MC_DEPTO ON T_MC_DEPTO.CD_DEPTO = T_MC_FUNCIONARIO.CD_DEPTO
LEFT JOIN T_MC_SGV_SAC ON T_MC_FUNCIONARIO.CD_FUNCIONARIO = T_MC_SGV_SAC.CD_FUNCIONARIO
WHERE T_MC_FUNCIONARIO.ST_FUNC = 'A'
GROUP BY T_MC_FUNCIONARIO.CD_FUNCIONARIO;

--LETRA J: Exiba a quantidade total de vídeos agrupados por produto. Exiba o código e nome do produto, o valor unitário e o status do produto. Exiba somente os produtos que estejam com status A(tivo) e, caso o produto esteja sem vídeo, exiba o valor zero para o agrupamento.
SELECT T_MC_PRODUTO.CD_PRODUTO AS "Código do produto",
       MAX(T_MC_PRODUTO.DS_PRODUTO) AS "Nome do produto",
       COUNT(T_MC_SGV_PRODUTO_VIDEO.NR_SEQUENCIA) AS "Total de vídeos do produto",
       MAX(T_MC_PRODUTO.VL_UNITARIO) AS "Valor unitário do produto",
       MAX(T_MC_PRODUTO.ST_PRODUTO) AS "Status do produto"
FROM T_MC_SGV_PRODUTO_VIDEO
RIGHT JOIN T_MC_PRODUTO ON T_MC_PRODUTO.CD_PRODUTO = T_MC_SGV_PRODUTO_VIDEO.CD_PRODUTO
WHERE T_MC_PRODUTO.ST_PRODUTO = 'A'
GROUP BY T_MC_PRODUTO.CD_PRODUTO;
