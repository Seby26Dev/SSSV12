# Double Oh No

La accesarea paginii `http://141.85.224.116:8905/double-oh-no`, serverul returna „Bond. James Bond.” si un cod `403 Forbidden`.

Numele provocarii („Double Oh No”) sugera o tema legata de spionaj, asa ca am încercat sa schimbam User-Agent cu James Bond. 

Serverul a raspuns cu `„Where are you from?”`, semnaland că asteapta un antet Referer.

Dupa ce am trimis un Referer tematic, precum `https://en.wikipedia.org/wiki/MI6`, folosind comanda 
```
curl -A "James Bond" -e "https://en.wikipedia.org/wiki/MI6" http://141.85.224.116:8905/double-oh-no
```
am primit flag-ul
