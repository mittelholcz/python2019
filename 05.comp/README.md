# Összetett adattípusok

(2019. 10. 21. – 5. óra)

Mittelholcz Iván

---

## 1. Rendezett sorozatok (*tuple*)

- objektumreferenciák rendezett sorozata
  - nem magukat az objektumokat tárol, hanem objektumokra való hivatkozásokat
  - nem változtatható (*immutable*)
- jelölés: `(x1, x2, ...)`
- indexelhető (`t[i]`) és szeletelhető (`t[i:j]`, ill. `t[i:j:k]`) a *string*ekhez hasonlóan
- kapcsolódó függvények: `tuple()`, `len()`, `min()`, `max()`, `sum()`, `all()`, `any()`, `sorted()`
- műveletek: `+`, `*`, `in`, `not in`
- metódusok: `t.index(x)`, `t.count(x)`

## 2. Listák (*list*)

- ugyan az, mint a *tuple*, csak változtatható (*mutable*)
- jelölés: `[x1, x2, ...]`
- kapcsolódó függvények: `list()`
- további műveletek: `l[i] = x`, `l[i:j] = [...]`, `del l[i]`, `del l[i:j]`
- további metódusok: `l.append(x)`, `l.pop()`, `l.insert(x)`, `l.remove(x)`, `l.sort()`

### 2.1. Feladat

1. Bontsunk fel egy szöveget szavak listájára!
1. Rendezzük a listát ábécé sorrendbe!

## 3. Halmazok (*set*)

- objektumreferenciák halmaza
  - minden értéket csak egyszer tárol
  - sorrend nem számít
  - változtatható (*mutable*)
- jelölés: `{x1, x2, ...}`
- nem indexelhető!
- kapcsolódó függvények: `set()`, `len()`, `min()`, `max()`, `sum()`, `all()`, `any()`, `sorted()`
- műveletek: `in`, `not in`, `s1 | s2`, `s1 & s2`, `s1 - s2`, `<`, `<=`, `>`,  `>=`
- metódusok: `s.add(x)`, `s.remove(x)`, `s.discard(x)`, `s.pop()`

### 3.1. Feladat

1. Bontsunk fel egy szöveget szavak listájára!
1. Milyen szavak szerepelnek a szövegben?

## 4. Szótárak (*dict*)

- Kulcs-érték párok halmaza
  - minden kulcsnak egyedinek kell lennie
  - a kulcsoknak változtathatatlanoknak kell lenniök
  - sorrend nem számít
  - maga a szótár változtatható (*mutable*)
- jelölés: `{k1: v1, k2: v2, ...}`
- indexelhető kulccsal, de nem sorszámmal: `d[k]`
- nem szeletelhető!
- kapcsolódó függvények: `dict()`, `len()`, `min()`, `max()`, `sum()`, `all()`, `any()`, `sorted()`
- műveletek: `key in d`, `key not in d`, `d[k] = v`, `del d[k]`
- metódusok: `d.get(k)`, `d.keys()`, `d.values()`, `d.items()`
