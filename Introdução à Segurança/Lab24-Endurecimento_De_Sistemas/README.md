# Laboratório de endurecimento de sistemas - Segurança 💻🛡🔒

<h3>Neste laboratório vamos utilizar o Patch Manager, recurso do AWS Systems Manager para aplicar patches de atualização em instâncias EC2.</h3>

## Task 1: Patch Linux instances using default baselines

Primeiro iremos acessar o **Systems Manager**, na aba lateral vamos em *Fleet Manager*, aqui podemos ver os nós do nosso sistema: <br>  
![](images/2025-10-15-21-07-01.png)

Selecionamos *Linux-1* e acessamos seus detalhes: <br>
![](images/2025-10-15-21-09-34.png)

Aqui podemos ver detalhes sobre essa instância, como tipo de plataforma, tipo de nó, nome do SO, e outros: <br>
![](images/2025-10-15-21-09-57.png)

Em seguida voltamos à página principal e acessamos **Patch Manager** e acessamos onde a tag 2 aponta: <br>
![](images/2025-10-15-21-10-51.png)

Fazemos a configuração e definimos que ela deve ser aplicada ao grupo *LinuxProd*: <br>
![](images/2025-10-15-21-15-52.png)

Em seguida criamos e aplicamos o patch: <br>
![](images/2025-10-15-21-16-49.png)

E agora podemos ver que ele foi aplicado às 3 instâncias Linux que nós temos: <br>
![](images/2025-10-15-21-23-43.png)



## Task 2: Create a custom patch baseline for Windows instances

Agora vamos criar uma linha de base de patches de atualização para as instâncias com Windows. Seguimos o caminho indicado na imagem: <br>
![](images/2025-10-15-21-25-50.png)

Realizamos a configuração da Patch Baseline, definindo nome, Sistema Operacional, definindo regras de SO...: <br>
![](images/2025-10-15-21-30-02.png)

Aqui criamos outra regra: <br>
![](images/2025-10-15-21-30-11.png)
<br> E em seguida criamos a Patch Baseline.


Agora selecionamos a *"PB"* que acabamos de criar, e vamos em **Modify Patch Groups**: <br>
![](images/2025-10-15-21-33-10.png)

Agora adicionamos o grupo *"WindowsProd"* para que o Patch seja aplicado às instâncias desse grupo: <br>
![](images/2025-10-15-21-33-43.png)


## Task 3: Patching the Windows instances
Nesta task vamos aplicar os patches às instâncias com base nas tags associadas a elas.

### Task 3.1: Tagging Windows instances

Acessamos o painel de instâncias em EC2, selecionamos uma das instâncias com Windows e vamos em tags, depois em "manage tags": <br>
![](images/2025-10-15-21-35-23.png)

Adicionamos a tag de WindowsProd e repetimos o processo para as três instâncias com Windows: <br>
![](images/2025-10-15-21-37-25.png)



### Task 3.2: Patching Windows instances

Agora, assim como fizemos para as instâncias Linux, faremos para as com SO Windows: <br>
![](images/2025-10-15-21-39-03.png)

E aqui podemos ver os patches sendo aplicados às instâncias: <br>
![](images/2025-10-15-21-54-31.png)






