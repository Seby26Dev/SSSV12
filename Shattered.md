# Shattered

Am descarcat arhiva si i-am dat unzip.

Am obtinut mai multe fisiere `f, l, a, g` pe care le-am dat `cat` inr-un alt fisier cu extensie `.zip` in aceasta ordine.

Acest fisier formeaza o arhiva cu mici probleme, motiv pt care am dat comanda 
```
zip -FF arhivacurenta.zip --out rezultat.zip
```
 Arhiva finala am dezarhivat-o si am obtinut o poza pe care am aplicat` strings`.
 
 Ultimul rand e flagul pe care l-am decodat cu comanda
 ```
echo '<input>' | base64 -d 
```
