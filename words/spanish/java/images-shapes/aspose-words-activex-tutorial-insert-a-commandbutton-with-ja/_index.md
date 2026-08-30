---
category: general
date: 2026-08-07
description: El tutorial de Aspose.Words ActiveX muestra cómo agregar un control CommandButton
  a un documento de Word usando Java. Aprende el código completo, la configuración
  y los pasos de guardado.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: es
lastmod: 2026-08-07
og_description: El tutorial de Aspose.Words ActiveX explica cómo incrustar un control
  ActiveX CommandButton en un documento de Word usando Java. Sigue el ejemplo completo
  para crear, configurar y guardar el documento.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutorial de Aspose.Words ActiveX – Guía paso a paso de Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutorial de Aspose.Words ActiveX – insertar un CommandButton con Java
url: /es/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial de Aspose.Words ActiveX – insertar un CommandButton con Java

Si necesita incrustar un control ActiveX en un archivo Word, este **tutorial de Aspose.Words ActiveX** le guía a través de todo el proceso. Verá cómo crear un documento en blanco, insertar un CommandButton, establecer sus propiedades y guardar el resultado, todo con código Java simple.

El ejemplo utiliza la API de Aspose.Words for Java, lo que elimina la necesidad de Microsoft Office en el servidor de compilación. Al final de esta guía podrá generar archivos .docx que contienen controles CommandButton totalmente funcionales, listos para usarse en entornos Windows.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

- Java Development Kit (JDK) 8 o superior instalado.
- Maven u otra herramienta de compilación para gestionar dependencias.
- Una licencia de Aspose.Words for Java (o una clave de evaluación temporal) para evitar marcas de agua de evaluación.
- Familiaridad básica con la sintaxis de Java y la programación orientada a objetos.

> **Consejo profesional:** Añada la dependencia Maven de Aspose.Words a su `pom.xml` para que el IDE resuelva las clases automáticamente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Paso 1: Crear un nuevo documento en blanco y un `DocumentBuilder`

La clase `Document` representa el archivo Word en memoria, mientras que `DocumentBuilder` proporciona una API fluida para editar el documento. Inicializar ambos objetos prepara el documento para modificaciones posteriores.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:**  
`DocumentBuilder` rastrea la posición actual del cursor, de modo que cualquier operación de inserción posterior —como agregar un control— aparece exactamente donde usted lo desea.

## Paso 2: Insertar un control ActiveX CommandButton

Aspose.Words expone `Forms2OleControl` para objetos ActiveX. El método `insertForms2OleControl` requiere el tipo de control, que se especifica mediante la enumeración `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Explicación:**  
El control insertado es un objeto basado en COM que Word renderizará como un botón clicable cuando el documento se abra en un entorno Windows.

## Paso 3: Configurar las propiedades del botón

Después de la inserción, puede ajustar el nombre, la leyenda, el tamaño y la posición del botón. Estas propiedades afectan cómo se ve y se comporta el control dentro de Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Por qué estas configuraciones son importantes:**  

- **Name** – Permite que las macros VBA hagan referencia al control (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Determina la etiqueta visible que los usuarios hacen clic.
- **Left / Top** – Controla la ubicación relativa a los márgenes de la página.
- **Width / Height** – Garantiza un tamaño visual consistente en diferentes resoluciones de pantalla.

## Paso 4: Guardar el documento

Llamar a `save` escribe la representación en memoria en un archivo físico. Puede elegir cualquier formato compatible (`.docx`, `.doc`, `.pdf`, etc.). Para este tutorial mantenemos el formato nativo de Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Resultado:**  
Al abrir `ActiveXDemo.docx` en Microsoft Word se muestra un CommandButton con la etiqueta **Submit** ubicado en las coordenadas especificadas. Al hacer clic en el botón se ejecuta el comportamiento predeterminado (no se adjunta código VBA por defecto).

## Código fuente completo

Uniendo las piezas, el programa completo y ejecutable se ve así:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Resultado esperado

- Un archivo llamado **ActiveXDemo.docx** ubicado en la carpeta `output`.
- Al abrirse en Microsoft Word (Windows), el documento muestra un botón **Submit** clickeable en la posición definida.
- El botón puede seleccionarse, moverse o enlazarse a código VBA mediante la interfaz de Word (Desarrollador → Propiedades).

## Manejo de variaciones comunes

| Escenario | Ajuste |
|----------|------------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word no expone eventos ActiveX a través de Aspose.Words. Debe agregar código VBA manualmente después de que se genere el documento. |
| **Multiple controls** | Repita el bloque de inserción/configuración con diferentes valores de `setName` y `setCaption`. |
| **Different control type (e.g., CheckBox)** | Utilice `Forms2OleControlType.CHECKBOX` en la llamada a `insertForms2OleControl`. |
| **Non‑Windows platforms** | Los controles ActiveX solo se renderizan en Word para Windows. Para soluciones multiplataforma, considere los controles de contenido (`StructuredDocumentTag`). |

## Mejores prácticas y trampas

- **License early** – Registre su licencia de Aspose.Words antes de crear el `Document` para evitar avisos de evaluación.
- **Coordinate system** – Las posiciones se miden en puntos (1 pt = 1/72 in). Convierta de píxeles o centímetros si su diseño UI usa esas unidades.
- **File paths** – Use rutas absolutas o la API `Paths` de Java para evitar `FileNotFoundException` cuando el directorio de salida no exista.
- **Thread safety** – `Document` y `DocumentBuilder` no son seguros para hilos. Cree instancias separadas por hilo si genera documentos en paralelo.
- **Testing** – Verifique el documento generado en la versión objetivo de Word (p. ej., Word 2016, Word 365) porque versiones más antiguas pueden mostrar los controles ActiveX de forma diferente.

## Conclusión

Este **tutorial de Aspose.Words ActiveX** demuestra cómo agregar programáticamente un control CommandButton a un documento Word usando Java. Aprendió a:

1. Inicializar un `Document` y un `DocumentBuilder`.
2. Insertar un `Forms2OleControl` de tipo `COMMAND_BUTTON`.
3. Establecer el nombre, la leyenda, el tamaño y la posición del botón.
4. Guardar el documento como archivo .docx que contiene el control ActiveX.

A partir de aquí puede explorar tipos de control adicionales, automatizar la inyección de macros VBA o combinar controles ActiveX con otras funciones de Aspose.Words, como combinación de correspondencia y controles de contenido. Experimente con diferentes diseños e integre los documentos generados en su canal de generación de informes basado en Java.

---


## ¿Qué debería aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Uso de objetos OLE y controles ActiveX en Aspose.Words para Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convertir Word a RTF con el tutorial de Aspose.Words para Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}