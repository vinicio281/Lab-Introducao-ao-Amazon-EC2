Documentação: Introdução ao Amazon EC2

Visão geral:

<img width="481" height="397" alt="image" src="https://github.com/user-attachments/assets/ecc431c7-d3ea-4907-aecc-6233c3a13bc0" />

Este laboratório apresenta uma visão geral básica de como executar, redimensionar, gerenciar e monitorar uma instância do Amazon EC2.

O Amazon Elastic Compute Cloud (Amazon EC2) é um serviço da web que fornece capacidade computacional redimensionável na nuvem. Ele foi projetado para facilitar a computação em nuvem na escala da web para os desenvolvedores.

A interface de serviço da web simples do Amazon EC2 permite que você obtenha e configure capacidade com o mínimo de esforço. Ela oferece um controle completo de seus recursos de computação e permite a execução no ambiente de computação comprovado da Amazon. O Amazon EC2 reduz o tempo necessário para obter e inicializar novas instâncias do servidor em minutos, permitindo o rápido escalonamento da capacidade para mais ou para menos, de acordo com a evolução dos requisitos de computação.

Tópicos abordados
Ao final deste laboratório, você será capaz de:

Iniciar um servidor web com proteção contra encerramento ativada

Monitorar sua instância do EC2

Modificar o grupo de segurança que seu servidor web está usando para permitir acesso HTTP

Redimensionar sua instância do Amazon EC2 de acordo com a necessidade

Testar a proteção contra encerramento

Terminar a instância do EC2

Duração
Este laboratório levará aproximadamente 45 minutos para ser concluído.

Tarefa 1: Iniciar sua instância do EC2
Nesta tarefa, você iniciará uma instância do Amazon EC2 com proteção contra encerramento. A proteção contra encerramento impede que você encerre acidentalmente uma instância do EC2. Você implantará sua instância com um script de dados do usuário que permitirá implantar um servidor web simples.

No Console de Gerenciamento da AWS, no menu Serviços, selecione EC2.

No painel de navegação da esquerda, selecione Painel do EC2 para garantir que você esteja na página do painel.

Clique em Executar instância e selecione Executar instância.

<img width="1891" height="1031" alt="image" src="https://github.com/user-attachments/assets/dd535471-9f2d-489e-93f7-2973027ddfb4" />
<img width="1897" height="960" alt="image" src="https://github.com/user-attachments/assets/b6ab082c-b214-4fcf-8994-bb9483b0b8d1" />


Etapa 1: Nomear sua instância do EC2
Quando você nomear sua instância, a AWS criará um par de chave-valor. A chave desse par é Nome, e o valor é o nome que você inseriu para sua instância do EC2.

No painel Name and tags (Nome e tags), na caixa de texto Name (Nome), digite Web Server.

<img width="1907" height="356" alt="image" src="https://github.com/user-attachments/assets/af0fe77a-3103-411c-babc-fc608d206565" />

Etapa 2: Selecionar uma imagem de máquina da Amazon (AMI)
Uma AMI fornece as informações necessárias para iniciar uma instância, que é um servidor virtual na nuvem. Uma AMI inclui o seguinte:

Um modelo para o volume-raiz da instância (por exemplo, um sistema operacional ou um servidor de aplicações com aplicações)

Permissões de execução que controlam quais contas da AWS podem usar a AMI para iniciar instâncias

Um mapeamento de dispositivos de blocos que especifica quais volumes devem ser anexados à instância quando ela for iniciada

O menu Quick Start (Início rápido) contém as AMIs mais usadas. Você também pode criar sua própria AMI ou selecionar uma AMI no AWS Marketplace, um armazenamento on-line no qual você pode vender ou comprar software executado na AWS.

Localize o painel Selecione uma imagem da aplicação ou do sistema operacional (Imagem de máquina da Amazon).

Em Imagem de máquina da Amazon (AMI), observe que a imagem Amazon Linux 2023* está selecionada por padrão. Mantenha essa configuração.

<img width="1907" height="971" alt="image" src="https://github.com/user-attachments/assets/cbc35e2f-e44b-4550-8029-1d89335cc663" />

Etapa 3: Selecionar um tipo de instância
O Amazon EC2 fornece uma ampla seleção de tipos de instância otimizados para se adequarem a diferentes casos de uso. Os tipos de instâncias consistem em várias combinações de CPU, memória, armazenamento e capacidade de redes, oferecendo flexibilidade de escolha da composição adequada de recursos para as suas aplicações. Cada tipo de instância inclui um ou mais tamanhos de instância para que você possa escalar seus recursos para os requisitos do workload de destino.

Selecione uma instância t3.micro. Esse tipo de instância tem duas CPUs virtuais e 1 GiB de memória.

No menu suspenso, selecione t3.micro.

OBSERVAÇÃO: talvez você não possa usar outros tipos de instância neste laboratório.

<img width="1915" height="318" alt="image" src="https://github.com/user-attachments/assets/7cc815c7-1b41-4902-9207-0a823d9ac184" />

Etapa 4: Configurar um par de chaves
O Amazon EC2 usa criptografia de chave pública para criptografar e descriptografar as informações de login. Para fazer login em sua instância, você deve criar um par de chaves, especificar o nome dele ao iniciar a instância e inserir a chave privada ao se conectar à instância.

Neste laboratório, você não fará login em sua instância e, portanto, não precisará de um par de chaves.

Em Key pair (login) (Nome do par de chaves [login]), selecione Proceed without a key pair (Not recommended) (Prosseguir sem um par de chaves [não recomendado]).

<img width="1912" height="250" alt="image" src="https://github.com/user-attachments/assets/ae31886f-8935-41e7-b9e7-90f2c3b299a4" />

Etapa 5: Definir as configurações de rede
Você usará esse painel para definir as configurações de rede.

A VPC indica em qual nuvem privada virtual (VPC) você deseja iniciar a instância. Você pode ter várias VPCs, como VPCs diferentes para desenvolvimento, teste e produção.

No painel Configurações de rede, selecione Editar.

Em VPC- required (VPC: obrigatório), selecione Lab VPC (VPC do laboratório).

Ainda no painel Network settings (Configurações de rede), configure o grupo de segurança da seguinte forma:

Nome do grupo de segurança: obrigatório: Web Server security group

Descrição: Security group for my web server

Um grupo de segurança atua como um firewall virtual que controla o tráfego para uma ou mais instâncias. Ao iniciar uma instância, você pode associar um ou mais grupos de segurança a ela. Você adiciona regras a cada grupo de segurança que permitem o tráfego de entrada ou de saída das instâncias correspondentes. É possível modificar as regras de um grupo de segurança a qualquer momento. As novas regras são aplicadas automaticamente a todas as instâncias associadas ao grupo de segurança.

Em Regras do grupo de segurança de entrada, selecione Remover.

Neste laboratório, você não fará login na instância usando o acesso SSH, já que a remoção desse acesso reforçará a segurança da instância.

<img width="1911" height="837" alt="image" src="https://github.com/user-attachments/assets/910f4cf6-c487-48c1-975f-523296a744b4" />

<img width="1918" height="482" alt="image" src="https://github.com/user-attachments/assets/932d18d3-3fcc-4344-a565-182bf70f73b0" />

Etapa 6: Adicionar armazenamento
O Amazon EC2 armazena dados em um disco virtual anexado à rede chamado Amazon Elastic Block Store (Amazon EBS).

Você iniciará a instância do EC2 usando um volume de disco padrão de 8 GiB. Esse é seu volume-raiz (também conhecido como volume de inicialização).

No painel Configure storage (Configurar armazenamento), mantenha a configuração padrão de armazenamento.

<img width="1911" height="402" alt="image" src="https://github.com/user-attachments/assets/dc3b3757-7f44-460c-a2c4-6812925588e1" />

Etapa 7: Configurar detalhes avançados
Expanda o painel Advanced details (Detalhes avançados).

Selecione o menu suspenso para Termination protection (Proteção contra encerramento) e, depois, selecione Enable (Habilitar).

<img width="1917" height="91" alt="image" src="https://github.com/user-attachments/assets/1fe1d506-8c49-4be7-8748-b27feb671d31" />


Ao iniciar uma instância no Amazon EC2, você tem a opção de passar dados do usuário para a instância. Esses comandos podem ser usados para executar tarefas de configuração automatizadas comuns, e podem até executar scripts após o início da instância.

Copie os comandos a seguir e cole-os no campo User data (Dados do usuário).

#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
O script fará o seguinte:

Instalará um servidor web Apache (httpd).

Configurará o servidor web para ser iniciado automaticamente na inicialização.

Ativará o servidor web.

Criará uma página da web simples.










