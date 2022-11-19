# Diretórios

![image](https://user-images.githubusercontent.com/80921933/202584611-2286eea2-09d3-4755-9422-a1994e3dbfa7.png)

![image](https://user-images.githubusercontent.com/80921933/202584714-e6d60530-166d-4b9a-9fcb-09bf21e5118f.png)

![a](https://user-images.githubusercontent.com/80921933/202585060-d7d8ee12-4563-4cf3-a431-4203806100f0.png)

![a](https://user-images.githubusercontent.com/80921933/202593547-fe98e703-27b0-428e-b70c-8f4cfd3699b5.png)


# Comandos Linux

**man <cmd_name>** - Manual dos comandos.

![a](https://user-images.githubusercontent.com/80921933/202582532-bb97a1cf-18e5-4c60-bebe-8e32684220d5.png)

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
