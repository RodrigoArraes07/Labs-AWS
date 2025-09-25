# Laboratório de introdução ao Amazon EC2 ☁️🖥️



# Task 1: Lauching Your EC2 Instance

Na homepage, buscamos pelo serviço EC2, e em seguida acessamos o EC2 Dashboard:
![Passo 1](images/image-1.png)
Nessa página, clicamos em <code>Launch Instance</code>

## Step 1: Naming your EC2 instance
![Passo 2](images/image-2.png)
Nomeei como _Web Server_

## Step 2: Choosing an Amazon Machine Image (AMI)
![Passo 3](images/image-3.png)
Para este laboratório, vamos manter a AMI padrão.

## Step 3: Choosing an instance type
![Passo 4](images/image-4.png)
<br>O tipo de instância, nós também manteremos como padrão, o **t3.micro**

## Step 4: Configuring a key pair
![Passo 5](images/image-5.png)
<br>Para este laboratório, também não vamos adicionar nenhuma key pair.

## Step 5: Configuring the network settings 
No campo de Network Settings, acessamos <code>Edit</code> :<br>
![Passo 6](images/image-6.png)
Determinamos a *VPC*: **Lab VPC**, e colocamos o nome do *Security Group*:<br>
*Security group name*: **Web server security group**;<br>
*Description*: **Security group for my web server**;<br>

Agora, após adicionar as informações que foram solicitadas, vamos em <code>Remove</code>
![Passo 7](images/image-7.png)


## Step 6: Adding storage
No campo de configuração do armazenamento, mantemos o padrão para este laboratório:
![Passo 8](images/image-8.png)

## Step 7: Configuring advanced details 
Buscamos **"Termination protection"**, e colocamos **Eneble**.
![Passo 9](images/image-9.png)

Em seguida vamos até o final da página e econtramos o campo **"User Data"** e colamos o script solicitado no lab:
![Passo 10](images/image-10.png)
### O script faz o seguinte:<br>
- Instala um servidor web Apache (httpd)<br>
- Configura o servidor web para iniciar automaticamente  na inicialização
- Ativa o servidor Web<br>
- Cria uma página web simples<br>

## Step 8: Launching an EC2 instance
Para inciar a intância, vamos em <code>Lauch Instance</code> em laranja:
![Passo 11](images/image-11.png)

E aguardamos a intância ser iniciada e checada, analisando o campo **"Status check"**
![Passo 12](images/image-12.png)

# Task 2: Monitor Your Instance
![Passo 13](images/image-13.png)
Agora podemos ver em **"Status check"** que a nossa intância não teve problemas em sua execução. E ao selecionarmos a nossa instância, também podemos realizar o monitoramento na aba **"Monitoring"** que exibe métricas do Amazon CloudWatch. 

Em seguida, acessamos <code>Actions -> Monitor and troubleshoot -> Get instance screenshot</code> :
![Passo 14](images/image-14.png)
E podemos ver a intância sendo executada:<br>
![Passo 15](images/image-15.png)

# Task 3: Update Your Security Group and Access the Web Server
Retornando para a página de instâncias, clicamos em **"Intance ID"**, e veremos a seguinte página:
![Passo 16](images/image-16.png)
Então vamos copiar o endereço IPv4 dessa intância, e vamos tentar acessar pelo navegador. Porém nçao vamos conseguir acessar, pois o *Security Group* que criamos não está permitindo trafego de entrada na porta 80, que é utilizada para solicitações HTTP da web.

Então, na barra lateral na esquerda buscamos <code>Network & Security -> Security Groups</code>, e vamos editar nosso *Security Group* para podermos acessar esta página.
![Passo 17](images/image-17.png)

Selecionamos o *Security Group* que criamos anteriomente, vamos em <code>Inbound Rules -> Edit inbound rules</code>
![Passo 18](images/image-18.png)

Selecionamos <code> Add rule</code> e teremos a seguinte tela:
![Passo 19](images/image-19.png)
Nos campos <code>Type</code> e <code>Source</code> e colocamos respectivamente: *HTTP* e *Anywhere-IPv4*. 

E então já podemos acessar a página Web:<br>
![Passo 20](images/image-20.png)

# Task 4: Resize Your Instance: Instance Type and EBS Volume
Para realizar a alteração do  tipo de armazenamento, primeiro precisamos stopar  a instância:
![Passo 21](images/image-21.png)
Lembrando que devemos aguardar que apareça *"Stopped"* em *Instance state* para prosseguir.

Em seguida vamos em <code>Actions -> Instance settings -> Change instance type</code>
![Passo 22](images/image-22.png)

Seremos direcionados para a página abaixo, onde vamos alterar o tipo de *t3.micro* para *t3.small*
![Passo 23](images/image-23.png)
No fim da página, clicamos em <code>Change instance type</code>.

Temos o retorno de que *Instance type* foi alterado com sucesso.
![Passo 24](images/image-24.png)

Em seguida, na barra lateral acessamos <code>Elastic Block Store -> Volumes</code>, em seguida vamos em <code>Actions -> Modify volume</code>.
![Passo 25](images/image-25.png)

Seremos direcionados para esta página, onde eu alterei **"Size(GiB)"** de 8 para 10.
![Passo 26](images/image-26.png)
E em seguida confirmei  alteração em <code>Modify</code>

Aqui em **"Size"** podemor ver o armazenamento já alterado.
![Passo 27](images/image-27.png)

Voltamos para a página das intâncias através da barra lateral <code>Instances -> Instances</code> e vamos startar a instância em <code>Instance state -> Start instance</code>.
![Passo 28](images/image-28.png)
E temos que nossa instância será inicializada com sucesso, e com as alterações de *Instance Type* e *Volume* realizadas.


## Task 5: Test Termination Protection
Com a instância rodando, se formos em <code>Instance state -> Terminate (delete) instance</code>:
![Passo 29](images/image-29.png)

Podemos ver que a instância não pode ser terminada, pois na sua criação, habilitamos o campo **"Termination protection"** em *"Advanced settings"*, que é um recurso de segurança para proteger a instância de um encerramento acidental. 
![Passo 30](images/image-30.png)

Para desativarmos este recurso, e podermos finalizar a instância, acessamos em <code>Actions -> Instance settings -> Change terminate protection</code> e desabilitamos essa função.
![Passo 31](images/image-31.png)

Com a proteção removida, podemos acessar <code>Instance state -> Terminate (delete) instance</code>:
![Passo 32](images/image-32.png)

E então, podemos observar que a intância foi terminada com sucesso.
![Passo 33](images/image-33.png)


## Conclusão:
<h3>
Por fim, neste laboratório, eu pude praticar a criação e configuração de uma instância EC2, entendendo como criar, iniciar, redimensionar, gerenciar e monitorar esta intância. E então, após concluir este laboratório eu aprendi:<br></h3>

- Como inciar um servidor web com proteção de encerramento habilitada;<br>
- Como monitorar uma intância EC2;<br>
- Como modificar o *Security Group* do meu servidor para permitir acesso HTTP;<br>
- Como redimensionar minha instância do Amazon EC2 para escalar;<br>
- Como realizar a proteção de término;<br>
- Como encerrar a intância;<br>
