Atividade Avaliativa 1
================
Andrei Paraizo dos Santos </br>
Estatistica 2021.1

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.6     v dplyr   1.0.7
    ## v tidyr   1.1.4     v stringr 1.4.0
    ## v readr   2.1.1     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
frango_dieta <- read_csv("dados/brutos/frango_dieta.csv")
```

    ## Rows: 578 Columns: 4

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## dbl (4): peso, tempo, frango, dieta

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(frango_dieta)

dados_co2 <- read_csv("dados/brutos/dados_co2.csv")
```

    ## Rows: 39 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## dbl (13): ano, jan, fev, mar, abr, mai, jun, jul, ago, set, out, nov, dez

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(dados_co2)

dados_co2_tidy <- read_csv("dados/tidy/dados_co2_tidy.csv")
```

    ## Rows: 468 Columns: 3

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr (1): mes
    ## dbl (2): ano, ppm

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(dados_co2_tidy)

tabela_1_4_ <- read_csv("dados/brutos/tabela 1 (4).csv")
```

    ## Rows: 8 Columns: 3

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr (1): Nome
    ## dbl (2): altura, peso

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(tabela_1_4_)
```

**Questao 01** **a** O erro ?? que ele considera a mala mais pesada sendo
a que representa o valor do quartis superior e an??lise de an??lise que
pelo boxplot existem malas mais pesadas entre esse quartil e o limite
superior (29kg), onde est?? localizado 25% da amostra (malas). Portanto,
23kg n??o representa a mala mais pesada da distribui????o.

**b** A mediana ?? representada pelo segundo quartil, assim, o seu valor
?? de 17kg.

**c** A dist??ncia interquart??lica ?? a diferen??a entre o quartil superior
pelo quartil inferior, assim, a dist??ncia seria 23 - 10 = 13.

**d** A quantidade de malas presente entre 5kg e 10kg est?? no primeiro
quartil que corresponde a 25% do total da amostra, assim, corresponderia
a 25% de 240 malas, ou seja, 60 malas.

**Questao 2** Obtive a soma de todas as m??dias dos 30 alunos,
multiplicando 30 pela m??dia aritm??tica das notas, ou seja, 6.40
encontrando como resultado 192. Da mesma forma, obtive a soma total das
m??dias dos outros 50 alunos da outra turma, multiplicando o total de
alunos (50) por 5,20 tendo como total 260. Feito isso, somei a soma
total das m??dias das duas turma (192 + 260 = 452) e dividi por 80 (total
de alunos correspondentes as duas turmas) (452/80) . Assim, obtive que a
m??dia aritm??tica dos 80 alunos ?? 5.65. Alternativa A.

**Questao 3**

``` r
X  <- c ( 68 , 70 , 72 , 58 , 90 , 110 , 68 , 70 , 72 , 80 , 80 , 67 , 90 , 94 , 100 , 80 , 75 , 79 , 84 , 90 )
(110:58)
```

    ##  [1] 110 109 108 107 106 105 104 103 102 101 100  99  98  97  96  95  94  93  92
    ## [20]  91  90  89  88  87  86  85  84  83  82  81  80  79  78  77  76  75  74  73
    ## [39]  72  71  70  69  68  67  66  65  64  63  62  61  60  59  58

**b** M??dia = 79,85; Primeiro quartil = 70,0; Mediana = 79,5; Quartil
Terceiro = 90; Desvio padr??o = 12.78681

Para encontrar essa resposta, utilizei os seguintes c??digos

``` r
mean ( X )
```

    ## [1] 79.85

``` r
quantile ( X )
```

    ##    0%   25%   50%   75%  100% 
    ##  58.0  70.0  79.5  90.0 110.0

``` r
median ( X )
```

    ## [1] 79.5

``` r
sd ( X )
```

    ## [1] 12.78681

**c** No histograma, ?? poss??vel perceber uma certa assimetria entre os
valores, por isso, acredito que a mediana representa a melhor medida
central do conjunto de dados.

**Questao 4** **a**

Ao analisar o conjunto de dados foi poss??vel identificar que cada coluna
representa uma vari??vel (peso, tempo, frango, dieta), cada linha
apresentava sobre as vari??veis e cada c??lula apresentava uma ??nica
observa????o, logo, este dataset est?? organizado na forma tidy

**b** Usando o codigo

``` r
mean(frango_dieta $ peso)
```

    ## [1] 121.8183

Encontrei que a m??dia do peso dos fragos ?? 121.8183.

**c** Usando o c??digo

``` r
sd( frango_dieta $ peso )
```

    ## [1] 71.07196

Encontrei como desvio padr??o o valor 71.07196

**d** A vari??vel peso ?? quantitativa cont??nua. A vari??vel tempo ??
quantitativa discreta A vari??vel ?? frango qualitativa nominal A vari??vel
dieta ?? qualitativa nominal

**Questao 5**

``` r
#---------------------------------------------------------
N <- 1000
x <- rnbinom(N, 4, .5)
hist(
x,
xlim = c(min(x), max(x)),
probability = T,
nclass = max(x) - min(x) + 1,
col = 'lightblue', xlab = ' ', ylab = ' ', axes = F,
main = 'Positive Skewed'
)
lines(density(x, bw = 1), col = 'red', lwd = 3)
```

![](Atividade-Avaliativa-1_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
#---------------------------------------------------------
```

Analisando esse gr??fico, ?? poss??vel perceber que a disposi????o dos
valores ?? assim??trica, logo, a mediana ?? a melhor medida central para
representar esses dados.

**Questao 6** **a**

``` r
dados_co2 <- read_csv("dados/brutos/dados_co2.csv")
```

    ## Rows: 39 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## dbl (13): ano, jan, fev, mar, abr, mai, jun, jul, ago, set, out, nov, dez

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

**b** N??o est?? no formato tidy, pois, as colunas n??o representam
vari??veis, nesse caso, acredito que deveria ter 3 colunas (ano, m??s,
co2)

**c**

``` r
dados_co2 %>%                
  pivot_longer (
    ! ano ,              
     names_to  =  " ano " ,    
     values_to  =  " dez "   
  )
```

    ## # A tibble: 468 x 3
    ##      ano ` ano ` ` dez `
    ##    <dbl> <chr>     <dbl>
    ##  1  1959 jan        315.
    ##  2  1959 fev        316.
    ##  3  1959 mar        316.
    ##  4  1959 abr        318.
    ##  5  1959 mai        318.
    ##  6  1959 jun        318 
    ##  7  1959 jul        316.
    ##  8  1959 ago        315.
    ##  9  1959 set        314.
    ## 10  1959 out        313.
    ## # ... with 458 more rows

Obs: O c??digo n??o roda no rnotebook.

**d**

``` r
dados_co2 <- read_csv("dados/brutos/dados_co2.csv")
```

    ## Rows: 39 Columns: 13

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## dbl (13): ano, jan, fev, mar, abr, mai, jun, jul, ago, set, out, nov, dez

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
dados_co2 %>% View()
```

``` r
dados_co2_tidy <- dados_co2 %>% 
  pivot_longer(
    !ano, 
   names_to = "mes",
   values_to = "ppm"
  )
```

``` r
write_csv(dados_co2_tidy, "dados/tidy/dados_co2_tidy.csv")
```

**e** Ao passar dos anos a media esta subindo exponencialmente.

``` r
co2_tidy <-  read_csv("dados/tidy/dados_co2_tidy.csv")
```

    ## Rows: 468 Columns: 3

    ## -- Column specification --------------------------------------------------------
    ## Delimiter: ","
    ## chr (1): mes
    ## dbl (2): ano, ppm

    ## 
    ## i Use `spec()` to retrieve the full column specification for this data.
    ## i Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
View(co2_tidy)

co2_tidy %>% glimpse()
```

    ## Rows: 468
    ## Columns: 3
    ## $ ano <dbl> 1959, 1959, 1959, 1959, 1959, 1959, 1959, 1959, 1959, 1959, 1959, ~
    ## $ mes <chr> "jan", "fev", "mar", "abr", "mai", "jun", "jul", "ago", "set", "ou~
    ## $ ppm <dbl> 315.42, 316.31, 316.50, 317.56, 318.13, 318.00, 316.39, 314.65, 31~

``` r
#-------------------------------------------
co2_tidy %>% # conjunto de dados
group_by(ano) %>% # agrupa por ano
summarise(media = round(mean(ppm), 2)) %>% # calcula a m??dia da variavel ppm em cada grupo
ggplot(aes(ano, media, group = 1)) + # cria o gr??fico
geom_line(color = "blue", size = 1)
```

![](Atividade-Avaliativa-1_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

``` r
#-------------------------------------------
```

Observando o gr??fico, ?? poss??vel perceber que a media da vari??vel ppm
aumentou com o passar dos anos.

**Questao 7**

**a**

``` r
tabela_tibble <- tribble(
  ~nome,       ~altura, ~peso,
  "Ana",       155,     50,
  "Ludmilla",  158,     61,
  "Cristina",  162,     65,
  "Tereza",    168,     68,
  "Patr??cia",  170,     69,
  "Mariana",   170,     65,
  "Ana Paula", 172,     82,
  "Dirce",     173,     79
)
```

**b** A vari??vel nome ?? uma vari??vel qualitativa nominal A vari??vel
altura ?? uma vari??vel quantitativa cont??nua A vari??vel peso ?? uma
vari??vel quantitativa cont??nua

**c**

``` r
mean(tabela_tibble$peso)
```

    ## [1] 67.375

``` r
median(tabela_tibble$peso)
```

    ## [1] 66.5

``` r
sd(tabela_tibble$peso)
```

    ## [1] 10.04188

``` r
mean(tabela_tibble$altura)
```

    ## [1] 166

``` r
median(tabela_tibble$altura)
```

    ## [1] 169

``` r
sd(tabela_tibble$altura)
```

    ## [1] 6.78233

Peso: Mediana= 66,5 M??dia= 67,375 Desvio padr??o= 9,39

Altura: Mediana= 169 M??dia = 166 Desvio padr??o= 6,34

**d**

``` r
plot(tabela_1_4_$"peso", tabela_1_4_$"altura" , col = "blue", xlab = "peso", ylab = "altura", main = "tabela 1")
```

![](Atividade-Avaliativa-1_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

Aparentemente, a rela????o observada ?? que, quanto maior o peso da pessoa,
maior ?? sua altura. Entretanto existe dois valores que distoam dessa
rela????o uma delas com o mesmo peso de 65kg porem maior do que a outra de
mesmo peso, e uma pesando acima de 80kg por??m mais baixa do que a pessoa
que pesa proximo a 80kg.
