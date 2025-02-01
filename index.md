# Análise de Dados com SQL do Brasileirão (2010-2019)

A análise de dados do Brasileirão (2010-2019) utilizando SQL e Google BigQuery revelou insights sobre o total de gols, a média de idade dos jogadores e os maiores públicos anuais. Os dados foram visualizados em gráficos no Excel, facilitando a compreensão das tendências do campeonato. Os resultados fornecem uma compreensão profunda do Brasileirão, auxiliando na tomada de decisões estratégicas e no engajamento do público.

**Objetivo:** Desvendar as tendências e características do Campeonato Brasileiro de Futebol entre 2010 e 2019, utilizando dados para gerar insights sobre os maiores públicos, total de gols e a média de idade dos jogadores.

**Desafios:**

*   **Explorar um vasto conjunto de dados:** O Brasileirão possui um histórico extenso de dados, demandando ferramentas e técnicas eficientes para análise.
*   **Extrair insights relevantes:** A análise dos dados precisava identificar padrões e informações relevantes para entender as características do campeonato.
*   **Apresentar os resultados de forma clara e concisa:** Os insights obtidos precisavam ser comunicados de maneira compreensível e visualmente atraente.

**Soluções:**
- **Coleta e organização dos dados:**
  - Foi utilizada a base de dados do Brasileirão disponível no Google BigQuery.
  - Consultas SQL foram elaboradas para extrair informações sobre público, gols e idade dos jogadores.

- **Análise de dados:**
  - As consultas SQL foram estruturadas para responder às seguintes questões:
    - Qual o total anual de gols?
    - Qual a media de idade anual últimos 10 anos?
    - Quais os maiores públicos nos últimos 10 anos?
  - **Visualização dos resultados:**
    - Os dados foram organizados e visualizados em gráficos no Excel, utilizando diferentes tipos de gráficos para apresentar os       insights de forma clara e concisa.
    - **Resultados:**
      
### Gols por Ano

```SQL
SELECT ano_campeonato,
SUM(gols_man + gols_vis) AS total_gols
FROM "basedosdados.mundo_transfermarkt_competicoes"."brasileirao_serie_a"
WHERE ano_campeonato BETWEEN 2010 AND 2019
GROUP BY ano_campeonato;
```
  ![GOLS POR ANO](https://chrome-crabapple-e07.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F29ecadbd-ece1-4339-9bb9-3123abde53f4%2F9ddb1a9c-63e4-4b78-bcdc-ed9d89c6dc23%2Fgols.jpeg?table=block&id=a1fe72d6-d706-4198-9dfb-055e9176f555&spaceId=29ecadbd-ece1-4339-9bb9-3123abde53f4&width=1120&userId=&cache=v2)

### Media de idade por ano

```SQL
SELECT ano_campeonato, AVG(subquery.total_idade) AS media_total_idade
FROM (
	SELECT ano_campeonato, (idade_media_titular_man + idade_media_titular_vis)/2 AS total_idade
	FROM basedosdados.mundo_transfermarkt_competicoes.brasileirao_serie_a
	WHERE ano_campeonato BETWEEN 2010 AND 2019
) AS subquery
GROUP BY ano_campeonato;
```
  ![MEDIA DE IDADE POR ANO](https://chrome-crabapple-e07.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F29ecadbd-ece1-4339-9bb9-3123abde53f4%2F6011014a-09c9-4534-af0b-d234c9736e1d%2Fidade.jpeg?table=block&id=c15233a1-4492-430e-9f1e-7d9f3fb63510&spaceId=29ecadbd-ece1-4339-9bb9-3123abde53f4&width=1420&userId=&cache=v2)

### Maiores públicos por ano

```SQL
SELECT ano_campeonato, MAX(publico) AS Maior_publico
FROM "basedosdados mundo_transfermarkt_competicoes. 'brasileirao_serie_a'
WHERE ano_campeonato BETWEEN 2010 AND 2019
GROUP BY ano_campeonato;
```
  ![Maiores públicos por ano](https://chrome-crabapple-e07.notion.site/image/https%3A%2F%2Fprod-files-secure.s3.us-west-2.amazonaws.com%2F29ecadbd-ece1-4339-9bb9-3123abde53f4%2F14175969-dd1d-446f-b78b-e79da6761281%2Fpublico.jpeg?table=block&id=811909aa-cb36-4305-9943-d3203f9df51e&spaceId=29ecadbd-ece1-4339-9bb9-3123abde53f4&width=1130&userId=&cache=v2)


#### Benefícios:

- Compreensão profunda do Brasileirão: A análise forneceu insights valiosos sobre as características do campeonato, permitindo uma melhor compreensão do contexto do futebol brasileiro.
- Tomada de decisões estratégicas: Os insights podem auxiliar times, patrocinadores e profissionais do esporte a tomar decisões estratégicas mais assertivas.
- Engajamento do público: A apresentação dos resultados de forma clara e visualmente atraente pode aumentar o engajamento do público em relação ao campeonato.

#### Habilidades:

- Análise de dados
- SQL
- Google BigQuery
- Excel
- Visualização de dados

## Conclusão:

A análise de dados do Brasileirão utilizando o Google BigQuery e o Excel permitiu gerar insights relevantes sobre os maiores públicos, total de gols e a média de idade dos jogadores entre 2010 e 2019. Essa análise possibilita uma compreensão mais profunda do campeonato, oferecendo subsídios para tomadas de decisões estratégicas e contribuindo para o crescimento e desenvolvimento do futebol brasileiro.
