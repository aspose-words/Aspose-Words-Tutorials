---
category: general
date: 2026-09-24
description: Establecer la posición del botón en un documento Word usando Java y Aspose.Words.
  Aprende cómo insertar un botón, agregar un control ActiveX y crear un documento
  Word al estilo Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: es
lastmod: 2026-09-24
og_description: Establecer la posición del botón en un documento Word usando Java.
  Esta guía muestra cómo insertar un botón, agregar un control ActiveX y crear un
  documento Word con Java usando Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Establecer la posición del botón en un documento Word con Java – guía completa
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Cómo establecer la posición del botón en un documento de Word con Java
url: /es/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer la posición del botón en un documento Word con Java

Si necesita **establecer la posición del botón** dentro de un archivo Word, esta guía le muestra una solución completa y ejecutable. Ya sea que esté creando una plantilla que requiera interacción del usuario o automatizando un formulario, aprenderá exactamente **cómo insertar un botón** usando Aspose.Words for Java y controlar su ubicación.

El tutorial cubre todo lo que necesita para **agregar control ActiveX** a un documento Word, explica cómo **agregar botón a Word**, y demuestra el proceso completo para **crear documento Word Java**. No se requieren referencias externas; simplemente copie, ejecute y verifique el resultado.

## Requisitos previos

* Java 17 (o cualquier tiempo de ejecución Java 8+ ) instalado.
* Maven o Gradle para gestionar dependencias.
* Una licencia de Aspose.Words for Java (la prueba gratuita funciona para evaluación).
* Un conocimiento básico de la sintaxis de Java.

> **Consejo:** Mantenga sus JARs de Aspose.Words en una carpeta `libs/` y añádalos al classpath de su proyecto para evitar conflictos de versiones.

## Paso 1: Configurar el proyecto Maven

Create a simple Maven project (or use Gradle) and add the Aspose.Words dependency:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Ejecutar `mvn clean compile` descarga la biblioteca y prepara la ruta de compilación.

## Paso 2: Crear un nuevo documento Word

La primera operación es **crear documento Word java**. Instancia un objeto `Document` y un `DocumentBuilder` que le permite editar el archivo.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

La clase `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` ofrece una API fluida para insertar contenido.

## Paso 3: Cómo insertar un botón – agregar control ActiveX

Aspose.Words expone la clase `Forms2OleControl` para insertar controles ActiveX heredados como un CommandButton. Este paso muestra la forma exacta de **cómo insertar un botón** en el documento.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

El método `insertForms2OleControl` devuelve una instancia de `Forms2OleControl` que puede configurar. Este es el núcleo del proceso de **agregar control ActiveX**.

## Paso 4: Establecer la posición del botón

Ahora realmente **establecemos la posición del botón**. Los métodos `setLeft` y `setTop` del control aceptan valores en puntos (1 pt = 1/72 in). Para alinear el botón con coordenadas de pantalla típicas, puede convertir píxeles a puntos (1 px ≈ 0.75 pt). En el ejemplo colocamos el botón a 100 px del borde izquierdo y 150 px del borde superior.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Dado que la lógica de **establecer la posición del botón** está encapsulada aquí, puede reutilizar estas líneas siempre que necesite mover un control. Ajuste los números para que se adapten a los requisitos de su diseño.

## Paso 5: Definir tamaño y título

Un botón sin etiqueta es confuso. Use `setWidth`, `setHeight` y `setCaption` para darle una apariencia visible.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

El tamaño también se expresa en puntos, por lo que convertimos desde píxeles para mantener la consistencia.

## Paso 6: Guardar el documento – completar el flujo de crear documento Word java

Finalmente, persista el archivo en disco. La ruta puede ser absoluta o relativa a la raíz del proyecto.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Ejecutar el programa produce `CommandButtonDemo.docx` dentro de la carpeta `output`. Abrir el archivo en Microsoft Word muestra un botón clicable posicionado exactamente donde lo estableció.

### Resultado esperado

* Un archivo `.docx` llamado **CommandButtonDemo.docx**.
* Dentro del documento, un **CommandButton** etiquetado “Click Me” aparece a 100 px del margen izquierdo y 150 px del margen superior.
* El botón responde a los clics cuando el documento se abre en Word (mostrará un mensaje ActiveX predeterminado a menos que adjunte código VBA personalizado).

## Paso 7: Variaciones comunes y casos límite

### Agregar varios botones

Si necesita **agregar botón a Word** más de una vez, repita los pasos 3‑5 con una nueva instancia de `Forms2OleControl` cada vez. Recuerde ajustar el valor de `setTop` para que los botones no se superpongan.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Trabajar sin licencia

Aspose.Words agrega una marca de agua cuando se usa sin licencia. Para código de producción, compre una licencia y aplíquela al inicio de `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibilidad con versiones antiguas de Office

Los controles ActiveX son compatibles con el formato `.doc` (Word 97‑2003). Para crear un archivo heredado, cambie el formato de guardado:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Código fuente completo (ejecutable)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Guarde el archivo como `src/main/java/CommandButtonDemo.java`, ejecute `mvn exec:java -Dexec.mainClass=CommandButtonDemo` y abra el documento generado para ver el resultado.

## Preguntas frecuentes

**P: ¿Esto funciona con OpenJDK?**  
R: Sí. Aspose.Words es puro Java y se ejecuta en cualquier implementación JDK 8+, incluido OpenJDK.

**P: ¿Puedo cambiar la fuente o el color del botón?**  
R: La apariencia del botón ActiveX está controlada por la aplicación anfitriona (Word). Puede adjuntar código VBA para modificar propiedades en tiempo de ejecución, pero la apariencia estática está limitada al estilo predeterminado.

**P: ¿Qué pasa si necesito colocar el botón dentro de una celda de tabla?**  
R: Mueva el cursor de `DocumentBuilder` a la celda antes de llamar a `insertForms2OleControl`. El control heredará el diseño de la celda, y aún podrá usar `setLeft`/`setTop` para ajustes finos.

## Conclusión

Ahora sabe cómo **establecer la posición del botón** en un documento Word usando Java, cómo **insertar un botón**, cómo **agregar control ActiveX**, y cómo **agregar botón a Word** siguiendo las mejores prácticas para proyectos **crear documento Word java**. El ejemplo completo muestra todo el flujo de trabajo, desde la configuración del proyecto hasta un archivo `.docx` guardado que contiene un CommandButton funcional.

### Próximos pasos

* Explore otros valores de `Forms2OleControl.ControlType` (p. ej., `CHECKBOX`, `TEXTBOX`) para crear formularios más complejos.
* Combine el botón con macros VBA para manejar clics personalizados.
* Use la función de combinación de correspondencia de Aspose.Words para generar documentos personalizados que ya contengan controles interactivos.

¡Feliz codificación y disfrute automatizando documentos Word con Java!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Agregar un campo de formulario Combo Box a un documento Word con Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Cómo cargar documentos Word con Aspose.Words Java: Guía completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}