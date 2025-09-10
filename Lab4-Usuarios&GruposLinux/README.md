## Laboratório de introdução aos usuários e grupos no Linux 🐧💻



## Task 1: Use SSH to connect to an Amazon Linux EC2 instance

Na task 1, vamos realizar a conexão SSH assim como fizemos no laboratório anterior, veja em [Lab2 - Introdução ao Linux](https://github.com/RodrigoArraes07/Labs-AWS/blob/main/Lab2-IntroducaoLinux/README.md).

Conexão realizada: <br>
![](images/2025-09-09-16-25-12.png)

## Task 2: Create Users

### Comandos novos que utilizaremos nesta task:

- <code>pwd</code>: Abreviação para *Print Working Directory*: Exibe o caminho para o diretório que estamos atualmente. <br>
- <code>sudo useradd nome_usuario</code>: Adiciona um novo usuário ao sistema. <br>
- <code>sudo passwd nome_usuario</code>: Cria ou altera a senha do usuário informado. <br>
- <code>sudo cat /etc/passwd | cut -d: -f1</code>: Exibe o conteúdo presente no arquivo *"/etc/passwd"*, e filtra para exibir apenas os elementos da primeira coluna de texto, que é o nome dos usuários.

Iniciamos com o comando <code>pwd</code>, em seguida criamos um usuário e definimos uma senha para este usuário, com os comandos <code>sudo useradd nome_usuario</code> e  <code>sudo passwd nome_usuario</code> respectivamente: <br>
![](images/2025-09-09-16-43-53.png) <br>
![](images/2025-09-09-16-44-14.png)

Em seguida, repetimos todo esse processo para os seguintes usuários: <br>
![](images/2025-09-09-16-56-00.png) <br>
Definindo suas respectivas senhas.

E após adiciona-los, podemos usar o comando <code>sudo cat /etc/passwd | cut -d: -f1</code> para confirmar a adição: <br>
![](images/2025-09-09-16-57-27.png)

## Task 3: Create Groups

### Comandos novos que utilizaremos nesta task:

- <code>sudo groupadd nome_grupo</code>: Adiciona um novo grupo ao sistema. <br>
- <code>cat /etc/group</code>: Exibe os grupos presentes no arquivo */etc/group*.
- <code>sudo usermod -a -G nome_grupo nome_usuario</code>: Adiciona o usuário ao grupo especificado. <br>

Primeiro criamos os grupos com o comando <code>sudo groupadd nome_grupo</code>: <br>
![](images/2025-09-09-17-05-49.png) <br>
Depois, com o comando <code>cat /etc/group</code>, vamos verificar se os grupos foram criados corretamente: <br>
![](images/2025-09-09-17-06-20.png)

Agora vamos utilizar o comando <code>sudo usermod -a -G nome_grupo nome_usuario</code> para adicionar os usuários aos respectivos grupos, solicitados pela atividade na tabela mostrada anteriormente: <br>
![](images/2025-09-09-17-14-57.png)

Depois, com o comando <code>cat /etc/group</code>, vamos verificar se os usuários foram adicionados aos grupos de forma correta: <br>
![](images/2025-09-09-17-15-11.png)


## Task 4: Log in using the new users

### Comandos novos que utilizaremos nesta task:

- <code>su nome_usuario</code>: Troca para o usuário especificado;
- <code>touch myFile.txt</code>: Cria um arquivo vazio chamado myFile.txt, caso ele já exista, vai atualizar a data e hora da última modificação;
- <code>sudo touch myFile.txt</code>: Faz a mesma coisa do comando anterior, porém, tentando utilizar a permissão de administrador para executar o comando;
- <code>exit</code>: Sai da seção atual, nesse caso, encerra o <code>su</code>;
- <code>sudo cat /var/log/secure</code>: Exibe o conteúdo do arquivo */var/log/secure*, esse arquivo é um **log** de registros de segurança, guarda tentativas de login, usos de <code>sudo</code> e autenticações.

Trocamos para o usuário *arosalez* utilizando o comando <code>su arosalez</code>: <br>
![](images/2025-09-09-17-18-07.png) <br>
Quando utilizamos o comando <code>touch myFile.txt</code>, o sistema retorna que não temos permissão para realizar a ação. Em seguida, tentamos utilizar o comando sudo, porém o usuário *arosalez* não faz parte da lista de Administradores. Portanto não pode usar *sudo*: <br>
![](images/2025-09-09-17-22-30.png) <br>
Aqui, após executar o comando <code>sudo cat /var/log/secure</code>, podemos ver o log que informa as ações "de risco" que tentamos realizar com o usuário *arosalez*: <br>
![](images/2025-09-09-17-21-51.png)


## Conclusão:

<h3>
Neste laboratório, pude conhecer e praticar comandos básicos para o controle de usuários e grupos no Linux, conhecimento que é de suma inportância no meio de trabalho. De forma resumida, neste laboratório aprendi: 
</h3>

- Criar novos usuários e novos grupos; <br>
- Definir senhas para usuários; <br>
- Adicionar usuários a grupos específicos; <br>
- Visualizar as informações de usuários e de grupos; <br>
- Trocar de usuário; <br>
- Vizualizar logs de segurança. <br>