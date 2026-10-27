---
category: general
date: 2026-10-23
description: Crea un documento Word en blanco con C# y aprende cómo insertar controles
  ActiveX, incluido un botón, usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: es
lastmod: 2026-10-23
og_description: Crea un documento Word en blanco con C# y aprende cómo insertar controles
  ActiveX, incluido un botón, usando Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Crear un documento Word en blanco y agregar un botón ActiveX en C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Crear un documento de Word en blanco y agregar un botón ActiveX en C#
url: /es/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear un documento Word en blanco y agregar un botón ActiveX en C#

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra exactamente cómo. Verás un ejemplo completo y ejecutable que crea un nuevo documento, inserta un CommandButton ActiveX y guarda el archivo, todo con Aspose.Words para .NET.

Trabajar con archivos Word a menudo requiere más que texto plano. Agregar un **botón ActiveX** te permite incrustar funcionalidad interactiva que puede usarse en plantillas con macros o soluciones solo para Windows. Al final de este tutorial podrás insertar cualquier control ActiveX, pero nos enfocaremos en el escenario más común: un **botón activex en documento Word** que envía un formulario.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.7+)
* Visual Studio 2022 (o cualquier IDE de C#)
* **Aspose.Words for .NET** paquete NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Familiaridad básica con la sintaxis de C#

> **Consejo profesional:** Aspose.Words es una biblioteca comercial, pero ofrece una licencia temporal gratuita para pruebas. Instala la licencia temprano para evitar la marca de agua de evaluación.

## Paso 1: Crear un documento Word en blanco con Aspose.Words

El primer paso es instanciar un objeto `Document`. Esto representa un archivo `.docx` vacío en memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` comienza sin secciones, páginas ni contenido. Es la hoja en blanco que necesitas para escenarios de **crear documento Word en blanco**, como generar informes desde cero.

## Paso 2: Obtener un DocumentBuilder para editar el documento

`DocumentBuilder` proporciona una API conveniente para agregar texto, imágenes y controles. Lo usaremos para posicionar el control ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

El builder agrega automáticamente una sección predeterminada y una primera página, por lo que puedes comenzar a insertar objetos de inmediato.

## Paso 3: Cómo insertar controles ActiveX en el documento

Aspose.Words expone `InsertForms2OleControl` para incrustar objetos OLE/ActiveX. El método requiere el tipo de control, ancho y alto (en puntos). A continuación insertamos un **CommandButton**, el botón de formulario clásico que ves en plantillas Word heredadas.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Por qué funciona:** `Forms2OleControlType.COMMANDBUTTON` indica a Word que cree un botón que pueda responder a eventos de clic cuando el documento se abre en un entorno Windows que soporta ActiveX.

## Paso 4: Crear un control ActiveX – establecer sus propiedades

Ahora le damos al botón un nombre programático y una leyenda visible. Esta es la parte de **crear control activex** que los desarrolladores a menudo pasan por alto.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` es el identificador que referenciarás desde macros VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` es la etiqueta que se muestra en el propio botón.

## Paso 5: Guardar el documento Word con el botón ActiveX

Finalmente, escribe el documento en disco. La extensión del archivo debe ser `.docx` (o `.docm` si planeas agregar macros más adelante). El ejemplo guarda en una carpeta de marcador de posición; reemplázala con tu propia ruta.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Cuando abras el archivo resultante en Microsoft Word (solo Windows), verás un **botón activex en documento Word** funcional que puede conectarse a código VBA.

## Ejemplo completo funcional

A continuación se muestra el programa completo que puedes copiar y pegar en un nuevo proyecto de consola.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Salida esperada al ejecutar el programa**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Abre el `ActiveXButton.docx` generado en Word, y verás un botón con la etiqueta **Submit** ubicado en la parte superior de la primera página.

## Casos límite y errores comunes

| Situación | Qué observar | Recomendación |
|-----------|--------------|---------------|
| Ejecutándose en macOS o Linux | ActiveX es una tecnología solo para Windows, por lo que el botón aparecerá como un marcador de posición. | Usa el tutorial solo para plantillas dirigidas a Windows. |
| Documento abierto en Word Online | Los controles ActiveX no son compatibles en la vista del navegador. | Proporciona una interfaz alternativa o indica a los usuarios que abran el archivo en el cliente de escritorio. |
| Necesitas un archivo con macros | Los archivos `.docx` no pueden almacenar código VBA. | Guarda como `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) y agrega la macro por separado. |
| Desajuste del tamaño del control | Los valores de ancho/alto están en puntos (1 pt ≈ 1/72 in). | Ajusta los valores numéricos para lograr el tamaño visual que deseas. |

## Preguntas frecuentes

**¿Cómo insertar controles ActiveX que no sean un botón?**  
Utiliza el mismo método `InsertForms2OleControl` pero pasa un valor diferente del enum `Forms2OleControlType`, como `COMBOBOX` o `LISTBOX`.

**¿Puedo cambiar la fuente o el color del botón?**  
La apariencia del botón ActiveX está gobernada por la aplicación anfitriona (Word) y el tema de Windows subyacente. Puedes modificar propiedades como `ForeColor` y `BackColor` mediante VBA después de abrir el documento.

**¿Existe una forma de agregar un manejador de clic directamente desde C#?**  
No. El evento de clic debe ser manejado por VBA o un complemento de Word porque el botón se ejecuta dentro del proceso de Word, no de tu aplicación .NET.

## Conclusión

Ahora sabes cómo **crear un documento Word en blanco** programáticamente e incrustar un **botón ActiveX** usando Aspose.Words para .NET. Los pasos cubiertos:

1. Instanciar un `Document`.
2. Usar `DocumentBuilder` para trabajar con el archivo.
3. Llamar a `InsertForms2OleControl` para **cómo insertar controles activex**.
4. Configurar las propiedades del control (**crear control activex**).
5. Guardar el archivo, obteniendo un **botón activex en documento Word** listo para la integración con VBA.

Desde aquí puedes explorar agregar otros tipos de controles, conectar macros VBA, o convertir el documento a PDF mientras preservas el botón (como una imagen estática). Experimenta con diferentes tamaños, leyendas y nombres.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo agregar un botón ActiveX en un documento Word con Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Crear documento Word con botón ActiveX – Guía C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}