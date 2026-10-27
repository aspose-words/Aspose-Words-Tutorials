---
category: general
date: 2026-10-16
description: Crea un documento Word en blanco con Java y aprende cómo agregar un botón
  ActiveX, establecer su texto y ajustar sus dimensiones usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: es
lastmod: 2026-10-16
og_description: Crea un documento Word en blanco con Java, luego agrega un botón ActiveX,
  establece su leyenda y define sus dimensiones usando Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Crear un documento Word en blanco e incrustar un botón ActiveX – Guía Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Crear un documento Word en blanco y agregar un botón ActiveX (Java)
url: /es/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco y agregar un botón ActiveX (Java)

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra cómo hacerlo con Java y Aspose.Words. También aprenderás cómo **agregar un botón ActiveX**, **establecer el texto del botón** y **definir las dimensiones del botón** para que el control se vea exactamente como esperas.

Esta guía cubre:

* Inicializar un archivo Word vacío con Aspose.Words para Java.  
* Insertar un control ActiveX `CommandButton`.  
* Configurar el texto y el tamaño del botón.  
* Guardar el archivo final `.docx`.

Debes tener conocimientos básicos de Java y una versión reciente de la biblioteca Aspose.Words para Java (el código funciona con la versión 23.9 y posteriores). No se requieren dependencias adicionales.

![Crear un documento Word en blanco con un botón ActiveX](/images/activex-button-example.png){: .align-center alt="Crear un documento Word en blanco con un botón ActiveX"}

## Crear un documento Word en blanco con Aspose.Words

El primer paso es instanciar un objeto `Document` vacío. Este objeto representa todo el archivo Word en memoria y proporciona la clase `DocumentBuilder` para la edición.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Por qué es importante:**  
Crear un documento en blanco te brinda un lienzo limpio, evitando estilos o secciones ocultas que puedan interferir con los cálculos de diseño posteriores.

## Agregar un botón ActiveX al documento

Aspose.Words te permite incrustar controles ActiveX heredados mediante la clase `Forms2OleControl`. El siguiente código inserta un control `CommandButton` en la posición actual del cursor.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Consejo:** El valor `setOleClassName` `"Forms.CommandButton.1"` es el ProgID del botón estándar de Microsoft Forms. Usar un ProgID diferente (p. ej., `"Forms.CheckBox.1"`) insertaría un tipo de control distinto.

## Establecer el texto del botón

Una leyenda es el texto que aparece en la cara del botón. Puedes cambiarla en cualquier momento antes de guardar el documento.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Por qué lo necesitas:** Los usuarios solo entienden un control cuando su propósito es claro. Establecer una leyenda significativa mejora la usabilidad, especialmente cuando el documento se abre en Word en Windows.

## Definir las dimensiones del botón

La posición y el tamaño se especifican en puntos (1 punto = 1/72 de pulgada). Ajusta los valores para que se adapten a tu diseño.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Variaciones comunes:**

| Escenario | Ajuste |
|----------|------------|
| Botón más grande para pantallas táctiles | Incrementar `setWidth` y `setHeight` proporcionalmente |
| Botón centrado en la página | Calcular `left = (pageWidth - width) / 2` |
| Múltiples botones en una columna | Incrementar `setTop` para cada nuevo botón |

## Guardar el documento que contiene el botón ActiveX

Finalmente, escribe el documento en disco. El formato `.docx` conserva el control ActiveX para las versiones de Microsoft Word en Windows.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Resultado esperado:** Al abrir `ActiveXCommandButton.docx` en Word (Windows) se muestra una página en blanco con un botón clicable etiquetado **Click Me** ubicado a 100 pt del margen izquierdo y 200 pt del margen superior.

## Ejemplo completo y ejecutable

Copia la clase completa a continuación en tu IDE, agrega el JAR de Aspose.Words para Java al classpath del proyecto y ejecútala.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Al ejecutar el programa se genera `ActiveXCommandButton.docx` en el directorio de trabajo. Ábrelo con Microsoft Word (Windows) para verificar que el botón aparece exactamente como se configuró.

## Por qué se recomienda este enfoque

* **Simplicidad:** Solo se utiliza la API central de Aspose.Words; no se requiere interop COM ni bibliotecas adicionales.  
* **Portabilidad:** El código se ejecuta en cualquier plataforma que soporte Java, aunque el control ActiveX solo funciona en versiones de Word para Windows.  
* **Mantenibilidad:** Todas las propiedades (texto, dimensiones, posición) se establecen mediante métodos claros y auto‑documentados, lo que facilita futuros ajustes.

## Errores comunes y cómo evitarlos

| Problema | Resolución |
|---------|------------|
| El botón no aparece en Word en macOS o Linux | Los controles ActiveX son solo para Windows. Usa un control diferente (p. ej., un control de contenido) para documentos multiplataforma. |
| La leyenda se trunca | Asegúrate de que el ancho del botón sea suficiente para el texto; aumenta `setWidth` o usa una leyenda más corta. |
| El botón se superpone a otro contenido | Ajusta los valores `setTop` y `setLeft`, o inserta un nuevo párrafo antes del control para darle su propio espacio. |

## Próximos pasos

Ahora que puedes **crear un documento Word en blanco**, **agregar un botón ActiveX**, **establecer el texto del botón** y **definir las dimensiones del botón**, podrías explorar:

* Añadir código de manejo de eventos mediante macros VBA (requiere incrustar un módulo de macro).  
* Insertar múltiples controles en un diseño de tabla para documentos tipo formulario.  
* Utilizar las APIs **FormField** de Aspose.Words para soluciones de formularios multiplataforma.

¡Experimenta con diferentes tamaños, posiciones y textos para adaptarlos a tu diseño de documento específico. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear documento Word Java – Agregar forma de rectángulo con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Agregar una marca de agua a un documento usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}