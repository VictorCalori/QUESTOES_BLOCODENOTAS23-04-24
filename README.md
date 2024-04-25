1) Crie uma consulta que mostre todos os carros
    SELECT * FROM `CARROS` WHERE 1;

2) Crie uma consulta que mostre as locaçõs que ocorreram com o carro código 1
  SELECT * FROM LOCAÇÕES
    WHERE CODCARRO = 1;

3)Crie uma consulta que mostre as locações que ocorreram com os carros á Gasolina e quem são os clientes e seus respectivos telefones

 SELECT L.*, CLI.NOME_CLIENTE AS NOME_CLIENTE, CLI.TELEFONE FROM LOCAÇÕES L INNER JOIN CARROS C ON L.CÓDIGO = C.CÓDIGO INNER JOIN CLIENTES CLI ON L.CÓDIGO = CLI.CÓDIGO WHERE C.COMBUSTÍVEL = 'Gasolina'



4) Liste os carros que já foram alugados e hoje em dia estão INDISPONÍVEIS
 SELECT * FROM `CARROS` WHERE ESTÁ_DISPONIVEL = 'NÃO'

5) Crie uma stored Procedure para o exercício 2 (também para 1, 3 e 4)
    2- BEGIN
  SELECT * FROM LOCAÇÕES
    WHERE CODCARRO = 1;
    END

1- DELIMITER //

CREATE PROCEDURE sp_listarcarros()
BEGIN
    SELECT * FROM CARROS WHERE 1;
END//

DELIMITER ;

3-
BEGIN
SELECT L.*, CLI.NOME_CLIENTE AS NOME_CLIENTE, CLI.TELEFONE FROM LOCAÇÕES L INNER JOIN CARROS C ON L.CÓDIGO = C.CÓDIGO INNER JOIN CLIENTES CLI ON L.CÓDIGO = CLI.CÓDIGO WHERE C.COMBUSTÍVEL = 'Gasolina';
END



4- BEGIN
   SELECT * FROM `CARROS` WHERE ESTÁ_DISPONIVEL = 'NÃO';
END


6) Crie uma stored Procedure para adicionar um novo carro.

  DELIMITER //

CREATE PROCEDURE sp_inserir_carro (
    IN p_codigo INT,
    IN p_nome_carro VARCHAR(50),
    IN p_marca VARCHAR(50),
    IN p_cor VARCHAR(50),
    IN p_combustivel VARCHAR(50),
    IN p_esta_disponivel VARCHAR(50),
    IN p_km_atual INT
)
BEGIN
    INSERT INTO CARROS (CÓDIGO, NOME_CARRO, MARCA, COR, COMBUSTÍVEL, ESTÁ_DISPONIVEL, KM_ATUAL) 
    VALUES (p_codigo, p_nome_carro, p_marca, p_cor, p_combustivel, p_esta_disponivel, p_km_atual);
END//

DELIMITER ;


    

