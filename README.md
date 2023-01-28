# Evolució de la matriculació de vehicles elèctrics a Espanya (2018-2022)

**Estudis**: UOC - Master en Ciència de Dades  
**Assignatura**: Visualització de dades  
**Pràctica 2**: Creació i lliurament d'una visualització de dades  
**Autor**: José V. Grimalt Aranda  
Gener, 2022.  

## Taula de continguts
- [Evolució de la matriculació de vehicles elèctrics a Espanya (2018-2022)](#evolució-de-la-matriculació-de-vehicles-elèctrics-a-espanya-2018-2022)
  - [Taula de continguts](#taula-de-continguts)
  - [Contingut del vídeo](#contingut-del-vídeo)
  - [El conjunt de dades que es visualitza.](#el-conjunt-de-dades-que-es-visualitza)
  - [Creació i desenvolupament](#creació-i-desenvolupament)
  - [Les preguntes que respon la visualització.](#les-preguntes-que-respon-la-visualització)
  - [Presentació de la visualtizació](#presentació-de-la-visualtizació)
  - [Elements interactius](#elements-interactius)
  - [Conclusions](#conclusions)

## Contingut del vídeo

1. [20%] El procés de creació seguit i les decisions de disseny que s'hagin pres al llarg del desenvolupament.
2. [20%] La presentació in situ de la visualització, és a dir, comentar les característiques de la visualització mentre es navega.
3. [15%] El conjunt de dades que es visualitza.
4. [20%] Les preguntes que respon la visualització.
5. [15%] Els elements interactius disponibles com a part de la visualització.

## El conjunt de dades que es visualitza.

* Dataset original: dades de matriculacions del Portal Estadístic de la DGT
  - URL: [sedeapl.dgt.gob.es](https://sedeapl.dgt.gob.es/WEB_IEST_CONSULTA/inicio.faces)
  - Fitxers mensuals (TXT) de matriculació de la secció `Microdades`.
  - S'han utiltizat les dades des gener de 2018 fins a desembre de 2022.

* Tranformacions realitzades: 
  - S'ha utiltizat Python i el paquet Pandas per a la càrrega, neteja i transformacions de les dades.
  - Els 60 fitxers contenin un més de 8.000.000 de files que hem filtrat i agrupat
  - Transformacions: 
    - els codis de la DGT en dades qualitatives
    - classificació per tipus de motor, combustible i tecnologia
    - tractament dels valors nuls amb diferents criteris (transformació, subsitució o eliminació)
  - Filtres: 
    - Sols dades de tràmits de primeres matrícules o pas de temporal a definitiva
    - Sols dades de turismes i furgonetes (95% de les matriculacions)
    - Eliminació d'alguns outlayers (errors com vehícles elèctrics amb més de 1000 km d'autonomia)
    - Selecció dels camps finals per analitzar

* Dataset utiltizats en les visualitzacions:
  - `matricula_mensuals_españa_2018-2022`: (12 MB) conté tota la inforamació tractada i d'on es treurà el contingut dels dataset per a les visaulitzacions
  - `matriculacions_co2_2018-2022.csv`: dades agrupades per mes, per a la visaulització introductoria d'evolució
  - `matriculacions_ev_provincia_2018-2022.csv`: dades agregades per mes i províncies

## Creació i desenvolupament

El procés de creació seguit:

- Refinament del conjunt de dades per obtenis les dades requerides per a la visualització.

- Per exemple, he escollit sols turismes i furgonetes, que represeten el 95% de les matriculacions.
  
- Per la complexitat i el volum de dades del dataset original, al haver de tractar diversos error o dades no homgènies he hagut de simplificar l'objectiu inicial i deixar de banda les dades per localitats i un anàlisi més profund de les emisions de CO2.
  
- El valor de total agregat de CO2 és una aproximació dels kg/km que emetirien el conjunt de vehicles matriculats eixe periode.

- He itentat utiltzar gràfics diferents als que ja havia utilitzat en pràctiques anterior, però o bé eren massa senzill i mostraven poca informació, o bé per la seua complexitat no ha aconseguit un resultat adient.
 
- He utiltzat el gràfic de Hans Rosling perquè m'ha semblat el millor per mostrar diversos valors a l'hora: percentatge de vehicles elèctrics, total d'emisisons, total de matriculacions...

- En aquesta visualització he ajuntat als elèctrics la categoria de vehicles híbribs endollabes atés que, malgrat es pot considerar com a a vehicle de combustió, si s'utilitza resposablement per part dels propietaris (junt a futures regualcions) és un element clau per aconseguir baixar les emisison especialment en entorns urbans.

- També hauri volgut incloure alguna variable amb les dades de matriculacions acumulades, però no 

## Les preguntes que respon la visualització.

* Com ha evolucionat la matriculació de vehicles elèctrics a Espanya ens els darrers anys?

* Composició de les diferents tecnologies d'electrificació: hibridació, electrics purs i electrics endollables.
  
* Anàlisi geogràfic: Dades de percentatge de vehicles elèctrics matriculats per províncies i emissions associades.

## Presentació de la visualtizació

Característiques de la visualització mentre es navega:

- Títol: Evolució de la matriculació de vehicles elèctrics a Espanya (2018-2022)


- S'inclouen 2 gràfics d'àreres apilades per a veure les dades generals i contestar les dues primeres preguntes sobre l'evolució mensuals i els diferents tipus de tecnologies de combustió i electrificació dels vehicles. 

- Tenim un per a les dades absolutes i l'altre per a les dades relatives:
- Es pot observar que les dades, tant absolutes com relatives, són força modestes.

- En el gràfic de Hans Rosling hem utilitzat els següents elemets:
- cada cercle representa una província on s'utiltiza el color per identificar la comunitat
- la mida del cercle és proporcional al nombre de matriculacions mensuals
- l'eix X representa el percentatge de vehicles elèctrics (BEV i PHEV) matriculats sobre el total mensual
- l'eix Y el total d'emisions de CO2 en kg/km de tots els vehicles matriculats cada mes
- l'objectiu seria que els cercles anaren desplaçant-se cap a la dreta i cap avall
- Els dos cercles de major tamnany representen les províncies de Madrid i Barcelona

Evolució del vehicle elèctric a Espanya

## Elements interactius

- Com es tracta d'una història disposem dels controls de navegació entre les diapositives que la formen

- En les dues primeres visualitzacions es permet escollir els diferents tipus de propulsió des de la llegenda.
- També poder fer clic sobre qualsevol punt de les àrees per obenir un panel amb les dades corresponents.

- En la visualització de Hans Rosling podem uilitzar el control del temps per a escollir un mes de forma manual o fer una reproducció automàtica.
- També podem escollir la comunitat autonoma des de la llegenda
- I també es mostra informació completa en una panel al fer clic sobre el cercle que representa cada província


## Conclusions

- S'observa un creixement molt lent del vehicle elèctric
- Sí que hi ha un major percentatge de vehiles híbrids sobre el total de combustió
- De moment no hi ha altres alternatives significatives al vehicle elèctric, atés la baixa representació de l'hidrogen GLC, GNL, REEV
  
- Caldrà esbrinar les raons d'aquest creixement tant lent: desconfiança dels usuaris, poca inversió en punts de càrrega, dificultat de les ajudes...

