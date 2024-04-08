# Uvod v Linux

V nadaljevanju se boste spoznali z nekaj osnovnimi ukazi, ki jih uporabljamo v ukazni vrstici. Med aplikacijami poiščemo Terminal oziroma gnome-terminal in ga odpremo.

Ukazna vrstica bo izgledala nekako takole:

```bash
user@machine:/working/directory$
```

Za domači imenik Linux uporablja okrajšavo `~`. Ta se ponavadi nahaja na `/home/username/`.

## Uporabniško ime in sprememba gesla

Naše uporabniško ime lahko poizvedemo z ukazom `whoami`.

Najprej bomo spremenili naše geslo za prijavo v sistem. To storimo z ukazom `passwd`.

Nato se odjavimo iz uporabniškega računa in ponovno prijavimo, da preverimo, če se je naše geslo res spremenilo.

## Uporaba ukazov

Kadar smo negotovi o uporabi nekega ukaza, se lahko o njem pozanimamo z vgrajenim uporabniškim priročnikom `man` ali pa z zastavico `--help`. Zastavico praviloma pišemo za ukazom, `man` pa uporabimo pred ukazom (npr. `man ls`).

Če želimo "počistiti" izpis na terminalu, uporabimo ukaz `clear`. Lahko tudi pridobimo zgodovino ukazov, ki smo jih uporabili, z ukazom `history`.

## Navigacija po imenikih

Z ukazom `pwd` pridobimo absolutno pot do imenika, kjer se trenutno nahajamo.

Sedaj želimo izpisati vsebino trenutnega imenika. Za to uporabimo ukaz `ls`.

Za podrobnejši izpis datotek uporabimo zastavico `-l`.

```bash
user@machine:~$ ls -l
total 2612
drwxr-xr-x  1 user      user          342 apr  8 21:21 Documents
...
```
Linux pa pozna tudi skrite datoteke, (ti. "dotfiles"), ki se začnejo s piko, npr. `.bashrc`. Te lahko izpišemo s pomočjo zastavice `-a`. Če želimo obe možnosti združiti, lahko uporabimo obe zastavici hkrati:

```bash
user@machine:~$ ls -la
total 2612
drwx--x---+ 1 user      user         1994 apr  8 21:36 .
drwxr-xr-x  1 root      root           40 jun 11  2023 ..
-rw-r--r--  1 user      user          348 okt 11 08:49 .aliases
-rw-r--r--  1 user      user           21 jan  8  2022 .bash_logout
-rw-r--r--  1 user      user           57 jan  8  2022 .bash_profile
-rw-r--r--  1 user      user          394 jan 27  2023 .bashrc
drwxr-xr-x  1 user      user          342 apr  8 21:21 Documents
```

Če se želimo premakniti v drug imenik, uporabimo ukaz `cd`. Pri tem lahko uporabimo absolutno pot (npr. `/home/user/Documents`) ali pa relativno pot (npr. `Documents`, če se nahajamo v domačem imeniku.) Za premik v višji imenik uporabimo ukaz `cd ..`.

Zdaj bomo ustvarili nov imenik z imenom "files". To storimo z ukazom `mkdir files`. Za poskus lahko odstranimo ustvarjeni imenik z ukazom `rmdir files`.
> `rmdir` odstrani samo prazne imenike

Ustvarimo sledečo strukturo imenikov:
> kjer nek parameter vsebuje presledek, uporabimo narekovaje za celoten parameter, npr "02 druga vaja"

```
vaje
|---01-prva
|---02 druga vaja
|---03-temp
|   |---kopiraj
|   |---premakni
```

Premaknemo se v imenik "01-prva". Ustvarimo novo datoteko z ukazom `touch primer.txt`.

Želimo kopirati novo ustvarjeno datoteko v drugo mapo "03-temp/kopiraj". To storimo na naslednji način:

```bash
user@machine:~/vaje/01-prva$ cp primer.txt ~/vaje/03-temp/kopiraj
```

Sedaj še premaknemo datoteko v drug imenik:

```bash
user@machine:~/vaje/01-prva$ mv primer.txt ~/vaje/03-temp/premakni
```
> ukaz `mv` uporabljamo tudi za preimenovanje datotek, npr. `mv primer.txt primer1.txt`

Sedaj se premaknemo v imenik "Documents", ki se nahaja v domačem imeniku. Z ukazom `cat` izpišemo vsebino datoteke "lorem1.txt" (`cat lorem1.txt`). Za daljše datoteke uporbljamo ukaz `less`, ki nam odpre iteraktivni pogled datoteke (delovanje preizkusimo z datoteko "lorem2.txt").  
Če želimo izpisati samo zadnjih 10 vrstic v datoteki, to storimo z ukazom `tail lorem2.txt`.
> izpišemo lahko poljubno število zadnjih vrstic v datoteki z zastavico `-n number_of_lines`

Ukaz `echo` nam izpiše podane argumente na standardni izhod (ukazna vrstica), npr. `echo "hello"`.
> izhod lahko iz standardnega izhoda preusmerimo v datoteko, npr. `echo "hello" >> example.txt`

Z ukazom `file` preverimo tip datoteke, npr. `file lorem1.txt`.

Vsak ukaz v Linuxu ima svoje mesto v datotečnem sistemu. Če želimo poiskati njegovo lokacijo (na primer ukaz `ls`), uporabimo ukaz `which ls`.

## Omrežni ukazi

Za preverjanje omrežne povezljivosti uporabimo ukaz `ping`. Poiskusimo `ping google.com`.

##  Uporaba urejevalnika

Za urejanje datotek uporabimo urejevalnik besedil `nano` (`nano primer.txt`).

## Administatorski ukazi

Za izvedbo nekaterih ukazov potrebujemo administratorske pravice. To storimo tako, da pred ukazom uporabimo `sudo`. Sedaj si poglejmo še dva ukaza, za katera potrebujemo administratorske pravice.

Prvi tak ukaz je ukaz `chown`. Z njim spreminjamo lastnika datoteke, npr. `sudo chown user loren1.txt`.

Drugi ukaz je `chmod`, s katerim lahko spremenimo pravice dostopa do datoteke.
> `chmod` lahko uporabimo brez `sudo` le v primeru, če smo lastnik datoteke

Pri podrobnem izpisu trenutnega imenika smo opazili "naključni" izpis črk na začetku vsake vrstice. Vendar ima vsaka črka svoj pomen.

Črka na prvem mestu predstavlja tip datoteke:

- `-` pomeni navadna datoteka
- `d` pomeni imenik
- `l` pomeni bližnjica (povezava na drugo datoteko)

Nato sledi trije nizi, sestavljeni iz treh črk:

- prvi niz predstavlja dovoljenja za lastnika datoteke
- drugi niz predstavlja dovoljenja za člane skupine
- tretji niz predstavlja dovoljenja za vse ostale

Vsaka črka v teh nizih predstavlja tip dovoljenj: branje (read - `r`), pisanje (write - `w`)in izvajanje (execute - `x`). Dovoljenja so vedno pisana v tem vrstnem redu. Če ne želimo določenega dovoljenja za datoteko, ustrezno oznako nadomestimo z `-`.

Ukaz `chmod` lahko uporabljamo na dva načina:

- ukazu sledi presledek ter črka:
  - `a` za vse, `u` za lastnika datoteke,`g` za skupino ter `o` za ostale
  - uporabimo znaka `+` in `-` za dodajanje oziroma odvzemanje pravic
  - primeri: `chmod a+rw filename`, `chmod o-rwx filename`, `chmod og-r filename`
- ukazu sledijo številke
  - največja vrednost, ki jo lahko dodelimo, je 7 (seštevek dovoljenj)
  - vrednost `1` predstavlja dovoljenje za izvajanje, vrednost `2` dovoljenje za pisanje, vrednost `4` pa dovoljenje za branje
  - primeri: `chmod 777 filename`, `chmod 755 filename`, `chmod 644 filename`

> če želimo spremeniti dovoljenja za vse datoteke v nekem imeniku, uporabimo zastavico `-r`