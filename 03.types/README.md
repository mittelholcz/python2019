# Programozás, típusok, értékadás

Vázlat:

1. Mi a programozás?
    - algoritmus implementálása egy programozási nyelven
    - Mi az algoritmus? Megengedett műveleteket tartalmazó eljárás, ami megold egy problémát.
        - I/O
        - megengedett műveletek: összetett feladat felbontása egyszerűbbekre, egészen addig, amíg olyan egyszerű feladatokhoz nem jutunk, amiknek már tudjuk a megoldását (a nyelv tartalmazza, pl. összehasonlítás)
    - summa: probléma -> algoritmus -> nyelv kiválasztása -> implementálás -> használat: probléma megoldva
1. Mi történik a gépben, ha futtatunk egy programot?
    - program a háttértáron (merevlemez)
    - beolvasás a memóriába
        - kód (utasítások)
        - adatok
    - kód futtatása: az adatokon a processzor elvégzi az utasításokat
    - kilépés a programból, a memória felszabadíthatóvá válik
1. Hogyan futtatunk egy programot linux-környezetben?
    - előfeltétel: fordítás vs. értelmezés
    - értelmezés: van egy program, az értelmező, ami egy utasítássort beolvas, és lefordítja gépi nyelvre
    - futtatás: `interpreter fájl`, pl. `bash myscript.sh`, vagy `python3 myscript.py`
    - első szkriptjeink megírása és futtatása
1. Hogyan adjunk egy változónak értéket?
    - az egyenlőségjel nem állítás, hanem utasítás (nem "*a* egyenlő *b*-vel", hanem "*a* **legyen** egyenlő *b*-vel")
1. Mik a főbb típusok pythonban? Mik ezek metódusai? Mik a műveletek? Mik a függvények? Mik a paraméterek? Megannyi kérdés!
