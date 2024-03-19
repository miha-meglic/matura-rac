# Številski sistemi

Osnovna gradbena enota računalnikov je tranzistor, ki pri svoje delovanju pozna dve stanji - "ugasnjeno" / **false** / **0** in "prižgano" / **true** / **1**, zato računalnik na najnižjem nivoju operira z binarnimi števili oz. **biti**.

Ker pa je binarni zapis običajno precej dolg in človeku nepregleden, v računalništvu običajno uporablajmo šestnajstiški zapis. Ker pa ljudje načeloma manipuliramo s števili v desetiškem sistemu, moramo razumeti pretvorbe med vsemi tremi sistemi.

**Dvojiški sistem:** uporabljamo samo števki 0 in 1

**Šestnajstiški sistem:** poleg števk 0-9 uporabljamo še črke A = 10, B = 11, C = 12, D = 13, E = 14 in F = 15

## Pretvorbe med sistemi

### Desetiški -> Dvojiški

Postopek:  
1. desetiško število delimo z dve (uporabimo celoštevilsko deljenje in zapišemo ostanek)
2. rezultat vzamemo in ponovno delimo z dve in zapišemo ostanek
3. ponavljamo drugi korak, dokler ni rezultat deljenja 0
4. dvojiško število preberemo iz ostankov deljenja (od zadnjega proti prvemu ostanku)

Primer - 42 iz desetiškega v dvojiški sistem:

$$
\begin{align*}
	42_{(10)} / 2 &= 21 &\text{ostanek}\;0 \\
	21_{(10)} / 2 &= 10 &\text{ostanek}\;1 \\
	10_{(10)} / 2 &= 5 &\text{ostanek}\;0 \\
	5_{(10)}  / 2 &= 2 &\text{ostanek}\;1 \\
	2_{(10)}  / 2 &= 1 &\text{ostanek}\;0 \\
	1_{(10)}  / 2 &= 0 &\text{ostanek}\;1 \\
	\hline
	42_{(10)} &= &101010_{(2)}
\end{align*}
$$

### Dvojiški -> Desetiški

Postopek:  
1. števila pomnožimo s faktorjem 2^i, kjer je i indeks števke (začnemo iz desne, z i = 0)
2. seštejemo zmnožke

Primer - 10011 iz dvojiškega v desetiški sistem:

$$10011_{(2)}= 1 \times 2^4 + 0 \times 2^3 + 0 \times 2^2 + 1 \times 2^1 + 1 \times 2^0 = 19_{(10)}$$

### Dvojiški -> Šestnajstiški

Postopek:
1. število od desne ločujemo na štiri števke dolge odseke
2. odsek pretvorimo v šestnajstiški sistem
3. odseke nazaj sestavimo v celoto

Primer - 11010110 iz dvojiškega v desetiški sistem:

$$1101\:0110_{(2)} = (1 \times 2^3 + 1 \times 2^2 + 1 \times 2^0 = 13_{(10)} = D_{(16)}) , (1 \times 2^2 + 1 \times 2^1 = 6_{(10)} = 6_{(16)}) = D6_{(16)}$$

### Šestnajstiški -> Dvojiški

Vsaka števka postane štiri števke dvojiškega števila - obraten postopek kot pri (2) -> (16).

### Desetiški -> Štestnajstiški

Isto kot (10) -> (2), samo da delimo s 16.

### Štestnajstiški -> Desetiški

Isto kot (2) -> (10), samo da je osnova potenc 16.

## Zapis ne-številskih podatkov

### Barve

Barve zapisujemo v formatu RGB, v katerem za vsako barvo rezerviramo 8-bitno vrednost. Običajen zapis barve se začne z lojtrico (simbol "#"), ki ji sledita dve cifri (v šestnajstiškem zapisu) za vsako od komponent (R - red, G - green, B - blue).

Primeri: <span style="color: #ff0000;">rdeča - #ff0000</span>, <span style="color: #00ff00;">zelena - #00ff00</span>, <span style="color: #0000ff;">modra - #0000ff</span>, <span style="color: #ffff00;">rumena - #ffff00</span>, <span style="color: #00ffff;">cyan - #00ffff</span>, <span style="color: #ff00ff;">magenta - #ff00ff</span>

Obstajajo tudi drugi zapisi, kot so RGBA, HSL, ...

### Znaki / črke

Tako kot barve je tudi zapis znakov standardiziran. Najpogostejša standarda s katerimi se boste srečevali sta ASCII in UNICODE.

**ASCII tabela:**

![ASCII Table](https://upload.wikimedia.org/wikipedia/commons/1/1b/ASCII-Table-wide.svg)
