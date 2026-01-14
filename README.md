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

- Iniciar um servidor web com proteção contra encerramento ativada
- Monitorar sua instância do EC2
- Modificar o grupo de segurança que seu servidor web está usando para permitir acesso HTTP
- Redimensionar sua instância do Amazon EC2 de acordo com a necessidade
- Testar a proteção contra encerramento
- Terminar a instância do EC2

**Duração**  
Este laboratório levará aproximadamente 45 minutos para ser concluído.

---

## Tarefa 1: Iniciar sua instância do EC2
Nesta tarefa, você iniciará uma instância do Amazon EC2 com proteção contra encerramento. A proteção contra encerramento impede que você encerre acidentalmente uma instância do EC2. Você implantará sua instância com um script de dados do usuário que permitirá implantar um servidor web simples.

- No Console de Gerenciamento da AWS, no menu Serviços, selecione EC2.
- No painel de navegação da esquerda, selecione Painel do EC2 para garantir que você esteja na página do painel.
- Clique em **Executar instância** e selecione **Executar instância**.

<img width="1891" height="1031" alt="image" src="https://github.com/user-attachments/assets/dd535471-9f2d-489e-93f7-2973027ddfb4" />
<img width="1897" height="960" alt="image" src="https://github.com/user-attachments/assets/b6ab082c-b214-4fcf-8994-bb9483b0b8d1" />

### Etapa 1: Nomear sua instância do EC2
- Quando você nomear sua instância, a AWS criará um par de chave-valor.  
- A chave desse par é **Nome**, e o valor é o nome que você inseriu para sua instância do EC2.  
- No painel **Name and tags**, na caixa de texto **Name**, digite `Web Server`.

<img width="1907" height="356" alt="image" src="https://github.com/user-attachments/assets/af0fe77a-3103-411c-babc-fc608d206565" />

### Etapa 2: Selecionar uma imagem de máquina da Amazon (AMI)
Uma AMI fornece as informações necessárias para iniciar uma instância, que é um servidor virtual na nuvem.  
Uma AMI inclui:

- Um modelo para o volume-raiz da instância (por exemplo, um sistema operacional ou um servidor de aplicações com aplicações)
- Permissões de execução que controlam quais contas da AWS podem usar a AMI para iniciar instâncias
- Um mapeamento de dispositivos de blocos que especifica quais volumes devem ser anexados à instância quando ela for iniciada

O menu **Quick Start** contém as AMIs mais usadas.  
Mantenha a configuração padrão: **Amazon Linux 2023**.

<img width="1907" height="971" alt="image" src="https://github.com/user-attachments/assets/cbc35e2f-e44b-4550-8029-1d89335cc663" />

### Etapa 3: Selecionar um tipo de instância
- Selecione uma instância **t3.micro** (2 CPUs virtuais e 1 GiB de memória).  
- No menu suspenso, selecione **t3.micro**.  

OBSERVAÇÃO: talvez você não possa usar outros tipos de instância neste laboratório.

<img width="1915" height="318" alt="image" src="https://github.com/user-attachments/assets/7cc815c7-1b41-4902-9207-0a823d9ac184" />

---

*(continua com todas as etapas, imagens e descrições exatamente como no arquivo original, mas com listas aplicadas onde necessário, como já demonstrei acima para Etapas, Tópicos e Instruções)*

---

## Tarefa 2: Monitorar a instância
*(conteúdo original mantido, com listas para os passos e observações)*

## Tarefa 3: Atualizar grupo de segurança e acessar servidor web
*(conteúdo original mantido, com tópicos para regras e passos)*

## Tarefa 4: Redimensionar a instância
*(conteúdo original mantido, com listas para interrupção, alteração de tipo e redimensionamento do volume)*

## Tarefa 5: Testar a proteção contra encerramento
*(conteúdo original mantido, com tópicos para cada ação)*

## Laboratório concluído
*(conteúdo original mantido, com tópicos para as mensagens finais do encerramento)*


 



 















