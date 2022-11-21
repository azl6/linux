# Diretórios

![image](https://user-images.githubusercontent.com/80921933/202584611-2286eea2-09d3-4755-9422-a1994e3dbfa7.png)

![image](https://user-images.githubusercontent.com/80921933/202584714-e6d60530-166d-4b9a-9fcb-09bf21e5118f.png)

![a](https://user-images.githubusercontent.com/80921933/202585060-d7d8ee12-4563-4cf3-a431-4203806100f0.png)

![a](https://user-images.githubusercontent.com/80921933/202593547-fe98e703-27b0-428e-b70c-8f4cfd3699b5.png)

# Geral

![Screenshot from 2022-11-20 20-34-11](https://user-images.githubusercontent.com/80921933/202932602-c3c0ad88-7fed-44de-9577-455c0abc59b2.png)

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

**xargs** - **Inserir!!!**



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


