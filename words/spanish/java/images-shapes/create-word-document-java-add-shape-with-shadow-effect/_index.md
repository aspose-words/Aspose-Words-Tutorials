---
category: general
date: 2026-06-30
description: Crear un ejemplo en Java para documento Word que muestre cómo agregar
  una forma al documento, establecer el color de relleno de la forma y aplicar un
  efecto de sombra a la forma en solo unas pocas líneas.
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: es
og_description: Crear tutorial de Java para documentos Word que muestre cómo agregar
  una forma al documento Word, establecer el color de relleno de la forma y aplicar
  un efecto de sombra a la forma.
og_title: Crear documento Word en Java – Añadir forma con efecto de sombra
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: Crear documento Word en Java – Añadir forma con efecto de sombra
url: /es/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word Java – Añadir forma con efecto de sombra

¿Alguna vez necesitaste **crear documento word java** con código que dibuje un rectángulo y le aplique una sombra sutil? No eres el único. Ya sea que estés generando informes, facturas o un simple volante, poder **añadir forma a documento word** de forma programática ahorra horas de ajustes manuales.  

En esta guía recorreremos un ejemplo completo, listo para ejecutar, que no solo crea un nuevo archivo Word, sino que también **establece el color de relleno de la forma**, **cómo añadir sombra a la forma**, y finalmente **aplica el efecto de sombra a la forma** con Aspose.Words for Java. Sin rodeos—solo los pasos exactos que puedes copiar‑pegar en tu IDE.

> **Consejo profesional:** Si eres nuevo en Aspose.Words, asegúrate de tener el último JAR en tu classpath. La API que usamos funciona con la versión 23.10 y superiores.

## Qué construirás

Al final de este tutorial tendrás un archivo `.docx` que contiene:

* Un documento Word en blanco creado desde cero.  
* Un rectángulo amarillo (150 × 80 pts) insertado en la primera página.  
* Una sombra gris suave desplazada unos puntos, que le da a la forma un aspecto elevado.  
* Todo lo anterior logrado con solo unas cuantas sentencias Java.

Sin plantillas externas, sin XML complicado—código Java puro que cualquiera puede ejecutar.

---

## Crear documento Word Java – Insertar una forma

Lo primero que necesitamos es un objeto `Document` nuevo y un `DocumentBuilder`. Piensa en el builder como un lápiz que nos permite dibujar dentro del documento.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por qué es importante:* `Document` representa todo el archivo, mientras que `DocumentBuilder` nos brinda métodos convenientes como `insertShape`. Sin el builder tendríamos que manipular nodos de bajo nivel directamente—mucho más trabajo.

## Añadir forma a documento Word – Insertar el rectángulo

Ahora realmente **añadimos forma a documento word**. En nuestro caso es un rectángulo, pero podrías elegir cualquier `ShapeType` que Aspose admita (elipse, flecha, etc.).

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

Esa única línea hace tres cosas:

1. Crea el objeto de forma.  
2. Lo posiciona en la ubicación actual del cursor (por defecto, la esquina superior izquierda de la página).  
3. Lo agrega a la colección interna de nodos del documento.

Si alguna vez te preguntaste *cómo añadir sombra a forma* después de esto, sigue leyendo—porque lo veremos a continuación.

## Establecer color de relleno de la forma – Personalizar la apariencia

Un rectángulo blanco simple no es muy emocionante, así que **establezcamos el color de relleno de la forma** a algo brillante. Usaremos la clase `java.awt.Color` de Java, que Aspose acepta directamente.

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

Si lo deseas, cambia `YELLOW` por `RED`, `GREEN` o cualquier valor RGB personalizado (`new Color(123, 45, 67)`). El color de relleno es la superficie que verás antes de que la sombra entre en juego.

## Cómo añadir sombra a forma – Configurar la sombra

Aquí es donde ocurre la magia. Aspose.Words expone un objeto `ShadowEffect` que nos permite afinar el aspecto de la sombra.

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**Por qué cada propiedad es importante:**

| Propiedad | Qué hace | Valores típicos |
|----------|----------|-----------------|
| `setColor` | Determina el tono de la sombra. El gris funciona en la mayoría de los casos, pero puedes usar `Color.BLUE` para algo más atrevido. | Cualquier `java.awt.Color` |
| `setBlurRadius` | Controla cuán suaves aparecen los bordes. Números mayores generan un aspecto más difuso. | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | Mueve la sombra horizontal y verticalmente. Valores positivos desplazan la sombra hacia abajo‑y‑derecha. | -10 – 10 |
| `setTransparency` | Define la opacidad; 0 es sólido, 1 es invisible. | 0.0 – 1.0 |

Si te preguntas **cómo añadir sombra a forma** sin desordenar el diseño, la clave es mantener los desplazamientos modestos. Un valor demasiado grande puede hacer que la sombra se extienda a la página siguiente.

## Aplicar efecto de sombra a la forma – Guardar el documento

Con la forma estilizada y la sombra configurada, solo queda persistir el archivo.

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Reemplaza `YOUR_DIRECTORY` con una ruta absoluta o relativa que exista en tu máquina. Después de ejecutar el programa, abre `ShadowShape.docx` en Microsoft Word o LibreOffice—deberías ver un rectángulo amarillo flotando sobre la página, gracias a la sombra gris que aplicamos.

---

## Verificar el resultado – Qué observar

Al abrir el archivo generado:

* El rectángulo debe estar centrado donde comenzó el cursor (esquina superior izquierda de la página por defecto).  
* Su relleno es de un amarillo brillante.  
* Una sombra gris sutil está desplazada 4 pts a la derecha y hacia abajo, con aproximadamente un 30 % de transparencia.

Si la sombra parece demasiado fuerte, reduce el `BlurRadius` o aumenta la `Transparency`. Si la forma no es visible, verifica la llamada a `setFillColor`—quizá el color elegido se mezcla con el fondo de la página.

---

## Problemas comunes y casos límite

| Problema | Causa | Solución |
|----------|-------|----------|
| **La sombra desaparece** | `Transparency` establecida en `1.0` (totalmente transparente). | Usa un valor menor, por ejemplo `0.3`. |
| **La forma no se ve** | El color de relleno coincide con el fondo de la página (a menudo blanco). | Elige un color contrastante con `setFillColor`. |
| **La sombra se corta en el margen** | Los desplazamientos empujan la sombra fuera del área imprimible. | Reduce `OffsetX`/`OffsetY` o amplía los márgenes mediante `PageSetup`. |
| **Error de compilación: `cannot find symbol ShadowEffect`** | Se está usando una versión antigua de Aspose.Words que no incluye soporte de sombra. | Actualiza a Aspose.Words 23.10+ (la API introdujo `ShadowEffect` en 22.12). |

---

## Próximos pasos – Más allá de lo básico

Ahora que sabes cómo **crear documento word java**, **añadir forma a documento word**, **establecer color de relleno de la forma**, **cómo añadir sombra a forma**, y **aplicar efecto de sombra a la forma**, quizás te preguntes qué más puedes hacer. Aquí tienes algunas ideas:

* **Colores dinámicos** – Obtén valores RGB de una base de datos para codificar colores de formas según su estado.  
* **Múltiples sombras** – Apila dos configuraciones de `ShadowEffect` clonando la forma y desplazando cada copia.  
* **Texto dentro de formas** – Usa `Shape.getTextFrame()` para incrustar un título o etiqueta.  
* **Exportar a PDF** – Llama a `document.save("output.pdf", SaveFormat.PDF)` para obtener una versión lista para imprimir con la misma fidelidad visual.

Cada una de estas extensiones se basa en el mismo patrón central que demostramos: crear un documento, insertar una forma, estilizarla y guardar.

---

## Ejemplo completo (listo para copiar‑pegar)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

Ejecutar la clase genera `ShadowShape.docx` en el directorio de trabajo actual. Ábrelo y verás el resultado exacto descrito anteriormente.

---

## Conclusión

Acabamos de mostrarte cómo **crear documento word java** desde cero, **añadir forma a documento word**, **establecer color de relleno de la forma**, **cómo añadir sombra a forma**, y finalmente **aplicar efecto de sombra a la forma**—todo con un fragmento de código compacto y fácil de entender.  

El enfoque es deliberadamente sencillo para que puedas adaptarlo a escenarios más complejos—ya sea que necesites múltiples formas, colores diferentes o sombras de estilo animado. Recuerda estar atento a la compatibilidad de la versión de la API y no dudes en ajustar los parámetros de sombra para que se adapten a tu lenguaje de diseño.

¿Probaste alguna variante? Tal vez colocaste una imagen detrás del rectángulo o añadiste una tabla dentro de la forma. Deja un comentario abajo; me encanta ver cómo los desarrolladores llevan estos ejemplos más allá. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}