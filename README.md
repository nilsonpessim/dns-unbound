![TechLabs](https://techlabs.net.br/wp-content/uploads/2021/09/logo_blog.png)

## Servidor DNS Recursivo com Unbound e DNSSEC
* :star_struck: Repositório de Instalação e Configuração do Servidor DNS.
 
## :computer: Requisitos do Sistema
Requisitos mínimos para instalação.
 
* :cd: Sistema Operacional: Ubuntu 18.04 Server
* :heavy_check_mark: Processador: 4 vCPU
* :heavy_check_mark: Memória RAM: 8GB
* :heavy_check_mark: Armazenamento: 50GB
* :heavy_check_mark: NIC: 1GB
* :heavy_check_mark: Endeçamento IP

## Instalação dos Pacotes Necessários
*   apt -y update && apt -y upgrade
*   apt -y install iptraf wget snmp sysstat iotop htop nmon dnsutils sshpass hping3 whois tcpdump traceroute nmap rsync unbound mtr lynx ntpdate

## Configurando os arquivos do Unbound.
*   cd /etc/unbound/
*   rm unbound.conf
*   wget https://raw.githubusercontent.com/nilsonpessim/dns-unbound/main/root.hints
*   wget https://raw.githubusercontent.com/nilsonpessim/dns-unbound/main/unbound.conf
*   chown unbound.unbound /etc/unbound/ -R
*   chmod 644 unbound_server.pem
*   chmod 644 unbound_server.key

## Informe o endereço IP
*	/etc/unbound.conf
*   /etc/resolv.conf

## Habilitando o Serviço do Unbound.
*	systemctl enable unbound
*	systemctl restart unbound
*	systemctl status unbound

## Testando o DNS.
*	dig nic.br

## Implementando o DNSSEC.
*	dig nic.br +dnssec +multi
*	unbound-anchor -a /var/lib/unbound/root.key -v
* 	Descomente a Linha no unbound.conf: #auto-trust-anchor-file: "/etc/unbound/root.key

## Checar as configurações do Unbound
*	unbound-checkconf
*	systemctl restart unbound

## Flags de validação! 
* qr: query - consulta (0) | resposta (1)
* rd: Recursão Desejada
* ra: Recursão Disponível
* ad: Dado Autenticado
* ns/a/ptr

## Referências
[![Vaanmonde](https://avatars.githubusercontent.com/u/21218780?s=48)](https://github.com/vaamonde/ubiquiti-unifi)

## Desenvolvedor :heart_eyes_cat:
[![Github Badge](https://img.shields.io/badge/-Github-000?style=flat-square&logo=Github&logoColor=white&link=https://github.com/nilsonpessim)](https://github.com/nilsonpessim)
[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://br.linkedin.com/in/nilsonpessim)](https://br.linkedin.com/in/nilsonpessim)
[![Whatsapp Badge](https://img.shields.io/badge/-Whatsapp-4CA143?style=flat-square&labelColor=4CA143&logo=whatsapp&logoColor=white&link=https://api.whatsapp.com/send?phone=5537999351046)](https://api.whatsapp.com/send?phone=5537999351046)