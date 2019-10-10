O Google Cloud oferece um SDK para manipulação de objetos e tarefas que são realizadas no dia a dia. Isso inclui ferramentas de gerenciamento do App Engine, BigQuery, Kubernertes e entre outros. 

No Cloud Shell, É padrão que venha com o Cloud SDK instalado e configurado. Para instalação em um host personalizado, utilize a documentação abaixo:
> https://cloud.google.com/sdk/install

O SDK também pode ser instalado via Powershell: `Install-Module Google Cloud`

Além disso, também está disponível uma imagem docker "Cloud SDK". 
**Imagem Docker: https://hub.docker.com/r/google/cloud-sdk/**

Ao ser instalado, é disponibilizado as seguintes linhas de comando:

	• gcloud - Gerenciamento de Recursos
	• BQ - Interação com BigQuery
	• Gsutil - Ferramenta para gerenciamento do Google Cloud Storage.


**Passos Iniciais**

Como passo inicial deve ser utilizado `gcloud init` para validar o acesso as APIs do Google cloud e configurar questões como projeto a ser utilizado e outros. Nesse processo de configuração, será solicitado a autenticação via navegador web no qual está utilizando OAuth2 para habilitar o acesso as APIs. Isso faz com que Seja Salvo um token em sua máquina, onde toda vez que a conexão for realizada o token também será validado.

Qualquer dúvida sobre o processo de autenticação, pode ser validado através do comando `gcloud list` ou `gcloud auth login`

Toda a configuração que foi realizada, pode ser revista através do comando `gcloud config list`

Para instalar e verificar quais opções estão disponíveis através do SDK, utilize o comando `gcloud components list`


**Configurações Default**
`gcloud config set compute/zone us-east1-c` | Especifica a zona padrão
`gcloud config set project homelab` | Especifica o projeto padrão

**Alpha e Beta**

Para funções e recursos que ainda estão em modo beta ou em teste, o GCP oferece alguns comandos para manipulação desses recursos.

Beta: `gcloud components install beta`
Alpha: `gcloud components install alpha`


Um recurso que pode ser utilizado quando se trabalha com múltiplos projetos e equipes, É criar "estados de configuração" para manipulação dos recursos.

`gcloud config configurations create {name}` - Cria estado de configuração

`gcloud config configurations list`
	1. gcloud config configurations activate - Utilizado para setar a configuração a ser utilizada no momento.
