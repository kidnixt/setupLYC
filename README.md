# setupLYC
:heavy_exclamation_mark:**Esta guía no es definitiva, puede haber (es muy probable que lo haya) más de una forma de hacer una instalación teniendo el mismo efecto. Utilizá la manera en la que te sientas más comodo**

## Instalación de GHCup en Linux
Antes de cualquier cosa, es necesario tener instalado Haskell (y todos los paquetes que este trae, en especial cabal o stack). Para hacer esto simplemente ir a este [link](https://www.haskell.org/ghcup/)

Luego de haber instalado GHCup con el comando que nos dice esa página. Ponemos en nuestra terminal el comando que aparece a continuación y debería pasar lo que se muestra en la imagen
```
ghcup tui
```

<p align = center>
<img src = "https://i.imgur.com/ecm0jZ1.png">
</p>
<p align = center>
Podemos ver que tenemos instalado Haskell, Stack y cabal
</p>


### Instalación de BNFC, Alex y Happy
Para poder trabajar en los laboratorios es necesario tener instalado:

 - **BNFC:** Software para poder ejecutar codigo escrito en la sintaxis BNFC y parsearlo.
 - **Alex:** El generador del lexer.
 - **Happy:** El generador del parser.

Para instalar esto simplemente pondremos los siguientes tres comandos:
```
cabal install BNFC
cabal install alex
cabal install happy
```

### Instalación extensión VSCode
Para poder tener el "lenguaje" de BNFC en nuestra IDE es necesaria instalar la siguiente extensión. 
<p align = center>
<img src = "https://i.imgur.com/Vavt9uL.png">
</p>
Sino estaremos escribiendo texto plano, aunque a niveles de las herramientas (alex, happy) esto da igual. 

## Ejemplo del Libro

:heavy_exclamation_mark:**Todo esto se hizo desde bash**
Pondremos el siguiente código en un archivo que se llame 
```
"Calc.cf"
```

```
EAdd. Exp ::= Exp "+" Exp1 ;
ESub. Exp ::= Exp "-" Exp1 ;
EMul. Exp1 ::= Exp1 "*" Exp2 ;
EDiv. Exp1 ::= Exp1 "/" Exp2 ;
EInt. Exp2 ::= Integer ;

coercions Exp 2 ;
```

Luego pondremos el siguiente comando
```
bnfc -m Calc.cf
```
Se nos deberían haber generado variso archivos entre ellos uno que se llama "Makefile", es el necesario para poder compilar nuestro compilador. Ejecutamos el siguiente comando

    make

Y si tenemos todo instalado correctamente deberia dar un output como este
<p align = center>
<img src = "https://i.imgur.com/gVqs9WS.png">
</p>

Luego, poniendo el siguiente comando 

    echo "5 + 6 * 7" | ./TestCalc

<p align = center>
<img src = "https://i.imgur.com/gRwbk96.png">
</p>


