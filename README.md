Análise de Preços Médios Mensais de Produtos Agropecuários (2023)


Integrantes
Jayce
Hariel
Igor

A base de dados

Fonte: dados da conab referente a diversos produtos: https://www.kaggle.com/datasets/jeffersonvalandro/conab-valor-dos-produtos-no-brasil?select=relatorio_preco_medio_mensal_2023.csv

Arquivo original: dados/relatorio_preco_medio_mensal_2023.csv

Estrutura original: 2.029 linhas × 15 colunas, em formato largo (um mês por coluna, 01/2023 a 12/2023). Cada linha representa um produto + unidade de medida + nível de comercialização (Produtor, Atacado ou Varejo) + UF, com o preço médio de cada mês.

Recorte temporal: janeiro a dezembro de 2023.

Perguntas que guiaram a análise
Qual produto apresentou o maior aumento percentual entre janeiro/2023 e dezembro/2023?
Qual região teve o preço médio mais alto para "Abacaxi Pérola (kg)" em 2023?
Existe sazonalidade no preço do Abacate (kg) ao longo dos meses?
O preço do arroz no atacado é diferente do preço no varejo?
Quais foram os 5 meses com maior preço médio geral (considerando todos os produtos e UFs)?
Diagnóstico de qualidade — principais problemas encontrados

A base exigiu tratamento real antes de qualquer análise ser confiável:

Colunas mescladas do Excel: Produto/Unidade e Nível de Comercialização vinham em branco em 73% e 85% das linhas, respectivamente — não eram dados faltantes, mas células mescladas na planilha original que "herdam" o valor da linha de cima. Tratado com ffill().
Linhas de rodapé: as 3 últimas linhas do CSV continham texto de fonte/licença da CONAB, não dados — removidas antes de qualquer processamento.
Unidade de medida embutida no nome do produto (ex.: "ABACAXI PÉROLA (kg)", "ABACAXI PÉROLA (t)", "ABACAXI PÉROLA (un)") — separada em duas colunas (produto_nome, unidade) via regex, para evitar comparar preços em escalas incompatíveis (kg × tonelada).
Números em formato brasileiro ("2.000,00") armazenados como texto — convertidos para float.

Respostas
1. Produto com maior aumento percentual (jan → dez/2023)
Grafico com os 10 produtos com maior ercentual de aumento de preços

3. Região com maior preço médio — Abacaxi Pérola (kg)

Gráfico com a região que apresentou maior preço médio

3. Sazonalidade no preço do Abacate (kg)

Gráico com a variação mensal do preço do abacate em 2023. Mês com maior preço: 04/2023 (R$7.00)
Mês com menor preço: 06/2023 (R$6.00)

Não foi identificado padrão sazonal claro: o preço variou entre R$ 6,00 e R$ 7,00 ao longo de todo o ano (~14% de amplitude), sem tendência de alta ou baixa em época específica.

Limitação importante: a base contém apenas um registro de Abacate (kg) no ano inteiro, referente a Roraima (Atacado). A conclusão acima vale para esse estado especificamente, não para o Brasil — não há dados suficientes para generalizar.

4. Arroz: atacado vs. varejo

Gráfico com comparaçao que o valor do arroz no varejo é 9.09% mais caro que o atacado

5. Os 5 meses com maior preço médio geral
Gráfico com o maior preço medio em 2023


Os dados brutos estão em dados/relatorio_preco_medio_mensal_2023.csv.
O notebook realiza, em ordem: diagnóstico de qualidade → limpeza e transformação → análise exploratória → conclusões.