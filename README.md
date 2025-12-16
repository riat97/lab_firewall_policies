# Configurando Políticas de Firewall no FortiGate #

<img width="691" height="197" alt="image" src="https://github.com/user-attachments/assets/0dfce2dc-56a6-4546-b848-168cbdf416e7" />
##

### Primeiro Passo ###

1. Criar um endereço de firewall para a sub-rede interna
2. Configurar a política de firewall
3. Verificar a configuração da política de firewall

##

No FortiGate, clique em Policy & Objects > Addresses > Create New:
* Nomeie a rede (Internal Network) e preencha o IP/Netmask: 10.0.1.0/24
* Selecione 'port 3' em Interfaces



<img width="1221" height="585" alt="image" src="https://github.com/user-attachments/assets/e1d9120b-23d7-4126-81a6-def4b700b5ce" />

### Segundo Passo ###

1. Criar um endereço de firewall para a sub-rede interna
2. Configurar a política de firewall
3. Verificar a configuração da política de firewall

Clique em Policy & Objects > Firewall Policy
Nomeie como Internet Access 
Selecione 'Incoming Interface' > port3
Selecione 'Outgoing Interface' > port1

<img width="1032" height="438" alt="image" src="https://github.com/user-attachments/assets/066c917a-b4d6-4d4b-a250-e96e2ffb1dbd" />

## 


 Clique em Source e selecione Internal Network
Destination > all
Service > HTTP, HTTPS e DNS


<img width="647" height="582" alt="image" src="https://github.com/user-attachments/assets/30d61e62-d828-4e59-abce-d8a958964c33" />

##

Esta é uma política de tráfego de saída, e o NAT está ativado:

<img width="413" height="228" alt="image" src="https://github.com/user-attachments/assets/7e5737c6-6218-4176-93f8-912102955057" />

Isso permite que o FortiGate traduza o endereço privado do dispositivo de rede para o endereço IP público da interface port1.

##

Em Logging Options, selecione All sessions:

<img width="577" height="162" alt="image" src="https://github.com/user-attachments/assets/482eb4cd-511c-4407-89ed-b8659b0ffd22" />


##

# Terceiro Passo #

Acesse www.fortinet.com e retorne ao FortiGate:

<img width="1176" height="295" alt="image" src="https://github.com/user-attachments/assets/1e2bcdcb-9108-4976-a031-fc4f32bbce45" />

##
Clique na política criada e escolha Show Matching Logs:



<img width="1179" height="522" alt="image" src="https://github.com/user-attachments/assets/98f997b8-6cb6-4ba5-b80d-cd74afd30854" />


* Os logs de Tráfego de Encaminhamento (Forward Traffic) para todo o tráfego que corresponde a esta política aparecem na tela, verificando que o FortiGate está aplicando a política.

##

Abra o Terminal e use o comando: telnet www.fortinet.com

A conexão falha pois a política não permite telnet

* Retorne ao FortiGate e encontre a aba Implicit:


<img width="824" height="339" alt="image" src="https://github.com/user-attachments/assets/98ac54e1-573f-4953-ba31-8315b92073c6" />

Clique em Implicit Deny > Show Matching Logs

Como o tráfego Telnet não corresponde à política "Internet Access", ele é processado e bloqueado pela política padrão "Implicit Deny".

A configuração da política de firewall foi verificada.

##

## Referências ##

Network Security Expert (NSE) - Fortinet















