## Laboratório de introdução aos usuários e grupos no Linux 🐧💻



## Task 1: Use SSH to connect to an Amazon Linux EC2 instance

Na task 1, vamos realizar a conexão SSH assim como fizemos no laboratório anterior, veja em [Lab2 - Introdução ao Linux](https://github.com/RodrigoArraes07/Labs-AWS/blob/main/Lab2-IntroducaoLinux/README.md).

Conexão realizada: <br>
![](images/2025-09-09-16-25-12.png)

## Task 2: Create Users

### Comandos que utilizaremos nesta task:

<code>pwd</code>: Abreviação para *Print Working Directory*: Exibe o caminho para o diretório que estamos atualmente. <br>
<code>sudo useradd nome_usuario</code>: Adiciona um novo usuário ao sistema. <br>
<code>sudo passwd nome_usuario</code>: Cria ou altera a senha do usuário informado. <br>
<code>sudo cat /etc/passwd | cut -d: -f1</code>: Exibe o conteúdo presente no arquivo *"/etc/passwd"*, e filtra para exibir apenas os elementos da primeira coluna de texto, que é o nome dos usuários.

Iniciamos com o comando <code>pwd</code>, em seguida criamos um usuário e definimos uma senha para este usuário, com os comandos <code>sudo useradd nome_usuario</code> e  <code>sudo passwd nome_usuario</code> respectivamente:
![](images/2025-09-09-16-43-53.png)
![](images/2025-09-09-16-44-14.png)

Em seguida, repetimos todo esse processo para os seguintes usuários:
![](images/2025-09-09-16-56-00.png) <br>
Definindo suas respectivas senhas.

E após adiciona-los, podemos usar o comando <code>sudo cat /etc/passwd | cut -d: -f1</code> para confirmar a adição: <br>
![](images/2025-09-09-16-57-27.png)

## Task 3: Create Groups

![](images/2025-09-09-17-05-49.png)
![](images/2025-09-09-17-06-20.png)


![](images/2025-09-09-17-14-57.png)
![](images/2025-09-09-17-15-11.png)


## Task 4: Log in using the new users

![](images/2025-09-09-17-18-07.png)
![](images/2025-09-09-17-22-30.png)
![](images/2025-09-09-17-21-51.png)