As contas de faturamento, podem ser de diversas naturezas. Por exemplo, uma conta de faturamento pode ser aplicada a projetos distintos, entre equipes e departamentos. A listagem das contas pode ser realizada tanto via interface gráfica, como via SDK. 
Ex:

`gcloud beta billing accounts list`


Geralmente, o gerenciamento do faturamento do GCP é realizado por algum time de custos, ou fica a par da propria administração da TI. Para isso, existe um conjunto de roles que realizam a liberação de algumas informações, de acordo com o que for necessário. 

> https://cloud.google.com/billing/docs/how-to/billing-access

**Associando um projeto a uma conta de Faturamento**
`gcloud beta billing projects link project-lab --billing-account 0X0X0X-0X0X0X-0X0X0X`


**Exportando arquivo de Faturamento**

 No console do GCP, Clique sobre a opção Faturamento > Exportação de Faturamento > Exportação de Arquivo. 

 Ao ativar a exportação do arquivo, será gerado um arquivo .JSON ou .CSV que será armazenado em um intervalo do Google Cloud Storage. 

Dica: Lembre-se que podemos listar os intervalos do Google Cloud Storage, usando o comando `gsutil ls`.

Exemplo: 

![Faturamento.png](/.attachments/Faturamento-4351daf1-b9fd-437c-82c0-da17a2ddbab6.png)


**Criando Alertas de Faturamento**

1. Logue na Opção de Faturamento > Orçamento e alertas
2. Escolha qual a porcentagem do orçamento que deve ser cotada.Por Exemplo:
   - 50%. 90%. 100% e entre outros..





Documentações:
- https://cloud.google.com/billing/docs/how-to/manage-billing-account
- https://cloud.google.com/sdk/gcloud/reference/beta/billing/projects/link
- https://cloud.google.com/billing/docs/how-to/budgets
- https://cloud.google.com/billing/docs/how-to/export-data-bigquery
- https://cloud.google.com/billing/docs/how-to/bq-examples
- https://cloud.google.com/billing/docs/how-to/export-data-file
- https://cloud.google.com/billing/docs/how-to/billing-access
