#Documentation BEM

* Block
* Element
* Modifier


```html
  <ul class="headerNav headerNav--xmas">
    <li class="headerNav__item">
      <a href="/a-propos" class="headerNav__itemLink">
        A propos
      </a>
    </li>
    <li class="headerNav__item">
      <a href="/home" class="headerNav__itemLink headerNav__itemLink--isActive">
        Acceuil
      </a>
    </li>
    <li class="headerNav__item">
      <a href="/a-propos" class="headerNav__itemLink--isDisabled">
        mon compte
      </a>
    </li>
  </ul>

```

```css

.headerNav{
  &--xmas{
    background : red;
  }
  &__item{
    list-style :none;
  }
  &__itemLink{
    &--isDisabled{
      color: grey;
    }
    &--isActive{
      color: green;
    }
  }
}

```

# Pseudo attribut ::after & ::before



```html
<section class='cover'>
  <h2 class="cover__title">Présnetation</h2>
</section>
```

```css
.cover{
  &__title{
    font-size: 24px;
    color: #bbb;
    text-align: center;
    &::before,
    &::after{
      content:'';
      position: absolute;
      top: 0;
      width: 50px;
      heigth: 50px;
      background: green;
    }
    &::before{
      left: 0;
    }
    &::after{
      right: 0;
    }
  }
}

```

## Les unités

### REM

```css
html{
  font-size: 62.5%
}

.mainTitle{
  font-size: 2.4rem;
}

.cover{
  width: 32rem;
}
```

### EM

### VM

## les grilles avec Flexboxgrid

* [Documentation](http://flexboxgrid.com/)


## Environnement de travail Autocompiler

Installation NodeJS.

npm install


# Install flexboxGrid in Parcel

- npm install flexboxGrid

# CSS Next

- http://cssnext.io/


## Fonction pour JUMP quelque part en JS (Jquery)


```JS
$section = $('section');
  $(function(){
      //Scrool doux
      $section.on('click', "a[href^='#']", function(event){
          event.preventDefault();
          var hash = this.href.split("#")[1];

          // Reset
          var yScroll=window.scrollY;
          location.hash = '';
          window.scroll(0, yScroll);
          smoothScroll(hash);
          $(".burgerbutton").toggleClass("active");
          $(".burger-menu").slideToggle();
               $(".andycls").toggleClass("active");
      });
  });
```
## Loading Screen
``` html
  <section id="loadercont" class="loadercontainer">
    <div class="loader">Andy DODAKAL</div>
  </section>
```
``` css
  .loadercontainer{
    background-color: $colorPrinci;
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: fixed;
    z-index: 999;
    overflow: hidden;
  }
  .loader {
    overflow: hidden;
    width: 250px;
    height: 50px;
    line-height: 50px;
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    font-family: 'Teko_regu';
    text-transform: uppercase;
    font-size: 20px;
    font-weight: 900;
    color: $white;
    letter-spacing: 0.2em;
    z-index: 101;

    &::before, &::after {
      content: "";
      display: block;
      width: 15px;
      height: 15px;
      background: $red;
      position: absolute;
      animation: load .7s infinite alternate ease-in-out;
      z-index: 101;
    }

    &::before {
      top: 0;
      z-index: 101;
    }

    &::after {
      bottom: 0;
      z-index: 101;
    }
  }

  @keyframes load {
    0% { left: 0; height: 30px; width: 15px }
    50% { height: 8px; width: 40px }
    100% { left: 235px; height: 30px; width: 15px}
  }
```
```JS
  $(window).on('load',function () {
    $('#loadercont').fadeOut();
  });
```
## Mettre une image de fond a une div sans que celle-ci soit déformée
```css
.projectBox{
  height: 30%;
  width: 80%;
  background-color: $white;
  border: 1px solid $red;
  margin: 5% auto auto auto;
  background-image: url(../images/Nespresso_project.jpg);
  width: 300px;
  height: 250px;
  background-size: cover;
}
```
## Mixins Responsive performante
```css

@mixin for-size($range) {
  $phone-upper-boundary: $bp-tablet;
  $tablet-portrait-upper-boundary: $bp-desktop;
  $tablet-landscape-upper-boundary: $bp-desktop-large;
  $desktop-upper-boundary: $bp-desktop-extra-large;

  @if $range == phone-only {
    @media (max-width: #{$phone-upper-boundary - 1}) { @content; }
  } @else if $range == tablet-portrait-up {
    @media (min-width: $phone-upper-boundary) { @content; }
  } @else if $range == tablet-landscape-up {
    @media (min-width: $tablet-portrait-upper-boundary) { @content; }
  } @else if $range == desktop-up {
    @media (min-width: $tablet-landscape-upper-boundary) { @content; }
  } @else if $range == big-desktop-up {
    @media (min-width: $desktop-upper-boundary) { @content; }
  }
}
```

### Transformer un logo en ligne SVG

- https://jakearchibald.github.io/svgomg/


# Bonne pratique de travail.

## Les Classes
Par exemple si on est dans le header il va falloir nommer ses classes, avec "Header-****" le nom de la section par exempple :
```html
<header class="Header">
  <div class="container">
    <div class="row middle-xs">
      <div class="col-xs-6 Header-left">
        <a class="Header-link" href="" title="Hostnfly - Conciergerie Airbnb">
          <svg class="Header-logo" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 146 32">
```
## les commentaires
On peut également notifier chaque fin de section ou de block par un commentaire afin de bien séparer les blocks permettant un code plus lisible et maintenable.
```html
</section>
<!-- Fin HeroPanel -->
<!-- Début Features -->
<section class="Features">
```
## Le style !
Etant donnée que l'on travail avec un Environnement de travil propre (Coucou parcel.js !)
Dans notre feuille de style principale il faut déclarer tout les élements nécessaire au bon fonctionnement du css dans **Style.scss**
```css
// global
@import './global/reset';
@import './global/variables';

// mixins
@import './mixins/forsize';
@import './mixins/button';
@import './mixins/mixins';
// components
@import './components/header';
@import './components/heropanel';
@import './components/features';
@import './components/care';
@import './components/revenus';
@import './components/Customer';
@import './components/faq';
@import "./components/partners";
@import "./components/services";
@import "./components/footer";
```

Dans **reset** nous aurrons la feuille permettant le reset css du navigateur.
Dans **variables** nous permet de lister toute les variable que l'on va utiliser.


# What is Vue.js
Vue.js est un framework Javascrip like React etc..
Cependant Vue.js n'est totalement utilisé dans le sens ou React, Angular etc.. sont plus utilisé que ce soit les grandes ou les petite entreprises.

# Point fort
Vue.js est un framework très rapide mais aussi très simple a apprendre.


# Point Faible
Vue.js est tenu que part une personne tandis que d'autre grand comme react et Angular sont tenu par Facebook, Google donc un grande communauté.


# Get start

 Vue.js peut être déclarer comme Jquery, en Cli ou en local.
 il existe diverse verison, dont une version light et une version dev qui permet d'afficher les erreurs.


 ```html
 <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
 ```

 Dans vue on peut déclarer des donnée avec un sytème de templating par exemple on veux afficher un lien, bah pas besoin de le faire directement en html.

```html
 <div class="ui main container" id="app">
   <a :href="link" :title='message'>{{ message }}</a>
 ```

 ```js
 new Vue({
   el: '#app',

   data : {
     message : 'On Fait pas du vue.js nous !',
     link : 'andydodakal.com',
     sucess : false
   }
 })

```

Résulat on bien dirigé vers mon lien "andydodakal.com".
## Whats is webpack

Webpack est un bundler comme parcel permettant d'avoir un Environnement de travail modulaire.
