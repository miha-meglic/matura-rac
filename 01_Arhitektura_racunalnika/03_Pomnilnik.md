# Pomnilnik

## Pomnilniška hierarhija

Računalniški pomnilnik hierarhično delimo glede na hitrost dostopa:

![Pomnilniška hierarhija](../img/Memory_Hierarchy.png)

**Primarni pomnilnik** je neposredno povezan z CPU, sestavljen iz zelo hitrih pomnilniških tehnologij (npr. SRAM, DRAM), neobstojni pomnilnik (volatile):

- *Registri procesorja* so sestavni del CPE, v več-jedrnih CPE ima vsako jedro svoje registre, običajno SRAM, velikosti v rangu Bajtov
- *Predpomnilnik* je interni pomnilnik, v več-jedrnih CPE si ga deli več jeder, običajno SRAM, velikosti v rangu MegaBajtov
- *Glavni pomnilnik (oz. RAM)* je zunanji pomnilnik povezan z pomnilniškim vodilom, hrani procese v teku, deli si ga celoten CPE, običajno DRAM, velikosti v rangu GigaBajtov

**Sekundarni pomnilnik** je povezan preko zunanjih nadzornih enot, drastično počasnejši od primarnega pomnilnika, sestavljen iz počasnejših in cenejših pomnilniških tehnologij (npr. NAND flash, magnetni zapis, omrežni pomnilnik, papirne kartice), obstojni pomnilnik (non-volatile).
