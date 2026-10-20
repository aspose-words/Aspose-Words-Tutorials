---
category: general
date: 2026-07-06
description: Crear una forma rectangular en Java usando Aspose.Words – aprenda cómo
  añadir sombra a la forma, establecer la transparencia de la forma y guardar el documento
  como PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: es
og_description: Crear una forma rectangular en Java con Aspose.Words. Esta guía muestra
  cómo agregar sombra a la forma, establecer la transparencia de la forma y guardar
  el documento como PDF.
og_title: Crear forma rectangular en Java – Tutorial de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Crear forma rectangular en Java con Aspose.Words – Guía completa
url: /es/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma de rectángulo en Java con Aspose.Words – Guía completa

¿Alguna vez te has preguntado cómo **crear una forma de rectángulo** en Java sin luchar con APIs de dibujo de bajo nivel? No estás solo. Muchos desarrolladores necesitan una forma rápida y fiable de insertar un rectángulo en un documento Word, darle una sombra sutil, ajustar su transparencia y luego entregar el resultado como PDF.  

En este tutorial recorreremos exactamente eso, paso a paso, con código completo y ejecutable. Al final sabrás **cómo añadir sombra** a una forma, cómo **establecer la transparencia de la forma** y cómo **guardar el documento como PDF** usando Aspose.Words para Java. Sin rodeos, solo guía práctica que puedes copiar‑pegar en tu proyecto hoy.

## Lo que aprenderás

- La configuración mínima necesaria para trabajar con Aspose.Words en un proyecto Java.  
- Cómo **crear una forma de rectángulo** programáticamente.  
- Las llamadas exactas necesarias para **añadir sombra a la forma** y ajustar su difuminado, desplazamiento y opacidad.  
- Formas de **establecer la transparencia de la forma** para que el rectángulo se mezcle bien con el contenido circundante.  
- El método más sencillo para **guardar el documento como PDF** sin pasos de conversión adicionales.  

Si ya manejas Java básico y tienes un proyecto Maven o Gradle, estás listo para comenzar.

## Requisitos previos

- Java 8 o superior.  
- Aspose.Words for Java 23.x (o la última versión disponible al momento de leer).  
- Un IDE o herramienta de línea de comandos (IntelliJ, Eclipse, Maven, Gradle—elige la que prefieras).  

> **Consejo profesional:** Aspose ofrece una licencia temporal gratuita para evaluación. Obténla desde el portal de tu cuenta y coloca el archivo `license.xml` en tu classpath; de lo contrario verás una marca de agua en el PDF.

---

## Paso 1: **Crear forma de rectángulo** con Aspose.Words

Lo primero que necesitamos es un `Document` vacío y un `DocumentBuilder`. El builder es el motor que nos permite insertar formas directamente en el flujo del documento.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Por qué es importante:** `ShapeType.RECTANGLE` indica a Aspose que queremos un rectángulo perfecto. El ancho y la altura se expresan en puntos (1 pt ≈ 1/72 in), lo que te brinda un control granular sobre el tamaño final.

---

## Paso 2: **Añadir sombra a la forma**

Ahora que tenemos un rectángulo, le daremos una sombra sutil. El objeto `ShadowFormat` expone todo lo que necesitamos: radio de difuminado, desplazamiento X/Y y hasta transparencia.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Por qué es importante:** Una sombra sin difuminado parece una línea dura, lo que rara vez es lo que los diseñadores desean. La llamada `setBlur` suaviza los bordes, mientras que `setTransparency` permite que la sombra se desvanezca en el fondo. Ajusta estos valores para que coincidan con tus guías de UI.

---

## Paso 3: **Establecer la transparencia de la forma**

A veces necesitas que el propio rectángulo sea semitransparente—por ejemplo, para superponer un logotipo o una marca de agua. Aspose lo hace con una sola línea.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Por qué es importante:** La transparencia puede salvarte cuando estás superponiendo formas. Ten en cuenta que la transparencia de la sombra es independiente, por lo que puedes tener una forma tenue con una sombra más oscura si eso encaja en tu diseño.

---

## Paso 4: **Guardar documento como PDF**

Todo el trabajo visual está listo; el paso final es persistir el documento. Aspose.Words puede escribir directamente a PDF, eliminando la necesidad de una biblioteca de conversión separada.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Por qué es importante:** Al especificar `SaveFormat.PDF`, la biblioteca se encarga del incrustado de fuentes, compresión de imágenes y cumplimiento de PDF/A bajo el capó. El archivo resultante está listo para distribución, impresión o archivado.

---

## Ejemplo completo funcional

Juntándolo todo, aquí tienes la clase completa, lista para ejecutar. Copia‑pega, ajusta la carpeta de salida y tendrás un PDF con un rectángulo que proyecta una sombra realista.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Salida esperada:** Cuando abras `RectangleWithShadow.pdf`, verás un rectángulo gris claro centrado en la primera página, ligeramente elevado del papel por una sombra suave y semitransparente. La propia forma tiene un 20 % de transparencia, permitiendo que cualquier texto subyacente (si lo añadieras) se asome.

---

## Preguntas frecuentes y casos límite

### 1️⃣ ¿Qué pasa si necesito un rectángulo más grande?

Simplemente cambia los parámetros de ancho y alto en `insertShape`. Recuerda que 72 pt = 1 in, así que `400.0, 200.0` te dará un rectángulo de 5.5 × 2.8 pulgadas.

### 2️⃣ ¿Puedo usar un color diferente para la sombra?

Claro. La clase `ShadowFormat` también expone `setColor(java.awt.Color)`. Para una sombra gris sutil, prueba `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ ¿Funciona **guardar documento como PDF** en todas las plataformas?

Sí. Aspose.Words for Java es independiente de la plataforma; el mismo código se ejecuta en Windows, macOS y Linux siempre que tengas una JRE compatible.

### 4️⃣ ¿Cómo elimino la sombra más adelante?

Llama a `rect.getShadowFormat().clear();` o establece la propiedad `Visible` a `false` (`shadow.setVisible(false);`).

### 5️⃣ ¿Qué pasa con DPI y calidad de imagen?

Al guardar en PDF, Aspose usa automáticamente 300 DPI para gráficos vectoriales como las formas, por lo que obtienes resultados nítidos sin importar el nivel de zoom.

---

## Consejos profesionales y buenas prácticas

- **Procesamiento por lotes:** Si necesitas generar docenas de PDFs, reutiliza una única instancia de `Document` y solo limpia sus secciones entre iteraciones para reducir la presión del GC.  
- **Licenciamiento:** Coloca `License license = new License(); license.setLicense("license.xml");` al inicio de `main` para evitar la marca de agua de evaluación.  
- **Rendimiento:** Renderizar sombras es barato para formas simples, pero rutas complejas pueden ralentizar la generación de PDF. Perfila si procesas lotes grandes.  
- **Pruebas:** Usa primero `Document.save(..., SaveFormat.DOCX)` para verificar que la forma aparece correctamente en Word antes de convertir a PDF.

---

## Conclusión

Ahora sabes cómo **crear una forma de rectángulo** en Java con Aspose.Words, **añadir sombra a la forma**, **establecer la transparencia de la forma** y, finalmente, **guardar el documento como PDF**. El código es autónomo, funciona con la última librería de Aspose y muestra las llamadas API esenciales que necesitarás para la mayoría de los escenarios de automatización de documentos.

¿Listo para el próximo desafío? Prueba cambiar el rectángulo por una elipse, experimenta con rellenos degradados o explora cómo **añadir sombra** a marcos de texto. Los mismos principios se aplican, y la API de Aspose lo hace tan fácil como un pastel.

¡Feliz codificación, y no dudes en dejar un comentario si encuentras algún obstáculo!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Añadir forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo guardar documento como PDF con Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Cómo crear campos de formulario y añadir contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}