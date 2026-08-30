---
category: general
date: 2026-07-26
description: Cómo insertar un botón ActiveX en un documento Word usando Aspose.Words
  – aprende a establecer el texto del botón, la posición y el tamaño en solo unas
  pocas líneas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: es
lastmod: 2026-07-26
og_description: Cómo insertar un botón ActiveX en un documento de Word con Aspose.Words.
  Sigue este tutorial paso a paso para establecer el texto del botón, la posición
  y el tamaño.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Cómo insertar un botón ActiveX en Word – Guía rápida
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Cómo insertar un botón ActiveX en Word – Establecer el texto del botón
url: /es/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar un botón ActiveX en Word – Establecer el texto del botón

¿Alguna vez te has preguntado **cómo insertar controles ActiveX** en un archivo Word sin abrir la interfaz de usuario? No eres el único. En muchas aplicaciones empresariales necesitas un botón clicable que ejecute una macro, y hacerlo programáticamente ahorra horas. Esta guía te muestra exactamente **cómo insertar un CommandButton ActiveX** usando Aspose.Words for Java, y—sí—cómo **establecer el texto del botón** para que el usuario sepa qué pulsar.

Recorreremos todo el proceso: desde configurar la biblioteca, crear un documento nuevo, colocar el botón, ajustar su tamaño y ubicación, darle un texto amigable, y finalmente guardar el archivo. Al final tendrás un `.docx` ejecutable que se abre en Word con un botón ActiveX totalmente funcional listo para disparar tu macro.

---

## Lo que aprenderás

- Instalar y referenciar Aspose.Words en un proyecto Java.  
- Crear un nuevo `Document` y `DocumentBuilder`.  
- **Insertar** un control CommandButton ActiveX con una sola línea de código.  
- **Establecer el texto del botón**, ajustar su posición y definir sus dimensiones.  
- Guardar el documento y abrirlo en Word para ver el resultado.

No se requiere experiencia previa con ActiveX; solo conocimientos básicos de Java y una copia de Aspose.Words.

---

## Requisitos previos

- Java 8 o superior instalado en tu máquina.  
- Maven o Gradle para la gestión de dependencias (mostraremos el fragmento para Maven).  
- Una copia con licencia o de evaluación de **Aspose.Words for Java** (la prueba gratuita funciona bien para esta demostración).  
- Microsoft Word (cualquier versión reciente) para probar el archivo generado.

---

## Paso 1: Configurar Aspose.Words en tu proyecto

Lo primero—agrega la dependencia de Aspose.Words. Si usas Maven, inserta esto en tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Los usuarios de Gradle pueden añadir:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Después de ejecutar un rápido `mvn clean install` (o `gradle build`) la biblioteca estará en tu classpath y estarás listo para codificar.

---

## Paso 2: Crear un documento nuevo y un builder

Un `Document` representa todo el archivo Word, mientras que `DocumentBuilder` te permite editarlo. Piensa en el builder como un lápiz que dibuja sobre un lienzo en blanco.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

¿Por qué comenzar con un documento vacío? Garantiza que tienes control total sobre cada elemento que añades, y no hay formato oculto que te sorprenda más adelante.

---

## Paso 3: Insertar el control CommandButton ActiveX

Ahora, la estrella del espectáculo. Aspose.Words expone `insertForms2OleControl` que puede colocar cualquier control ActiveX que especifiques. Aquí solicitamos un **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

El método devuelve un objeto `Forms2OleControl`, dándote acceso programático a las propiedades del botón. Aquí es donde **cómo insertar activex** se convierte en una sola línea—sin tener que manipular APIs COM de bajo nivel.

---

## Paso 4: Posicionar, dimensionar y establecer el texto del botón

Un botón que flota en medio de la página no es muy útil. Querrás colocarlo donde los usuarios lo esperen, darle un tamaño razonable y—lo más importante—**establecer el texto del botón** para que sepan qué hará al pulsarlo.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**¿Por qué estos números?** Word usa puntos (1 pt ≈ 1/72 pulgada). `100 pt` ≈ 1.4 pulgadas desde la izquierda, `150 pt` ≈ 2.1 pulgadas desde la parte superior—aproximadamente el centro de una página A4 estándar. Ajústalos según tu diseño.

Establecer el texto es crucial; sin él el botón parece un rectángulo vacío. El método `setCaption` acepta cualquier cadena, por lo que puedes localizarlo más tarde si lo deseas.

---

## Paso 5: Guardar el documento

Finalmente, escribe el documento en disco. Puedes elegir cualquier carpeta que desees; solo asegúrate de que la ruta exista.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Al abrir `ActiveXButton.docx` en Word, verás un botón bien colocado con la etiqueta **“Click Me.”** Si haces doble clic, Word te pedirá habilitar macros (ya que los controles ActiveX se consideran habilitados para macros). Desde allí puedes vincular una rutina VBA al evento `Click` del botón.

---

## Casos límite y consejos que podrías pasar por alto

- **Formato habilitado para macros**: Word desactiva los controles ActiveX en archivos `.docx` normales a menos que el usuario habilite las macros. Si necesitas que el botón funcione directamente, considera guardar como `.docm` (macro‑enabled) usando `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibilidad**: Las versiones antiguas de Word (previas a 2007) usan el formato binario `.doc`. Aspose.Words puede guardar en ese formato, pero las propiedades del control pueden renderizarse ligeramente diferente.
- **Configuración de seguridad**: Algunos entornos corporativos bloquean ActiveX. Si tu botón no aparece, revisa Centro de confianza de Word → Configuración de ActiveX.
- **Múltiples botones**: ¿Quieres más de uno? Simplemente repite la llamada a `insertForms2OleControl` y ajusta los valores `Left`/`Top` de cada botón. Mantén referencia a los objetos devueltos para poder establecer textos individuales.
- **Estilizar el texto**: El texto hereda la fuente predeterminada. Para cambiarlo, tendrías que editar el XML subyacente o aplicar un estilo de Word después de la inserción—fuera del alcance de esta guía rápida, pero posible con la API `ParagraphFormat` de Aspose.Words.

---

## Ejemplo completo y funcional

A continuación tienes la clase Java completa, lista para ejecutar. Copia‑pega en tu IDE, ajusta la ruta de salida y pulsa **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Salida esperada**: Después de ejecutar, la consola muestra la ubicación de guardado. Al abrir el archivo generado en Word verás un botón colocado aproximadamente en el centro de la página, etiquetado “Click Me”. Al pulsarlo se disparará el evento estándar de click de ActiveX (deberás adjuntar una macro VBA para responder).

---

## Conclusión

Ahora sabes **cómo insertar controles CommandButton ActiveX** en un documento Word de forma programática con Aspose.Words, y has visto exactamente cómo **establecer el texto del botón**, posicionarlo y dimensionarlo. Este enfoque elimina el trabajo manual de la UI, se integra limpiamente en generadores de informes automatizados y te brinda control total sobre el

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}