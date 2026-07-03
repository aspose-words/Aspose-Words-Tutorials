---
category: general
date: 2026-07-03
description: Crear forma de rectángulo en Java y aprender cómo agregar sombra a la
  forma, aplicar efecto de sombra, establecer la transparencia de la forma y crear
  un documento en blanco rápidamente.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: es
og_description: Crea una forma rectangular en Java con sombra, transparencia y un
  documento en blanco. Sigue esta guía para dominar el manejo de formas.
og_title: Crear forma de rectángulo en Java – Tutorial completo de programación
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Crear forma de rectángulo en Java – Guía completa paso a paso
url: /es/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Java – Guía completa paso a paso

¿Alguna vez te has preguntado cómo **crear una forma rectangular** en un documento Word usando Java? No eres el único: los desarrolladores a menudo necesitan una forma rápida de añadir gráficos geométricos y luego darles una sombra sutil para que el diseño se vea más pulido. En este tutorial recorreremos todo el proceso: desde generar un **documento en blanco** hasta **añadir sombra a la forma**, **aplicar efecto de sombra** e incluso **establecer la transparencia de la forma** para lograr un aspecto profesional.

El fragmento de código a continuación es un ejemplo completamente funcional que puedes copiar y pegar en tu proyecto. No se requiere documentación externa; solo sigue los pasos, comprende el “por qué” y generarás rectángulos con sombra en segundos.

## Lo que aprenderás

- Cómo **crear forma rectangular** programáticamente con Aspose.Words for Java.  
- Las llamadas exactas necesarias para **añadir sombra a la forma** y configurar sus propiedades visuales.  
- Formas de **aplicar efecto de sombra** y ajustar parámetros como desplazamiento, radio de desenfoque y color.  
- Técnicas para **establecer la transparencia de la forma** y obtener una apariencia más sutil.  
- Cómo **crear documento en blanco**, insertar la forma y guardar el resultado.

> **Consejo profesional:** Todas estas acciones se realizan sobre una única instancia de `Document`, lo que significa que puedes encadenarlas sin preocuparte por operaciones intermedias de I/O de archivos.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java 17 (o cualquier JDK reciente) instalado.  
- Biblioteca Aspose.Words for Java añadida a tu proyecto (coordenadas Maven: `com.aspose:aspose-words:23.12`).  
- Un IDE de Java o un editor de texto simple; nada sofisticado, solo un lugar para compilar y ejecutar.

Si te falta alguno de estos, descarga el JDK de Oracle y agrega la dependencia de Aspose mediante Maven o Gradle. Una vez hecho esto, estarás listo para continuar.

## Paso 1: **Crear documento en blanco** – el lienzo para todo

Lo primero que necesitas es un objeto `Document` vacío. Piensa en él como una hoja de papel fresca; sin él, no hay dónde colocar tu rectángulo.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

¿Por qué comenzar con un documento en blanco? Porque cada forma vive dentro de una `Section`, y un `Document` recién instanciado ya contiene una sección predeterminada con un cuerpo listo para recibir nodos. Omitir este paso te obligaría a crear secciones manualmente más adelante, lo que añade complejidad innecesaria.

## Paso 2: **Crear forma rectangular** y definir su tamaño

Ahora que tenemos un lienzo, vamos a **crear forma rectangular**. La clase `Shape` recibe la referencia al documento y un `ShapeType`. Aquí elegimos `RECTANGLE` y establecemos ancho/alto en puntos (1 pt ≈ 1/72 pulgada).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

¿Por qué establecer `WrapType.INLINE`? El ajuste en línea hace que la forma se comporte como un carácter dentro del párrafo, asegurando que se mueva con el texto circundante. Si necesitas un comportamiento flotante, cambia a `WrapType.SQUARE` o `WrapType.TOP_BOTTOM`.

## Paso 3: **Aplicar efecto de sombra** – dar profundidad al rectángulo

Un rectángulo plano se ve… plano. Añadir una sombra lo hace destacar. **Aplicaremos efecto de sombra** creando una instancia de `ShadowEffect` y luego ajustando sus propiedades visuales.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Desglosemos esto un poco:

- **Color** – `Color.getGray(0.5)` produce un gris al 50 %, neutro y que funciona en la mayoría de fondos.  
- **OffsetX/Y** – Valores positivos desplazan la sombra a la derecha y hacia abajo; valores negativos la moverían a la izquierda/arriba.  
- **BlurRadius** – Valores mayores crean una sombra más suave y difusa.  
- **Transparency** – Va de `0` (opaco) a `1` (totalmente transparente). Aquí elegimos `0.3` para un efecto sutil.

## Paso 4: **Añadir sombra a la forma** – vincular el efecto

Crear el efecto no es suficiente; debemos **añadir sombra a la forma** asignando el objeto `ShadowEffect` al rectángulo.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Detrás de escena, esta llamada actualiza el marcado OpenXML subyacente (`<w:shdw>`) que Word usa para renderizar sombras. Si inspeccionas el `.docx` guardado, verás un elemento `<w:effect>` poblado con los parámetros que configuramos.

## Paso 5: **Establecer la transparencia de la forma** – opcional pero a menudo útil

A veces deseas que el propio rectángulo sea semitransparente, permitiendo que el texto de fondo se vea. La clase `Shape` expone `setFillColor` y `setFillTransparency`. Aquí tienes un ejemplo rápido que hace que el rectángulo sea 40 % transparente:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

¿Por qué podrías hacer esto? Imagina una marca de agua o una llamada resaltada donde el contenido subyacente debe seguir siendo legible. Ajusta el valor de transparencia según tu lenguaje de diseño.

## Paso 6: Insertar la forma en el documento

Hemos construido el rectángulo, añadido una sombra y (opcionalmente) establecido su transparencia. El paso final es **añadir la forma a la primera sección del documento**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Agregar la forma al cuerpo la coloca al final del primer párrafo. Si necesitas un punto de inserción específico, recupera el `Paragraph` objetivo y usa `insertBefore` o `insertAfter`.

## Paso 7: Guardar el documento – ver el resultado

Todo ese trabajo culmina en una única llamada a `save`. Elige una ruta que tenga sentido para tu entorno.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Abre el `ShadowShape.docx` resultante en Microsoft Word o LibreOffice, y verás un rectángulo nítido con una suave sombra gris, ligeramente transparente si mantuviste el paso opcional. El aspecto visual coincide con los parámetros que definimos programáticamente.

---

![crear forma rectangular con sombra en un documento Word](https://example.com/images/rectangle-shadow.png "crear forma rectangular con sombra")

*Texto alternativo de la imagen:* **crear forma rectangular con sombra** – representación visual del resultado final.

## Preguntas frecuentes y casos límite

### ¿Qué pasa si quiero un color de sombra diferente?

Simplemente cambia la llamada a `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Recuerda que sombras demasiado vivas pueden parecer poco profesionales; los tonos sutiles suelen funcionar mejor.

### ¿Puedo aplicar la misma sombra a varias formas?

Sí. Crea una instancia de `ShadowEffect`, configúrala y reutilízala:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Solo evita mutar el `ShadowEffect` después de haberlo adjuntado a otras formas, a menos que quieras actualizar todas simultáneamente.

### ¿Cómo cambio dinámicamente el desenfoque de la sombra?

Expon un control deslizante en la UI que mapee a `setBlurRadius`. Valores entre `2` y `12` son típicos; números mayores producen un “resplandor” en lugar de una sombra nítida.

### ¿Qué ocurre si necesito que la forma flote en lugar de estar en línea?

Cambia el tipo de ajuste:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Las formas flotantes te dan más libertad de diseño, pero requieren lógica adicional de posicionamiento.

## Ejemplo completo funcional

A continuación tienes el programa completo, listo para copiar y pegar, que incorpora todos los pasos que discutimos. Ejecútalo como una aplicación Java normal.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Salida esperada:** Al abrir `ShadowShape.docx`, verás un rectángulo blanco de 200 × 100 pt, centrado en el primer párrafo, con una sombra gris medio desplazada 5 pt, desenfocada con radio 8 y 30 % transparente. El propio rectángulo es 40 % transparente, permitiendo que cualquier texto subyacente se asome.

## Conclusión

Acabamos de **crear forma rectangular** desde cero, **añadir sombra a la forma**, **aplicar efecto de sombra** e incluso **establecer la transparencia de la forma**, todo mientras **creamos documento en blanco** como base. El enfoque es sencillo, se basa en la API fluida de Aspose.Words y puede ampliarse a círculos, estrellas o polígonos personalizados.

¿Qué sigue en tu hoja de ruta? Prueba cambiar `ShapeType.RECTANGLE` por `ShapeType.OVAL` para generar círculos con sombra, o experimenta con rellenos degradados para

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}