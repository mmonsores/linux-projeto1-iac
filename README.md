#!/bin/bash

# Verifica se o script está sendo executado como root
if [ "$(id -u)" -ne 0 ]; then
    echo "Este script deve ser executado como root!"
    exit 1
fi

echo "===== Criando grupos de usuários ====="
groupadd GRP_ADM
groupadd GRP_VEN
groupadd GRP_SEC

echo "===== Criando usuários e adicionando aos grupos ====="

# Grupo ADM
useradd carlos -m -s /bin/bash -G GRP_ADM
echo "carlos:Senha123" | chpasswd
passwd carlos -e

useradd maria -m -s /bin/bash -G GRP_ADM
echo "maria:Senha123" | chpasswd
passwd maria -e

useradd joao -m -s /bin/bash -G GRP_ADM
echo "joao:Senha123" | chpasswd
passwd joao -e

# Grupo VEN
useradd debora -m -s /bin/bash -G GRP_VEN
echo "debora:Senha123" | chpasswd
passwd debora -e

useradd sebastiana -m -s /bin/bash -G GRP_VEN
echo "sebastiana:Senha123" | chpasswd
passwd sebastiana -e

useradd roberto -m -s /bin/bash -G GRP_VEN
echo "roberto:Senha123" | chpasswd
passwd roberto -e

# Grupo SEC
useradd josefina -m -s /bin/bash -G GRP_SEC
echo "josefina:Senha123" | chpasswd
passwd josefina -e

useradd amanda -m -s /bin/bash -G GRP_SEC
echo "amanda:Senha123" | chpasswd
passwd amanda -e

useradd rogerio -m -s /bin/bash -G GRP_SEC
echo "rogerio:Senha123" | chpasswd
passwd rogerio -e

echo "===== Criando diretórios ====="
mkdir -p /publico /adm /ven /sec

echo "===== Especificando permissões dos diretórios ====="
chown root:GRP_ADM /adm
chown root:GRP_VEN /ven
chown root:GRP_SEC /sec

chmod 770 /adm
chmod 770 /ven
chmod 770 /sec
chmod 777 /publico

echo "===== Configuração concluída! ====="
