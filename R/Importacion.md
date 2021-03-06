Importacion
================

\#Creación de un objeto de Series de Tiempo y gráficas \#\# Serie de
interés

``` r
tipos88 <- read.table("/Users/sergiocalderon/Documents/GitHub/TimeSeries/Bases de Datos/Estacionarias/tipos88.dat", quote="\"", comment.char="")
Intanual=tipos88$V5  #Tipo de interés Anual
plot(as.ts(Intanual))
```

![](Importacion_files/figure-gfm/importacion-1.png)<!-- --> \#Creando y
graficando la serie de retornos para ver los cambios

``` r
camrelintanual=log(Intanual[2:length(Intanual)]/Intanual[1:(length(Intanual)-1)])
sercamrelint=ts(camrelintanual,start=c(1988,01),frequency=12)
sercamrelint
```

    ##                Jan           Feb           Mar           Apr           May
    ## 1988 -0.0647016108 -0.0741533020 -0.0070054419  0.0293291983 -0.0632213053
    ## 1989  0.0139674578  0.0344748736 -0.0294196546 -0.0059224928 -0.0012020838
    ## 1990  0.0038282443  0.0052716944 -0.0217734011  0.0009706540 -0.0130856983
    ## 1991 -0.0473362125 -0.0706593752 -0.0339776755 -0.0481090624 -0.0231102722
    ## 1992 -0.0149215258 -0.0035059797  0.0031081914 -0.0065464069  0.0244483873
    ## 1993 -0.0589149305  0.0147553635 -0.0165192353 -0.0852823342 -0.1391477367
    ## 1994  0.0060385913 -0.0121138688 -0.0203524613 -0.0056001165  0.0452893463
    ## 1995 -0.0471507488  0.0551783149 -0.0092757060 -0.0105269213  0.0060978750
    ## 1996 -0.0217146052 -0.0128283028 -0.0978837216 -0.0221283356 -0.0194630166
    ## 1997  0.0162605209  0.0369435152 -0.0513841993 -0.0618754037 -0.0136321488
    ## 1998 -0.0205721541 -0.0400524677  0.0143200538  0.0000000000 -0.0071343941
    ## 1999 -0.0065574005 -0.0032948959 -0.1116139846 -0.0186225121  0.0441248049
    ## 2000  0.0424533163  0.0360182992  0.0279087881  0.1065066476  0.0204088716
    ## 2001  0.0065574005 -0.0242569776 -0.0044742804  0.0111483875 -0.0500104206
    ## 2002  0.0255333020  0.0624354709                                          
    ##                Jun           Jul           Aug           Sep           Oct
    ## 1988  0.0259173638  0.0157958089  0.0494844305  0.1018021619  0.0140727599
    ## 1989  0.0188653617 -0.0127365037 -0.0195157587 -0.0033239525  0.0330813019
    ## 1990 -0.0039395980  0.0076678948  0.0255887121 -0.0254581467 -0.0079958481
    ## 1991  0.0332037416  0.0007904514 -0.0306482071  0.0131122882  0.0195881731
    ## 1992  0.0264563655  0.0558804584  0.0200256113  0.0000000000 -0.0038173382
    ## 1993 -0.0182263892 -0.0436960290 -0.0470847509 -0.0251694779 -0.0403551732
    ## 1994  0.0177723350  0.0162837139  0.0452920643  0.0106473407  0.0054477871
    ## 1995 -0.0088200233 -0.0286382759 -0.0419413010  0.0064563382 -0.0214024116
    ## 1996 -0.0103613554  0.0093988252 -0.0412864028 -0.0450123628 -0.0428987345
    ## 1997  0.0058651195  0.0154741966 -0.0431439460 -0.0020060187 -0.0347328069
    ## 1998 -0.0120049461 -0.0170527884 -0.0607781963 -0.0508811215 -0.0055096558
    ## 1999  0.0828059037  0.0672253058  0.0092450581  0.1019805770  0.0137553751
    ## 2000  0.0298529631  0.0327898228 -0.0152966654  0.0000000000 -0.0057971177
    ## 2001  0.0023282898 -0.0451919942 -0.0890040711 -0.1154586116 -0.0489394290
    ## 2002                                                                      
    ##                Nov           Dec
    ## 1988  0.0655985012  0.0614237306
    ## 1989  0.0439829152 -0.0160439727
    ## 1990  0.0046610949  0.0015706810
    ## 1991  0.0189797551 -0.0127697756
    ## 1992  0.0271098835 -0.0468516019
    ## 1993 -0.0593814004 -0.0181288649
    ## 1994  0.0461520378  0.0984334555
    ## 1995 -0.0316734437 -0.0536234104
    ## 1996 -0.0643298182 -0.0871631566
    ## 1997 -0.0403023790 -0.0442550090
    ## 1998 -0.1109006960 -0.0571584138
    ## 1999  0.0401660417  0.0284624647
    ## 2000 -0.0598981416 -0.0637158144
    ## 2001  0.0155524130  0.0714589640
    ## 2002

``` r
plot(sercamrelint)
```

![](Importacion_files/figure-gfm/retornos%20interes-1.png)<!-- -->

``` r
acf(sercamrelint,ci.type='ma')
```

![](Importacion_files/figure-gfm/retornos%20interes-2.png)<!-- -->

``` r
acf(sercamrelint,type='partial')
```

![](Importacion_files/figure-gfm/retornos%20interes-3.png)<!-- -->

\#Serie COLCAP

``` r
library(xts)
```

    ## Loading required package: zoo

    ## 
    ## Attaching package: 'zoo'

    ## The following objects are masked from 'package:base':
    ## 
    ##     as.Date, as.Date.numeric

``` r
library(readxl)
Colcap<- read_excel("/Users/sergiocalderon/Documents/GitHub/TimeSeries/Bases de Datos/Datos históricos COLCAP-3.xlsx")

TsColCap=xts(Colcap$Ultimo, order.by = as.Date(Colcap$Fecha, "%Y-%m-%d"))
```

    ## Warning in as.POSIXlt.POSIXct(x, tz = tz): unknown timezone '%Y-%m-%d'

``` r
plot(TsColCap)
```

![](Importacion_files/figure-gfm/Colcap-1.png)<!-- -->

``` r
acf(TsColCap)
```

![](Importacion_files/figure-gfm/Colcap-2.png)<!-- -->
