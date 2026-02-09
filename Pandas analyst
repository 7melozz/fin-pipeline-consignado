import pandas as pd

df = pd.read_csv('esteira (1).csv', sep=';')

df = df[['Proposta', 'ADE', 'ADE2','Data Pagamento',
          'Data Retorno', 'Data Cancelamento',
          'Banco','Vl Liquido-Destinario','Produto',
          'Etapa', 'Status', 'Valor Contrato'
          ]]

df["Produto"] = df["Produto"].replace({'CARTAO BENEFICIO':'CARTAO'})

df_pago = df[df['Etapa'] == 'Pago']
df_cancelado = df[df['Etapa'] == 'Reprovada']
df_retencao = df[df['Status'] == 'RETENCAO CLIENTE']
df_total_propostas = len(df['Proposta'].unique())

df["Valor Contrato"] = (
    df["Valor Contrato"]
    .astype(str)
    .str.strip()
    .str.replace(".", "", regex=False)
)

df["Valor Contrato"] = pd.to_numeric(
    df["Valor Contrato"]
    .astype(str)
    .str.replace(".", "", regex=False)
    .str.replace(",", ".", regex=False), 
    errors='coerce'
)

df_total_pago = df_pago['Valor Contrato'].sum()
df_total_cancelado = df_cancelado['Valor Contrato'].sum()
df_total_retencao = df_retencao['Valor Contrato'].sum()


df_total_pago = pd.DataFrame({"Total Pago": [df_total_pago]})
df_total_cancelado = pd.DataFrame({"Total Cancelado": [df_total_cancelado]})
df_total_retencao = pd.DataFrame({"Total Retencao": [df_total_retencao]})


df.to_excel("analise_consolidada.xlsx", index=False)


