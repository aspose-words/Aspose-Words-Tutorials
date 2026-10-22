---
category: general
date: 2026-09-30
description: Agrega un control ActiveX a un documento de Word usando C#. Aprende cómo
  insertar un botón ActiveX, añadir un botón de comando y hacerlo clicable.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: es
lastmod: 2026-09-30
og_description: Agrega un control ActiveX a un documento de Word con C#. Sigue esta
  guía completa para insertar un botón ActiveX, añadir un botón de comando y hacerlo
  clicable.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Agregar una palabra de control ActiveX a documentos de Word – guía paso
  a paso en C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Cómo agregar un control ActiveX en Word con C#
url: /es/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar una palabra de control ActiveX en Word con C#

Si necesita incrustar una **palabra de control ActiveX** dentro de un archivo Microsoft Word, esta guía le muestra exactamente cómo hacerlo. Verá un ejemplo completo y ejecutable que inserta un botón clicable, guarda el documento y funciona con la última versión de Aspose.Words para .NET.

Agregar una palabra de control ActiveX le permite crear formularios interactivos, diálogos personalizados o elementos de UI simples que se comportan como controles nativos de Word. Ya sea que esté construyendo una plantilla de contrato que requiera interacción del usuario o un informe que necesite un botón “Ejecutar”, los pasos a continuación cubren todo lo que necesita.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

* .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.8)
* Visual Studio 2022 (o cualquier IDE que admita C#)
* Aspose.Words for .NET instalado (`dotnet add package Aspose.Words`)
* Un conocimiento básico de C# y de la estructura de documentos Word

> **Consejo profesional:** El método `InsertForms2OleControl` funciona solo con los controles heredados “Forms 2.0”, que son los controles ActiveX que Word usa para los campos de formulario. Si apunta a versiones más recientes de Office, el control sigue renderizándose correctamente en el cliente de escritorio.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Cree un nuevo proyecto de consola y agregue las declaraciones `using` requeridas. Esto garantiza que el compilador pueda encontrar las clases `Document`, `DocumentBuilder` y `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

El espacio de nombres `Aspose.Words` proporciona APIs de alto nivel para el procesamiento de Word, mientras que `Aspose.Words.Drawing` contiene la enumeración `OleControlType` necesaria para especificar el tipo de control ActiveX.

## Paso 2: Cargar el documento Word de origen

Debe comenzar con un archivo Word que desee modificar. El siguiente código carga `input.docx` desde la carpeta que indique.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Si el archivo no existe, Aspose.Words lanza una `FileNotFoundException`. Envuelva la llamada en un bloque `try/catch` si necesita un manejo de errores más elegante.

## Paso 3: Crear un DocumentBuilder para editar el documento

`DocumentBuilder` es la herramienta principal para insertar texto, imágenes y controles. Mantiene un cursor que apunta a la ubicación donde se colocará el siguiente elemento.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Por defecto, el cursor del builder está posicionado al inicio de la primera sección. Puede moverlo con métodos como `MoveToDocumentEnd()` o `MoveToParagraph(index)` si desea que el botón aparezca en otro lugar.

## Paso 4: Insertar un control ActiveX CommandButton

Ahora llega el núcleo del tutorial: insertar una **palabra de control ActiveX** que aparece como un botón clicable. El método `InsertForms2OleControl` toma dos argumentos: el tipo de control y una leyenda (o nombre) para el control.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **¿Por qué usar `OleControlType.CommandButton`?**  
  Indica a Word que cree un botón clásico de Forms 2.0, que muestra una leyenda y puede enlazarse a una macro o script VBA posteriormente.

* **¿Qué hace la leyenda?**  
  La cadena `"ClickMe"` se convierte en el texto visible del botón. Puede cambiarla por cualquier texto que se ajuste a su UI.

### Insertar el botón en una ubicación específica

Si necesita el botón después de un párrafo concreto, mueva primero el builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Paso 5: Guardar el documento modificado

Después de insertar el control, persista los cambios en un archivo nuevo (o sobrescriba el original).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Al abrir `output.docx` en la versión de escritorio de Word, verá el botón etiquetado **ClickMe** (o **Submit**, según la leyenda que haya usado). Hacer clic en el botón en modo de diseño no produce ninguna acción por defecto; puede asignar una macro más tarde mediante la pestaña “Developer” de Word.

## Ejemplo completo y ejecutable

A continuación se muestra un programa autocontenido que demuestra todo el flujo de trabajo. Copie el código en `Program.cs` de una nueva aplicación de consola y ejecútelo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Salida esperada

* La consola muestra el mensaje de éxito con la ruta de salida.
* Al abrir `output.docx` se muestra un botón **ClickMe** en la ubicación donde el builder lo insertó.
* El botón puede seleccionarse, redimensionarse o asignarse a una macro mediante **Developer → Design Mode** de Word.

## Preguntas comunes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Cómo insertar un botón ActiveX en el encabezado/pie de página?** | Mueva el builder al encabezado/pie con `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` antes de llamar a `InsertForms2OleControl`. |
| **¿Qué pasa si necesito una casilla de verificación en lugar de un botón?** | Use `OleControlType.CheckBox` y proporcione una leyenda como `"Agree"`. |
| **¿Funcionará el botón en Word Online?** | No. Word Online no admite los controles heredados Forms 2.0 ActiveX. El botón solo se renderiza en el cliente de escritorio. |
| **¿Puedo establecer el tamaño del botón programáticamente?** | Después de la inserción, recupere el objeto `Shape` mediante `builder.CurrentParagraph.Runs[0].GetShape()` y ajuste `Width`/`Height`. |
| **¿Existe una forma de asignar una macro desde código?** | Aspose.Words no expone la edición de macros. Debe abrir el documento en Word y adjuntar una macro manualmente o usar la API Office Interop. |

## Consejos para uso en producción

* **Evite rutas codificadas literalmente** – use `Path.Combine` y archivos de configuración.
* **Libere `Document`** – envuélvalo en una instrucción `using` si trabaja con archivos grandes para liberar memoria rápidamente.
* **Valide la salida** – compruebe programáticamente que el documento contiene una forma del tipo `OleControl` iterando `doc.GetChildNodes(NodeType.Shape, true)`.
* **Nota de seguridad** – los controles ActiveX pueden ejecutar código en la máquina del cliente. Distribuya los documentos solo a usuarios de confianza y considere firmas digitales.

## Conclusión

Ahora sabe cómo agregar una **palabra de control ActiveX** a un documento Word usando C#. Al cargar un documento, crear un `DocumentBuilder`, insertar un botón de comando con `InsertForms2OleControl` y guardar el archivo, puede automatizar la creación de formularios Word interactivos. Experimente con otros valores de `OleControlType`, coloque controles en encabezados o tablas, y combínelos con macros para ofrecer experiencias de usuario más ricas.

---

*Próximos pasos*: explore **cómo insertar controles ActiveX** de otros tipos, aprenda **cómo agregar manejadores de eventos a botones de comando** mediante VBA, y lea sobre las **mejores prácticas para insertar botones ActiveX** en entornos multiplataforma.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Incrustar objetos OLE y controles ActiveX en documentos Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Agregar un campo de formulario Combo Box a un documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Agregar un campo de formulario Check Box a un documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}