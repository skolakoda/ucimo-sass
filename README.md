![sass](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/320px-Sass_Logo_Color.svg.png)

# Učimo Sass

[Sass](http://sass-lang.com/) je nadskup CSS-a. Svaki validan `.css` fajl je istovremeno validan `.scss` fajl.

Sass pretvara CSS u ozbiljan programski jezik, dodajući mu varijable, petlje i funkcije. U Sassu možete napraviti sopstveni CSS framework ili delove koji vam trebaju, kao grid sistem.

## Instalacija

Da biste instalirali `Sass` morate imati instaliran [Ruby](https://www.ruby-lang.org/en/) programski jezik:
```
sudo apt install ruby
```

Nakon toga naredite:

```
gem install sass
```

## Kompajliranje

Komanda `sass` kompajlira prosleđeni `scss` fajl u `css`:
```
sass style.scss
```

## Posmatranje

Komanda `sass` sa opcijom `watch` posmatra sve `scss` fajlove i kompajlira ih u `css`:
```
sass --watch .
```

## Pokretanje lekcija

Da bi radio na lekcijama, potrebno je ući u odgovarajući folder. Na primer:
```
cd 10-varijable
```

Zatim pokrenuti komandu koja će posmatrati direktorij `sass` i kompajlirati fajlove u `css`:
```
sass --watch sass:css
```

### NPM watch

Za `npm` pakete moraš imati instaliran [Node.js](https://nodejs.org). Nakon toga instaliraš `node-sass`:
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
