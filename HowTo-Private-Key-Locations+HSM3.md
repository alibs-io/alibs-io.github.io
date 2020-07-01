---
layout: post
title:  "Welcome "
date:   2020-07-02 15:49:15 -0300
categories: jekyll update
---

# Configure HSM - nShield Connect

## Encontrar o site do Produto

1. **Abrir link da Broadcom**
<br/>
**Configure the nShield Connect**
https://techdocs.broadcom.com/content/broadcom/techdocs/us/en/ca-enterprise-software/layer7-api-management/api-gateway/9-4/install-configure-upgrade/configure-the-appliance-gateway/configure-hardware-security-modules-hsm/configure-thales-hardware-security-modules/configure-the-nshield-connect.html
<br/>

1. **Copiar o nome do produto**
<br/>
![image Info](http://localhost:9991/img0000002-nShield-Family-Broadcom-Reference.png "Image Description")
<br/>

1. **Pesquisar no Google**
<br/>
![image Info](http://localhost:9991/img0000001-nShield-Family-Google-Search.png "Image Description")
<br/>

1. **Abrir link do produto**
<br/>
    ### nShield Connect Product Site
    https://www.ncipher.com/products/general-purpose-hsms

![image Info](http://localhost:9991/img0000003-nShield-Family-Product-Site.png "Image Description")




****







<br/>
<br/>
<br/>
<br/>

# Before You Begin

1. Ensure that the following pre-conditions exist before configuring the nShield Connect. 
<br/>
    1.  <font color='red'><b>The Gateway appliance must not have an internal HSM. You cannot connect an nShield Connect appliance to a Gateway appliance that already uses an internal HSM.
        1. Como validar ?</b></font>
    <br/>


    1. Verificar a versão do ssg-nshieldpci
        ```
        rpm -qa | grep ssg-nshieldpci
        ``` 

    1. Verificar se usuários layer7 e gateway estão no grupo nfast
        ```
        egrep -i "^nfast" /etc/group
        ```
        ==>> nfast: x:504:gateway,layer7
        <br/>

    1. Se algun dos usuários não estiver no grupo
        ```
        usermod -g layer7 -G 'layer7,nfast' layer7
        usermod -g gateway -G 'gateway,pkcs11,nfast' gateway
        ```

    1. <font color='red'><b>Three nShield Administrator cards must be available. 
        1. Como validar ?</b></font>
    <br/>

    1. <font color='red'><b>The nShield Connect appliance is running. 
        1. Como validar ?</b></font>
    <br/>




****

1. Foram execudos procedimento no HSM no DataCenter
==>> incluir IPs das máquinas novas
==>> outras configurações





<br/>
<br/>
<br/>
<br/>

## Procedimentos no Gateway

1. Obter (com infra) o IP do HSM
    IP HSM: 172.28.204.138

1. Executar (tipo status)
    ```
    ./opt/nfast/binenquiry
    ```


### 1985 e 1984

1. Executar o comando abaixo
    ```
    ./opt/nfast/binnethsmenroll 172.28.204.140
    ```
    Foi executado com o IP 172.28.204.138 mas não funcionou
yes
OK

1. Elson disse que mudou permissão de alguns arquivos pois deu erro ao subir o gateway após reboot
/opt/nfast/kmdata/
config = 664 e chown nfast:nfast
reboot


****

1. Validar se existe o comando abaixo
    /opt/nfast/java/docs/com/ncipher
    Não foi usado

