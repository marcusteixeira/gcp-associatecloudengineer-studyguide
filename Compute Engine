Google Cloud Launcher(MarketPlace)

  É o menu utilizado para configurar aplicações que estão presente no marketplace. Tendo alguns benefícios. Como:

	1. Calcular o custo da aplicação, antes de ela estar rodando. 
	2. Escolher o tipo das máquinas, tamanho do disco. Tudo isso antes do deploy
	3. Modificar configurações, como renomear instâncias e etc..

Tipo de Imagens:
	• Publica: São imagens que são fornecidas por padrão pela Google, dentre elas estão Linux e Windows Server
		○ Linux: CentOS, CoreOS, Debian, RHEL, SUSE, FreeBSD, openSuse
		○ Windows: SRV 2016, SRV 2012, SRV 2008
	• Privadas: Imagens personalizadas, que podem ser criadas ou importadas. 

Sempre que uma instância é criada na GCP, existem algumas funcionalidades que são incluídas por padrão. 

	•  O criador da VM sempre terá privilégios de root
		○ Esse privilégio pode ser compartilhado com outros usuários

Quando uma instância é criada, é preciso especificar algumas opções:
 - Zona
 - Sistema Operacional
 - Tipo de Máquina

Ao criar uma instância no Compute Engine, você pode utilizar os modelos pré-definidos ou realizar modificações. Isso possibilita você especificar quanto de memória, disco e CPU sua instância deve ter. 


Armazenamento

No Compute Engine, são providos os seguintes blocos de armazenamento:
	- Discos Persistentes
		○ Standard - Limite 64 TB
		○ SSD - Limite 64 TB
	- Local SSDs
		○ A diferença para o Local SSD, é que é um disco que é colocado na máquina. Oferecendo uma latência menor e maior performance.
	- Discos de Memória

Number of Cores	Disk Number Limit
Shared Core	16
1 Core	32
2-4 Cores	64
8 or more cores	128
		

As opções de armazenamento, garantem o redimensionamento de disco e a migração sem qualquer down-time.

Rede

As instâncias do GCE, oferecem alguns recursos de rede:

	- Redes padrão e customizdas
	- Regras de Firewall de Entrada/Saída, baseada em IP e tags
	- Balanceamento HTTP Regional
	- Redes globais e multiregionais

Em casos de alto processamento, pode-se colocar uma GPU em uma instância. Isso é muito utilizado para casos de Machine Learning

