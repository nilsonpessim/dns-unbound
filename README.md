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

## Habilitando o Serviço do Unbound.
*	systemctl enable unbound
*	systemctl restart unbound
*	systemctl status unbound

## Testando o Serviço.
*	Utilizando a ferramenta dig, vamos testar: dig nic.br @ip-do-servidor  - ns/a/ptr
*	Altere o DNS do Servidor

## Implementando o DNSSEC.
*	unbound-anchor -a /var/lib/unbound/root.key -v

## Checar as configurações do Unbound
*	unbound-checkconf
*	systemctl restart unbound

## Verificando os Resource Records do DNSSEC
*	DNSKEY (Chave pública do domínio) - dig nic.br DNSKEY
*	DS (Ponteiro para a cadeia de confiança) - dig nic.br DS
*	RRSIG (Assinatura do RRset) - dig nic.br RRSIG

## Referências
[![Vaanmonde](https://avatars.githubusercontent.com/u/21218780?s=48)](https://github.com/vaamonde/ubiquiti-unifi)

## Desenvolvedor :heart_eyes_cat:
[![Github Badge](https://img.shields.io/badge/-Github-000?style=flat-square&logo=Github&logoColor=white&link=https://github.com/nilsonpessim)](https://github.com/nilsonpessim)
[![Linkedin Badge](https://img.shields.io/badge/-LinkedIn-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://br.linkedin.com/in/nilsonpessim)](https://br.linkedin.com/in/nilsonpessim)
[![Whatsapp Badge](https://img.shields.io/badge/-Whatsapp-4CA143?style=flat-square&labelColor=4CA143&logo=whatsapp&logoColor=white&link=https://api.whatsapp.com/send?phone=5537999351046)](https://api.whatsapp.com/send?phone=5537999351046)