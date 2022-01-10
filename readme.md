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
|S|DOMINGO|
|M|SEGUNDA|
|T|TERÇA|
|W|QUARTA|
|H|QUINTA|
|F|SEXTA|
|A|SÁBADO|
