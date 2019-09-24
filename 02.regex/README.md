# Reguláris kifejezések

(2019. 10. 01. - 2. óra)

Mittelholcz Iván

---

## 1. Stringmanipuláció

Keresés:

`grep <kifejezés>`: Fájl vagy a stdin szűrése, a kifejezést tartalmazó sorokra.

- `-i`: ignore case
- `-v`: fordított működés - a nem illeszkedő sorokat átengedi, az illeszkedőket kiszűri
- `-r <könyvtár>`: rekurívan keres a könyvtár minden alkönyvtárjában

Csere:

`sed "s/mit/mire/g"`: Kifejezés keresése és cseréje fájlban vagy stdin-en.

Rendezés:

`sort`: Rendezés.

- `-n`: numerikus rendezés (a default lexikális helyett, pl. 10 > 9)
- `-r`: fordított sorrend

Egyelés:

`uniq`: Sorok egyelése. Csak az egymást követő azonos sorokat egyeli, ezért előtte szükséges lehet rendezni.

- `-c`: a sorok elé írja, hány darab volt belőlük

### Feladat

Csináljunk szógyakorisági listát a tmp könyvtárunkban lévő fájlokból.

- segítség: sortörést a `\n` karktersorozattal lehet helyettesíteni
