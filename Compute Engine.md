Work Itens Associados: 
#131
#138

Como todo recurso no GCP é associado a um projeto, a primeira coisa a ser feita é validar se já foi criado um Projeto e se existe uma conta de faturamento associada.

`gcloud beta billing projects link gcp-bigdata --billing-acount=XXXXXX-XXXXXX-XXXXXX`

##Criação de VM
1. No console do Google Cloud Shell, digite: `gcloud compute instances create another-instance --zone us-central1-a`
1. Utilize o comando " gcloud compute instances create --help" caso tenha dúvidas na hora da criação.
	

Para acessar a instância que foi criada, podemos utilizar o comando "`gcloud compute ssh nome`". 
 
> Obs: Caso não consiga conectar a instância que foi criada. Utilize o parâmetro --zone, no comando que foi descrito acima. 


## Criação de Discos
`gcloud compute disks create disk-lab --zibe=10GB --zone us-east1-c`

Para validação da criação do disco, utilize: `gcloud compute disks list`. Após o disco ser criado, Clique sobre a instância a ser anexada o disco e clique em "editar". Após isso, sobre o item "discos adicionais" clique em adicionar item e selecione o disco criado anteriormente. 

Uma outra opção é realizar via SDK: `gcloud compute instances attach-disk another-instance --disk disk-lab --zone us-east1-c` 


##Gerenciamento de Chaves SSH

##Cotas

A política de cotas impõe o limite de recursos(projeto) que podem ser utilizados, com o propósito de estabelecer controle sobre as implementações e  garantia de uso não devido. 


 **IAM & Admin > Quotas**
![image.png](/.attachments/image-10889156-c684-4bf4-b29b-4d0c15947110.png)



> https://cloud.google.com/compute/quotas?hl=pt-br

##Realocação de Instância

Para realizar a migração de uma instância "a quente" para outra zona, utilize a operação de `move` para a zona de destino.
Ex: `gcloud compute instances move --zone us-east1-c lab-gce --destination-zone=us-east1-a`

> Esse processo de move aciona uma série de snapshots dos discos, movendo esses discos para uma nova zona e cria a instância. Observe que não são todos os casos que é permitido essa opção de migração. 

Uma outra estratégia é a de armazenar os dicos de uma instância existente e criar uma máqina do zero, a partir dos discos pré-existentes.

##AutoScaling

O primeiro passo para configurar o auto provisionamento é criar um Template que inclua scripts de inicialização e desligamento para automatizar tarefas de instalação de software, logs e entre outros.
Após isso, É criar um grupo de instâncias gerenciadas e configurar o auto provisionamento juntamente com suas políticas.

1. Crie o Modelo de Instâncias:

`gcloud compute instance-templates create app-lab \
--machine-type f1-micro \ ## Use gcloud compute machine-types list 
--region us-east1 \ ## Use gcloud compute regions list
--tags pagadoria-server 
--metadata-from-file startup-script=./startup-script-pagadoria-v1.sh
`
> Neste caso estamos criando um modelo que  irá criar instâncias em várias zonas da região us-east1, se atente que ao criar instâncias em zonas diferentes que precisam de comunicação entre si, é realizado a cobrança de tráfego de rede para qualquer tráfego de saída.

2. Crie os Grupos Gerenciados:

`gcloud compute instance-groupos managed create application-lab --template app-lab --size 4 --region us-east1 `
> Isso faz com que quatro instâncias sejam criadas, a partir do modelo que foi definido anteriormente. 

3. Configure a Política de AutoScaling:

`gcloud compute instances-groups managed set-autoscaling application-lab --max-num-replicas 5 --target-cpu-utilization 0.75 --cool-down-period 90`

> No comando acima, estamos criando uma política de AutoScaling baseado no Consumo de CPU de cada máquina. Para esse caso, foi utilizado como base o número máximo de 5 máquinas e utilização acima de 75%.

![scale-in.png](/.attachments/scale-in-78d071f0-a288-4322-a50f-e02adf24f238.png)


##AutoHealing


##StackDriver

O Google Stackdriver oferece funcionalidades de monitoramento, geração de registros e diagnóstico. Ele proporciona insights sobre a integridade, o desempenho e a disponibilidade de aplicativos com tecnologia de nuvem, agilizando a detecção e correção de problemas.

> https://cloud.google.com/monitoring/agent/install-agent?hl=pt-br












