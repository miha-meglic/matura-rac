# Centralna procesna enota (CPE / CPU)

... je osrednji del računalnika, ki obdeluje podatke in nadzoruje/upravlja ostale naprave. Sekvenčno bere in izvaja ukaze iz pomnilnika.

Lastnosti CPE:

- bitna širina oz. število bitov, ki jih obdela hkrati (običajno 8/16/32/64 bitov)
- takt oz. frekvenca izvrševanja ukazov
- takt podatkovnih vodil

## Izvajanje ukaza CPE

Procesor (v teoriji) pri izvajanju ukaza sledi sledečim korakom:

- Fetch (pridobi ukaz iz pomnilnika)
- Decode (analizira / dekodira ukaz)
- Execute (izvede ukaz)
- Store / Writeback (shrani rezultate)

Odvisno od implementacije procesorja je teh korakov lahko tudi več.

## Krmilna enota

- krmili, nadzoruje in usklajuje delocanje vseh enot/naprav
- organizira prenose podatkov
- razpoznava, analizira in skrbi za izvajanje ukazov

### Programski števec

... je register v CPE, ki skrbi za naslavljanje ukazov v pomnilniku. Običajno torej samo inkrementira čez naslove, v primeru skoka (kot npr. pri izvajanju `if` stavka ali klicu funkcije) pa se premakne na naslov podani naslov.  
Ob resetu se vsi registri v procesorju ponastavijo na znano začetno, torej se tudi programski števec ponastavi na začetni naslov.

## Aritmetično logična enota (ALE / ALU)

... opravlja računske/aritmetične in logične operacije.
