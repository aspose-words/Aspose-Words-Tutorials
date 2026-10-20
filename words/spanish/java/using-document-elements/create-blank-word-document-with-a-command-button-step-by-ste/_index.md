---
category: general
date: 2026-08-04
description: Crear un documento de Word en blanco e insertar un botón de comando usando
  Aspose.Words. Aprende a establecer el tamaño del botón y añadir un botón clicable
  en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: es
lastmod: 2026-08-04
og_description: Crear un documento de Word en blanco con Aspose.Words e insertar un
  botón de comando. Esta guía muestra cómo establecer el tamaño del botón, agregar
  un botón clicable y guardar el archivo.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Crear documento de Word en blanco y añadir un botón de comando – tutorial
  completo de C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crear documento de Word en blanco con un botón de comando – guía paso a paso
url: /es/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco con un botón de comando – guía paso a paso

Si necesitas **crear documento Word en blanco** que contenga un botón interactivo, este tutorial te muestra exactamente cómo hacerlo con Aspose.Words para .NET. Aprenderás a **insertar botón de comando**, ajustar su apariencia y hacerlo clicable, todo en unas pocas líneas de C#.

La guía cubre todo, desde la configuración del proyecto hasta guardar el archivo final, para que puedas copiar‑pegar la solución completa en tu propia aplicación. A lo largo del camino también explicaremos cómo **agregar botón clicable**, **establecer el tamaño del botón** y **crear botón de comando** de forma programática.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado.
* Visual Studio 2022 (o cualquier IDE que soporte .NET).
* Paquete NuGet Aspose.Words for .NET (`Aspose.Words` versión 23.12 o más reciente).
* Familiaridad básica con C# y programación orientada a objetos.

No se requieren ensamblados adicionales de interop de Office porque Aspose.Words funciona de manera completamente independiente de Microsoft Word.

## Paso 1: Configurar el proyecto .NET

Crea una aplicación de consola que alojará el código de automatización de Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Este comando crea una nueva carpeta `WordButtonDemo` con un `Program.cs` listo para ejecutarse y agrega la biblioteca Aspose.Words.

## Paso 2: Crear documento Word en blanco

La primera operación es **crear documento Word en blanco**. Aspose.Words proporciona la clase `Document` que representa un archivo Word vacío listo para usar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Crear un documento en blanco te brinda un lienzo limpio sobre el cual puedes añadir párrafos, tablas o, en este caso, un botón de comando OLE.

## Paso 3: Inicializar DocumentBuilder

`DocumentBuilder` es el asistente que te permite insertar contenido en el documento. Necesitas asociarlo al documento que acabas de crear.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder mantiene la posición actual del cursor, de modo que cualquier inserción posterior ocurre exactamente donde lo deseas.

## Paso 4: Insertar botón de comando

Ahora **insertamos botón de comando** (un OLE `Forms2OleControl`) en el documento. El método `InsertForms2OleControl` requiere tres argumentos:

1. El ProgID del control OLE – `"CommandButton"` para un botón estándar.
2. Un `Rectangle` que define el **establecer tamaño del botón** y la posición.
3. El texto que aparecerá en el botón.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Cuando el documento se abre en Word, el botón se comporta como cualquier control de formulario nativo: puedes hacer clic en él y Word ejecutará la macro asociada (si existe). Esto satisface el requisito de **agregar botón clicable**.

### ¿Por qué usar Forms2OleControl?

`Forms2OleControl` incrusta un objeto OLE directamente en el archivo DOCX, preservando las propiedades del control sin necesidad del ensamblado Interop de Word. Es la forma más fiable de **crear botón de comando** que funciona en distintas versiones de Word.

## Paso 5: Personalizar el botón (opcional)

Quizá quieras **establecer el tamaño del botón** con mayor precisión o cambiar propiedades adicionales como la fuente o el color de fondo. Aspose.Words expone el objeto OLE subyacente, lo que permite ajustes finos.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Si necesitas un tamaño diferente, simplemente ajusta los valores del `Rectangle` en el Paso 4. Las coordenadas se miden en puntos (1 pt = 1/72 pulgada), por lo que `120` corresponde aproximadamente a 1,67 pulgadas de ancho.

## Paso 6: Guardar el documento

Finalmente, escribe el documento en disco. El archivo resultante contiene un **documento Word en blanco** con un botón de comando totalmente funcional.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Al abrir `CommandButtonDemo.docx` en Microsoft Word, verás un botón con la etiqueta “Click Me”. Al hacer clic, se mostrará el cuadro de diálogo de macro predeterminado, a menos que asocies una macro personalizada.

## Código fuente completo

A continuación tienes el programa completo que puedes copiar en `Program.cs`. Incluye todos los pasos descritos arriba y compila sin modificaciones.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Resultado esperado

Ejecutar el programa genera `CommandButtonDemo.docx`. Al abrir el archivo en Word se muestra:

* Una sola página que contiene un botón con la etiqueta **Click Me**.
* El botón respeta el **establecer tamaño del botón** (120 × 30 puntos).
* Al hacer clic, se activa el comportamiento predeterminado del botón de comando de Word, confirmando que la operación **agregar botón clicable** se realizó con éxito.

## Preguntas frecuentes y casos especiales

| Pregunta | Respuesta |
|----------|-----------|
| **¿Esto funciona con archivos .doc?** | Sí. Cambia la extensión del archivo en `doc.Save("file.doc")`. El control OLE también se almacena en el formato binario heredado. |
| **¿Qué pasa si necesito varios botones?** | Llama a `InsertForms2OleControl` repetidamente, ajustando el `Rectangle` para cada nuevo botón y evitando solapamientos. |
| **¿Puedo adjuntar una macro al botón?** | El botón en sí no contiene código de macro. Debes agregar una macro VBA al documento manualmente o mediante la colección `Modules` del objeto `Document`. |
| **¿El botón es visible al exportar a PDF?** | Cuando exportas el DOCX a PDF usando Aspose.Words, el botón se renderiza como una imagen estática, no como un control interactivo. |
| **¿Qué versiones de Word son compatibles?** | El botón de comando OLE funciona en Word 2007 y posteriores, ya que sigue la especificación estándar Forms2.0. |

## Conclusión

Ahora sabes cómo **crear documento Word en blanco**, **insertar botón de comando**, **agregar botón clicable** y **establecer el tamaño del botón** usando Aspose.Words para .NET. El ejemplo completo demuestra el flujo de trabajo **crear botón de comando** de principio a fin, proporcionándote una base sólida para tareas de automatización de Word más avanzadas.

## Próximos pasos

* Explora otros controles OLE (p. ej., `CheckBox`, `ListBox`) cambiando el ProgID en `InsertForms2OleControl`.
* Combina el botón con una macro VBA para ejecutar acciones personalizadas cuando el usuario haga clic.
* Usa `DocumentBuilder` de Aspose.Words para añadir contenido adicional como tablas, imágenes o notas al pie antes de insertar el botón.
* Experimenta con valores de **establecer tamaño del botón** para que coincidan con los requisitos de diseño de tu documento.

¡Feliz codificación y disfruta creando documentos Word más ricos con controles interactivos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear documento Word en blanco con forma rectangular con sombra – guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crear documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}