# Face/Off

BME VIK Gólyatábor előfeladat megoldása.
### 1. feladat
Nézzük meg, hogy melyik sprite-ok aktívak:
```basic
? peek(53269)
1
```
Tehát a sprite #0 aktív. A [C64 Wikiből](https://www.c64-wiki.com/wiki/Sprite#Sprite_locations) kiderül, hogy ennek a sprite-nak az y-kooordinátája az `53249` alatt van. Nézzük meg a mostani értékét!
```basic
? peek(53249)
245
```
A (maximális, csak x-irányban van plusz bit!) `255`-höz képest ez elég nagy, tehát arra következtetek, hogy a számozás fentről (vsz. a bal felső sarokból) indul. Ezért, ha nagyjából a felére állítom, nagyjából a képernyő felénél lesz. Tehát a parancs:
```basic
poke 53249, 120
```
**QED.**
### 2. feladat
A következő program a betöltött `DATA`-bufferből tölti fel a #0-ás sprite-ot.
```basic
10 pO 53269, pE(53269) aN 254: rem kikapcsoljuk
20 pO 2040, 200: rem ahova betoltjuk
30 fO i=12800 to 12862: rE b: pO i,b: nE: rem betoltjuk az adatokat
40 pO 53269, pE(53269) or 1: rem visszakapcsoljuk
```
Tehát ha a `DATA`-buffert a gyönyörű arcom adataival töltjük fel:
```basic
1 data 15,255,240,16,0,8,32,0,4,64,0,2,128,0,1,135,129,225,131,0,193,128,0,1,128
2 data 0,1,128,0,1,128,0,1,128,0,1,136,0,17,132,0,33,130,0,65,129,255,129,128,0
3 data 1,64,0,2,32,0,4,16,0,8,15,255,240
```
![vice-screen-2024081021254638](https://github.com/user-attachments/assets/c36692fb-87cd-4b7e-92c2-c574c4e75103)
|![1723319339835](https://github.com/user-attachments/assets/a3759736-79df-42f6-b974-69646ce3cb07)|
|---|
|Egy minimális demót azért a C64C-n is csináltam 😄|

