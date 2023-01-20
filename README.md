**Informações gerais sobre o Linux** <br>
[Diretórios](#diretórios) <br>
[Comandos Linux](#comandos-linux) <br>
[Redirection](#redirection) <br>
[Piping](#piping) <br>
[Expansion](#expansion) <br>
[Permissions](#permissions) <br>
[Bash Scripting básico](#bash-scripting-básico) <br>
[Cron jobs sem root necessário](#cron-jobs-sem-root-necessário) <br>
[Cron jobs com root](#cron-jobs-com-root) <br>

**SSH** <br>
[SSH](#ssh) <br>
[SSH na AWS](#ssh-na-aws) <br>
[SSH manual](#ssh-manual) <br>
[Servidor Ubuntu contêinerizado com o openssh-server up](#servidor-ubuntu-contêinerizado-com-o-openssh-server-up) <br>

**Gerenciando usuários e grupos** <br>
[Arquivo para verificar todos os usuários do sistema](#arquivo-para-verificar-todos-os-usuários-do-sistema) <br>
[Adicionando um novo usuário ao sistema](#adicionando-um-novo-usuário-ao-sistema) <br>
[Deletando um usuário ao sistema](#deletando-um-usuário-ao-sistema) <br>
[Mostrando de quais grupos o usuário faz parte](#mostrando-de-quais-grupos-o-usuário-faz-parte) <br>
[Arquivo para verificar todos os grupos do sistema](#arquivo-para-verificar-todos-os-grupos-do-sistema) <br>
[Criando um grupo](#criando-um-grupo) <br>
[Deletando um grupo](#deletando-um-grupo) <br>
[Adicionando um usuário a um grupo](#adicionando-um-usuário-a-um-grupo) <br>
[Removendo um usuário de um grupo](#removendo-um-usuário-de-um-grupo) <br>

**Logs** <br>
[Logs de boot](#logs-de-boot) <br>
[Logs para SSH](#logs-para-ssh) <br>
[Logs do sistema](#logs-do-sistema) <br>
[Logs de serviços com o journalctl](#logs-de-serviços-com-o-journalctl) <br>

**Mountpoints e dispositivos** <br>
[Listando dispositivos plugados](#listando-dispositivos-plugados) <br>
[Removendo um mountpoint](#removendo-um-mountpoint) <br>
[Criando uma nova partição em um dispositivo](#criando-uma-nova-partição-em-um-dispositivo) <br>
[Criando um servidor NFS](#criando-um-servidor-nfs) <br>

**Utilitários** <br>
[Baixando arquivos da internet com o wget](#baixando-arquivos-da-internet-com-o-wget) <br>
[Comprimindo e extraindo arquivos com o tar](#comprimindo-e-extraindo-arquivos-com-o-tar) <br>
[Gerenciando serviços como apache2 sshd httpd pelo systemctl](#gerenciando-serviços-como-apache2-sshd-httpd-pelo-systemctl) <br>
[Utilizando o find para encontrar e manipular arquivos](#utilizando-o-find-para-encontrar-e-manipular-arquivos) <br>

# Diretórios 

![image](https://user-images.githubusercontent.com/80921933/202584611-2286eea2-09d3-4755-9422-a1994e3dbfa7.png)

![image](https://user-images.githubusercontent.com/80921933/202584714-e6d60530-166d-4b9a-9fcb-09bf21e5118f.png)

![a](https://user-images.githubusercontent.com/80921933/202585060-d7d8ee12-4563-4cf3-a431-4203806100f0.png)

![a](https://user-images.githubusercontent.com/80921933/202593547-fe98e703-27b0-428e-b70c-8f4cfd3699b5.png)


# Comandos Linux

**man <cmd_name>** - Manual dos comandos.

<br>

**pwd** - Printa onde estamos.

<br>

**less** - Mesma coisa que o comando ``cat``, porém, paginado.

<br>

**head** - Printa as 10 primeiras linhas de um arquivo. 
- Option ``-n <lines_number>`` permite que escolhamos o números de linhas desejadas. 

<br>

**tail** - Printa as 10 últimas linhas de um arquivo.
- Option ``-n <lines_number>`` permite que escolhamos o números de linhas desejadas. 
- Option ``-f`` segue as alterações do arquivo. Util para monitorar logs.

<br>

**wc** - Conta a quantidade de linhas, palavras e bytes (nesta ordem) em um arquivo.
- Option ``-w`` printa a quantidade de palavras.
- Option ``-l`` printa a quantidade de linhas.

<br>

**sort** - Ordena o conteúdo de um arquivo
- Option ``-n`` ordena números. 
- Option ``-r`` reverte a ordenação
- Option ``-u`` ordena por valores únicos
- Option ``-k <col_number>`` ordena pela coluna especificada, exemplo -> VALORES: 1 alex 7.00, COLUNAS: id nome nota. Útil para ordenar o **ls -l** por exemplo.

<br>

**tee** - Cria um arquivo com o stdout e o copia para um próximo pipe.

![Screenshot from 2022-11-19 21-10-28](https://user-images.githubusercontent.com/80921933/202876631-7ea008e1-bab6-421f-808c-a01121d13df6.png)

<br>

**grep <PATTERN> <FILE>** - Busca por ocorrências de um padrão dentro de um arquivo/texto.

- Option ``-i`` deixa a busca case-insensitive
- Option ``-w`` busca somente ocorrências isoladas, Ex: `grep -w "car" arquivo.txt` irá encontrar a palavra "car", mas não "ufscar"
- Option ``-r`` busca recursivamente por ocorrências a partir do diretório onde estamos (mas também podemos fornecer um diretório a ser buscado)

![Screenshot from 2022-11-20 20-14-19](https://user-images.githubusercontent.com/80921933/202931762-b989cd95-1e50-405d-bbc0-dd9ecd9cccf8.png)

Podemos também usar expansion (ou regex) em um `grep`

![Screenshot from 2022-11-20 20-17-45](https://user-images.githubusercontent.com/80921933/202931919-9ae2965d-a748-42d2-83ad-e95ce893f77c.png)

- Option ``-C <number>`` printará `<number>` linhas antes e depois de cada ocorrência encontrada
- Option ``-n <number>`` printará o número das linhas encontradas

<br>

**chmod** - Fornece ou remove permissões em arquivos/diretórios.

Possíveis destinos das permissões:
- **u** (usuário/dono)
- **g** (grupo)
- **o** (outros)
- **a** (todos)

Operações de adição ou remoção de permissões:
- **+** (adiciona)
- **-** (remove)
- **=** (atualiza as permissões, removendo todas as anteriores e atribuindo todas as novas)
 
 **chown <{user_name, :group_name}> <{arquivo, diretorio}>** - Muda o dono e/ou grupo dono de um arquivo/diretório.

**su** - Loga como outro usuário (switch/substitute user)

- Option obrigatória ``--login`` (ou somente ``-``) evitará que os ambientes dos usuários sejam misturados. Use sempre essa flag!

**useradd \<USERNAME>** - Cria um usuário
 
 ![image](https://user-images.githubusercontent.com/80921933/206821201-8991ad5e-29e0-4e70-aa3f-3600edc7ebf8.png)
 
**passwd \<USERNAME>** - Altera a senha do usuário

**userdel \<USERNAME>** - Deleta um usuário

**groups <user_name>** - Lista os grupos dos quais um usuário faz parte.

**add group <group_name>** - Cria um grupo.

**adduser <user_name> <group_name>** - Adiciona um usuário a um grupo.

**printenv** - Printa as variáveis de ambiente.

**export \<key>=\<value>** - Cria uma variável de ambiente com o \<value> informado. As mudanças só valem para a sessão do terminal onde a variável foi criada. Para que as mudanças sejam permanentes, deve-se alterar o arquivo ~/.bashrc

**alias \<key>='\<value>'** - Cria um alias para algum comando especificado no \<value>. As mudanças só valem para a sessão do terminal onde a variável foi criada. Para que as mudanças sejam permanentes, deve-se alterar o arquivo ~/.bashrc

**awk** - Serve para manipularmos colunas e printarmos seus conteúdos com um separador. Por padrão, o awk utiliza como separador um espaço. Esse comportamento pode ser alterado.

Exemplos de utilização:

**cat \<arquivo.txt> | awk '{print $1}'** - Printa a primeira coluna (representada por $1) do \<arquivo.txt>, utilizando um espaço como separador.
 
   ![Screenshot from 2022-11-26 14-22-09](https://user-images.githubusercontent.com/80921933/204101337-7a0d6159-af55-4f38-9b17-3d3a216e6bf7.png)
 
 **cat \<separadoPorPonto.txt> | awk -F ":" '{print $1}'** - Printa a primeira coluna (representada por $1) do \<arquivo.txt>, utilizando ':' como separador.
 
   ![Screenshot from 2022-11-26 14-33-29](https://user-images.githubusercontent.com/80921933/204101617-d60bee3f-c31a-4369-bffd-7b73514bd979.png)

**uniq** - Usado para pegar ocorrências únicas

   ![Screenshot from 2022-11-26 14-43-05](https://user-images.githubusercontent.com/80921933/204101967-6d5edca8-1392-4203-8153-99ea41a021c6.png)

**sed** - Serve para substituirmos ocorrências de strings no arquivo com a seguinte sintaxe: 

```
sed 's/<STRING_PARA_REMOVER>/<STRING_SUBSTITUTA>/g' <INPUT_FILE>
```

![Screenshot from 2022-12-05 18-38-26](https://user-images.githubusercontent.com/80921933/205748249-c9946ad2-0c7e-44ec-b6b4-2c071161f38e.png)

Comandos pendentes de inserção:

**xargs** <br>
**curl** <br>
**wget** <br>

![comandos network](https://user-images.githubusercontent.com/80921933/203087910-e28c49ea-a5ac-4a07-8c21-192ec7af0ce2.png)

# Redirection

Podemos redirecionar a saída (stdout) de um comando para outros destinos além do terminal, como para um arquivo, utilizando o operador `>`
```
$ date > outputAqui.txt
$ cat outputAqui.txt
```
O approach do `>` irá sobreescrever os dados com o novo input. Para concatenar, usamos o `>>`

![concatRedirection](https://user-images.githubusercontent.com/80921933/202872814-bdd77014-4b4f-42ce-b261-32444cd01e07.png)

Já o comando `<` direciona um input (stdin) para um comando. Perceba que, até o momento, ambos os comandos terão o mesmo output.

![inputRedir](https://user-images.githubusercontent.com/80921933/202872959-436f9fab-860d-424d-893d-e1ef8918afee.png)

Para redirecionar erros (stderr), podemos utilizar o operador `2>`, ou contatenar com o `2>>`

![Screenshot from 2022-11-19 19-10-06](https://user-images.githubusercontent.com/80921933/202873358-4c728e80-a087-4ef4-8e98-44f844df105b.png)

![Screenshot from 2022-11-19 19-07-42](https://user-images.githubusercontent.com/80921933/202873286-b3c1584a-79d4-4133-b0d4-c0d057e03591.png)

# Piping

Quando jogamos um stdout para o stdin de outro comando.

No exemplo abaixo, usamos a saída do comando `ls -l` na entrada do comando `sort`

![Screenshot from 2022-11-19 20-46-40](https://user-images.githubusercontent.com/80921933/202876019-c4d65bbb-9963-4604-a0b4-bb6f80f4ece8.png)


![Screenshot from 2022-11-19 20-42-07](https://user-images.githubusercontent.com/80921933/202876027-9283c60e-ab5e-4edb-a1c5-ff171994905a.png)

# Expansion

![Screenshot from 2022-11-20 12-53-59](https://user-images.githubusercontent.com/80921933/202912034-3f3d208d-6fa1-4a21-81d2-66f4a20ccdab.png)

![Screenshot from 2022-11-20 12-30-34](https://user-images.githubusercontent.com/80921933/202911952-d7891c7f-01a9-4f20-8006-f39a46dd8c00.png)

![Screenshot from 2022-11-20 12-30-38](https://user-images.githubusercontent.com/80921933/202911961-3ecda255-d467-40c8-90f2-770e989e52c8.png)

![Screenshot from 2022-11-20 12-56-27](https://user-images.githubusercontent.com/80921933/202912144-7a8b48d0-0a49-4fff-b445-fc645ab43766.png)

![Screenshot from 2022-11-20 12-58-49](https://user-images.githubusercontent.com/80921933/202912247-3eb3d246-45ee-4045-ba0f-f47a99d4139e.png)

![Screenshot from 2022-11-20 13-01-33](https://user-images.githubusercontent.com/80921933/202912404-b8205fcb-b48b-4a79-9aa8-ac891183498b.png)

# Permissions

![Screenshot from 2022-11-23 21-43-53](https://user-images.githubusercontent.com/80921933/203669915-6c956dcd-4ec8-4910-9123-863ba9e992ba.png)

![Screenshot from 2022-11-23 21-48-20](https://user-images.githubusercontent.com/80921933/203670213-c617c312-2684-43fa-8a8f-e5197f808eb3.png)

![Screenshot from 2022-11-23 21-51-32](https://user-images.githubusercontent.com/80921933/203670546-e1168483-127f-4e15-9d56-c55f3e789b4a.png)


# Bash Scripting básico

Para criar um primeiro bash script:

- Criar um script e inserí-lo no arquivo **hi**

```shell
echo "Hello, $USER!"
echo "This is my first script!"
```

- Para executar o comando sem o `sudo`, devemos dar permissão de execução para os usuários:

```
chmod a+x hi
```

- Depois, atualizamos a variável PATH. A variável PATH é o que o S.O usa para buscar scripts executáveis em nosso PC. Para isso, abrimos o arquivo `~/.bashrc` e inserimos a linha:

```
# ...
export PATH="/$HOME/bin:$PATH" 
# ...
```
  
Para que o script seja utilizável sem precisarmos abrir uma nova sessão do terminal, executamos:
  
```
source ~/.bashrc
```

Pronto! Já podemos executar o nosso script de qualquer parte do PC.

# Cron jobs sem root necessário

![Screenshot from 2022-11-25 22-23-56](https://user-images.githubusercontent.com/80921933/204067185-383523da-e3c0-4863-b81d-2278b3f89368.png)

![Screenshot from 2022-11-25 22-24-47](https://user-images.githubusercontent.com/80921933/204067218-8dba4c2d-85f0-449d-bf9a-3c7549b3c585.png)

![Screenshot from 2022-11-25 22-26-08](https://user-images.githubusercontent.com/80921933/204067245-7b2f8ab3-abec-4be1-b995-211cf36c0c23.png)

![Screenshot from 2022-11-25 22-27-08](https://user-images.githubusercontent.com/80921933/204067265-7abc5123-86df-4482-aed7-155a073ef468.png)

![Screenshot from 2022-11-25 22-29-26](https://user-images.githubusercontent.com/80921933/204067339-f3441ae6-a7c8-49e9-a378-e7580b4a2145.png)

Para escrever os cronjobs, abrimos o arquivo de configuração com o comando

```
crontab -e
```

Depois, basta especificar, no final do arquivo, o cron job e o caminho do script a ser rodado. Além disso, é possível direcionar os erros com o 2>> para um arquivo, caso aconteçam:

```
# ...
* * * * * * ~/bin/script 2>> ~/erros/errosComando.txt
```
 
Para cronjobs, também é possível lançarmos scripts dentro dos **cron directories**, que basicamente rodam os scripts lá armazenados com a periodicidade definida no sufixo (weekly, hourly, daily...) **(NÃO É PERMITIDO COLOCAR O CARACTER PONTO (.) NO NOME DOS SCRIPTS ARMAZENADOS LÁ)**
 
![image](https://user-images.githubusercontent.com/80921933/206558166-188e5fa2-40d4-4f29-9067-bb9f50747dd2.png)
 
Para verificarmos/alterarmos a data com que cada pasta roda os scripts, podemos consultar o arquivo /etc/crontab
 
![image](https://user-images.githubusercontent.com/80921933/206558777-309d6813-f3ed-4286-806f-49e0741b9932.png)

# Cron jobs com root
 
Para rodarmos cronjobs com comandos que só podem ser executados pelo **root user**, devemos:
 
```
sudo nano /etc/crontab
```
 
Implementamos aqui o nosso cronjob, e depois executamos:
 
```
sudo service cron restart
```

 
# SSH

Para criar um server onde podemos "entrar" com o SSH, executamos a seguinte linha:

```
sudo apt install openssh-server
```

O server é "entrável" 24/7. Para verificar o seu status, rodamos:

```
sudo systemctl status ssh
```
![Screenshot from 2022-11-26 15-07-52](https://user-images.githubusercontent.com/80921933/204102886-1afd09fe-518c-4b74-ab9f-7f8c92182193.png)

Para permitirmos acesso ao server, devemos liberar a porta 22 (SSH) do ufw (firewall do Linux). Para checar se o firewall está up, executamos:

```
sudo systemctl status ufw
```
![Screenshot from 2022-11-26 15-16-14](https://user-images.githubusercontent.com/80921933/204103247-c607af32-9181-41fa-9308-cb85dc45f7d4.png)

Caso esteja tudo funcionando, executamos o seguinte comando para liberar a porta do SSH:

```
sudo ufw allow ssh
```

Agora, sub a perspectiva do ssh-client, nos conectamos ao server. A sintaxe padrão de conexão é **ssh \<user>@\<ip>**.

Para vericarmos o ip do server, executamos (no server):

```
ip a
```
![Screenshot from 2022-11-26 15-39-59](https://user-images.githubusercontent.com/80921933/204104152-e6347acd-0748-42d4-a5dd-0b913775c511.png)

Depois, basta executar, a partir do client, o comando `ssh <\SERVER_USER>@\<IP_ENCONTRADO>`. A senha do usuário será requisitada, bastando informá-la para acessar o servidor.

Caso queiramos criar uma chave ssh e acessar o servidor remoto a partir dela:

1. Primeiro, criamos uma chave na máquina do client com o comando `ssh-keygen -f \<KEY_NAME>`
2. Depois, enviamos a chave ao server com o comando `ssh-copy-id \<SERVER_USER>@\<SERVER_IP>`

Os 2 passos acima são representados pela seguinte imagem:

![Screenshot from 2022-11-26 15-51-10](https://user-images.githubusercontent.com/80921933/204104831-10b08723-9cd9-46f2-ba1e-906d25e972da.png)

Depois disso, basta conectar normalmente ao servidor via ssh.

# SSH na AWS
 
Conexões com instâncias EC2 são feitas a partir do seguinte comando:
 
 ```
 ssh -i /path/key-pair-name.pem instance-user-name@instance-public-dns-name
 ```
 
# SSH manual
 
 Se queremos conectar dois servidores, client e server, podemos:
 
 - Gerar a chave no client
 
     ```
     ssh-keygen -f exemplo
     ```
 
 - Copiar o contéudo da chave pública
 
    ```
    cat exemplo.pub
    ```
 
 - No servidor remoto, colar o contéudo copiado no arquivo $HOME/.ssh/authorized_keys
 
 No servidor remoto, o arquivo authorized_keys deve ter permissões 400, e a pasta .ssh deve ter permissão 700.
 
 Pronto! 
 
# Servidor Ubuntu contêinerizado com o openssh-server up
 
 Vídeo usado como referência: https://www.youtube.com/watch?v=VQfrtRY6Szk
 
 Dockerfile:
 
```yml
 FROM ubuntu

# Criando pasta necessária (ainda não sei o porquê)
RUN mkdir -p /var/run/sshd 

# Instalando o libs básicas e o ssh server
RUN apt update && \
    apt install -y lsb-core && \
    apt install -y openssh-server

# Criando usuário usuarioUbuntuServer com a senha 123
RUN useradd usuarioUbuntuServer && \
    echo "usuarioUbuntuServer:123" | chpasswd

# Criando diretórios necessários do usuário usuarioUbuntuServer
RUN mkdir -p /home/usuarioUbuntuServer/.ssh/authorized_keys

# Informando que o usuário usuarioUbuntuServer é o dono das pastas /home/usuarioUbuntuServer/** 
RUN chown -R usuarioUbuntuServer:usuarioUbuntuServer /home/usuarioUbuntuServer

# Copiando a chave pública para o contêiner
COPY chavejenkins.pub /home/usuarioUbuntuServer/.ssh/authorized_keys/

# Iniciando o ssh-server
CMD [ "/usr/sbin/sshd", "-D" ]
```

# Arquivo para verificar todos os usuários do sistema

```
/etc/passwd
```
 
# Adicionando um novo usuário ao sistema

```
sudo useradd <USER_NAME>
```
 
**-m** cria um home directory para o usuário
**-r** indica que o usuário será um system user, com um UUID menor que 1000. System users não aparecem na tela de login, e são usados para tarefas de background
**-s** especifica o shell padrão do usuário
 
# Deletando um usuário ao sistema

```
sudo userdel <USER_NAME>
```
 
**-r** deleta também o home directory do usuário
 
# Mostrando de quais grupos o usuário faz parte
 
 ```
 groups
 ```
 
# Arquivo para verificar todos os grupos do sistema

 ```
 /etc/group
 ```
 
# Criando um grupo
 
 ```
 sudo groupadd <GROUP_NAME>
 
 ```
 
# Deletando um grupo
 
 ```
 sudo groupdel <GROUP_NAME>
 ```
 
# Adicionando um usuário a um grupo
 
 ```
 sudo usermod -aG <GROUP_NAME> <USER_NAME>
 ```
  
 **-a** é "appendar"
 **-G** vem de Grupo
 
 Alternativamente, podemos usar o comando gpasswd
 
 ```
 sudo gpasswd -a <USER_NAME> <GROUP_NAME>
 ```
 
# Removendo um usuário de um grupo
 
 ```
 sudo gpasswd -d <USER_NAME> <GROUP_NAME>
 ```
 
# Logs de boot
 
 Os logs de boot podem ser encontrados no seguinte arquivo
 
 ```
 /var/log/boot.log
 ```
 
 São úteis para troubleshooting de problemas ao bootar o PC
 
# Logs para SSH
 
 Os logs para SSH podem ser encontrados no seguinte arquivo
 
 ```
 /var/log/auth.log
 ```
 
 Nele, podemos verificar todos os erros que ocorreram em tentativas de SSH ao servidor em questão, juntamente ao comando **tail -f** (-f significando follow)
 
# Logs do sistema
 
 Os logs do sistema estão localizados no arquivo 
 
 ```
 /var/log/syslog
 ```
 
 Nele, podemos realizar o troubleshooting de tudo que acontece (ou deveria acontecer) no sistema
 
# Logs de serviços com o journalctl
 
 Os logs de algum **serviço** específico podem ser verificados pelo seguinte comando 
 
 ```
 journalctl -u <NOME_SERVIÇO>
 ```
 
 Os **serviços** que podem ser passados no parâmetro **\<NOME_SERVIÇO>** são todos aqueles que podem ser iniciados com o comando **service** ou **systemctl**, como docker, apache2, httpd, ssh, etc...
 
# Listando dispositivos plugados
 
 List block devices
 
 ```
 lsblk
 ```
 
 ou
 
 ```
 sudo fdisk -l
 ```
 
 ou
 
 ```
 df -h
 ```
 
# Removendo um mountpoint
 
 ```
 sudo umount <MOUNT_PATH>
 ```

 O \<MOUNT_PATH> pode ser encontrado pelo comando **lsblk**, na columa **MOUNTPOINT**, ou pelo comando **fdisk -l**
 
# Criando uma nova partição em um dispositivo
 
 Em um dispositivo **sem mountpoint**, podemos executar 
 
 ```
 sudo fdisk <DEVICE_PATH>
 ```
 
 **Obs:** O \<DEVICE_PATH> é o disco, **E NÃO A PARTIÇÃO**, como **sdb**, **sdc**, mas não **sdb1** ou semelhantes!!
 
 Com o prompt do fdisk funcionando, podemos, nesta ordem:
 
 **g** - cria uma nova partition-table GPT <br>
 **n** - cria uma nova partição. basta dar enter nos passos do prompt, ou personalizar os tamanhos, se desejar. <br>
 **w** - commita as alterações <br>
 
 Após commitar as alterações do **fdisk** com a option **w**, devemos usar o comando **mkfs** para criar um file-system
 
 ```
 sudo mkfs.<FILESYSTEM_TYPE> <PARTITION_PATH>
 ```
 
 Opções válidas para o **\<FILESYSTEM_TYPE>** são **ext4** (para Linux), **fat**, dentre outras. (testei ext4 e não obtive sucesso ao plugar o pendrive!) <br>
 **\<PARTITION_PATH>** se refere a **PARTIÇÃO** (geralmente em /dev juntamente aos dispositivos), e **NÃO** ao dispositivo!
 
 Depois, basta montar o dispositivo em alguma pasta, geralmente em **/media** para dispositivos temporários ou **/mnt** para dispositivos mais "permanentes", como um segundo HD, etc.
 
 ```
 mount <PARTITION_PATH> <PATH_TO_MOUNT>
 ```
 
# Baixando arquivos da internet com o wget
 
 Podemos copiar o link de download de algum site, da seguinte forma
 
 ![wget](https://user-images.githubusercontent.com/80921933/210285599-7a5fd2f9-ed22-4915-9615-8bb005b5a9e6.png)

 Com o link copiado, basta usarmos ele no wget
 
 ```
 wget <LINK>
 ```
 
 **-P \<PATH>** - especificando o caminho do download, já que por padrão, o wget baixará o arquivo na pasta onde foi executado. <br>
 **-i \<FILE>** - especificando um arquivo com links para o wget baixar sequencialmente
 
# Comprimindo e extraindo arquivos com o tar
 
 **tar -f <destiny> <origin>** - Usado para comprimir arquivos (similar ao .zip)
- Option ``-c`` Compacta um diretório
- Option ``-x`` Extrai um arquivo .tar
- Option ``-z`` Usa o algorítmo gzip para compactar/extrair
- Option ``-v`` Forma verbosa, arquivos extraidos/compactados serão listados
- Option ``-f`` Especifica o nome do arquivo gerado (já está incluido no comando pq é sempre utilizado)

Exemplo de utilização:

tar -cf pasta-a-ser-gerada pasta <br>
tar -xf pasta-comprimida
 
# Gerenciando serviços como apache2 sshd httpd pelo systemctl
 
 Verificar o status de um serviço,
 
 ```
 systemctl status <SERVICE_NAME>
 ```
 
 Com o status, podemos ver se um serviço está **ENABLED** ou **DISABLED**

 Serviços **DISABLED** não iniciarão juntamente ao boot do sistema, e terão de ser ativados a todo momento que o PC reiniciar!
 
Para setar o status de um serviço como **ENABLED**, executamos:
 
 ```
 sudo systemctl enable <SERVICE_NAME>
 ```
 
 Para iniciar um serviço, executamos:
 
 ```
 sudo systemctl start <SERVICE_NAME>
 ```
 
 Para parar um serviço, executamos:
 
 ```
 sudo systemctl stop <SERVICE_NAME>
 ```
 
 Para desativar um serviço, executamos:
 
 ```
 sudo systemctl disable <SERVICE_NAME>
 ```
 
 # Criando um servidor NFS
 
 Primeiramente, no **server**, instalamos os seguintes pacotes
 
 ```bash
 sudo apt install nfs-kernel-server nfs-common rpcbind
 ```
 
 No **server**, criamos a pasta que será compartilhada via NFS, e fornecemos as permissões desejadas via chmod
 
 ```bash
 sudo mkdir /tmp/nfs-share && sudo chmod 777 /tmp/nfs-share -R
 ```
 
 Agora, alteramos o arquivo **/etc/exports**, que é uma lista de controle de acessos ao NFS, inserindo uma linha no seguinte formato:
 
 ```bash
 <DIR_NFS> <IPS_LIBERADOS> (rw,sync,no_subtree_check)
 ```
 
 Em nosso exemplo, essa linha ficaria assim (usei * porque quero permitir que todas as máquinas possam montar essa diretório):
 
 ```bash
 /tmp/nfs-share *(rw,sync,no_subtree_check)
 ```
 Agora, liberamos NFS em nosso firewall
 
 ```bash
 sudo ufw allow nfs
 ```
 
 Podemos confirmar que o mountpoint foi criado com o comando:
 
 ```bash
 showmount -e
 ```
 
 No **client**, criamos um diretório para servir de mountpoint, e aplicamos as permissões desejadas
 
 ```bash
 sudo mkdir /mnt/my-mountpoint && sudo chmod 777 /mnt/my-mountpoint -R
 ```
 
 Ainda no client, instalamos os pacotes:
 
 ```
 sudo apt install rpcbind nfs-common
 ```
 
 Agora, basta montarmos o diretório com o comando **mount**
 
 ```
 sudo mount 222.222.222.222:/tmp/nfs-share /mnt/my-mountpoint
 ```
 
 Agora, no arquivo **/etc/fstab**, inserimos a seguinte linha (adaptando para a sua realidade)
 
 ![image](https://user-images.githubusercontent.com/80921933/213751778-bc31e1ea-644a-49a2-883f-caeaf9200484.png)

 Pronto! O mountpoint já deve estar funcionando. Tente criar algum arquivo lá!
  
 # Utilizando o find para encontrar e manipular arquivos
  
**find** - Busca arquivos com base no padrão informado.

- Option ``-name "<padrão>"`` busca por arquivos e diretórios cujo nome bata com o padrão fornecido.
- Option ``-type <type>`` busca por arquivos (type=f) ou diretórios (type=d)
- Option ``-exec <COMANDO> {} +`` executa um comando nos itens encontrados pelo **find**

**Exemplos do comando find:**

Buscando todos os **arquivos e diretórios** a partir do homedir que terminam com ".txt"
```
find /home/azl6 -name "*.txt"
```

Buscando todos os **arquivos** (e não diretórios!) a partir do homedir cujo nome é exatamente "Documents" 
```
find /home/azl6 -name "Documents" -type f
```

Buscando e removendo arquivos a partir do current dir que terminem com ".txt"
```
find . -name "*.txt" -exec rm {} +
```
  
  
