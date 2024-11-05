# ProvaSQL


-- 1. Views

CREATE VIEW Produtos
AS
SELECT TOP (100)
productName,
brandName,
colorName
FROM dimProduct --Puxa dados específicos da tabela dimProduct, como o nome do produto, nome da marca e a cor.



-- 2. Subqueries

SELECT
*
FROM dimProduct
SELECT SUM(productKey)
FROM dimProduct
WHERE colorName = 'Red' ; -- puxa a quantidade de rodutos da tabela dimProduct, que estejam na cor vermelha.



-- 3. CTEs (Common Table Expressions)

WITH quantidade(produtos, [Qtd.Vendida])
AS
(
SELECT TOP(100)
productSubcategoryName,
COUNT(factSales.productKey)
FROM
DimProductSubcategory
INNER JOIN dimProduct
ON dimProduct.productKey = dimProductSubcategory.productSubcategoryKey
INNER JOIN factSales
ON factSales.productKey = dimProduct.productKey
WHERE dateKey LIKE '%2008%'
GROUP BY productSubcategoryName
ORDER BY COUNT(factSales.productKey) DESC 
)

SELECT * FROM quantidade --Puxa um resultado para a pesquisa de produtos da tabela dimProductSubcategory e a quantidade vendida.

-- 4. Window Functions



-- 5. Functions



-- 6. Loops



-- 7. Procedures



-- 8. Triggers

