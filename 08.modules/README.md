# Másolás, modulok, fájlkezelés

(2019. 11. 19. – 8. óra)

Mittelholcz Iván

---

## 1. Másolás

### 1.1. Mellékhatás, változékonyság

Változékony (*mutable*) adattípusok (`list`, `set`, `dict`) kezelésére kétféle függvényt is írhatunk:

1. tisztát, ami új konténerrel tér vissza, az eredetit nem változtatja meg

  ```py
  def pure_increment(mylist):
      res = []
      for i in mylist:
          res.append(i+1)
      return res
```

2. mellékhatásosat, ami nem tér vissza semmivel, de megváltoztatja a paraméterként megkapott konténert

  ```py
  def increment(mylist):
      for i in range(len(mylist)):
          mylist[i] += 1
  ```

### 1.2. Másolás

Lehetőségek a másolásra:

```py
l1 = [1, 2, 3]
l2 = l1[:]
l3 = l1.copy()
```

Változtatunk, semmi probléma:

```py
increment(l2)
increment(l3)
increment(l3)
```

### 1.3. Shallow vs. deep copy

Probléma:

```py
L1 = [l1, l2, l3]
L2 = L1.copy()
increment(L1[0])
```

Megoldás:

```py
import copy
L2 = copy.deepcopy(L1)
```

#### Tanulság

Mellékhatás hatékony, de veszélyes lehet. Csak akkor használjuk, ha tényleg megéri (nagy adat).

## 2. Modulok, csomagok

### 2.1. Nyelvek felépítése

<img alt="langs" src="img/langs.png" style="width: 50%;">

b.i.: *built-in* (függvények, típusok) – nem kell telepíteni, nem kell importálni

S.L.: *Standard Library* (csomagok) – nem kell telepíteni, de importálni kell

3rd p.: *Third party* (csomagok) – telepíteni kell, imortálni kell

### 2.2. Telepítés

Python csomag telepítése rendszer szinten:

```
sudo pip3 install package_name
```

Python csomag telepítése felhasználóként:

```
pip3 install --user package_name
```

Telepített csomagok listázása:

```
pip3 freeze
```

Telepített csomag törlése:

```
pip uninstall package_name
```

Dokumentáció: <https://pip.pypa.io/en/stable/>

### 2.3. Importálás

Csomag importálása:

```py
import package

package.fun()
```

Csomag egy darabjának importálása (függvény, típus, akármi):

```py
from package import fun

fun()
```

Csomag, vagy egy darabjának importálása más néven:

```py
import package1 as pkg1
from package2 import function as fun

pkg1.fun()
fun()
```

### 2.4. Python Standard Library

Pár fontosabb csomag:

- `sys`: magával a pythonnal kapcsolatos dolgok
- fájlok, könyvátrak, stb: `os`, `glob`
- szövegek: `string`, `re` (reguláris kifejezések)
- `collections`: továbib gyűjteményes adattípusok
- `pprint`: printelés csinosan
- `csv`: CSV és TSV fájlok kezelése
- matek: `random`, `math`, `statistics`

Dokumentáció: <https://docs.python.org/3/library/index.html>

### 2.5. Saját modulok és csomagok írása 

- *modul*: Fájl, python kóddal. Importáláskor a fájlnevet adjuk meg, a '.py' végződés nélkül.
  - Ha elérési utat kell megadnunk, akkor a `/` helyett a `.`-ot használjuk szeparátorként (`import a.b`).
- *csomag*: könyvtár, python fájlokkal és egy `__init__.py` fájl.
  - Az `__init__.py` maradhat üresen is (ekkor a fájlokat külön-külön kell importálni), de definiálhatjuk az `__all__` válozóban a csomagszinten delegálandó válozók, függvények, egyebek listáját (l. az `src/` könyvtárat)
- olvasnivaló, ha szeretnénk ilyet csinálni: <https://docs.python.org/3/tutorial/modules.html>
- olvasnivaló, ha saját *pip*-pel telepíthető csomagot szeretnénk csinálni: <https://packaging.python.org/tutorials/packaging-projects/> (haladó)

### 2.6. Kódszervezés

Legyen a kód futtatható és importálható is:

```py
import sys

def hasznos_fuggveny(param1, param2):
   # ...
   return 42
   
if __name__ == '__main__':
    hasznos_fuggveny(sys.argv[1], sys.argv[2])
```

## 3. Fájlkezelés

### 3.1. Fájl olvasása

Fájl megnyitása:

```py
f = open('path/to/file', 'r')
```

Szöveges fájl tartalmának beolvasása strgingbe:

```py
text = f.read()
```

Szöveges fájl sorainak beolvasása listába:

```py
lines = f.readlines()
```

Szöveges fájl bejárása közvetlenül:

```py
for line in f:
    process(line)
```

Fájl bezárása:

```py
f.close()
```

### 3.2. Fájl írása

Fájl megnyitása írásra:

```py
f = open('path/to/file', 'w')
```

Fájl megnyitása hozzáfűzésre:

```py
f = open('path/to/file', 'a')
```

Írás fájlba:

```py
f.write(text)
```

Vagy

```py
print(text, file=f)
```

Fájl bezárása: volt már...

### 3.3. `with` – avagy a `close()` megspórolása

(Úgy hívják, hogy kontextus menedzser...)

```py
with open('path', 'r') as inp:
    for line in inp:
        process(line)
        # ...
```

### 3.4. stdin, stdout, stderr

Nem kell megnyitni (és bezárni sem), csak importálni!

Olvasás a stdin-ről:

```py
import sys

for line in sys.stdin:
    process(line)
```

Írás:

```py
sys.stdout.write(text)
```

vagy

```py
print(text, file=sys.stdout)
```

stderr: ugyanez

## 4. Feladatok

1. Írjatok egy parancssorból futtatható programot ami a stdin-ról olvas, a stdout-ra ír, és szógyakoriságot számol (csökkenő sorrend)!
2. Ugyan ez, de lehessen parancssorból is futtatni és modulként is importálni.
3. Ugyan ez, de paranccsoros futtatásnál lehessen neki fájlt megadni és csak akkor olvasson a stdin-ről, ha nincs fájlnév megadva neki.
