# Documentação: Introdução ao Amazon EC2

## Índice

- Documentação: Introdução ao Amazon EC2
- Visão Geral
- Tópicos Abordados
- Tarefa 1: Iniciar sua instância do EC2
- Tarefa 2: Monitorar a instância
- Tarefa 3: Atualizar grupo de segurança e acessar servidor web
- Tarefa 4: Redimensionar a instância
- Tarefa 5: Testar a proteção contra encerramento
- Laboratório Concluído

# Visão geral:

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

<img width="1898" height="528" alt="image" src="https://github.com/user-attachments/assets/23589965-2204-4135-a938-5f353b90954f" />

Instalará um servidor web Apache (httpd).

Configurará o servidor web para ser iniciado automaticamente na inicialização.

Ativará o servidor web.

Criará uma página da web simples.

Etapa 8: Iniciar uma instância do EC2
Agora que você configurou sua instância do EC2, é hora de iniciá-la.

No painel direito, selecione Executar instância

Selecione Visualizar todas as instâncias

A instância aparece em um estado Pendente, o que significa que ela está sendo iniciada. Depois, o estado muda para Em execução, o que indica que a instância começou sua inicialização. Depois de um curto período, você poderá acessá-la.

A instância recebe um nome DNS público, que você pode usar para contatar a instância pela Internet.

Marque a caixa  ao lado do seu Web Server. A guia Details (Detalhes) exibe informações detalhadas sobre sua instância.

 Para visualizar mais informações na guia Details (Detalhes), arraste o divisor da janela para cima.

Analise as informações exibidas nas guias Details, Security (Detalhes, Segurança) e Networking (Rede).

Aguarde até que a instância exiba:

Observação: Atualize se necessário.

Estado da instância:  Em execução

Verificações de status:   2/2 verificações aprovadas

<img width="1603" height="216" alt="image" src="https://github.com/user-attachments/assets/e42a27a8-4572-44f6-8949-629493c08a34" />

Tarefa 2: Monitorar a instância
O monitoramento é uma parte importante da manutenção da confiabilidade, disponibilidade e do desempenho das instâncias do Amazon Elastic Compute Cloud (Amazon EC2) e das soluções da AWS.

Selecione a instância marcando a caixa de seleção ao lado da instância e navegue até o final da tela para a guia Status checks (Verificações de status).

 Com o monitoramento de status de instâncias, você pode determinar rapidamente se o Amazon EC2 detectou problemas que podem impedir suas instâncias de executar aplicações. O Amazon EC2 realiza verificações automáticas em cada instância do EC2 em execução para identificar problemas de hardware e software.

Observe que as verificações System reachability (Acessibilidade do sistema) e Instance reachability (Acessibilidade de instâncias) foram aprovadas.

Selecione a guia Monitoring (Monitoramento).

Essa guia exibe as métricas do Amazon CloudWatch para sua instância. Atualmente não há muitas métricas a serem exibidas, porque a instância foi iniciada recentemente.

Você pode selecionar um grafo para ver uma visualização expandida.

 O Amazon EC2 envia métricas ao Amazon CloudWatch referentes às suas instâncias do EC2. Por padrão, o monitoramento básico (cinco minutos) está ativado. Você pode ativar o monitoramento detalhado (um minuto).

No menu Ações , selecione Monitorar e solucionar problemas . Get Instance Screenshot (Obter captura de tela da instância).

Isso mostra como seria seu console de instância Amazon EC2 se uma tela estivesse associada a ele.

<img width="1905" height="727" alt="image" src="https://github.com/user-attachments/assets/d4d69c90-5f61-4bfe-aecc-014ca702de70" />

<img width="1032" height="951" alt="image" src="https://github.com/user-attachments/assets/f3084d91-85cb-40ba-83f2-ab347b25948a" />

Selecione a opção Cancelar localizada na parte inferior da captura de tela da instância.

 Parabéns! Você explorou várias maneiras de monitorar sua instância.

Tarefa 3: atualizar o grupo de segurança e acessar o servidor web
Ao iniciar a instância do EC2, você forneceu um script que instalou um servidor web e criou uma página da web simples. Nesta tarefa, você acessará o conteúdo do servidor web.

Selecione a instância marcando a caixa e selecione a guia Details (Detalhes).

Copie o código no campo Public IPv4 address (Endereço IPv4 público) da instância para a área de transferência.

Abra uma nova guia no navegador da web, cole o endereço IP que você acabou de copiar e pressione Enter.

Pergunta: Você consegue acessar seu servidor web? Por que não?

Você não consegue acessar seu servidor web neste momento porque o grupo de segurança não está permitindo o tráfego de entrada na porta 80, que é usada para solicitações da web HTTP. Esta é uma demonstração do uso de um grupo de segurança como firewall para restringir o tráfego de rede permitido para dentro e para fora de uma instância.

Para corrigir isso, agora você atualizará o grupo de segurança para permitir o tráfego na web na porta 80.

Mantenha a guia do navegador aberta, mas volte para a guia EC2 Management Console (Console de gerenciamento do EC2).

No painel de navegação à esquerda, selecione Security Groups (Grupos de segurança) na seção Network & Security (Rede e segurança).

Selecione  Web Server security group (Grupo de segurança do servidor Web).

<img width="1917" height="703" alt="image" src="https://github.com/user-attachments/assets/6cd6e2b4-ecf7-46d2-8291-be828f5ed476" />

Selecione a guia Inbound rules (Regras de entrada).

No momento, o grupo de segurança não tem regras.

Selecione Editar regras de entrada, depois, selecione Adicionar regra e defina a regra com as seguintes configurações:

Tipo: HTTP

Origem: IPv4 em qualquer lugar

Clique em Salvar regras.

Volte para a guia do servidor web que você abriu anteriormente e atualize  a página.

Você deve ver a mensagem Hello From Your Web Server! (Olá do seu servidor web!)

 Parabéns! Você modificou com êxito o grupo de segurança para permitir tráfego HTTP de entrada em sua instância do Amazon EC2.

<img width="1917" height="961" alt="image" src="https://github.com/user-attachments/assets/18b761ca-8921-47e1-acda-594be2ad2654" />

Tarefa 4: redimensionar a instância: tipo de instância e volume do EBS
Conforme suas necessidades mudam, você pode observar que sua instância está superutilizada (muito pequena) ou subutilizada (muito grande). Se isso ocorrer, você poderá alterar o tipo de instância. Por exemplo, se uma instância t3.micro for muito pequena para seu workload, você poderá alterá-la para uma instância m5.medium. Da mesma forma, também poderá alterar o tamanho de um disco.

Interromper a instância
Antes de redimensionar uma instância, você deve interrompê-la.

 Quando você interrompe uma instância, ela é desligada. Não há cobrança para uma instância do EC2 interrompida, mas a cobrança de armazenamento para volumes do Amazon EBS conectados é mantida.

No EC2 Management Console (Console de gerenciamento do EC2), no painel de navegação esquerdo, selecione Instances (Instâncias).

 O servidor web já deve estar selecionado.

Selecione Estado da instância > Interromper instância.

Selecione Interromper.

A instância fará um desligamento normal e, depois, interromperá a execução.

Aguarde até que o campo Instance State (Estado da instância) exiba Stopped (Interrompida).

<img width="1606" height="270" alt="image" src="https://github.com/user-attachments/assets/2a54940b-d77c-4058-8ca2-6a7ff6aaffcf" />

Alterar o tipo de instância
No menu Ações , selecione Configurações de instância  Alterar tipo de instância e configure:

<img width="1897" height="506" alt="image" src="https://github.com/user-attachments/assets/32f70f94-9da6-4166-ba24-996bf7021aba" />

Tipo de instância: t3.small

Selecione Alterar tipo de instância.

Quando a instância for iniciada novamente, ela será do tipo t3.small, que tem o dobro de memória de uma instância t3.micro. OBSERVAÇÃO: talvez você não possa usar outros tipos de instância neste laboratório.

<img width="1910" height="470" alt="image" src="https://github.com/user-attachments/assets/a83f7e9f-f6d0-4c53-a5c9-7282ae29445e" />

Redimensionar o volume do EBS
No menu de navegação à esquerda, selecione Volumes localizado em Elastic Block Store.

Selecione o volume marcando a caixa, navegue até o menu Ações  e selecione Modificar volume.

<img width="1912" height="521" alt="image" src="https://github.com/user-attachments/assets/8a2ca270-2771-4042-9a23-051b993978a8" />

Atualmente, o volume do disco é de 8 GiB. Agora, você aumentará o tamanho desse disco.

Altere o tamanho para: 10 OBSERVAÇÃO: a criação de grandes volumes do Amazon EBS pode estar restrita neste laboratório.

Selecione Modificar.

Selecione Modificar para confirmar e aumentar o tamanho do volume.

<img width="1911" height="775" alt="image" src="https://github.com/user-attachments/assets/3bf6248b-44ee-4108-8cef-09ef41db7fbd" />

Iniciar a instância redimensionada
Neste momento, você iniciará a instância novamente, agora com mais memória e mais espaço em disco.

No painel de navegação à esquerda, selecione Instâncias.

Marque a caixa de seleção da instância Web Server e, depois, navegue até Estado da instância > Iniciar instâncias.

Parabéns! Você redimensionou a instância do Amazon EC2. Nesta tarefa, você alterou o tipo de instância de t3.micro para t3.small. Você também modificou o volume do disco-raiz de 8 GiB para 10 GiB.

Tarefa 5: testar a proteção contra encerramento
Você pode excluir sua instância quando não precisar mais dela. Esse procedimento é chamado de encerramento da instância. Não é possível se conectar nem reiniciar uma instância depois que ela foi terminada.

Nesta tarefa, você aprenderá a usar a proteção contra encerramento.

No painel de navegação à esquerda, selecione Instâncias.

Marque a caixa de seleção da instância Web Server, navegue até a parte superior, clique no menu Estado da instância e selecione  Encerrar (excluir) instância.

Observação: a mensagem On an EBS-backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated (Em uma instância baseada no EBS, a ação padrão é o volume raiz do EBS ser excluído quando a instância é terminada). Storage on any local drives will be lost (O armazenamento não será mantido em nenhuma unidade local). será exibida e você deverá confirmar se tem certeza se deseja terminar a instância. Você poderá clicar no botão Encerrar.

Observação: você notará que a instância não foi terminada e uma mensagem de erro vermelha é exibida na parte superior que diz: Falha ao terminar uma instância: talvez a instância não tenha sido terminada. O motivo é porque ela tem a proteção contra encerramento ativada.

No menu Ações , selecione Configurações de instância  Change termination protection (Alterar proteção contra encerramento).

<img width="1593" height="437" alt="image" src="https://github.com/user-attachments/assets/0a29c539-2c28-4e0b-8598-be700baa005c" />

Desmarque  Enable (Ativar) e clique em Save (Salvar)

<img width="860" height="347" alt="image" src="https://github.com/user-attachments/assets/474a4f2d-0d19-4424-9c53-403af587f84a" />

Agora você pode terminar a instância.

No menu Ações, selecione Estado da instância  Terminate instance (Terminar instância).

Selecione Encerrar

 Parabéns! Você testou com êxito a proteção contra encerramento e terminou sua instância.

Laboratório concluído 

Escolha  End Lab (Encerrar laboratório) na parte superior desta página e, em seguida, selecione Yes (Sim) para confirmar que você deseja encerrar o laboratório.

Um painel indica DELETE has been initiated... You may close this message box now. (EXCLUSÃO iniciada... Agora você pode fechar esta caixa de mensagem).

A mensagem Ended AWS Lab Successfully (Encerramento bem-sucedido do laboratório da AWS) é exibida brevemente, indicando que o laboratório foi encerrado.

 



 















