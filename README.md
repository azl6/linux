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

**find** - Busca arquivos com base no padrão informado.

- Option ``-type <type>`` busca por arquivos (type=f) ou diretórios (type=d)
- Option ``-name "<padrão>"`` busca por arquivos que atendam ao padrão especificado. Ex: find -name "*.txt" busca por todos os arquivos finalizados em ".txt".
- Option ``-mmin {+,-}<time>`` busca por arquivos com o modification time maior/menor que <time>.
- Option ``-amin {+,-}<time>`` busca por arquivos com o access time maior/menor que <time>.
- Option ``-mtime {+,-}<time>`` busca por arquivos com o modification time maior/menor que <time>. Diferentemente do mmin, o mtime busca por <time>*24, ou seja, o <time> informado no parâmetro representa o período de um dia inteiro.

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

**su** - Loga como outro usuário (switch/substitute user)

- Option obrigatória ``--login`` (ou somente ``-``) evitará que os ambientes dos usuários sejam misturados. Use sempre essa flag!

**chown <{user_name, :group_name}> <{arquivo, diretorio}>** - Muda o dono e/ou grupo dono de um arquivo/diretório.

**groups <user_name>** - Lista os grupos dos quais um usuário faz parte.

**add group <group_name>** - Cria um grupo.

**adduser <user_name> <group_name>** - Cria um grupo.

**printenv** - Printa as variáveis de ambiente.

**export \<key>=\<value>** - Cria uma variável de ambiente com o \<value> informado. As mudanças só valem para a sessão do terminal onde a variável foi criada. Para que as mudanças sejam permanentes, deve-se alterar o arquivo ~/.bashrc

**alias \<key>='\<value>'** - Cria um alias para algum comando especificado no \<value>. As mudanças só valem para a sessão do terminal onde a variável foi criada. Para que as mudanças sejam permanentes, deve-se alterar o arquivo ~/.bashrc

**awk** - Serve para manipularmos colunas e printarmos seus conteúdos com um separador. Por padrão, o awk utiliza como separador um espaço. Esse comportamento pode ser alterado.

Exemplos de utilização:

**cat \<arquivo.txt> | awk '{print $1}'** - Printa a primeira coluna (representada por $1) do \<arquivo.txt>, utilizando um espaço como separador.
 
   ![Screenshot from 2022-11-26 14-22-09](https://user-images.githubusercontent.com/80921933/204101337-7a0d6159-af55-4f38-9b17-3d3a216e6bf7.png)
 
 - **cat \<separadoPorPonto.txt> | awk -F ":" '{print $1}'** - Printa a primeira coluna (representada por $1) do \<arquivo.txt>, utilizando ':' como separador.
 
   ![Screenshot from 2022-11-26 14-33-29](https://user-images.githubusercontent.com/80921933/204101617-d60bee3f-c31a-4369-bffd-7b73514bd979.png)

**uniq** - Usado para pegar ocorrências únicas

    ![Screenshot from 2022-11-26 14-43-05](https://user-images.githubusercontent.com/80921933/204101967-6d5edca8-1392-4203-8153-99ea41a021c6.png)


**tar -f <destiny> <origin>** - Usado para comprimir arquivos (similar ao .zip)
- Option ``-c`` Compacta um diretório
- Option ``-x`` Extrai um arquivo .tar
- Option ``-z`` Usa o algorítmo gzip para compactar/extrair
- Option ``-v`` Forma verbosa, arquivos extraidos/compactados serão listados
- Option ``-f`` Especifica o arquivo (já está incluido no comando pq é sempre utilizado)


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

# Cron jobs

![Screenshot from 2022-11-25 22-23-56](https://user-images.githubusercontent.com/80921933/204067185-383523da-e3c0-4863-b81d-2278b3f89368.png)

![Screenshot from 2022-11-25 22-24-47](https://user-images.githubusercontent.com/80921933/204067218-8dba4c2d-85f0-449d-bf9a-3c7549b3c585.png)

![Screenshot from 2022-11-25 22-26-08](https://user-images.githubusercontent.com/80921933/204067245-7b2f8ab3-abec-4be1-b995-211cf36c0c23.png)

![Screenshot from 2022-11-25 22-27-08](https://user-images.githubusercontent.com/80921933/204067265-7abc5123-86df-4482-aed7-155a073ef468.png)

![Screenshot from 2022-11-25 22-29-26](https://user-images.githubusercontent.com/80921933/204067339-f3441ae6-a7c8-49e9-a378-e7580b4a2145.png)

Para escrever os cronjobs, abrimos o arquivo de configuração com o comando

```
crontab -e
```

Depois, basta especificar, no final do arquivo, o cron job e o caminho do comando a ser rodado. Além disso, é possível direcionar os erros com o 2>> para um arquivo, caso aconteçam:

```
# ...
* * * * * * ~/bin/comando 2>> ~/erros/errosComando.txt
```

# SSH (Secure Shell)

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

1. Primeiro, criamos uma chave na máquina do client com o comando `ssh-keygen -t \<KEY_NAME>`
2. Depois, enviamos a chave ao server com o comando `ssh-copy-id \<SERVER_USER>@\<SERVER_IP>`

Os 2 passos acima são representados pela seguinte imagem:

![Screenshot from 2022-11-26 15-51-10](https://user-images.githubusercontent.com/80921933/204104831-10b08723-9cd9-46f2-ba1e-906d25e972da.png)

Depois disso, basta conectar normalmente ao servidor via ssh.
 
 **IMPORTANTE** Conexões com instâncias EC2 são feitas a partir do seguinte comando:
 
 ```
 ssh -i /path/key-pair-name.pem instance-user-name@instance-public-dns-name
 ```
