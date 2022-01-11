## 🛠 Dev Proxy Squid | Instalar e configurar. 


O Squid é um proxy da web HTTP de cache e encaminhamento.  

Ele tem uma ampla variedade de utilizações, incluindo acelerar um servidor web ao armazenar em cache solicitações repetidas, caching web, DNS e outras pesquisas de rede de computador para um grupo de pessoas que compartilham recursos de rede e auxiliar na segurança ao filtrar o tráfego.


#### Apresentação;

* OpenSource 
* Josenilto L da Silva
* Gradudo em **Ciência da Computação** pela **Universidade Veiga de Almeida - UVA**, Rio de Janeiro
* Atuando na área de TI desde 2002
* Foco em soluções Linux desde 2008

#### O que é um Servidor Proxy ?

Dispositido que fica entre a conexão de um cliente e um servidor.  

Pode ter como função a filtragem de conteúdo, onde através de uma lista de controle de acesso permite ou não que a requisição de um cliente seja concretizada.  

Também pode ter a função de proxy cache, nesse tipo o servidor proxy armazena em seu cache os objetos solicitados por seus clientes. Caso algum cliente faça uma requisição de um objeto e o mesmo já existe no cache do proxy, a resposta será enviada imediatamente.


#### O que é Squid ?

* Proxy cache que tem suporte aos protocolos **`HTTP, HTTPS, FTP`** e Outros.
* Licenciado pela GNU GPL.
* Algumas possibilidades: **`Controle de Acesso, Logs, Gerenciamento de tráfego`**.
* Melhora sua performance continuamente.
* Compatibilidade com várias plataformas e uma variedade de software para análise de logs e geração de relatórios. 



#### Acl de tipo TIME (Por Horário)

| SIGLA SQUID | DIA DA SEMANA |
|---|---|
|S|DOMINGO|
|M|SEGUNDA|
|T|TERÇA|
|W|QUARTA|
|H|QUINTA|
|F|SEXTA|
|A|SÁBADO|

* Atualização do servidor

```bash
sudo yum update -y && sudo yum upgarde -y
```

* Instalação do **`VIM`**  

```bash
sudo yum -y install vim
```

* Desabilitar o **`SELinux`** `cat /etc/selinux/config`

* Defina permanentemente o modo SELinux  

Se precisarmos definir o modo SELinux permanentemente como permissivo , também teremos que configurá-lo no arquivo de configuração do SELinux. Assim, na próxima inicialização o SELinux iniciará no modo permissivo .

```bash
sed -i s/^SELINUX=.*$/SELINUX=permissive/ /etc/selinux/config
setenforce 0
```

* Desative permanentemente o SELinux  

Não é possível desabilitar o SELinux temporariamente enquanto um servidor CentOS estiver em execução. Devemos desabilitar o SELinux através de seu arquivo de configuração, então na próxima reinicialização do sistema o SELinux não será mais habilitado.

```bash
sed -i s/^SELINUX=.*$/SELINUX=disabled/ /etc/selinux/config  
systemctl reboot
```

* Após isso, vamos verificar o status do firewall com o comando

```bash
sestatus
```

Abra a porta do firewall para Squid.</br>
Se você tiver um serviço firewalld em execução, permita a porta **`3128`** na rede:

```bash
sudo firewall-cmd --permanent --add-service=squid

sudo firewall-cmd --permanent --remove-service=dhcpv6-client
sudo firewall-cmd --permanent --remove-service=cockpit

sudo firewall-cmd --reload
sudo firewall-cmd --list-all 
```


```bash
sudo yum -y install net-tools
```

```bash
sudo yum -y install psmisc
```

Se o route for utilizado sem nenhuma opção, exibe a tabela de rotas.

```bash
route -n
```

A mesma informação pode ser vista com o comando ip:

```bash
 ip route show
```

O comando **netstat -r** também lista a tabela de rotas:

```bash
netstat -r
```

## Instalando o SQUID  
Para realizar a instalação do squid é muito simples. Buscamos o pacote direto dos repositórios.

```bash
sudo yum -y install squid
```

## Configurando o SQUID
Agora vamos efetuar as configurações do SQUID no ambiente Linux.  
O primeiro passo a fazer é um backup do arquivo **squid.conf**.

```bash
cp -p -Rfa /etc/squid/squid.conf{,.bkp}
```

Agora vamos acessar o diretório de configuração do SQUID.

```bash
cd /etc/squid/
```


```bash
tail -f /var/log/squid/access.log
```

### Realizar backup do arquivo .conf

```bash
cp -p -Rfa /etc/squid/squid.conf{,.bk.`date +%Y%m%d`}
```

### Iniciando o SQUID  
Agora vamos criar o diretório de cache do squid.

```bash
squid -z
```

Vamos deixar o squid configurado para iniciar junto ao boot do sistema linux.

```bash
systemctl enable squid
```

Em seguida iniciamos o serviço do Squid.

```bash
systemctl start squid
```

Verificando o status no sistema.

```bash
systemctl status squid
```

### Testando o funcionamento do SQUID  
Para testar o servidor Squid insira o IP e porta nas configurações de proxy do navegador.

Acompanhe os logs de acessos.

```bash
tail -f /var/log/squid/access.log
```
