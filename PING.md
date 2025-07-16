# PING

Am observat ca comanda `ping -c 1 <input>` prelua inputul asa ca am testat comanda ` ;ls `

Dupa am observat ca, comanda ` ;ls -la ` nu functiona, deoarece in input era `cmd=<input>&ping=<input> `, iar daca exista un spatiu liber comanda ping nu mai era luata in considerare si propozitia nu mai era valida . Am incercat `URL Encode` si nu functiona , dupa ceva cautare ChatGbt ne-a recomandat sa folosim comanda
```
;ls${IFS}-la
```
si functiona , asa ca am dat cat la flag `;cat${IFS}/flag`

