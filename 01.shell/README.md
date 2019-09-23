# A parancssor használatának alapjai

(2019. 09. 24. - 1. óra)

Mittelholcz Iván

---

## 1. Alapfogalmak

Kernel (rendszermag): erőforrások kezelése, absztrakció

- feladatütemezés (folyamatok hozzáférése a CPU-hoz)
- memória (RAM) kezelés
- fájlrendszer
- stb.

Alkalmazások:

- külön programok
- a kernelen keresztül férnek hozzá a gép erőforrásaihoz

Shell (rendszerhéj): karakteres felhasználói felület alkalmazások futtatására

- maga is alkalmazás, több féle van, cserélhető
- mostanában Linux-ok többségén és OS X-en a bash az alapértelmezett
- programozási nyelv is

## 2. Törtlnelem

- 1969: UNIX oprendszer. Kezdetben hozzávágják mindenkihez, aki gépet vesz, aztán rájönnek, hogy a szoftver is lehet üzlet $\to$ zárt lesz.
- 1983: GNU (GNU's Not Unix). UNIX-szerű, de nem tartalmaz UNIX-ból származó kódot (mindent újraimplementálnak nulláról). Open source. Kernel nincs, minden más van (C fordító, debugger és library, shell, make, TeX, ablak kezelő, stb.).
- 1991: Linux kernel.
- Azóta:
  - __UNIX-like__: olyan rendszerek, amik *hasonlóan néznek ki*, mint a UNIX (GNU/Linux, BSD, OS X, stb.)
  - __GNU/Linux__: Linux kernel + GNU eszközök + mindenféle más. Röviden ezt nevezik Linux-nak.
  - __Linux disztribúció__: *GNU/Linux* + csomagkezelő, grafikus felület, egyéb programok

## 3. Parancsok


```sh
ls # sima parancs
ls -l # kapcsoló
ls /home # argumentum / paraméter
ls -al *rc # wildcard
```

paraméterek:

* opcionálisak vagy kötelezőek
* rövidítettek vagy hosszúak (pl. `-a` vagy `--all`)
* össze nem vontak vagy összevontak (pl. `-a -l` vagy `-al`) -- ez csak a rövidítettekre működik!
* értéktelenek vagy értékesek esetleg opcionálisan értékesek (pl. az `ls --color` ugyan az, mint az `ls --color=always`, de nem ugyanaz, mint a `--color=never`).

kapcsolók

argumentumok
