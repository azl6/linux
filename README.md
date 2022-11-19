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




