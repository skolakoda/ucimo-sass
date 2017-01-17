![sass](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/320px-Sass_Logo_Color.svg.png)

# Učimo Sass

[Sass](http://sass-lang.com/) je skriptni programski jezik, koji se prevodi u CSS. Koristi ekstenziju `scss`. U potpunosti podržava CSS sintaksu, tako da je svaki validan `css` fajl istovremeno validan `scss` fajl. Samo zamenite ekstenziju i radi!

Sass pretvara CSS u ozbiljan programski jezik, dodajući mu varijable, petlje i funkcije. U Sasu možete lako napraviti sopstveni CSS radni okvir ili neku alatku koje vam treba, kao na primer grid sistem.

## Instalacija

Da biste instalirali Sass morate imati instaliran [Ruby](https://www.ruby-lang.org/en/) programski jezik:
```
sudo apt install ruby
```

Sass se instalira komandom:
```
gem install sass
```

## Pokretanje

Prvo kloniraš repo i uđeš u njega:
```
git clone https://github.com/skolakoda/ucimo-sass.git
cd ucimo-sass
```

Zatim uđeš u folder neke lekcije, na primer:
```
cd 10-varijable
```

Odatle pokreneš komandu koja posmatra folder `sass` i kompajlira fajlove u folder `css`:
```
sass --watch sass:css
```

Za svaku lekciju Sass prevodilac se pokreće na isti način.

## Opcije

Komanda `sass` kompajlira prosleđeni `scss` fajl u `css`:
```
sass style.scss
```

Komanda `sass` sa opcijom `watch` i lokacijom `.` posmatra sve `scss` fajlove i kompajlira ih u `css`:
```
sass --watch .
```
Možemo specifikovati različiti ulazni i izlazni folder (ulaz `sass`, izlaz `css`):
```
sass --watch sass:css
```

## Node Sass

`node-sass` je prilagođen za rad sa `npm`-om, za automatizaciju build procesa. Podrazumeva se da imaš instaliran [Node.js](https://nodejs.org) i napravljen `npm` paket (`package.json`). Nakon toga instaliraš `node-sass`:
```
npm install --save-dev node-sass
```

Dodatne opcije (watch, ulazni i izlazni folder) se navode na sledeći način:
```
node-sass -w src/sass -o dist/css
```

Takođe, možeš odmah izvesti minifikovan css:
```
node-sass -w src/sass -o dist/css --output-style compressed
```

Sve opcije možeš pronaći [ovde](https://github.com/sass/node-sass#command-line-interface).
