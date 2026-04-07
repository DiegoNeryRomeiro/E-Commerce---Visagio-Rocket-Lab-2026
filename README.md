# E-Commerce---Visagio-Rocket-Lab-2026
Pipeline de Dados - Arquitetura Medalhão no Databricks
Este repositório contém a implementação de um pipeline de engenharia de dados automatizado, desenvolvido no Databricks. O projeto utiliza a arquitetura Medalhão para processar dados brutos de vendas, transformando-os em tabelas analíticas prontas para consumo de negócios.

# Estrutura do Projeto
O pipeline é composto por três notebooks principais, cada um responsável por uma camada específica da arquitetura:

- Camada Bronze (Ingestão): * Leitura dos dados brutos da Landing Zone.

Conversão dos arquivos para o formato Delta.

Adição de metadados de controle, como o timestamp de ingestão.

- Camada Silver (Limpeza e Padronização): * Aplicação de deduplicação de registros utilizando Window Functions.

Padronização de textos e renomeação de colunas para nomes amigáveis em português.

Garantia da evolução de esquema com a configuração de overwriteSchema.

- Camada Gold (Agregação e Negócio): * Criação de visões agregadas, como o ranking de produtos mais vendidos e performance por vendedor.

Cálculo de KPIs essenciais para a área comercial.

Dados prontos para integração com ferramentas de visualização (BI).

#Automação e Orquestração
Para garantir que os dados estejam sempre atualizados, foi configurado um Workflow (Job) no Databricks:

Dependências: As tarefas foram encadeadas de forma sequencial (Bronze -> Silver -> Gold), garantindo que uma fase só inicie após o sucesso da anterior.

Agendamento (Trigger): O pipeline está configurado para execução automática diária, programada para as 13:00.

Resiliência: O uso de overwriteSchema e o modo de escrita overwrite nas camadas finais garantem que o Job suporte mudanças estruturais e mantenha a consistência dos dados.

Tecnologias Utilizadas
Azure Databricks / Databricks Community

PySpark (Spark SQL): Para o processamento distribuído de grandes volumes de dados

Pandas: Utilizado para a manipulação de DataFrames em memória, análise exploratória rápida e formatação de resultados para exibição.

Delta Lake: Armazenamento otimizado com suporte a transações ACID

Databricks Workflows: Orquestração e agendamento das tarefas.

# Como utilizar
Para replicar este projeto, importe os notebooks na ordem numérica para o seu workspace do Databricks e configure um Job apontando para os arquivos correspondentes, respeitando as dependências de cada tarefa.