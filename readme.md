## Comando usado en el paso 11
`git reset --hard HEAD~1`
> Usamos **reset --hard** para poder deshacer todos los cambios en nuestro *working copy*. Usamos **HEAD~1** para deshacer desde donde nos encontramos (donde se encuentra nuestro puntero HEAD) hasta un paso atrás siguiendo el árbol.

## Comando usado en el paso 12
```
git reflog
git reset --hard 6223d19
```
> Usamos **reset --hard** por los mismos motivos que en el paso 11. En esta ocasión, en lugar de movernos al deshacer mediante el puntero HEAD, nos movemos directamente a un commit, que previamente hemos visto en el *reflog*.

## ¿Causó conflicto el merge del paso 13?
> **NO** causó conflicto, pues la rama *styled* ya contiene a la rama *master*, es decir, está por delante de la rama.

## ¿Causó conflicto el merge del paso 19?
> **SÍ** causó conflicto, pues la rama *styled* y la rama *htmlify* contenían versiones diferentes del mismo archivo en las mismas líneas.

## ¿Causó conflicto el merge del paso 21?
> **NO** causó conflicto, ya que las líneas modificadas en del archivo en cada rama son diferentes, por lo que simplemente actualiza su contenido.


## Comando usado en el paso 25
`git log --graph --decorate --pretty=oneline`
> Usamos **log** para mostrar todos los commits. Añadimos **--graph** para que nos lo muestre con forma de gráfica ("líneas de metro). Con **--decorate** conseguimos que nos diga además dónde se encuentrar nuestros punteros/ramas. Y con **--pretty=oneline** le decimos que nos muestre menos información y más compactada.

## El merge del paso 26, ¿podría ser fast-forward?
`git merge --no-ff title`
> **SÍ** podría ser un *fast forward*. De hecho, debemos indicar de manera forzada que no sea así con el comando arriba expuesto. Se produciría un *merge fast forward* ya que la rama *title* se encuentra inmediatamente por encima de *master*, por lo que para actualizar *master* no habría más que mover el puntero de la rama *master* a *title*, lo que conllevaría un *merge fast forward*.

## Comando usado en el paso 27
`git reset HEAD^1` o `git reset c538aa3`
> He usado la primera opción para poder volver atrás sin perder los cambios. Con **HEAD^1** volvemos un nivel atrás recorriendo el árbol. Ya que la rama *master* se encuentra tras un merge, tenemos una bifuración previa: *master* y *title*. Con el **^1** le indicamos que tome el camino previo al merge. No podríamos usar **git reset HEAD~1** puesto que no sabría qué camino tomar. En realidad sí que se puede, y tomaría el camino correcto, es decir el del previo al merge, pero es desaconsejable y me resulta más claro.

## Comando usado en el paso 28
`git checkout -- git-nuestro.md`
> Con este comando logramos descartar los cambios del working copy, como sugiere git al hacer un **git status**.

## Comando usado en el paso 29
`git branch -D title`
> Debemos utilizar **-D** (en mayúscula) ya que la rama *title* no estaba completamente mergeada.

## Comando usado en el paso 30
```
git reflog
git reset --hard c538aa3
```
> Primero usamos **reflog** para poder averiguar el id del commit en el que hicimos el merge. Despues, hacemos un **reset --hard** a dicho commit para rehacer todos los cambios. 
> 
> Hay varias formas de hacer esto mismo. También podríamos hacer un **checkout** al commit, crear una nueva rama y luego, desde master, hacer un merge con la nueva rama y borrar la rama auxiliar creada.

## Comando usado en el paso 32
```
git reflog
git reset --hard 52caec8
```
> Simplemente realizamos un **reflog** para buscar nuestro commit inicial y hacemos un **reset --hard** a éste. Recordemos que con **--hard** afectamos a nuestro *working copy*.

## Comando usado en el paso 33
```
git reflog
git reset --hard c538aa3
```
> De igual modo que en el paso 32, realizamos el paso inverso buscando nuestro commit del merge con el título y saltamos a él.