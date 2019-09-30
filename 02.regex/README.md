# Reguláris kifejezések

(2019. 10. 01. - 2. óra)

Mittelholcz Iván

---

## 1. Stringmanipuláció

### Keresés

`grep <kifejezés>`: Fájl vagy a stdin szűrése, a kifejezést tartalmazó sorokra.

- `-i`: ignore case
- `-v`: fordított működés - a nem illeszkedő sorokat átengedi, az illeszkedőket kiszűri
- `-r <könyvtár>`: rekurzívan keres a könyvtár minden alkönyvtárjában

### Csere

`sed "s/mit/mire/g"`: Kifejezés keresése és cseréje fájlban vagy stdin-en.

### Rendezés

`sort`: Sorok ábécé szerinti rendezése.

- `-n`: numerikus rendezés (a default lexikális helyett, pl. 10 > 9)
- `-r`: fordított sorrend

### Egyelés

`uniq`: Dupla sorok szűrése. Csak az egymást követő azonos sorokat egyeli, ezért előtte szükséges lehet rendezni.

- `-c`: a sorok elé írja, hány darab volt belőlük

### Feladat

Csináljunk szógyakorisági listát a tmp könyvtárunkban lévő fájlokból.

- segítség: sortörést a `\n` karktersorozattal lehet helyettesíteni

## Reguláris kifejezések elmélete

ábécé: karakterek nem üres, véges halmaza

string: az ábécé karaktereiből álló véges sorozat

üres string: nulla hosszúságú string

Kleene-csillag (v. lezárt): az ábécé feletti összes string halmaza

nyelv: Kleene-lezárt egy részhalmaza

reguláris kifejezés: Stringek egy halmazát határozza meg (egy *reguláris nyelvet*). Tartalmazhat literális karaktereket ill. az alábbi műveleti jeleket.

Műveletek:

- Konkatenáció: *R1* és *R2* reguláris kifejezés, ekkor *R1R2* is regularis
  kifejezés és *R1R2* = {*ab* : *a* eleme *R1* és *b* eleme *R2*}.
- Unió: *R1* és *R2* reguláris kifejezés, ekkor *R1 unió R2* is regularis
  kifejezés és *R1 unió R2* = {*a* : *a* eleme *R1* vagy *a* eleme *R2*}.
- Kleene csillag: *R* reguláris kifejezés, ekkor *R\** is reguláris
  kifejezés, mely tartalmazza az üres stringet és *R* elemeinek tetszőleges
  konkatenációját.
