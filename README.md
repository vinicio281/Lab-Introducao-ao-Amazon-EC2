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


