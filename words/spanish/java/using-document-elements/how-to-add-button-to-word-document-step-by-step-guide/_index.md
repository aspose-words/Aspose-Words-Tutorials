---
category: general
date: 2026-07-20
description: Cómo agregar un botón a un documento Word usando Aspose.Words. Aprende
  a insertar un botón Forms2OleControl con DocumentBuilder en minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: es
lastmod: 2026-07-20
og_description: Cómo agregar un botón a un documento de Word con Aspose.Words. Sigue
  esta guía práctica para incrustar un CommandButton de Forms2OleControl usando Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Cómo agregar un botón a un documento de Word – Tutorial completo de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Cómo agregar un botón a un documento de Word – Guía paso a paso
url: /es/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar un botón a un documento Word – Tutorial completo de Aspose.Words

¿Alguna vez te has preguntado **cómo agregar un botón a un documento Word** sin abrir la interfaz y hacer clic por todas partes? No eres el único. Muchos desarrolladores necesitan incrustar controles interactivos de forma programática—piensa en un botón “Enviar” en una plantilla que luego será completada por un usuario final. ¿La buena noticia? Con Aspose.Words for Java puedes hacerlo en unas pocas líneas.

En este tutorial recorreremos los pasos exactos para insertar un `Forms2OleControl` de tipo **CommandButton** usando el `DocumentBuilder`. Al final tendrás un archivo `.docx` listo para usar que muestra un botón clicable etiquetado “Click Me”. Sin misterios, solo código claro y la lógica detrás de cada línea.

## Lo que aprenderás

- Cómo crear un nuevo documento Word desde cero.
- Cómo usar **DocumentBuilder** para colocar un **Forms2OleControl**.
- Por qué debes establecer el texto del botón y el tamaño como lo hacemos.
- Cómo guardar y verificar el resultado.
- Trampas comunes (p. ej., bibliotecas faltantes, tipos de control no compatibles) y cómo evitarlas.

**Prerequisitos** – Necesitas Java 8+ (o superior) y la biblioteca Aspose.Words for Java (versión 23.12 o posterior). Un IDE como IntelliJ IDEA o Eclipse hará las cosas más fluidas, pero cualquier editor de texto funciona.

---

## Paso 1: Configura tu proyecto e importa dependencias

Antes de que se ejecute cualquier código, Maven (o Gradle) debe saber dónde obtener Aspose.Words. Añade este fragmento a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Si prefieres Gradle, el equivalente es:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Consejo profesional:** Usa la última versión; las versiones anteriores pueden no incluir la API `Forms2OleControl`.

Una vez que la dependencia se resuelva, estás listo para escribir código Java.

---

## Paso 2: Crea un nuevo documento y obtén un DocumentBuilder

La clase `Document` representa todo el paquete `.docx`, mientras que `DocumentBuilder` es el pincel que usas para pintar contenido sobre él. Piensa en `DocumentBuilder` como el “cursor” que sabe dónde debe ir el siguiente elemento.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:** Inicializar un `Document` nuevo te brinda un lienzo limpio. El builder apunta automáticamente al primer párrafo, por lo que no tienes que gestionar secciones o páginas manualmente.

---

## Paso 3: Inserta un Forms2OleControl de tipo CommandButton

Ahora llega la estrella del espectáculo: `insertForms2OleControl`. Este método crea un control OLE (Object Linking and Embedding) que Word trata como un elemento de formulario. Pasaremos tres argumentos:

1. `Forms2OleControlType.COMMANDBUTTON` – indica a Word que queremos un botón.  
2. `100` – ancho en puntos (≈1.39 pulgadas).  
3. `30` – alto en puntos (≈0.42 pulgadas).  

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Cómo funciona:** Internamente Aspose.Words crea el XML apropiado en la parte `word/document.xml`, haciendo referencia al objeto OLE. Las dimensiones que proporcionas son respetadas por el motor de diseño de Word, por lo que el botón aparece exactamente donde está posicionado el cursor del builder.

---

## Paso 4: Establece la leyenda (texto) del botón

Un botón sin etiqueta es confuso—imagina un botón de ascensor silencioso. El método `setCaption` establece el texto visible:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Puedes cambiar la leyenda a cualquier cosa: “Submit”, “Approve”, o incluso una cadena localizada. La leyenda se almacena en las propiedades del objeto OLE, por lo que Word la renderizará de forma nativa.

---

## Paso 5: Guarda el documento y verifica el resultado

Finalmente, escribe el archivo en disco. Elige una carpeta a la que tengas permiso de escritura; de lo contrario obtendrás una `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Abre `button-demo.docx` en Microsoft Word. Deberías ver un botón etiquetado **Click Me** posicionado en la parte superior del documento. Al hacer clic en él en Word se activará el comportamiento OLE predeterminado (normalmente un mensaje de marcador de posición, a menos que asocies una macro).

---

## Casos límite comunes y cómo manejarlos

| Situación | Por qué ocurre | Solución |
|-----------|----------------|----------|
| **Falta el tipo `Forms2OleControl`** | Las versiones más antiguas de Aspose.Words no exponían este enum. | Actualiza a 23.12+ o posterior. |
| **El botón aparece como una imagen** | La configuración de seguridad de Word bloquea los controles OLE. | Habilita “Trust access to the VBA project object model” en el Centro de confianza, o usa un `.docm` habilitado para macros. |
| **Tamaño incorrecto** | Confusión entre puntos y píxeles. | Recuerda que 1 punto = 1/72 pulgada. Ajusta los números en consecuencia. |
| **Al guardar lanza `FileNotFoundException`** | La ruta no existe. | Asegúrate de que el directorio (`output/`) se cree antes de `doc.save`. Usa `new File("output").mkdirs();`. |

---

## Extender el ejemplo: agregar varios botones u otros controles

Si necesitas más de un botón, simplemente mueve el cursor del builder con `builder.moveTo` o `builder.writeln()` antes de llamar nuevamente a `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

También puedes insertar un **CheckBox**, **ComboBox** o **ListBox** cambiando `Forms2OleControlType.COMMANDBUTTON` por el valor enum apropiado (`CHECKBOX`, `COMBOBOX`, etc.). Los mismos parámetros de ancho/alto se aplican.

---

## Cómo encaja esto en flujos de trabajo de automatización de Word más amplios

- **Generación de plantillas:** Construye una plantilla de contrato que incluya un botón “Approve” para la firma posterior.
- **Informes:** Genera un informe diario con un botón “Refresh Data” que activa una macro.
- **Distribución de formularios:** Envía un cuestionario con controles interactivos pre‑poblados.

Todos estos escenarios se benefician del enfoque de **automatización de Word** que demostramos. Al incrustar controles programáticamente, eliminas la edición manual y reduces errores humanos.

---

## Código fuente completo (listo para copiar y pegar)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Salida esperada:** Cuando abras `output/button-demo.docx` en Microsoft Word, verás dos botones—“Click Me” y “Submit”—apilados verticalmente en la parte superior del archivo.

---

## Conclusión

Hemos respondido **cómo agregar un botón a un documento Word** usando Aspose.Words for Java, paso a paso. Partiendo de un `Document` vacío, utilizamos **DocumentBuilder** para insertar un `Forms2OleControl` de tipo **CommandButton**, establecer una leyenda amigable y guardar el resultado. El enfoque escala a múltiples controles e se integra limpiamente en pipelines más amplios de **automatización de Word**.

¿Listo para el próximo desafío? Prueba cambiar el botón por un **CheckBox**, o enlaza una macro para que reaccione cuando el usuario haga clic en el botón en un archivo `.docm`. El mismo patrón se aplica—solo cambia el enum y ajusta la leyenda.

Si encuentras algún problema, verifica nuevamente la versión de tu biblioteca y los permisos de la carpeta de salida. No dudes en dejar un comentario abajo con preguntas o compartir tu propio caso de uso. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insertar imagen en línea en documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}