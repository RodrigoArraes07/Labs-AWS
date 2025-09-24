# Laboratório de gerenciamento de serviços no Linux 🐧.


## Task 1: Use SSH to connect to an Amazon Linux EC2 instance

Na task 1, vamos realizar a conexão SSH assim como fizemos no laboratório anterior, veja em [Lab2 - Introdução ao Linux](https://github.com/RodrigoArraes07/Labs-AWS/blob/main/Lab2-IntroducaoLinux/README.md).

## Task 2: Check the Status of the httpd Service

Nesta task, vamos iniciar utilizando o comando <code>sudo systemctl status httpd.service</code> para verificar o status do serviço *httpd*. Podemos ver que ele está inativo, então usamos o comando <code>sudo systemctl start httpd.service</code> para ativar o serviço, e em seguida repetimos o comando inicial para verificar se o serviço foi iniciado com sucesso: <br>
![](images/2025-09-17-21-12-39.png)

Se acessarmos o serviço através do navegador web, utilizando *http://id_maquina* podemos visualizar que o serviço está ativo: 
![](images/2025-09-17-21-12-21.png)

Em seguida, utilizamos o comando <code>sudo systemctl stop httpd.service</code> para estopar o serviço e depois utilizamos <code>sudo systemctl status httpd.service</code> para verificar se ele foi realmente estopado: <br>
![](images/2025-09-17-21-13-47.png)

## Task 3: Monitoring a Linux EC2 instance

Agora na task 3, iremos realizar o monitoramento da instância, tanto através do terminal, quanto através dos recursos da própria AWS. Iniciamos utilizando o comando <code>./stress.sh & top</code>, onde executamos um arquivo de estresse *.sh* em segundo plano na máquina, e em seguida o <code>top</code> será executado em primeiro plano, onde poderemos acompanhar o estado da máquina trabalhando com o arquivo de estresse: <br>
![](images/2025-09-17-21-14-50.png)

Após isso, no painel da AWS, podemos utilizar o serviço **AWS CloudWatch** para realizar o monitoramento da máquina, porém de forma gráfica. No primeiro gráfico, podemos visualizar o pico de utilização da CPU durante a execução do arquivo de estresse, chegando a cerca de 95% de uso da CPU da instância, também podemos ver o uso de NetworkIn e diversos outros tópicos de monitoramento: <br>
![](images/2025-09-17-21-32-38.png)

*O **AWS CloudWatch** é um serviço de extrema importância da AWS, pois é principalmente através dele que podemos monitorar o funcionamento da nossa instância e visualizar aumentos e diminuições de demandas, garantindo o pleno funcionamento do servidor e a redução de custos para o cliente.
