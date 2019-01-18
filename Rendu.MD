# Rendu TP2 CCNA

## I Creation et installation d'une VM CentOS

### 1-Configuration d'une machine CentOS

a-

````
curl -SL www.google.com
````
cette comande permet de faire une requete HTTP  
on recoit le code HTML de la page lorsque la connexion internet est fonctionnele.  

b-  
Dans la VM on effectue :
```
ping 192.168.127.1
```
si ca fonctionne on recoit : 
```
bytes from 192.168.127.1: icmp_seq=1 tt1=128 time=0.361ms
```
ensuite depuis son PC on fait:
```
ping 192.168.127.10
```
si ca fonctionne on recoit:
```
Réponse de 192.168.127.10 : octets=32 temps<1ms TTL=64
```
c-  
Il faut tout dabord installer net-tools
```
sudo yum install net-tools
```
ensuite on fait:
```
netstat -rn
```
On obtient:

![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/commande.png?raw=true)
  

# II. Notion de ports et SSH  
## A-SSH

La connexion via le port 2222 ne fonctionne pas car elle n'est pas accepté par le firewall.  
Il faut créer une regle qui permet de se connecter via ce port.  

## B-netcat

La communication entre les deux VM (une sur windows et une sur linux) fonctionne avec netcat en acceptant les port d'ecoutes via le firewall.  

![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/200%20IQ.png?raw=true)

# III- Routage statique  
## 1-preparation des hotes  
### Check
Nous cherchons à pinger le pc de l'autre et la manipulations fonctionne : 
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/Communications.png?raw=true)  
*** 
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/communication2.png?raw=true)  
***
Ping de la VM1 vers le PC1:  
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/ping_VM1_PC1.png?raw=true)  
***
Ping de la VM2 vers PC2:  
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/Ping_vm2_pc2.png?raw=true)  
***

Hôte 1 : 
``` 192.168.101.0    255.255.255.0         On-link     192.168.101.1    281  ```
Hote 2 : 
```   192.168.102.0    255.255.255.0         On-link     192.168.102.1 281  ```
***
## 2-Configuration du routage ## 

![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/shema.png?raw=true)  
***
Creation des routes:  
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/OK!.png?raw=true)
***
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/ok.png?raw=true)
***
on arrive a PING depuis la VM1:
Le PC2
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/VM1_PC2.png?raw=true)
La VM2
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/VM1_VM2.png?raw=true)
et vice versa.

## 3-Configuration des noms de domaine.  
Apres la configuration des hostname il est possible de se ping grace aux hostname:  
![](https://github.com/thomasmlc/CCNA-TP2/blob/master/images/VM1_PC2_hostname.png?raw=true)