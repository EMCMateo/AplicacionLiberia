# Informe de Auditoría de Estándares HTML y CSS

**Auditor:** Mateo Molina N.º 16  
**Compañero Auditado:** Mateo Miller N.º 15

## 1. Revisión de Requisitos (Qué esperaba y qué encontré)

### Requisitos Base
* **Estructura semántica:** Esperaba encontrar las etiquetas principales (`header`, `nav`, `main`, `section`, `aside`, `footer`) y los títulos en orden. *Verificación:* Sí cumple, el HTML está bien estructurado y los títulos bajan de h1 a h2 y h3 sin saltarse niveles.
* **Formulario:** Esperaba un formulario de al menos 5 campos con `label`, agrupados con `fieldset` y con validaciones nativas. *Verificación:* Cumple, tiene 7 campos bien agrupados y usa atributos como `required` y `min/max`. 
* **Tabla de datos:** Esperaba una tabla con `caption`, `thead`, `tbody` y encabezados `scope`. *Verificación:* Cumple. La tabla tiene todo y se puede navegar bien.
* **Layout Flexbox/Grid:** Esperaba el uso de Grid para la página entera y Flexbox para algo interno. *Verificación:* Cumple, usa Grid con `grid-template-areas` para acomodar la página y Flexbox para las tarjetas y el menú.
* **Colores y contraste:** Esperaba un contraste mínimo de 4.5:1. *Verificación:* Cumple, los colores de texto oscuros sobre los fondos claros pasan la prueba sin problema.
* **Accesibilidad por teclado y W3C:** Esperaba que se pueda navegar con la tecla Tab y que no tenga errores en el validador. *Verificación:* Cumple, se nota el outline naranja al navegar y no dio errores en la página del W3C.
* **Imágenes:** Esperaba que tengan el atributo `alt`. *Verificación:* Cumple, todas tienen su texto alternativo (incluso la primera tiene `alt=""` para que los lectores la ignoren por ser decorativa).

### Requisitos de la Ficha 15
* **Temática:** Agencia turística. *Verificación:* Cumple, hizo la página de la agencia "Andes Tours".
* **Campos especiales:** Fecha y hora de reserva. *Verificación:* Cumple, usó `input type="date"` y `type="time"`.
* **Breakpoint principal:** 768 px. *Verificación:* Cumple, en el CSS usó `@media (min-width: 768px)`.
* **Restricción especial:** Tipografía fluida con `clamp()`, sin media queries para los tamaños de letra. *Verificación:* Cumple, revisé el CSS y todos los tamaños de fuente usan la función `clamp()`.

---

## 2. Tabla de Hallazgos

El trabajo en general está súper bien hecho, pero le encontré un problema de validación con el número de teléfono y unos textos repetidos que afectan a los lectores de pantalla.

| N.º | Requisito | Ubicación (archivo y línea) | Hallazgo | Norma que incumple | Evidencia | Severidad |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Base 2: Formulario | `index_4.html`, línea 110 | El `pattern` del teléfono exige que se escriba todo seguido (`\+593[0-9]{9}`), pero el `placeholder` pone un ejemplo con un espacio (`+593 991234567`). Si un usuario copia el ejemplo tal cual, el formulario da error y no lo deja enviar. | WCAG 2.2, Criterio 3.3.2 (Etiquetas o instrucciones) |[Foto de el error en el espacio](/docs/evidencias/evidencia1.pngevidencia1.png) | Media |
| 2 | Base 2: Estructura de formulario | `index_4.html`, línea 139 | Ruptura de la estructura semántica. El formulario agrupa perfectamente la información en 3 `<fieldset>` (Datos, Detalles, Fecha), pero el campo de "Comentarios" quedó huérfano y suelto afuera de cualquier grupo. Esto desorienta a los usuarios de lectores de pantalla, ya que el formulario pierde su jerarquía lógica al final. | WHATWG HTML Standard (Uso semántico de Fieldset para agrupar controles lógicamente) | [Captura de código mostrando el textarea fuera de los fieldsets](/docs/evidencias/evidencia2.png) | Media |