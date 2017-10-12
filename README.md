# Taller de Github pages

**__Update: estoy trabajando en un post en Medium en el que muestro paso por paso el mismo tutorial en Windows y escrito más formal. Si la U no ataca nuevamente lo liberaré dentro de los próximos días__**

## Presentación
<Todo>



# Inicio

Crear repositorio con nombre usuario.github.io
En consola:
```
git clone https://github.com/usuario/usuario.github.io
```
Cambiar al directorio del proyecto.
```
cd usuario.github.io
touch index.html
```
Index es el archivo que por default se utiliza como frontpage o página de inicio.
Abrir el archivo con un editor (Sublime/VSCode/Atom/Vim/Emacs/etc):
```
subl index.html
```
Escribir hello zawarudo y guardar.
Abrir el archivo en un Web Browser
OMG lo que sale aparece en Internet!!
Mmm <fogs> no aún, el buscador esta abriendo la página desde los archivos del PC,
pero eso no significa que otro pueda ver la misma página, si se pudiera asi de simple
otra persona podria acceder a los archivos de tu pc con igual facilidad y robar tus memes. ¿Ya pero entonces por qué sale? Internet es un sistema de transferencia de archivos, esto significa que cuando ustedes ven una página web en verdad la descargan y luego el Web Browser se las muestra, por lo mismo es sencillo para gente que hace phishing copiar la página de un banco y tratar de que ustedes entren a la página incorrecta.

... ¿Pucha, entonces como lo subo?
En general esta parte detiene a muchos, hay que configurar muchas cosas, un dominio, DNS un Host etc etc. 
Github pages se encarga de todo esto, de forma gratuita (si suena a algo muy bueno y lo es). Github te permite
utilizar su dominio para mostrarle tu sitio a los demás, pero bajo ciertas condiciones, Github solo permite 
páginas simples y la idea es que la uses para mostrar tus proyectos, no para transacciones bancarias y similares.
¿OMG y como lo uso?
Bueno, ya crearon el repositorio, por lo que solo hay que subir el código de la página al repositorio.
```
git add index.html
git commit -m "mensaje util"
git push origin master
```
Dentro de los próximos minutos deberían poder ver la página en <usuario>.github.io.

OMG aparece en internet: si, y de hecho ahora con el link cualquiera puede verla.
Oye, y puedo comprar un dominio y hacer todo eso con Github ? Si, pero dado que eso involucra comprar un dominio no lo veremos.
Sin embargo esta documentado en Github <poner documentacion>.

# Template
Lo anterior se ve super simple, pero es el inicio para hacer páginas que vendan humo y se vean más p r o f e s i o n a l e s.
En verdad la mayoría usa un template y lo rellena con cosas, pero muchos no saben cambiar el template cuando necesiten algo,
la idea es que aprendan el como modificar cosas para después agregar/quitar/cambiar lo que quieran de cualquier template
que utilicen. Por lo mismo, usaremos el template más vacío de la vida y veremos como modificarlo y agregar nuestros propios elementos.

Descargar el starter template de materialize css.
En consola (Ctrl+Alt+T):
```
wget http://materializecss.com/templates/starter-template.zip
```
También se puede descargar de [página de materialize](http://materializecss.com/getting-started.html)

Esto lo descomprimen y mueven el contenido de la carpeta a la carpeta de su proyecto/repositorio/repo.

Solo para hacer la prueba, pusheen nuevamente al repo. ¿Qué es pushear al repo? mmmm de forma simplificada es usar: 
```
git add -A
git commit -m "template de materialize"
git push origin master
```
**__Ojo:__* el -A significa All, es decir, se envian todos los archivos de la carpeta del proyecto a Github. Su página debería verse más boni ahora.

En general uno cambia cosas a los templates y los va transformando, pero como dije antes este template es bastante vacío. En general es mejor trabajar en *local* es decir, en el PC y mandar los cambios importantes a Github. Por lo mismo, mantegan abierto el index.html en el buscador y veamos como se reflejan cambios simples.

Por ejemplo, en la línea 6 cambiemos "Starter Template - Materialize" por "Mi página" y guarden, en el buscador presionen F5, arriba el nombre de la pestaña debería haber cambiado. Pero todo se ve confuso con < algo >< /algo > y otras cosas que no entiendo. Estos son tags, y lamentablemente cada < yo > tiene un significado distinto y realiza cosas distintas, < algo > abre y < /algo > cierra, todo lo que esta dentro adquirá propiedades definidas de ese algo. Por ejemplo, en el tag head entre las líneas 3-12 se encuentran los scripts, links al CSS que se está usando y otras cosas que no se muestran directamente en la página. El < body > contiene la página, < div > define una división del documento y ayuda a separar elementos cuando la página queda mal configurada y hay cosas encima de otras. < ul > se utiliza para listas, < a > para links. No necesitan recordar todo esto, solo saber como se estructura el archivo/documento html.

 ¿Oye pero como sabes todo eso? Lo googlié mientras escribía esto, Google o **__inserte buscador que no invada su privacidad __** es su mejor amigo. ¿Y esas cosas que dicen class, href y todo lo que esta dentro de los tags? mmm href es donde pones un link al que deberia llevarte clickear el elemento (puede ser un link a tu propia página, y tampoco es tan cuadrado su uso). Las clases son otra cosa muy distinta, la clase es lo que permite definir un estilo para un elemento, de modo que cada vez que llamemos a la clase el elemento usara los parametros que definimos para el estilo de esa clase. En general los templates tienen varias clases que definen el estilo y que usamos para mantener un formato de la página y que se vea boni. ¿Dónde estan todas estas cosas, porque dices que hay muchas clases, supongo que eso no se busca en internet? mmm no, de hecho estan definidas en una carpeta de su proyecto llamada "css" y dentro de ella un archivo llamado materialize.css (la version min es una version minimizada y menos legible de lo mismo).

 Por ejemplo, en la línea 34 se encuentra el código que indica que ahí va un botón, ¿Cómo se que es un botón? bueno, tiene el texto del botón, de otro modo los buscadores tienen un comando inspect al hacer click derecho que te ayuda a identificar los elementos en las páginas que ves. Entonces, en la parte de "class=btn-large waves-effect waves-light orange" se define el estilo del botón, busquemos esto en el archivo del css (lo que comienza con . es una clase). Debería aparecer algo asi

```
.btn-large {
  height: 54px;
  line-height: 54px;
}
```

<oveja con jejejej> 
Height es altura, cambiemos la altura del botón a 20px (height corresponde al boton, line-height a la altura donde se ubica el texto dentro). F5 en el Browser y el botón cambió, yay! ¿Podemos cambiar el color? el color no esta dentro de los parámeotros de btn-large, debe estar en otro lado. Waves-effect me dice que es un efecto para el color, sabemos que orange es un color OMG puedo ponerle red? Veamos... si, funciona. Ahora, si buscamos ".orange" en el css vemos algo como:

```
.orange {
  background-color: #killmepls !important;
}
```
#ff9800 es el color escrito en hexadecimal, de hecho si lo escriben en google deberia aparecer una seleccion para colores. Entonces...¿qué pasa si cambiamos este naranjo por #00f6ff? El botón cambia, para el botón esta clase define su color. Deberiamos guardarlo como:

```
.colorfeo {
  background-color: #00ff43 !important;
}
```
Y dejar el naranjo como estaba, si ponemos ahora colorfeo en vez de orange el color debería seguir (o el color que elijan). Aquí cambién el color para que el cambio se notara. 

Oye pero esto es una lata, ¿quién va a escribir todo este código para definir un simple botón? mmm bueno, eso ya esta hecho, pero es importante que puedan tener control y cambiar lo que sea que necesiten cambiar. En general nos atendremos a la documentación del css que estemos usando, en este caso materialize tiene su documentación [aquí](http://materializecss.com/). Y aquí comienza lo interesante.

# Utilizando Materialize
## Utilizando el código de ejemplo
La documentación tiene los colores, botones, memes y todo lo que se te pueda ocurrir. Por ejemplo las cards son cartas donde suele ponerse una imagen.
 ```
 <div class="card">
    <div class="card-image waves-effect waves-block waves-light">
      <img class="activator" src="images/office.jpg">
    </div>
    <div class="card-content">
      <span class="card-title activator grey-text text-darken-4">Card Title<i class="material-icons right">more_vert</i></span>
      <p><a href="#">This is a link</a></p>
    </div>
    <div class="card-reveal">
      <span class="card-title grey-text text-darken-4">Card Title<i class="material-icons right">close</i></span>
      <p>Here is some more information about this product that is only revealed once clicked on.</p>
    </div>
  </div>
  ``` 
  Donde la imagen va en <img src="direccion_de_imagen.jpg"> si copiamos y pegamos queda una imagen gigante. Esto es porque el elemento se adapta al espacio que tiene definido, por lo que debemos definirle un espacio más pequeño.

  ```
  <div class="container">
    <div class="section">
      <div class="row">
          <div class="col s12 m4">
        <div class="card">
          <div class="card-image waves-effect waves-block waves-light">
            <img class="activator" src="imgs/fogs.jpg">
          </div>
          <div class="card-content">
            <span class="card-title activator grey-text text-darken-4">Card Title<i class="material-icons right">more_vert</i></span>
            <p><a href="#">This is a fogs</a></p>
          </div>
          <div class="card-reveal">
            <span class="card-title grey-text text-darken-4">Descripcion<i class="material-icons right">close</i></span>
            <p>En el dcc usamos muchos fogs, tal vez lo vieron en algunas auxiliares.</p>
          </div>
        </div>
      </div>
    </div>
    </div>
  </div>
  ```
Ahí si, mmm y ¿cómo pongo varias en fila? debemos ponerlas en la misma fila (row).

```
  <div class="container">
    <div class="section">
      <div class="row">
        <div class="col s12 m4">
          <div class="card">
            <div class="card-image waves-effect waves-block waves-light">
              <img class="activator" src="imgs/fogs.jpg">
            </div>
            <div class="card-content">
              <span class="card-title activator grey-text text-darken-4">Card Title<i class="material-icons right">more_vert</i></span>
              <p><a href="#">This is a fogs</a></p>
            </div>
            <div class="card-reveal">
              <span class="card-title grey-text text-darken-4">Descripcion<i class="material-icons right">close</i></span>
              <p>En el dcc usamos muchos fogs, tal vez lo vieron en algunas auxiliares.</p>
            </div>
          </div>
        </div>
        <div class="col s12 m4">
          <div class="card">
            <div class="card-image waves-effect waves-block waves-light">
              <img class="activator" src="imgs/fogs.jpg">
            </div>
            <div class="card-content">
              <span class="card-title activator grey-text text-darken-4">Card Title<i class="material-icons right">more_vert</i></span>
              <p><a href="#">This is a fogs</a></p>
            </div>
            <div class="card-reveal">
              <span class="card-title grey-text text-darken-4">Descripcion<i class="material-icons right">close</i></span>
              <p>En el dcc usamos muchos fogs, tal vez lo vieron en algunas auxiliares.</p>
            </div>
          </div>
        </div>
        <div class="col s12 m4">
          <div class="card">
            <div class="card-image waves-effect waves-block waves-light">
              <img class="activator" src="imgs/fogs.jpg">
            </div>
            <div class="card-content">
              <span class="card-title activator grey-text text-darken-4">Card Title<i class="material-icons right">more_vert</i></span>
              <p><a href="#">This is a fogs</a></p>
            </div>
            <div class="card-reveal">
              <span class="card-title grey-text text-darken-4">Descripcion<i class="material-icons right">close</i></span>
              <p>En el dcc usamos muchos fogs, tal vez lo vieron en algunas auxiliares.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
```
# Link a otra página

Yay much fogs. Ahora, ¿Cómo hago para que me lleve a otra de mis páginas? Creamos otro archivo .html. En consola, en el mismo espacio que index.html:
```
touch pag2.html
```
Dentro del archivo pongamos "Holirijillo mundirijillo" y una imagen por ahora. Copiamos el head y abajo:
```
<body>
    <div class="row center">
        <img src="imgs/meeseeks.jpg">
    </div>
</body>
      
```

Debemos linkear esta página con la otra, para ello pongamos otro botón al lado del anterior.

```
<a href="pag2.html" class="waves-effec waves-light btn-large red"><i class="material-icons left">cloud</i>Click me</a>
```
El href="pag2.html" es lo que te lleva al archivo pag2.html. Yay... con esto ya podemos tomar cualquier cosa y modificarla como queramos. Pero falta una última herramienta muy importante: javascript. No planeo enseñarles Javascript, pero si mostrar como se utilizan los comandos de Materialize que recurren a este lenguaje.

El código de pag2.html se dejará en el repo. Lo importante es cargar javascript y dejar los elementos dinámicos activados por medio de javascript, en javascript se pueden hacer funciones y activarlas con imágenes, botones, calcular etc. Es un lenguaje de programación cuyo uso principal es desarrollo web.
