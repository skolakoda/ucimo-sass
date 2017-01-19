# Kako napraviti responsive grid sistem?

U nekoliko prostih koraka napravićemo grid sistem, sličan onom koji koristi Bootstrap. Grid sistem zapravo simulira tabelu, koja nam omogućava napredno pozicioniranje HTML elementa. Kao i svaka tabela, sastoji se od redova i kolona.

Pored grida, obično postoji i `container` koji se brine za ukupnu širinu stranice. Iako idu u paketu, container nije deo grida, i grid može raditi potpuno nezavisno od njega.

## Korak 0: priprema terena

Po defaultu, CSS uračunava padding u širinu elementa. Mi želimo da menjamo unutrašnji razmak po potrebi, a da širina elementa ostaje ista. Zato svima dodajemo `box-sizing: border-box`:

```css
* {
  box-sizing: border-box;
}
```
## Korak 1: definisanje varijabli

Prvo, definišemo broj kolona i razmak između njih:

```scss
$columns: 12;
$spacing: 20px;
```

Možete imati kolona koliko hoćete, ali ljudi često biraju 12 jer je deljivo sa mnogim brojevima (6, 4, 3).

## Korak 2: pravljenje grida

Prvo, kolonama stavljamo `float: left`, kako bi se poređale jedna pored druge. Podrazumevana širina će im biti 100%, za najmanje uređaje. Pored toga, daćemo `padding-right` radi razmaka, svakoj koloni osim poslednje:

```scss
[class*='col-'] {
  float: left;
  width: 100%;
  &:not(:last-of-type) {
    padding-right: $spacing;
  }
}
```

Pošto kolone imaju `float`, red mora imati `overflow: auto` da bi sačuvao svoju visinu:
```css
.row {
  overflow: auto;
}
```

Grid pravimo tako što, za prosleđenu veličinu, broj kolona podelimo sa širinom stranice, i svakoj damo odgovarajuću širinu:

```scss
@mixin grid($breakpoint, $size) {
  @media (min-width: $breakpoint) {
    @for $i from 1 through $columns {
      .col-#{$size}-#{$i} {
        width: (100% / $columns) * $i;
      }
    }
  }
}
```

Konačno, pozivamo funkciju prosleđujući joj tačke preloma koje želimo:
```scss
@include grid('sm', 544px);
@include grid('md', 768px);
@include grid('lg', 1200px);
```

## Korak 3: upotreba

Prilagodljivi grid sada možemo koristiti na sledeći način:
```html
<div class="row">
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
  <div class="col-sm-6 col-md-4 col-lg-1">Hello World</div>
</div>
```

Ovo znači da će naš sadržaj:
* na malim uređajima zauzimati 6 kolona od 12 (pola ekrana)
* na srednjim uređajima 4 kolone od 12 (trećinu ekrana)
* a na velikim uređajima 1 kolonu od 12 (dvanaestina ekrana)
Na najmanjim uređajima će zauzimati punu širinu.
