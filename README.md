## Documentação do Processo ETL com Integração ao BigQuery e Looker

### Objetivo
O objetivo deste documento é detalhar o processo de extração, transformação e carga de dados (ETL) que utiliza o Google BigQuery para armazenar os dados nas camadas bronze e ouro. Além disso, os dados transformados são visualizados através de dashboards no Looker Studio.

### Fonte de Dados
Os dados utilizados neste projeto são provenientes do seguinte conjunto:
- [Histórico de Planos de Saúde](https://dados.gov.br/dados/conjuntos-dados/historico-de-planos-de-saude)

### Descrição do Processo

#### 1. Extrair Dados do CSV
Os dados iniciais são extraídos de um arquivo CSV, contendo o histórico de planos de saúde. O arquivo está localizado no diretório especificado. A função utilizada para essa extração lê o arquivo e trata os dados brutos, renomeando a coluna `#ID_PLANO` para `ID_PLANO` para adequação ao esquema do BigQuery.

#### 2. Definir Credenciais
Antes de qualquer interação com o BigQuery, são definidas as credenciais de autenticação. Utilizamos um arquivo de credenciais JSON, cujo caminho é carregado a partir de variáveis de ambiente.

#### 3. Carregar Dados Brutos na Tabela (Camada Bronze)
Após a extração dos dados do CSV, o próximo passo é carregar esses dados brutos na **tabela bronze** do BigQuery. A camada bronze armazena os dados em seu estado original, sem qualquer transformação. Isso garante que temos uma cópia fiel dos dados antes de qualquer manipulação.

#### 4. Transformar Dados
Os dados na camada bronze passam por um processo de transformação. Nessa etapa, regras de negócio são aplicadas para organizar, limpar e enriquecer os dados, de acordo com as necessidades analíticas da empresa.

#### 5. Carregar Dados Transformados na Tabela (Camada Ouro)
Os dados transformados são então carregados na **camada ouro**, que é a camada preparada para análise. Esta tabela contém os dados finais e prontos para serem consumidos pelas ferramentas de visualização, como o Looker.

#### 6. Visualização no Looker Studio
Os dados na camada ouro são conectados ao **Looker Studio**, onde dashboards são criados para facilitar a análise visual e tomada de decisão. A integração com o Looker permite a geração de insights rápidos e dinâmicos sobre os dados transformados.

Você pode acessar o dashboard do Looker Studio através do link:
[Monitoramento de Planos de Saúde Ativos e Cancelados
](https://lookerstudio.google.com/u/1/reporting/3803c230-4673-46ab-87b4-427befd47fa1/page/ci7GE)

### Entregas
- **Entrega BigQuery:** Dados brutos carregados na tabela bronze e dados transformados na tabela ouro.
- **Entrega Looker:** Dashboards interativos criados a partir dos dados na camada ouro.

### Diagrama do Processo ETL
O diagrama a seguir ilustra o fluxo do processo, desde a extração dos dados até a visualização no Looker Studio:

![Diagrama do Processo ETL](C:\Users\Bruno\Desktop\projetos_engenharia\Histórico de Planos de Saúde\processo.png)

### Considerações Finais
Esse processo garante uma abordagem eficiente e escalável para a manipulação de dados em ambientes de Big Data. A visualização final no Looker Studio permite que as equipes de Business Intelligence e gestão tenham acesso a dashboards dinâmicos e atualizados.
