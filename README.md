![sass](http://sass-lang.com/assets/img/logos/logo-b6e1ef6e.svg)

# Učimo Sass

[Sass](http://sass-lang.com/) je nadskup CSS-a. Svaki validan .css fajl je istovremeno validan .scss fajl. Sass daje dodatne moći CSS-u, između ostalog varijable i funkcije.

## Preduslovi

Da biste instalirali Sass morate imati instaliran Ruby programski jezik.


## Instalacija
```
gem install sass
```

## Pokretanje 

Kompajlira scss fajl u css:
```
sass style.scss
```

Posmatra sve scss fajlove i kompajlira ih u css:
```
sass --watch .
```

Opciono možeš dodati ulazni i izlazni folder (ulazni `sass`, izlazni `css`):
```
sass --watch sass:css
```
