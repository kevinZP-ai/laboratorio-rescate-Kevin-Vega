# Bitácora del laboratorio de rescate.

--------------------------------------------------------------------------------------------------------------------------

1. ¿qué muestra cada comando?

- git log

commit 8ec6660c1dd541905e36bad0827be8ce421e51a8 (HEAD -> main, origin/main, origin/HEAD)
Author: kevin vega <vegaperezkevinsantiago@gmail.com>
Date:   Wed Nov 25 15:47:25 2026 -0500

    feat: agrega notas y bitácora

commit 4b2960d6c368166c2eee0f3226f93b7257940429
Author: kevinZP-ai <vegaperezkevinsantiago@gmail.com>
Date:   Wed Nov 25 15:39:18 2026 -0500

    Initial commit

 RTA: Muestra la lista de todos los cambios que he guardado (commits), con el código de cada uno, quién lo hizo y cuándo.

- git log --oneline

8ec6660 (HEAD -> main, origin/main, origin/HEAD) feat: agrega notas y bitácora
4b2960d Initial commit
 
 RTA: Muestra la misma lista de cambios, pero resumida en una sola línea por cambio: solo el código corto y el mensaje.

-  git log --oneline --graph --all

* 8ec6660 (HEAD -> main, origin/main, origin/HEAD) feat: agrega notas y bitácora
* 4b2960d Initial commit

 RTA: Muestra la lista resumida de cambios y además dibuja con asteriscos (*) cómo se van conectando unos con otros.
 
- 1.2 ¿Qué es el código que aparece al inicio de cada commit?

RTA: Es como el número de cédula de cada cambio: un código único que Git le pone a cada commit para poder reconocerlo.
--------------------------------------------------------------------------------------------------------------------------

2.  ¿por qué el segundo git diff no mostró nada?

RTA: Porque después de usar git add, los cambios ya quedaron "apartados" para guardarse. Y git diff solo muestra lo que todavía NO se ha apartado.

- git add (nombre del archivo/documento)

RTA: Aparta el archivo para el próximo guardado. Es como poner algo en una caja antes de cerrarla.

- git diff  

RTA: Muestra lo que cambió en los archivos: si agregaste algo sale con (+) en verde, y si quitaste algo sale con (-) en rojo.

- git commit -m "Clave: lo que se hizo"

RTA: Guarda los cambios que ya estaban apartados con git add, y les pone un mensaje para recordar qué se hizo.

- 2.2 ¿Qué muestra --staged?

- git diff --staged

RTA: Muestra los cambios que ya están apartados (con git add), comparando cómo estaban antes y cómo quedaron. Sale porque antes usé git add notas.txt.

--------------------------------------------------------------------------------------------------------------------------

3. ¿qué hace git restore ? 

- git restore 

RTA: Devuelve un archivo borrado a como estaba antes, pero solo funciona si ese archivo ya se había guardado alguna vez con un commit.

- git status

RTA: Muestra cómo están los archivos ahora: cuáles fueron modificados, cuáles están apartados para guardar y cuáles Git todavía no conoce.

- del 

RTA: Es el comando de Windows para borrar un archivo de la carpeta.

- 3.2 ¿Funcionaría si nunca hubieras hecho commit de ese archivo?

RTA: No, porque git restore necesita una copia guardada antes para poder devolverla. Si nunca guardaste ese archivo, no hay de dónde recuperarlo.

--------------------------------------------------------------------------------------------------------------------------

4. ¿qué diferencia hay entre git restore y git restore --staged ?

RTA: git restore borra los cambios y deja el archivo como estaba en el último guardado. En cambio, git restore --staged solo saca el archivo de la "caja" donde estaba apartado, pero los cambios siguen ahí.

- git add .

RTA: Aparta todos los archivos modificados de una vez para el próximo guardado.

- git restore --staged

RTA: Saca el archivo de la caja donde estaba apartado, pero no borra los cambios. Es lo contrario de git add.

- git push

RTA: Sube los cambios guardados a internet (por ejemplo, a GitHub), para que queden en el servidor.

--------------------------------------------------------------------------------------------------------------------------

5. "Escribí mal el mensaje del commit"

- git commit --amend -m "Clave: lo que se hizo"

RTA: Sirve para corregir el mensaje del último guardado, pero solo si todavía no lo has subido a internet. Si ya lo subiste, estarías cambiando algo que otras personas ya tienen.

--------------------------------------------------------------------------------------------------------------------------

6. ¿git revert borró el commit equivocado o creó uno nuevo? ¿Por qué es la opción segura cuando ya se hizo push?

- git revert HEAD

RTA: git revert NO borra el cambio equivocado: crea un cambio nuevo que deshace lo que hizo el anterior. Es seguro porque no toca lo que ya está subido a internet, solo agrega un cambio nuevo encima. Así nadie más sale afectado.

--------------------------------------------------------------------------------------------------------------------------

7. ¿qué diferencia hay entre git reset --soft y git revert? 

RTA: git reset --soft borra el último guardado del historial (solo se usa en tu computadora, antes de subirlo) pero deja los cambios ahí, listos para volver a guardar. git revert, en cambio, no borra nada: crea un guardado nuevo que deshace lo anterior, y por eso se puede usar aunque ya esté subido.

- 7.2 ¿Cuándo se usa cada uno?

- git reset --soft HEAD~1

RTA: Deshace el último guardado pero deja los cambios apartados, listos para volver a guardar. Se usa cuando ese guardado todavía no lo has subido.

- git reset --hard

RTA: Deshace el guardado y además borra los cambios para siempre, sin poder recuperarlos fácilmente. Por eso no se usa en este laboratorio.

--------------------------------------------------------------------------------------------------------------------------

8. ¿para qué sirve git stash? 

- git stash

RTA: Guarda temporalmente los cambios que no quieres guardar todavía, y deja la carpeta limpia. Sirve para cambiar de rama sin perder lo que estabas haciendo.

- git stash list

RTA: Muestra la lista de cosas que has guardado temporalmente con git stash.

- git switch -c fix/urgente

RTA: Crea una rama nueva llamada fix/urgente y se pasa a ella.

- git switch main

RTA: Se devuelve a la rama principal (main).

- 8.2 ¿Qué hace git stash pop?

- git stash pop

RTA: Devuelve los cambios que habías guardado temporalmente y los borra de la lista de guardados temporales.

--------------------------------------------------------------------------------------------------------------------------

9. Copia en tu bitácora el resultado final de git log --oneline --graph.

- git log --oneline --graph

RTA:

* af79556 (HEAD -> main, origin/main, origin/HEAD) docs: agrega línea 5 a notas
* 119f3ff (fix/urgente) feat: agrega borrador completo
* 762dbfa Revert "fix: limpia notas"
* 7f26897 fix: limpia notas
* 0436f30 docs: agrega línea 4 a notas
* 3ab4a8c fix: limpia notas
* 0273ae3 docs: agrega línea 4 a notas
* 06835d1 docs: modifica línea 2 de notas
* 8ec6660 feat: agrega notas y bitácora
* 4b2960d Initial commit

--------------------------------------------------------------------------------------------------------------------------