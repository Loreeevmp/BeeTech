# 🐝 BeeTech - Juego de la Abeja en MIT App Inventor

¡Bienvenido a **BeeTech**, un videojuego móvil de agilidad y reflejos desarrollado completamente en la plataforma **MIT App Inventor**! El objetivo principal es ayudar a una pequeña abeja a polinizar tantas flores como pueda mientras esquiva los peligrosos pesticidas que caen de forma ilimitada del cielo.

## Mecánica del Juego

* **Puntaje:** Cada vez que la abeja recolecta una **Flor (`SpriteImagen2`)**, ganas `+1` punto.
* **Vidas:** El jugador inicia con `3` vidas. Si la abeja choca contra un **Pesticida (`SpriteImagen3`)**, pierde `1` vida.
* **Fin del Juego (Game Over):** Al llegar a `0` vidas, el juego se pausa y despliega una ventana interactiva (Notificador) con dos opciones: **Reintentar** (restablece marcadores a 0 puntos / 3 vidas y reinicia la caída) o **Salir** (cierra la pantalla).
* **Ciclo Infinito (Lluvia de Sprites):** Si los elementos (flores/pesticidas) caen al fondo sin ser recolectados, el temporizador detecta el suelo y los teletransporta automáticamente al techo con coordenadas `X` aleatorias, creando un flujo continuo sin fin.

## Arquitectura de los Bloques (Lógica de Programación)

El proyecto cuenta con un sistema de control perimetral y lógica de colisiones optimizada en tres módulos principales:

### 1. Control del Movimiento y Límites de la Abeja
Se implementó la función matemática **`tomar dentro de los límites` (Clamp)** en el evento `.Arrastrado` de la abeja. Esto restringe sus coordenadas máximas y mínimas para asegurar que el jugador nunca pueda arrastrar el sprite fuera de la pantalla del celular.

### 2. Ciclo del Temporizador (`Clock1.Temporizador`)
Un reloj de alta velocidad (`100ms` - `200ms`) que monitorea constantemente la posición vertical de los proyectiles:
* Se aplica una resta matemática en el eje vertical (`Lienzo1.Alto - 50`) para anticipar de forma precisa el contacto con el suelo.
* Al tocar fondo, el bloque `MoverA` reinicia el sprite en el eje `Y` a `0`, recalculando la posición horizontal mediante `entero aleatorio entre 1 y (Lienzo1.Ancho - Sprite.Ancho)`. Esto previene el error común de desbordamiento por la derecha.
* Se inyectan bloques nativos de **Velocidad** y **Dirección (270°)** para evitar el congelamiento de objetos en el techo.

### 3. Matriz de Colisiones Avanzada (`SpriteImagen1.EnColisiónCon`)
Manejo estructurado de colisiones por capas empleando condicionales anidados independientes (`si... entonces` separados):
* **Capa Flor:** Incrementa la variable global `puntos`, concatena limpiamente el string en la etiqueta correspondiente y reposiciona el sprite arriba de inmediato.
* **Capa Pesticida:** Decrementa la variable `vidas`, actualiza el texto y evalúa de forma asíncrona si la variable ha llegado a cero. Si se cumple, detiene el ciclo y dispara el Notificador interactivo mediante `MostrarDialogoDeElección`.


## Componentes del Canvas Utilizados
* **Lienzo1 (Canvas):** Contenedor gráfico con fondo campestre adaptado a escala del dispositivo.
* **SpriteImagen1 (Abeja):** Sprite controlado por el usuario a través de eventos táctiles drag-and-drop.
* **SpriteImagen2 (Flor):** Proyectil benéfico de aparición aleatoria.
* **SpriteImagen3 (Pesticida):** Proyectil de penalización con velocidad incremental.
* **Clock1 (Reloj):** Motor de física encargado de simular el bucle de gravedad infinita.
* **Notifier1 (Notificador):** Cuadro de diálogo modal nativo para el manejo de elecciones críticas en el Game Over.

Hecho con ❤️ y bloques de App Inventor. ¡Disfruta protegiendo a las abejas! 🐝

## Elaborado por:
* **Chan Dzib Valeri Samantha**
* **Chim Chable Reyna Alexandra**
* **Hobac Can Jimena Ashanty**
* **Mukul Basto Guadalupe Yoseline**
* **Parra Cruz Lorena Patricia**
6A de Programación
# AMA_DGETI
