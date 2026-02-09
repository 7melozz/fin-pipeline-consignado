Consignado Data Analytics: Python & Power BI Pipeline
📝 Sobre o Projeto
Este repositório contém um projeto completo de Análise de Dados focado no setor de crédito consignado. O fluxo abrange desde a engenharia de dados inicial até a entrega de um dashboard executivo de alta fidelidade.

O principal objetivo foi demonstrar como transformar dados brutos e "sujos" em insights acionáveis, mantendo o foco na segurança da informação (LGPD) através da anonimização completa de valores e nomes.

🛠️ Tecnologias e Ferramentas
Python & Pandas: Limpeza, normalização e transformação de dados monetários.

Power BI: Modelagem de dados, medidas DAX e visualização.

Canva: Design de interface (UI) e background personalizado para otimização de layout.

🧮 Processamento de Dados (ETL)
Utilizei o Pandas para resolver o desafio de converter strings monetárias brasileiras (ex: "1.500,00") em formatos numéricos operacionais. O código foi estruturado de forma limpa (Clean Code) utilizando parênteses para facilitar a manutenção:

df["Valor Contrato"] = pd.to_numeric(
    df["Valor Contrato"]
    .astype(str)
    .str.replace(".", "", regex=False)  # Remove milhar
    .str.replace(",", ".", regex=False), # Converte decimal
    errors='coerce'
)
