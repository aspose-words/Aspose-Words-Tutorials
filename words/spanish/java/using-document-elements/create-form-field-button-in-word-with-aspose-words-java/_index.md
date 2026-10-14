---
category: general
date: 2026-10-13
description: Cree un botón de campo de formulario en Word usando Aspose.Words para
  Java. Aprenda cómo insertar campos de formulario de botón de comando en Word y establecer
  el texto del botón de comando en unos pocos pasos sencillos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: es
lastmod: 2026-10-13
og_description: Crear botón de campo de formulario en Word con Aspose.Words para Java.
  Este tutorial muestra cómo insertar campos de botón de comando en Word y establecer
  rápidamente el texto del botón de comando.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Crear botón de campo de formulario en Word – Guía de Aspose.Words para Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Crear botón de campo de formulario en Word con Aspose.Words Java
url: /es/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear botón de campo de formulario en Word con Aspose.Words Java

Si necesitas **crear botón de campo de formulario** en un documento Word, esta guía te muestra el proceso completo usando Aspose.Words para Java. Ya sea que estés construyendo una plantilla de formulario rellenable o añadiendo controles interactivos a un informe, aprenderás cómo **insertar campos de formulario command button word** y **establecer el texto del botón command button** con un código mínimo.

El tutorial cubre todo, desde la configuración de Maven hasta un ejemplo completamente ejecutable, para que puedas copiar‑pegar el código, ejecutarlo y ver un archivo `.docx` que contiene un botón clicable listo para personalizar.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java 17 (o superior) instalado y configurado en tu máquina.
- Maven 3.6+ para la gestión de dependencias.
- Un IDE o editor de texto de tu elección (p. ej., IntelliJ IDEA, VS Code).
- Una licencia válida de Aspose.Words para Java (la prueba gratuita funciona para evaluación).

## Paso 1: Añadir Aspose.Words a tu proyecto Maven

Crea un `pom.xml` (o edita el existente) e incluye la dependencia de Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Consejo:** Mantén el número de versión actualizado. Las nuevas versiones añaden soporte para las últimas funciones de Word y mejoran el rendimiento.

## Paso 2: Inicializar un documento vacío y un `DocumentBuilder`

La clase `DocumentBuilder` proporciona una API fluida para editar un documento Word. En este paso creamos un `Document` vacío y le asociamos un builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Crear el documento es la base para **crear objetos de botón de campo de formulario** más adelante en el tutorial.

## Paso 3: Insertar un campo de formulario command button

Aspose.Words expone la clase `Forms2OleControl` para los controles de formulario OLE. Para **insertar campos de formulario command button word**, llama a `insertForms2OleControl` con el valor del enumerado `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

El método devuelve una instancia de `Forms2OleControl` que podemos configurar antes de guardar.

## Paso 4: Definir el tamaño y la posición del botón

Un command button necesita dimensiones y ubicación explícitas en la página. Ajusta el ancho, la altura y las coordenadas según tu diseño.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Afinar estos valores garantiza que el botón aparezca exactamente donde lo deseas en el documento final.

## Paso 5: **Establecer el texto del botón command button**

El texto visible en el botón se controla mediante el método `setCaption`. Aquí es donde **establecemos el texto del botón command button** para guiar al usuario.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Puedes reemplazar `"Click Me"` por cualquier etiqueta que coincida con la intención de tu formulario, como `"Submit"` o `"Approve"`.

## Paso 6: Guardar el documento

Finalmente, escribe el documento en disco. El archivo resultante contiene el botón interactivo y puede abrirse en Microsoft Word o LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Ejecutar el programa genera `CommandButtonDemo.docx`. Al abrirlo en Word verás un botón con la etiqueta **Click Me** posicionado a 50 pts desde la izquierda y 100 pts desde la parte superior de la página.

### Salida esperada

- Un archivo `.docx` llamado `CommandButtonDemo.docx`.
- El documento contiene una sola página con un campo de formulario command button.
- El botón muestra la etiqueta que configuraste (p. ej., **Click Me**).

## Variaciones comunes y casos límite

| Situación | Cómo adaptarlo |
|-----------|----------------|
| **Múltiples botones** | Llama a `insertForms2OleControl` repetidamente, ajustando `setLeft`/`setTop` para cada nuevo botón. |
| **Texto diferente por botón** | Usa `setCaption` con una cadena única después de cada inserción. |
| **Botón dentro de una celda de tabla** | Mueve el cursor a la celda deseada con `builder.moveTo(cell.getFirstParagraph())` antes de insertar el control. |
| **Formatos Word heredados (.doc)** | Guarda usando `doc.save("Demo.doc", SaveFormat.DOC);` – el command button se conserva. |
| **Formularios de solo lectura** | Después de la inserción, establece `commandButton.setEnabled(false);` para impedir la interacción del usuario. |

## Consejos para una implementación robusta

- **Validar dimensiones**: Anchos extremadamente grandes pueden hacer que el botón se desborde del margen de la página.
- **Aplicación de licencia**: Sin una licencia válida, Aspose.Words añade una marca de agua al documento generado. Aplica tu licencia al inicio con `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Pruebas**: Abre el archivo generado en Word y activa **Design Mode** (Desarrollador → Design Mode) para ver las propiedades del botón.

## Resumen del código fuente completo

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Copia el código en un archivo llamado `InsertCommandButtonDemo.java`, compílalo con Maven (`mvn compile`) y ejecútalo (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). El documento generado aparecerá en la carpeta raíz de tu proyecto.

## Conclusión

Ahora sabes cómo **crear botón de campo de formulario** en Word usando Aspose.Words para Java, cómo **insertar campos de formulario command button word** y cómo **establecer el texto del botón command button** de forma programática. Este ejemplo de extremo a extremo te brinda una base sólida para crear documentos Word más ricos e interactivos, ya sea que necesites un solo botón de envío o una suite completa de controles de formulario.

### ¿Qué sigue?

- Explora otros controles de formulario como casillas de verificación (`Forms2OleControlType.CHECKBOX`) y cuadros de texto (`Forms2OleControlType.TEXTBOX`).
- Combina campos de formulario con combinación de correspondencia para generar cuestionarios personalizados.
- Usa la API `FormField` de Aspose.Words para leer los datos introducidos por el usuario después de que el documento se haya completado.

Siéntete libre de experimentar con diferentes tamaños, textos y ubicaciones. Una vez que domines los command buttons, añadir formularios con todas sus funciones a tus pipelines de automatización de Word se vuelve una tarea sencilla. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}