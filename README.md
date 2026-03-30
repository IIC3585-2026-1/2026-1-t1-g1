# 2026-1-t1-g1

## Setup 
Abrir HTML con Live Server.

## Referencias
* Patrón CSS del fondo: https://superdesigner.co/tools/css-backgrounds

## Uso de IA

Se utilizó ChatGPT y Claude principalmente para implementar la lógica del pergamino, específicamente para acceder y mostrar los fragmentos correctos de código CSS. Como resultado, la IA sugirió el uso de expresiones regulares (regex) que permiten identificar y extraer secciones específicas del código, facilitando su posterior visualización dinámica en la interfaz. En este caso, esto se realiza a partir de secciones comentadas del código que delimitan el contenido correspondiente a cada poción.

En relación con lo anterior, también se solicitó adaptar el contenedor que muestra el código para convertirlo en un área con *scrollbar*, permitiendo visualizar contenido extenso. Esto se logró mediante tres propiedades CSS:
- `word-break`: permite dividir palabras largas para evitar desbordamientos.
- `white-space`: respeta los saltos de línea del código original, agregando nuevos saltos cuando el contenido excede el ancho del contenedor.
- `overflow-y`: habilita la barra de desplazamiento vertical cuando el contenido supera la altura del contenedor.

Además, se utilizó ChatGPT para implementar la lógica de *drag and drop* de la poción hacia el caldero. Al comenzar el arrastre, se activa el evento `dragstart`, donde se guarda el `id` de la poción en formato de texto simple (`text/plain`). Posteriormente, se habilita el evento que permite soltar elementos sobre el caldero mientras un elemento está siendo arrastrado.

Durante este proceso, se agrega la clase `drag-over` al caldero para mostrar un efecto visual cuando una poción se encuentra sobre él. Cuando la poción sale del área del caldero, se activa el evento `dragleave`, eliminando dicha clase y devolviendo el caldero a su estado original.

Adicionalmente, al hacer clic en cualquier parte de la página, se activa un evento `click` en el `body`. Si el clic ocurre fuera del caldero, se eliminan todas las clases de pociones aplicadas al `body`, removiendo los efectos visuales y restaurando el estado inicial del contenido mostrado.

Finalmente, se utilizó Codex para implementar la interacción táctil en dispositivos móviles. Mediante `touchstart` se inicia el arrastre de la poción; `touchmove` permite desplazar una copia visual de esta y resaltar el caldero al pasar por encima; `touchend` aplica el efecto de la poción si se suelta sobre el caldero; y `touchcancel` limpia el estado del arrastre en caso de interrupciones.
