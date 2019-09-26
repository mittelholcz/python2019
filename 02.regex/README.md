
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>

<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>

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

\\(\sum\\) : az ábécé (karakterek nem üres, véges halmaza)

\\(string\\): $\sum$ karaktereiből álló véges sorozat

\\(\varepsilon\\): üres string

\\(\sum^\ast\\) : \\(\sum\\) feletti összes string halmaza ($\sum$ Kleene-lezárása)

\\(nyelv\\): \\(\sum^\ast\\) egy részhalmaza

\\(reguláris\ kifejezés\\): Stringek egy halmazát határozza meg (egy *reguláris nyelvet*). Tartalmazhat literális karaktereket ill. az alábbi műveleti jeleket.

Műveletek:

- Konkatenáció: $R^1$ és $R^2$ reguláris kifejezés, ekkor $R^1R^2$ is regularis kifejezés és $R^1R^2 = \{\alpha\beta \ :\ \alpha \in R^1\ és\ \beta \in R^2\}$.
- Unió: $R^1$ és $R^2$ reguláris kifejezés, ekkor $R^1\mid R^2$ is regularis kifejezés és $R^1\mid R^2 = \{\alpha\ :\ \alpha \in R^1\ vagy\ \alpha \in R^2\}$.
- Kleene csillag: $R$ reguláris kifejezés, ekkor $R^\ast$ is regularis kifejezés és, mely tartalmazza az üres stringet ($\varepsilon$) és $R$ elemeinek tetszőleges konkatenációját.
