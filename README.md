Operaciones básicas con matrices
================

``` r
#Institucion: Programa de Ingenieria en Topografia de las Unidades Tecnológicas de Santander

# autor: "Aponte Saravia Jhonathan"
```

## Descripciones preliminares

En este proceso se intenta de presentar algunas operaciones básicas de
algrbra lineal con matrices, siendo ello la primera aproximación para
realizar operaciones matriciales con datos espaciales, ya que estos
datos como los imagenes de satelite, los modelos digitales de elevacion,
está compuesta por una estructura rectangular, por ello se intenta
abordar estos procesos utlizando programas de codigo libre, con el
proposito de mostrar de manera sencilla las opereciones y sirva de guia
de aprendizaje para los estudiantes de los programas de ingenieria y
público interesado, considerando el ambito nacional e internacional.

## Generando matrices

A continuación se muestran las opreaciones básicas de matrices, tales
como la suma, la resta, la multiplicación por valores escalares,
producto de matrices y operaciones de potencia con matrices, utilizando
R Package. En tal sendido, se presentan algunos procesos de las
operaciones básicas antes mencionados:

``` r
A<- matrix(4:16,nrow = 4,byrow = TRUE)
```

    ## Warning in matrix(4:16, nrow = 4, byrow = TRUE): la longitud de los datos [13]
    ## no es un submúltiplo o múltiplo del número de filas [4] en la matriz

``` r
A
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    4    5    6    7
    ## [2,]    8    9   10   11
    ## [3,]   12   13   14   15
    ## [4,]   16    4    5    6

``` r
# Creando valores matriciales a partir de los datos vectoriales

a<- c(6,7,8,0)
b<- c(2,4,5,3)
c<- c(9,6,3,2)
d<- c(5,2,1,8)

# Convertiendo en matriz

B <-rbind(a,b,c,d)
B
```

    ##   [,1] [,2] [,3] [,4]
    ## a    6    7    8    0
    ## b    2    4    5    3
    ## c    9    6    3    2
    ## d    5    2    1    8

#### Suma de matrices

``` r
S <- A+B
S
```

    ##   [,1] [,2] [,3] [,4]
    ## a   10   12   14    7
    ## b   10   13   15   14
    ## c   21   19   17   17
    ## d   21    6    6   14

#### Resta de matrices

``` r
R1<- A-B
R1
```

    ##   [,1] [,2] [,3] [,4]
    ## a   -2   -2   -2    7
    ## b    6    5    5    8
    ## c    3    7   11   13
    ## d   11    2    4   -2

``` r
r2 <- B-A
r2
```

    ##   [,1] [,2] [,3] [,4]
    ## a    2    2    2   -7
    ## b   -6   -5   -5   -8
    ## c   -3   -7  -11  -13
    ## d  -11   -2   -4    2

#### Multiplicación de una matriz por un valor escalar

``` r
m <- 4*B
m
```

    ##   [,1] [,2] [,3] [,4]
    ## a   24   28   32    0
    ## b    8   16   20   12
    ## c   36   24   12    8
    ## d   20    8    4   32

#### multiplicación de matrices

``` r
M <- A%*%B 
M
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]  123   98   82   83
    ## [2,]  211  174  150  135
    ## [3,]  299  250  218  187
    ## [4,]  179  170  169   70

cargamos la libreria

``` r
library(Biodem)
```

#### Calculamos los valores de la transpuesta

``` r
AA<-mtx.exp(A,2)
AA
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]  240  171  193  215
    ## [2,]  400  295  333  371
    ## [3,]  560  419  473  527
    ## [4,]  252  205  236  267

``` r
M==AA
```

    ##       [,1]  [,2]  [,3]  [,4]
    ## [1,] FALSE FALSE FALSE FALSE
    ## [2,] FALSE FALSE FALSE FALSE
    ## [3,] FALSE FALSE FALSE FALSE
    ## [4,] FALSE FALSE FALSE FALSE

#### Algebra lineal de matrices (transpuesta)

``` r
tb<- t(B)
tb
```

    ##      a b c d
    ## [1,] 6 2 9 5
    ## [2,] 7 4 6 2
    ## [3,] 8 5 3 1
    ## [4,] 0 3 2 8

#### Estimando la diagonal de la matriz

``` r
db <- diag(B)
db
```

    ## [1] 6 4 3 8

#### Calculo de la traza de una matriz, que es la sumatoria de la diagonal

``` r
tr <- sum(db)
tr
```

    ## [1] 21

#### Hallando el valor de la determinate

``` r
det <-det(B)
det
```

    ## [1] -372

#### Calculo de la inversa en una matriz

``` r
i <- solve(B)
i
```

    ##                a          b            c           d
    ## [1,]  0.35483871 -0.5322581 -0.137096774  0.23387097
    ## [2,] -0.76344086  0.9784946  0.575268817 -0.51075269
    ## [3,]  0.52688172 -0.4569892 -0.400537634  0.27150538
    ## [4,] -0.09677419  0.1451613 -0.008064516  0.07258065

#### descomposición de la matriz

``` r
qr(B)
```

    ## $qr
    ##          [,1]       [,2]       [,3]      [,4]
    ## a -12.0830460 -9.4347071 -7.4484530 -5.296678
    ## b   0.1655212 -3.9982873 -6.4342618  2.494219
    ## c   0.7448453 -0.5451373  1.4563044  3.842879
    ## d   0.4138029 -0.6363302 -0.5026538  5.287378
    ## 
    ## $rank
    ## [1] 4
    ## 
    ## $qraux
    ## [1] 1.496564 1.545811 1.864488 5.287378
    ## 
    ## $pivot
    ## [1] 1 2 3 4
    ## 
    ## attr(,"class")
    ## [1] "qr"

#### calculo de la varianza de los datos de la matriz

``` r
var(B)
```

    ##           [,1]      [,2]      [,3]     [,4]
    ## [1,]  8.333333  3.166667 -1.166667 -2.50000
    ## [2,]  3.166667  4.916667  5.083333 -7.25000
    ## [3,] -1.166667  5.083333  8.916667 -8.75000
    ## [4,] -2.500000 -7.250000 -8.750000 11.58333
