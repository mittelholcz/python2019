# Objektumorientált programozás és egyebek

(2019. 12. 03. – 10. óra)

Mittelholcz Iván

---

## 1. Objektumorientált programozás

## 1.1. Felhasználói típusok

Alapfogalmak:

- Osztály (class, type): Dolgok egy modellezendő csoportja (számok, szavak, emberek, épületek, akármi).
- Objektum (object, instance): Osztályok példányai vagy egyedei.

Változók / adatok:

- Osztályváltozó: Osztály szintű változók (minden példánynál egyezik az értékük)
- **Példányváltozó**: Példány szintű változók (minden példánynak saját van). Általában a konstruktorban definiáljuk őket.

Függvények / metódusok:

- Osztálymetódus: Az osztály egészével kapcsolatos függvény, ami csak osztályváltozókhoz fér hozzá.
- **Példánymetódus**: Olyan függvény, ami csak egy-egy példánnyal kapcsolatos, osztály- és példányváltozókhoz egyaránt hozzáfér.

## 1.2. Példa

```py
from datetime import date

class Person:

    # konstruktor:
    def __init__(self, name, year):
        self.name = name
        self.year = date

    def get_age(self):
        return date.today().year - self.year

mari = Person('Mária', 1969)
print('{0} {1}-ben született.'.format(mari.name, mari.year))
print('{0} {1} éves.'.format(mari.name, mari.get_age()))
```

## 1.3. Szintaxis

- definíció: `class` + név + `:`, alatta indentálva a változók és metódusok

- példányfüggvény:
  - definiálása: Sima függvénydefiníció a `class` alatt indentálva. Első paramétere legyen mindig a `self`!
  - hívása: Példányon lehet meghívni, ponttal elválasztva (`peldany.metodus(...)`). Az első paramétert (`self`) soha nem kell megadni (az a példány maga – olyan, mintha azt mondanák: `metodus(peldany, ...)`).
- példányváltozó:
  - definiálása: *konstruktor* függvényben adjuk meg (`def __init__(self, x): self.x = x`)
  - hivatkozás rá: Példányon, ponttal elválasztva (`peldany.x` vagy értékadásnál `peldany.x = 11`)
- példányosítás: Az osztály nevét függvényként hívjuk, a konstruktor paramétereivel (`self` nélkül).

  ```py
  Osztaly(param1, param2)
  ```

## 1.4. Öröklődés

Egy osztály alosztálya, specializált részhalmaza (pl. szó–ige, ember–nyelvész, stb.) örökli az alap osztály a változóit és metódusait. Szokás *is a* relációnak is hívni, szemben a példányváltozók jelentette *has a* relációval.

Szintaxis: Osztály definiálásánál az osztály neve után zárójelben szerepel az ős osztály. Az ősre a `super()` függvénnyel lehet hivatkozni.

Példa:

```py
class Linguist(Person):
    def __init__(self, name, year, spec):
        self.spec = spec
        super().__init__(name, year)
    def get_info(self):
        return '{0} {1} éves, szakterülete a {2}'.format(
            self.name, self.year, self.get_age())

chom = Linguist('Chomsky', 1928, 'szintaxis')
print(chom.get_info())
```

## 1.5. Irodalom

- <https://docs.python.org/3/tutorial/classes.html>
- <https://realpython.com/python3-object-oriented-programming/>

## 2. Vegyes apróságok

## 2.1. Stringek formázása

- Stringekbe bármilyen érték illeszthetó a `str.format()` metódussal.
- A stringben az illesztés helyét kapcsols zárójelekkel + sorszámmal (0-val kezdünk) jelöljük.
- A `format()` paramétereiként felsorolt értékek behelyettesítődnek a stringbe, a #0 helyére a format 1. paramétere kerül, az #1 helyére a 2. paraméter kerül, sít.

Példa:

```py
x = 10
y = 20

s = '{0} meg {1} az {2}. A {0} szép szám!'
print(s.format(x, y, x+y))
# output: '10 meg 20 az 30. A 10 szép szám!'
```

- További formázási lehetőségek: <https://docs.python.org/3/library/string.html#formatstrings>
- *f-string*ek (3.7 vagy újabb python kell hozzá): <https://realpython.com/python-f-strings/>

## 2.2. Listák, halmazok és szótárak röviden

Listák:

```py
l1 = [1, 2, 3, 4, 5]
# szűrés (csak páratlanok):
l2 = [x for x in l1 if x % 2 != 0]
# leképezés (négyzetszámokra):
l3 = [x**2 for x in l2]
# egy lépésben:
l4 = [x**2 for x in l1 if x % 2 != 0]
```

Halmazok és szótárak hasonlóan:

```py
# szöveg szavainak halmaza:
s = {w for w in text.split()}
# szavak és hosszúságaik szótára:
d = {w: len(w) for w in text.split()}
```

## 2.3. Dokumentációs stringek

- Függvényeket, modulokat és osztályokat lehet és hasznos dokumentálni.
- Ehhez egy közvetlenül a definíció után következő név nélküli stringet lehet használni.
  - A dokumentáció 1. sora tartalmazza a függvény/osztály/modul rövid leírását.
  - Ha részletezni akarjuk, akkor üres sor, majd lehet részletezni a működést, lehet pl. a paraméterekről és a visszatérési értékről írni (opcionális)
- Több soros stringet hármas idézőjelpár között lehet megadni (`'''` vagy `"""`). Ezt máshol is lehet használni (pl. változó megadásánál).

```py
def fun():
    """Kiírja, hogy 'fun'.

    Nincs se paraméter, se visszatérési érték.
    """
    print('fun')

# interaktív python-nál hasznos (less-szerű felület)
help(fun)

# sima print, bármikor használható
print(fun.__doc__)
```
