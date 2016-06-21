![sass](https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Sass_Logo_Color.svg/320px-Sass_Logo_Color.svg.png)

# Učimo Sass

[Sass](http://sass-lang.com/) je nadskup CSS-a. Svaki validan .css fajl je istovremeno validan .scss fajl. Sass daje dodatne moći CSS-u, između ostalog varijable i funkcije.

## Instalacija

Da biste instalirali `Sass` morate imati instaliran [Ruby](https://www.ruby-lang.org/en/) programski jezik. 

```
gem install sass
```

Ukoliko ga koristite preko `npm` paketa, onda morate imati instaliran [Node.js](https://nodejs.org).

## Kompajliranje 

Kompajlira scss fajl u css:
```
sass style.scss
```

## Posmatranje 

Posmatra sve scss fajlove i kompajlira ih u css:
```
sass --watch .
```

Opciono možeš dodati ulazni i izlazni folder (ulazni `sass`, izlazni `css`):
```
sass --watch sass:css
```

### NPM watch

Za `npm` treba instalirati `node-sass`: 
```
npm install --save-dev node-sass
```

Ulazni (`src/sass`) i izlazni folder (`dist/css`) se navode na sledeći način:
```
node-sass -w src/sass -o dist/css
```

Možeš odmah izvesti minifikovan css:
```
node-sass -w src/sass -o dist/css --output-style compressed
```

