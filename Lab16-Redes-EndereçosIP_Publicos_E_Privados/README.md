# Laboratório de endereços IPs públicos e privados -  Redes🌐📡

<h3>Este laboratório simula uma situação de suporte a um cliente que encontrou problemas com conectividade de instâncias EC2</h3>

## Task 1: Investigate the customer's environment
Aqui podemos ver o email que recebemos do cliente, informando o que estava acontecendo, tentando tirar uma dúvida e anexando a estrutura da VPC.
![](images/2025-10-01-20-40-13.png)

Ao acessarmos o painel AWS do cliente, e: <br>
1. Acessar o serviço **EC2**; <br>
2.  Acessar **Instâncias** na barra lateral; <br>
3.  Marcar *Instância A*; <br>
![](images/2025-10-01-20-34-50.png) <br>
Se analisarmos o retângulo vermelho, a *Instância A* não contém um IP público, apenas o privado, essa informação vai ser importante para solucionarmos o problema. <br>

Se marcarmos a *Instância B*, podemos analisar que ela contém endereço IP público. <br>
![](images/2025-10-01-20-35-33.png)


## Task 2: Send the Response to the customer

 
<blockquote>
Olá, Jess! <br>
<br>
Após analisar a situação das suas instâncias EC2, pude constatar o problema: A Instância A não contém endereço IP público, e por isso ela não pode ter acesso à internet e também não pode ser acessada via SSH. Por conter apenas o endereço privado, esta instância é capaz de se comunicar apenas dentro de sua sub-rede. <br>
<br>
Sobre sua dúvida  sobre o intervalo de endereços IP para uma VPC, você não pode usar o intervalo de IP público <code>12.0.0.0/16</code> pois ele já é utilizado por outra organização, e seleciona-lo pode dar conflitos de endereçamento IP e fazer com que a VPC trate esses IPs como internos, impossibilitando o acesso à internet. <br>
Sempre use intervalos privados reservados pelo **RFC 1918**, como: <br>
- <code>10.0.0.0/8</code><br>
- <code>172.16.0.0/12</code> <br>
- <code>192.168.0.0/16</code> <br>
<br>

Espero ter ajudado, estou à disposição! <br>
Rodrigo <br>
Suporte de Nuvem.
</blockquote>
