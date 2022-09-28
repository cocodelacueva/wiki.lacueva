# HTML Y CSS

## Animaciones

### librerias:
https://greensock.com/get-started/

https://scrollmagic.io/


## Tutorials Web de apple
https://www.juanoa.com/desarrollo/haciendo-animaciones-como-las-de-la-web-de-apple
THIS IS THE BEST:
https://css-tricks.com/lets-make-one-of-those-fancy-scrolling-animations-used-on-apple-product-pages/


## REFERENCIAS
bara: https://piscinasdecemento.com/en/technology
https://www.cssportal.com/css-clip-path-generator/



## HTML TEMPLATES

```html
<picture>
  <source srcset="assets/imagesmdn-logo.svg" type="image/svg+xml">
 <source srcset="assets/images/intel-logo-blanco.png 1x, assets/images/intel-logo-blanco@2x.png 2x, assets/images/intel-logo-blanco@3x.png 3x" media="(min-width: 992px)">
 <source srcset="assets/images/intel-logo-blanco.png 1x, assets/images/intel-logo-blanco@2x.png 2x, assets/images/intel-logo-blanco@3x.png 3x" media="(min-width: 768px)">
  <source srcset="assets/images/intel-logo-blanco.png 1x, assets/images/intel-logo-blanco@2x.png 2x, assets/images/intel-logo-blanco@3x.png 3x" media="(min-width: 100px)">
  <img src="assets/images/intel-logo-blanco.png" alt="Intel Logo">
</picture>


<img src="assets/images/intel-logo-blanco.png" alt="Intel Logo" srcset=“assets/images/intel-logo-blanco.png 1x, assets/images/intel-logo-blanco@2x.png 2x, assets/images/intel-logo-blanco@3x.png 3x” loading="lazy">


<img src="assets/images/" alt="Laptop Image" srcset="assets/images/ 1x, assets/images/ 2x, assets/images/ 3x">
```

## CSS TEMPLATES
```css
@media (min-width: $md) {}
@media (max-width: 767px) {}


-webkit-
-moz-
-ms-
-o-


display: flex;
display: -o-flex;
display: -ms-flex;
display: -moz-flex;
display: -webkit-flex;
-webkit-align-items: center;
-moz-align-items: center;
-ms-align-items: center;
-o-align-items: center;
align-items: center;
-webkit-justify-content: center;
-moz-justify-content: center;
-ms-justify-content: center;
-o-justify-content: center;
justify-content: center;
-webkit-justify-content: space-between;
-moz-justify-content: space-between;
-ms-justify-content: space-between;
-o-justify-content: space-between;
justify-content: space-between;




&:hover {
  zoom: 1;
  filter: alpha(opacity=50);
  opacity: 0.5;
}







@media only screen and (-webkit-min-device-pixel-ratio: 1.5), only screen and (min--moz-device-pixel-ratio: 1.5), only screen and (min-resolution: 240dpi) {
  background-image: url(../images/header-bk-360@2x.jpg);
  background-size: cover;
}


@media (min-width: $xs) and (-webkit-min-device-pixel-ratio: 1.5), (min-width: $xs) and (min--moz-device-pixel-ratio: 1.5), (min-width: $xs) and (min-resolution: 240dpi) {
  background-image: url(../images/header-bk-1024@2x.jpg);
  background-size: cover;
  background-position: right center;
}


3x
@media only screen and (-webkit-min-device-pixel-ratio: 2.25), only screen and (min--moz-device-pixel-ratio: 2.25), only screen and (min-resolution: 2.25dppx) {
  background-image: url(../images/header-bk-360@2x.jpg);
  background-size: cover;
}


@media (min-width: $xs) and (-webkit-min-device-pixel-ratio: 2.25), (min-width: $xs) and (min--moz-device-pixel-ratio: 2.25), (min-width: $xs) and (min-resolution: 2.25dppx) {
  background-image: url(../images/header-bk-1024@2x.jpg);
  background-size: cover;
  background-position: right center;
}


@1x image (Pixel Ratio 1.0)
@2x image (Pixel Ratio of 1.25+)
@3x image (Pixel Ratio of 2.25+)
@4x image (Pixel Ratio of 3.25+)


/* @2x Images (Pixel Ratio of 1.25+) */
@media only screen and (-o-min-device-pixel-ratio: 5/4),
       only screen and (-webkit-min-device-pixel-ratio: 1.25),
       only screen and (min--moz-device-pixel-ratio: 1.25),
       only screen and (min-device-pixel-ratio: 1.25),
       only screen and (min-resolution: 1.25dppx) {
    #dgst_shopping_bag {background-image:url(img/shopping_bag@2x.png);}
}


::-webkit-input-placeholder { /* Chrome/Opera/Safari */
  color: pink;
}
::-moz-placeholder { /* Firefox 19+ */
  color: pink;
}
:-ms-input-placeholder { /* IE 10+ */
  color: pink;
}
:-moz-placeholder { /* Firefox 18- */
  color: pink;
}


@mixin image-2x($image, $size) {
    @media (min--moz-device-pixel-ratio: 1.3),
           (-o-min-device-pixel-ratio: 2.6/2),
           (-webkit-min-device-pixel-ratio: 1.3),
           (min-device-pixel-ratio: 1.3),
           (min-resolution: 1.3dppx) {
      /* on retina, use image that's scaled by 2 */
      background-image: url($image);
      background-size: $size;
    }
}


@mixin image-3x($image, $size) {
    @media (min--moz-device-pixel-ratio: 2.25),
           (-webkit-min-device-pixel-ratio: 2.25),
           (min-device-pixel-ratio: 2.25),
           (min-resolution: 2.25dppx) {
      /* on retina, use image that's scaled by 2 */
      background-image: url($image);
      background-size: $size;
    }
}


@include image-2x('../images/bg-main-tablet@2x.jpg', cover);
@include image-3x('../images/bg-main-tablet@3x.jpg', cover);




Esto quita el fondo que se le da al hacer click en los mobiles:
-webkit-tap-highlight-color: transparent;


Esto es para la barra del navegador:
::-webkit-scrollbar {
  // El ancho de la barra
}


::-webkit-scrollbar-track {
  // El color de fondo de la barra
}


::-webkit-scrollbar-thumb {
  //El color de la barra
}


::-webkit-scrollbar-thumb:hover {
 //Para hacer hover
}


```