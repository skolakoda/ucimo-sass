# Postavljanje sistema boja na frontendu

Da bismo dosledno primenili dizajn, veoma je bitno postaviti sistem boja na frontendu. Recimo da smo od dizajnera dobili ovu [paletu osnovnih boja](https://color.adobe.com/Organic-color-theme-9091984/edit/?copy=true) i ovu [paletu sivih nijansi](https://color.adobe.com/grayscale-color-theme-7771446/edit/?copy=true).

## Korak 1: definisanje varijabli

Prvo prevodimo kodove boja u format čitljiv za ljude (sa [ovom alatkom](http://chir.ag/projects/name-that-color)) i pravimo odgovarajuće varijable.

```scss
// osnovne boje
$jacaranda: #410533;
$wheat: #F4D7BD;
$fire: #A53F05;
$red-berry: #8C1C00;
$rosewood: #590C01;

// sive nijanse
$black: #050505;
$cod-gray: #0D0D0D;
$mine-shaft: #262626;
$bombay: #B4B5B7;
$white: #FEFEFE;
```

Sada smo uspostavili paletu boja za projekat, i nadalje ćemo koristi isključivo varijable. Na primer:

```scss
.primary-btn {
  color: $fire;
  background-color: $white;
}
```

Ukoliko neku boju nemamo u varijablama, ili ćemo je dodati ili je nećemo koristiti, kako bi dizajn ostao dosledan.

## Korak 2: pravljenje pomoćnih klasa

Pored varijabli, trebaju nam i pomoćne klase za boju slova i pozadine. Da ne bismo ručno pravili sve te klase, napravićemo funkciju (`mixin`) kojoj prosleđujemo ime boje i njenu vrednost, a ona pravi CSS klase nazvane po toj boji:

```scss
@mixin color($name, $value) {
  .#{$name} {
    color: $value;
  }
  .#{$name}-bg {
    background-color: $value;
  }
}
```

Nakon toga pozivamo funkciju `color` sa svim bojama koje želimo:

```scss
@include color('jacaranda', $jacaranda);
@include color('wheat', $wheat);
@include color('fire', $fire);
@include color('red-berry', $red-berry);
@include color('rosewood', $rosewood);

@include color('black', $black);
@include color('cod-gray', $cod-gray);
@include color('mine-shaft', $mine-shaft);
@include color('bombay', $bombay);
@include color('white', $white);
```

Kao rezultat dobijamo sledeće CSS klase:
```css
.jacaranda {
  color: #410533;
}

.jacaranda-bg {
  background-color: #410533;
}

.wheat {
  color: #F4D7BD;
}

.wheat-bg {
  background-color: #F4D7BD;
}

.fire {
  color: #A53F05;
}

.fire-bg {
  background-color: #A53F05;
}

.red-berry {
  color: #8C1C00;
}

.red-berry-bg {
  background-color: #8C1C00;
}

.rosewood {
  color: #590C01;
}

.rosewood-bg {
  background-color: #590C01;
}

.black {
  color: #050505;
}

.black-bg {
  background-color: #050505;
}

.cod-gray {
  color: #0D0D0D;
}

.cod-gray-bg {
  background-color: #0D0D0D;
}

.mine-shaft {
  color: #262626;
}

.mine-shaft-bg {
  background-color: #262626;
}

.bombay {
  color: #B4B5B7;
}

.bombay-bg {
  background-color: #B4B5B7;
}

.white {
  color: #FEFEFE;
}

.white-bg {
  background-color: #FEFEFE;
}
```

## Korak 3: upotreba klasa

Sada je naš sistem boja uspostavljen, i pomoćne klase možemo koristiti širom projekta na sledeći način:

```html
<p class="fire">Vel quod quis quasi illo ea amet, omnis aliquid voluptatem officia.</p>

<button class="jacaranda-bg white">I agree!</button>
```

Ovo što sada imamo je sasvim solidan temelj za razvoj velikih projekata.

## Eksperimentisanje

Ja sam nastavio još malo da eksperimentišem za svoju zabavu. Dodao sam suptilnu boju ivica i blago posvetljenje boje slova na hover, koristeći ugrađene funkcije `darken` i `lighten`:

```scss
@mixin color($name, $value) {
  .#{$name} {
    color: $value;
  }
  .#{$name}:hover {
    color: lighten($value, 10%);
  }
  .#{$name}-bg {
    background-color: $value;
    border-style: solid;
    border-color: darken($value, 5%);
  }
}
```

Eksperimentišite malo za svoju zabavu, ali za projekte stvarnog sveta preporučujem da se zaustavite na koraku 3.

Srećno!
