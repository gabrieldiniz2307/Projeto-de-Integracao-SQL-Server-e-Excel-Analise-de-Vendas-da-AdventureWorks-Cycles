
#
Projeto de Integração SQL Server e Excel: Análise de Vendas da AdventureWorks Cycles
#
Apresentação

Este projeto tem como objetivo integrar o banco de dados AdventureWorks do SQL Server com o Excel para analisar as vendas online da empresa fictícia AdventureWorks Cycles. O foco principal é extrair informações pertinentes sobre as vendas realizadas em 2013 e apresentá-las de maneira clara e organizada no Excel.
#
Link para Download Banco de Dados:
https://drive.google.com/file/d/1SW-luLwTOKgUmq9pjFoWQtCL64HHIFbO/view
#
Indicadores do Projeto

Os indicadores analisados neste projeto são:
Total de vendas online por categoria de produto
Receita total online por mês do pedido
Receita e custo total online por país
Total de vendas online por sexo do cliente
#
Tabelas Analisadas

As tabelas do banco de dados AdventureWorks utilizadas neste projeto são:
FactInternetSales: Contém informações sobre as vendas online, como número do pedido, data, quantidade vendida, custo e receita.
DimCustomer: Contém informações sobre os clientes, como nome, sobrenome e sexo.
DimSalesTerritory: Contém informações sobre os territórios de vendas, como país.
DimProductCategory: Contém informações sobre as categorias de produtos, como nome.
DimProductSubcategory: Contém informações sobre as subcategorias de produtos.
DimProduct: Contém informações sobre os produtos.
#
Colunas da View VENDAS

Para facilitar a análise dos dados, foi criada a view VENDAS com as seguintes colunas:
```sql
CREATE OR ALTER VIEW VENDAS AS
SELECT
    f.SalesOrderNumber AS 'Numero do Pedido',
    f.OrderDate AS 'Data do Pedido',
    pc.EnglishProductCategoryName AS 'Categoria ',
    c.FirstName + ' ' + c.LastName AS 'Nome do Cliente',
    c.Gender AS 'Sexo',
    st.SalesTerritoryCountry 'País',
    f.OrderQuantity 'Quantidade Vendida',
    f.TotalProductCost AS 'Custo Total do Produto',
    f.SalesAmount AS 'Receita da Venda'
FROM
    FactInternetSales AS f
JOIN
    DimCustomer AS c ON f.CustomerKey = c.CustomerKey
JOIN
    DimSalesTerritory AS st ON f.SalesTerritoryKey = st.SalesTerritoryKey
JOIN
    DimProduct AS p ON f.ProductKey = p.ProductKey
JOIN
    DimProductSubcategory AS ps ON p.ProductSubcategoryKey = ps.ProductSubcategoryKey
JOIN
    DimProductCategory AS pc ON ps.ProductCategoryKey = pc.ProductCategoryKey;
```


#
Integração com o Excel

Após a criação da view VENDAS, os dados foram importados para o Excel utilizando ferramentas como Microsoft Query ou Power Query. No Excel, foram criadas tabelas dinâmicas, gráficos e outros recursos para analisar os indicadores de vendas definidos no projeto.

Dashboard Resultante

Screenshots e Exemplos

![Projeto de Integração SQL Server e Excel Análise de Vendas da AdventureWorks Cycles](https://github.com/user-attachments/assets/bc56281d-81aa-48b9-b855-eef60ccbfc5f)


Abaixo estão algumas imagens do dashboard gerado:


Receita Total versus Custo Total por País:

![Receita Total](https://github.com/user-attachments/assets/1840f433-7e61-4dc4-88a5-2e65406785dd)

Vendas por Mês:

![Vendas por Mes](https://github.com/user-attachments/assets/91664cb4-f91f-4172-b4c3-efc59428f721)

Vendas por Categoria:

![Vendas Categoria](https://github.com/user-attachments/assets/299c19ed-922a-4605-ab77-8169b64a9a50)

Vendas por Gênero:

[Vendas por genero](https://github.com/user-attachments/assets/f09f04e0-35f0-470f-af0b-a678ee2e31e8)
#
Conclusão!


Este trabalho demonstra como integrar dados do SQL Server com o Excel para a análise eficaz das vendas, proporcionando insights valiosos para a tomada de decisões. O uso da view VENDAS simplificou o processo de extração de dados e permitiu uma análise mais ágil e visual no Excel.
Através da análise de vendas da AdventureWorks Cycles, podemos extrair alguns insights importantes:
Desempenho de vendas por categoria de produto: Podemos identificar quais categorias de produto têm maior ou menor desempenho em termos de vendas online. Isso pode ajudar a direcionar esforços de marketing e tomadas de decisão relacionadas à oferta de produtos.
Tendências de vendas ao longo do tempo: Ao analisar a receita total online por mês do pedido, podemos identificar padrões sazonais ou tendências de crescimento nas vendas ao longo do ano. Essas informações são valiosas para o planejamento estratégico e de estoque.
Análise de vendas por país: Ao analisar a receita e o custo total online por país, podemos identificar quais países têm o maior volume de vendas e onde os recursos estão sendo investidos proporcionalmente. Isso permite uma alocação de recursos mais eficiente e a identificação de mercados que podem ser promissores para expansão.
Segmentação do mercado por sexo do cliente: Ao analisar o total de vendas online por sexo do cliente, podemos identificar diferenças no comportamento de compra entre homens e mulheres. Essas informações são valiosas para personalização de marketing e campanhas direcionadas.
Esses são apenas alguns exemplos dos dados relevantes que podem ser extraídos da análise de vendas da AdventureWorks Cycles. Com base nesses insights, é possível tomar decisões informadas para impulsionar o crescimento e o sucesso do negócio.
