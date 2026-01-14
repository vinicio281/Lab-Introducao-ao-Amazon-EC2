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

## Tópicos abordados
Ao final deste laboratório, você será capaz de:

- Iniciar um servidor web com proteção contra encerramento ativada
- Monitorar sua instância do EC2
- Modificar o grupo de segurança que seu servidor web está usando para permitir acesso HTTP
- Redimensionar sua instância do Amazon EC2 de acordo com a necessidade
- Testar a proteção contra encerramento
- Terminar a instância do EC2

**Duração:** Este laboratório levará aproximadamente 45 minutos para ser concluído.

---

## Tarefa 1: Iniciar sua instância do EC2
Nesta tarefa, você iniciará uma instância do Amazon EC2 com proteção contra encerramento.  
A proteção contra encerramento impede que você encerre acidentalmente uma instância do EC2.  
Você implantará sua instância com um script de dados do usuário que permitirá implantar um servidor web simples.

**Passos:**
1. No Console de Gerenciamento da AWS, no menu Serviços, selecione EC2.
2. No painel de navegação da esquerda, selecione Painel do EC2.
3. Clique em **Executar instância** e selecione **Executar instância**.

### Etapa 1: Nomear sua instância do EC2
- No painel **Name and tags**, na caixa de texto **Name**, digite `Web Server`.

### Etapa 2: Selecionar uma imagem de máquina da Amazon (AMI)
- Uma AMI inclui:
  - Modelo para o volume-raiz da instância (SO ou servidor de aplicações)
  - Permissões de execução
  - Mapeamento de dispositivos de blocos
- Mantenha a configuração padrão: **Amazon Linux 2023**.

### Etapa 3: Selecionar um tipo de instância
- Selecione **t3.micro** (2 CPUs virtuais e 1 GiB de memória).

### Etapa 4: Configurar um par de chaves
- Selecione **Proceed without a key pair (Not recommended)**.

### Etapa 5: Definir as configurações de rede
- VPC: selecione **Lab VPC**.
- Grupo de segurança:
  - Nome: `Web Server security group`
  - Descrição: `Security group for my web server`
  - Remova regras de entrada (sem SSH).

### Etapa 6: Adicionar armazenamento
- Volume padrão: **8 GiB** (Amazon EBS).

### Etapa 7: Configurar detalhes avançados
- Ative **Termination protection**.
- Adicione script de **User data** para:
  - Instalar Apache (httpd)
  - Configurar inicialização automática
  - Criar página web simples

### Etapa 8: Iniciar instância
- Selecione **Executar instância** → **Visualizar todas as instâncias**.
- Aguarde até que:
  - Estado: **Em execução**
  - Verificações de status: **2/2 aprovadas**

---

## Tarefa 2: Monitorar a instância
- Verifique **Status checks** (System reachability e Instance reachability).
- Acesse a guia **Monitoring** para métricas do CloudWatch.
- Use **Get Instance Screenshot** para visualizar console da instância.

---

## Tarefa 3: Atualizar grupo de segurança e acessar servidor web
- Copie o **Public IPv4 address** da instância.
- Abra no navegador → não acessível (porta 80 bloqueada).
- Atualize grupo de segurança:
  - Tipo: HTTP
  - Origem: IPv4 Anywhere
- Atualize navegador → mensagem **Hello From Your Web Server!**

---

## Tarefa 4: Redimensionar a instância
### Interromper instância
- Estado da instância → **Interromper instância**.

### Alterar tipo de instância
- Configurações → **Alterar tipo de instância** → selecione **t3.small**.

### Redimensionar volume do EBS
- Elastic Block Store → Volumes → **Modificar volume** → de 8 GiB para 10 GiB.

### Reiniciar instância
- Estado da instância → **Iniciar instâncias**.

---

## Tarefa 5: Testar a proteção contra encerramento
- Tente encerrar instância → falha (proteção ativada).
- Ações → Configurações de instância → **Change termination protection** → desmarque.
- Agora encerre instância → sucesso.

---

## Laboratório concluído
- Escolha **End Lab** → confirme.
- Mensagem: **Ended AWS Lab Successfully**.


 Parabéns! Você testou com êxito a proteção contra encerramento e terminou sua instância.

Laboratório concluído 

Escolha  End Lab (Encerrar laboratório) na parte superior desta página e, em seguida, selecione Yes (Sim) para confirmar que você deseja encerrar o laboratório.

Um painel indica DELETE has been initiated... You may close this message box now. (EXCLUSÃO iniciada... Agora você pode fechar esta caixa de mensagem).

A mensagem Ended AWS Lab Successfully (Encerramento bem-sucedido do laboratório da AWS) é exibida brevemente, indicando que o laboratório foi encerrado.

 



 















