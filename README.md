![sass](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/320px-Sass_Logo_Color.svg.png)

# Učimo Sass

[Sass](http://sass-lang.com/) je skriptni programski jezik, koji se prevodi u CSS. Koristi `.scss` ekstenziju. U potpunosti podržava CSS sintaksu, tako da je svaki validan `css` fajl istovremeno validan `scss` fajl (samo zameniš ekstenziju).

Sass pretvara CSS u ozbiljan programski jezik, dodajući mu varijable, petlje i funkcije. U Sasu možete lako napraviti sopstveni CSS radni okvir ili neku alatku koje vam treba, kao na primer grid sistem.

## Instalacija

Moraš prvo instalirati [Ruby](https://www.ruby-lang.org/en/), a potom Sass. Na Linuxu:

```
sudo apt install ruby
gem install sass
```

## Prevođenje

Komanda `sass` prima dva argumenta, ulazni (`.scss`) i izlazni (`.css`) fajl:

```
sass style.scss style.css
```

Da ne bismo nakon svake izmene ručno prevodili fajl, koristimo opciju `--watch`:

```
sass --watch style.scss:style.css
```

U praksi redovno držimo izvorne i prevedene fajlove u zasebnim folderima. Sledećom komandom prevodimo sve fajlove iz ulaznog (`sass`) u izlazni (`css`) folder:

```
sass --watch sass:css
```

## Pokretanje primera

Pošto kloniraš repo, uđeš u folder neke lekcije i pokreneš komandu:

```
sass --watch sass:css
```

Za svaku lekciju Sass prevodilac se pokreće na isti način.

## Node i npm 

Nakon instalacije [Node.js](https://nodejs.org) i [npm](https://npm.org), instaliraj sve module jednom komandom
```
npm install
```
Ako želiš da instaliraš pojedinačne module, uputstva se nalaze ispod.

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
