--Letra A, parte 1: O nome do cliente dentro da tabela T_MC_CLIENTE está como único. Favor excluir essa restrição. Qual é a instrução SQL ideal para executar essa ação?


ALTER TABLE T_MC_CLIENTE DROP CONSTRAINT uk_mc_cliente_nome_cliente;


--Letra B, parte 1:  As colunas QT_ESTRELAS, ST_CLIENTE e DS_EMAIL da tabela T_MC_CLIENTE devem ser obrigatórias. Favor realizar esse ajuste. Quais as instruções SQL ideais para executar essa ação?

ALTER TABLE T_MC_CLIENTE MODIFY (qt_estrelas NOT NULL);
ALTER TABLE T_MC_CLIENTE MODIFY (st_cliente NOT NULL);
ALTER TABLE T_MC_CLIENTE MODIFY (ds_email NOT NULL);

--Letra C, parte 1: A coluna NM_LOGIN da tabela T_MC_CLIENTE deve receber conteúdo único. Favor realizar esse ajuste. Qual é a instrução SQL ideal para executar essa ação?

ALTER TABLE T_MC_CLIENTE ADD CONSTRAINT uk_mc_cliente_nome_login UNIQUE (nm_login);

--Letra D, parte 1: As colunas DT_FUNDACAO e NR_CNPJ da tabela T_MC_CLI_JURIDICA devem ter conteúdo como sendo obrigatório. Quais as instruções SQL ideais para executar essa ação? 

ALTER TABLE T_MC_CLI_JURIDICA MODIFY (dt_fundacao NOT NULL);
ALTER TABLE T_MC_CLI_JURIDICA MODIFY (nr_cnpj NOT NULL);

--Letra E, parte 1: As colunas NR_MINUTO_VIDEO e NR_SEGUNDO_VIDEO na parte de controle da visualização do vídeo devem ter conteúdos obrigatórios. Identifique o nome da tabela e realize esses ajustes.

ALTER TABLE t_mc_sgv_visualizacao_video MODIFY (nr_minuto_video NOT NULL);
ALTER TABLE t_mc_sgv_visualizacao_video MODIFY (nr_segundo_video NOT NULL);

--Letra F, parte 1: As colunas ST_PRODUTO, ST_VIDEO_PROD, ST_END, ST_FUNC e ST_CATEGORIA somente pode receber dois valores possíveis: A ou I, sendo (A)tivo ou (I)nativo. Identifique em quais tabelas se localizam essas colunas e realize os ajustes.

ALTER TABLE t_mc_produto ADD CONSTRAINT ck_st_produto CHECK (st_produto = 'A' or st_produto = 'I');
ALTER TABLE t_mc_sgv_produto_video ADD CONSTRAINT ck_st_video_prod CHECK (st_video_prod = 'A' or st_video_prod = 'I');
ALTER TABLE t_mc_end_cli ADD CONSTRAINT ck_st_end CHECK (st_end = 'A' or st_end = 'I');
ALTER TABLE t_mc_funcionario ADD CONSTRAINT ck_st_func CHECK (st_func = 'A' or st_func = 'I');
ALTER TABLE t_mc_categoria_prod ADD CONSTRAINT ck_st_categoria CHECK (st_categoria = 'A' or st_categoria = 'I');
