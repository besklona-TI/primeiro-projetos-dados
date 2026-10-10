# Dashboard de análise de vendas

Dashboard interativo para a atividade de Fundamentos de IA e Análise de Dados. A página começa com 200 registros fictícios em public/dados-exemplo.csv, distribuídos entre janeiro e dezembro de 2025. A etiqueta “Demonstração” identifica essa base.

A base original fornecida, vendas_hamburgueria.csv, foi preservada na raiz. Ela tem 1.367 registros e não contém a coluna regiao; ao importá-la, o dashboard classifica esses registros como “Região não informada”. Para uma análise regional, use um CSV que contenha essa coluna.

## Como executar

Abra public/index.html diretamente no navegador. Também é possível publicar a pasta public como site estático. O dashboard não possui backend e lê os CSVs localmente no navegador.

Chart.js 4.4.4 e Papa Parse 5.4.1 são carregados por CDN. Portanto, é preciso ter acesso à internet para que os gráficos e a importação funcionem. A amostra inicial está incorporada no JavaScript, então a página mantém os dados demonstrativos sem usar fetch.

## Como usar

1. Use os filtros de período, categoria e região para atualizar cartões, gráficos e tabela.
2. Pesquise na tabela e clique nos títulos das colunas para ordenar.
3. Clique em Escolher CSV para substituir a base. A leitura acontece localmente.
4. Clique em Exportar CSV para baixar os registros filtrados e correspondentes à pesquisa.
5. Limpar filtros remove período, categoria e região; a pesquisa da tabela pode ser apagada no próprio campo.

O CSV precisa ter as colunas obrigatórias id_venda, data, produto, categoria, quantidade e preco_unitario. A coluna regiao é opcional. Datas devem estar no formato AAAA-MM-DD e números sem símbolo de moeda. Linhas com data inválida, quantidade ou preço ausente, inválido ou negativo são descartadas e a quantidade é informada na tela. Zero é preservado como valor válido. Linhas duplicadas não são removidas automaticamente porque cada linha pode representar uma venda diferente; a contagem usa IDs únicos.

## Indicadores e fórmulas

- Faturamento da linha = quantidade × preco_unitario.
- Faturamento total = soma do faturamento das linhas filtradas.
- Quantidade de vendas = número de id_venda únicos nas linhas filtradas.
- Unidades vendidas = soma de quantidade.
- Ticket médio = faturamento total ÷ quantidade de vendas. Sem vendas, o resultado é R$ 0,00.

## Publicar no Render pelo GitHub

1. Envie este projeto para um repositório no GitHub.
2. No Render, crie um novo Static Site e conecte o repositório.
3. Em Branch, selecione a branch que contém o projeto.
4. Deixe Root Directory vazio.
5. Use Build Command: echo "Site pronto".
6. Use Publish Directory: public.
7. Crie o serviço.

## Verificação

A estrutura, a sintaxe do JavaScript e os cálculos foram revisados localmente. A demonstração permite testar filtros combinados, limpeza, pesquisa, ordenação, exportação e estado sem resultados. A verificação visual em navegador e em telas grandes e pequenas depende de abrir o arquivo em um navegador com internet; a responsividade está prevista no CSS para telas de até 760px.

