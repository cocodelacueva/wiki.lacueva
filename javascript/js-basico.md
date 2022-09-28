## Javascript básico

* On load:
```js
window.addEventListener('load', function(){})
docready:
document.addEventListener('DOMContentLoaded', function(){})
```

//Remueve elemento del dom
```js
var elem = document.querySelector('#some-element');
elem.parentNode.removeChild(elem);
```

## DETECTA EL BROWSER, DEVUELVE EL BROWSER

```js
function browserDetection() {
  let userAgent = navigator.userAgent.toLowerCase(); 
  let browser;
  if ( userAgent.indexOf('trident') > -1 || userAgent.indexOf('msie') > -1) {
      browser = 'ie';
  } else if ( userAgent.indexOf('edge') > -1 ) {
      browser = 'edge';
  } else if (userAgent.indexOf('safari')!=-1){ 
      if (userAgent.indexOf('chrome')  > -1){
          browser = 'chrome';
      } else if((userAgent .indexOf('opera')  > -1)||(userAgent.indexOf('opr')  > -1)){
          browser = 'opera';
      } else {
          browser = 'safari';
      }


  } else if (userAgent.indexOf('firefox') !=-1) {
      browser = 'firefox';
  } else {
      browser = 'dont-know';    
  }
  
  return browser;
}

```


## CALCULA LA POSICION DE UN ELEMENTO

```js
function getOffset( el ) {
  var _x = 0;
  var _y = 0;
  while( el && !isNaN( el.offsetLeft ) && !isNaN( el.offsetTop ) ) {
      _x += el.offsetLeft - el.scrollLeft;
      _y += el.offsetTop - el.scrollTop;
      el = el.offsetParent;
  }
  return { top: _y, left: _x };
}
```



## VE SI EL ELEMENTO ESTA VISIBLE EN LA PANTALLA

```js
function isVisible ( el ) {
  var result = false;
  // Browser viewport
  var viewport_h = window.innerHeight;
  var viewport_top = window.pageYOffset;
  var viewport_bottom = viewport_top + viewport_h;
  // DOM Element
  var el_h = el.offsetHeight;                  // Height
  var el_top = el.getBoundingClientRect().top; // Top
  var el_bottom = el_top + el_h;               // Bottom
  // Is inside viewport?
  if ( el_bottom > 0 && el_top < viewport_h ) { 
    result = 1.0 - ( el_top + el_h ) / ( viewport_h + el_h );
  }
  
  return result;
}

```


## Send high to parent

```js
//este envia su altura
function sendHeight(){
    var actual_height = document.querySelector('body').scrollHeight;
    var data = {
      'contentheight':actual_height
    }
    window.parent.postMessage(JSON.stringify(data),"*");
}




//el padre recibe la altura del hijo y ajusta
window.addEventListener("message", receiveMessage, false);


function receiveMessage(event) {
    console.log(event.data)
    var pass_data = JSON.parse(event.data);
    if(pass_data.contentheight){
        page.style.height = pass_data.contentheight + 'px';
    }
}
```

## SMOTH SCROLL

```js
//hace smoth scroll al elemento seleccionado, se le pasa el selector, #id .clase o tag tipo h1


function smoothScroll(eID) {


  //toma la posicion del elemento, el cual debe pasarse para que sea uno solo por queryselector: '.clase', '#id', 'tag'
  function elmYPosition(eID) {
      var elm = document.querySelector(eID);
      var y = elm.offsetTop;
      var node = elm;
      while (node.offsetParent && node.offsetParent != document.body) {
          node = node.offsetParent;
          y += node.offsetTop;


          if ( window.innerWidth < 768) {
              y-=50;   
          }
      }
      return y;
  }
  
  //toma la posicion actual de la ventana
  function currentYPosition() {
      // Firefox, Chrome, Opera, Safari
      if (self.pageYOffset) return self.pageYOffset;
      // Internet Explorer 6 - standards mode
      if (document.documentElement && document.documentElement.scrollTop)
          return document.documentElement.scrollTop;
      // Internet Explorer 6, 7 and 8
      if (document.body.scrollTop) return document.body.scrollTop;
      return 0;
  }




  //smoth scroll
  var startY = currentYPosition();
  var stopY = elmYPosition(eID);
  var distance = stopY > startY ? stopY - startY : startY - stopY;
  if (distance < 100) {
      scrollTo(0, stopY); return;
  }
  var speed = Math.round(distance / 100);
  if (speed >= 20) speed = 20;
  var step = Math.round(distance / 25);
  var leapY = stopY > startY ? startY + step : startY - step;
  var timer = 0;
  if (stopY > startY) {
      for ( var i=startY; i<stopY; i+=step ) {
          setTimeout("window.scrollTo(0, "+leapY+")", timer * speed);
          leapY += step; if (leapY > stopY) leapY = stopY; timer++;
      } return;
  }
  for ( var i=startY; i>stopY; i-=step ) {
      setTimeout("window.scrollTo(0, "+leapY+")", timer * speed);
      leapY -= step; if (leapY < stopY) leapY = stopY; timer++;
  }
}

```


## LAZY LOAD IMAGES

HTML:

```html
<figure class="imagen lazy-load-image">
                                <img src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" data-src=“rutaurlcompleta separadas por coma” data-src-768="" data-src-mobile=" alt="Gaming invasion picture">
                                <noscript>
                                    <img src="" alt="Gaming invasion picture">
                                </noscript>
                            </figure>

```


```js

FUNCION: 
function loadLazyImages() {
    let dimensiones = {
        mobile: 50,
        tablet: 768,
        desktop: 992,
    }


    let lazyImages = document.querySelectorAll('.lazy-load-image');


    
    if ( lazyImages.length > 0 ) {


        //cargamos todas las imagenes
        lazyImages.forEach(element => {
        
            //recuperamos data de imagen orginal
            let image = element.querySelector('img');
            //recoletamos los datos del elemento
            let iSrc = image.getAttribute('data-src');
            let iSrc768 = image.getAttribute('data-src-768');
            let iSrcMov = image.getAttribute('data-src-mobile');
            let iSrcSVG= image.getAttribute('data-src-svg');
            let alt = image.getAttribute('alt');
    
            if ( iSrc.trim() == '' ) { 
                return;
            }




            //elemento picture
            let picture = document.createElement('picture');


            
            //elemento svg 
            if ( iSrcSVG != null ) {


                let sourceSVG = document.createElement('source');
                    sourceSVG.setAttribute('type', 'image/svg+xml' );
                    sourceSVG.setAttribute('srcset', iSrcSVG.trim() );


                picture.append(sourceSVG);
            }


            //elemento source por defecto, es el mayor


            let srcDefaults = iSrc.trim().split(',' );
            let dataSrcDesktop = '';


            for (let a = 0; a < srcDefaults.length; a++) {
                if (a !=0) {
                    dataSrcDesktop += ', ';
                }
                dataSrcDesktop += srcDefaults[a] + ' ' + (a+1) + 'x';
            }




            let sourcedesktop = document.createElement('source');
                sourcedesktop.setAttribute('media', '(min-width: '+dimensiones.desktop+'px)' );
                sourcedesktop.setAttribute('srcset', dataSrcDesktop );


            
            picture.append(sourcedesktop);
           


            //elemento source segundo


            if ( iSrc768.trim() != '' ) {
                let src768 = iSrc768.trim().split(',' );


                let dataSrc768 = '';


                for (let b = 0; b < src768.length; b++) {
                    if (b !=0) {
                        dataSrc768 += ', ';
                    }
                    dataSrc768 += src768[b] + ' ' + (b+1) + 'x';
                }




                let source768 = document.createElement('source');
                    source768.setAttribute('media', '(min-width: '+dimensiones.tablet+'px)' );
                    source768.setAttribute('srcset', dataSrc768 );


                
                picture.append(source768);
            }
            


            //elemento source mobile


            if ( iSrcMov.trim() != '' ) {
                let srcMobile = iSrcMov.trim().split(',' );


                let dataSrcMobile = '';


                for (let c = 0; c < srcMobile.length; c++) {
                    if (c !=0) {
                        dataSrcMobile += ', ';
                    }
                    dataSrcMobile += srcMobile[c] + ' ' + (c+1) + 'x';
                }




                let sourceMobile = document.createElement('source');
                    sourceMobile.setAttribute('media', '(min-width: '+dimensiones.mobile+'px)' );
                    sourceMobile.setAttribute('srcset', dataSrcMobile );


                
                picture.append(sourceMobile);
            }
            


            //creamos elemento img por defecto
            let img = document.createElement('img');
                img.src = srcDefaults[0];
                img.setAttribute('alt', alt);


                picture.append(img);
            


            //borro la imagen original si es que estaba
            element.innerHTML = '';
            //agregamos la imagen al dom
            element.append(picture);
    
        });
    }
}
```