# Climate & Energy Data Pipeline - Architecture Medallion 🌍🔋

Este projeto implementa um pipeline de Engenharia de Dados completo utilizando a **Arquitetura Medallion (Bronze, Silver e Gold)** no **Databricks** com **Apache Spark / PySpark**. O objetivo é ingerir, tratar e consolidar dados complexos sobre emissões de CO2, matrizes energéticas globais, anomalias de temperatura e eventos climáticos extremos para geração de insights analíticos.

---

## 📁 Estrutura do Pipeline (Notebooks)

O processamento foi dividido em três camadas lógicas para garantir governança e qualidade dos dados:

1. **`01_bronze_layer.ipynb` (Ingestão Raw)**:
   * Leitura dos arquivos brutos em formato CSV a partir do diretório de dados (`raw-data`).
   * Preservação do estado original dos dados adicionando metadados cruciais de governança (`ingestion_timestamp`).
   * Gravação das tabelas no catálogo Delta no formato nativo da camada: `bronze.co2_raw`, `bronze.energy_raw`, `bronze.temperature_raw` e `bronze.climate_raw`.

2. **`02_silver_layer.ipynb` (Limpeza e Padronização)**:
   * Tratamento de tipos de dados (conversão de strings para formatos nativos de `date`, `timestamp`, `double` e `integer`).
   * Padronização de nomes de colunas utilizando o padrão *snake_case*.
   * Enriquecimento simples de dados e tracking temporal através da coluna `silver_timestamp`.
   * Persistência das tabelas limpas: `silver.co2_emissions`, `silver.energy_mix`, `silver.temperature_anomaly` e `silver.climate_events`.

3. **`03_gold_layer.ipynb` (Camada Analítica / Negócio)**:
   * Criação de agregados analíticos de alta performance prontos para consumo por ferramentas de BI (Power BI, Tableau) ou dashboards internos.
   * Cruzamento de dados entre o mix energético e anomalias de temperatura global para responder a perguntas críticas de negócio e estudos climáticos.

---

## 🛠️ Tecnologias e Padrões Utilizados

* **Plataforma**: Databricks Lakehouse.
* **Motor de Processamento**: Apache Spark (PySpark DataFrame API & Spark SQL).
* **Formato de Armazenamento**: Delta Lake (Transações ACID, Schema Enforcement e Time Travel).
* **Arquitetura**: Medalhão (Isolamento de estágios de maturação do dado).

---

## 🧠 Perguntas Frequentes de Arquitetura (FAQ)

### Por que separar o pipeline nas camadas Bronze, Silver e Gold?
Isso garante o princípio da idempotência e segurança. Se uma regra de negócio mudar na camada Gold, você não precisa re-ingerir os dados brutos da fonte; basta reprocessar a partir da camada Silver ou Bronze, economizando tempo e custos de computação.

### Qual a vantagem de salvar os dados como tabelas Delta?
O formato Delta Lake resolve os problemas de arquivos Parquet ou CSV comuns, pois fornece transações ACID (garante que a escrita termine com sucesso ou falhe por completo sem corromper o dado), permite versionamento dos arquivos (Time Travel) e otimiza as consultas através de índices automáticos do Databricks.

### O Spark SQL e o PySpark operam de forma diferente no cluster?
Não, por debaixo do capô, ambos utilizam o Catalyst Optimizer do Spark. A escolha entre PySpark e Spark SQL neste projeto foi feita com base na legibilidade: PySpark para pipelines de ETL estruturados (Bronze e Silver) e Spark SQL para queries de agregações analíticas complexas (Gold).

