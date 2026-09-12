---
category: general
date: 2026-09-11
description: Aprende a crear un documento de Word en C# y a añadir programáticamente
  un botón de comando usando Aspose.Words en unos simples pasos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: es
lastmod: 2026-09-11
og_description: Crear documento Word en C# y agregar programáticamente un botón de
  comando con Aspose.Words. Sigue esta guía completa para una solución funcional.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Crear documento Word en C# – agregar un botón de comando programáticamente
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Cómo crear un documento Word en C# y agregar programáticamente un botón de
  comando
url: /es/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con C# y agregar programáticamente un botón de comando

Si necesitas **crear un documento Word con C#** e incrustar un botón interactivo, esta guía te muestra exactamente cómo hacerlo. Usando Aspose.Words puedes agregar programáticamente un botón de comando en solo unas pocas líneas de código, eliminando la necesidad de trabajo manual de UI en Word.

En este tutorial aprenderás a:

* Inicializar un archivo Word en blanco con C#.
* Insertar un control **CommandButton** ActiveX.
* Configurar propiedades del botón como nombre y título.
* Guardar el documento para que el botón aparezca al abrir el archivo en Microsoft Word.

No se requieren herramientas externas más allá de la biblioteca Aspose.Words para .NET, y los pasos funcionan con .NET 6+ o .NET Framework 4.6.2 y posteriores.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

| Requisito | Razón |
|------------|--------|
| .NET 6 SDK (o .NET Framework 4.6.2+) | Proporciona el runtime para el proyecto C#. |
| Visual Studio 2022 (o cualquier IDE de C#) | Facilita escribir, compilar y ejecutar el código. |
| Paquete NuGet Aspose.Words para .NET | Suministra las clases `Document`, `DocumentBuilder` y `Forms2OleControl` usadas en el ejemplo. |
| Conocimientos básicos de sintaxis C# | Permite seguir el código sin curvas de aprendizaje adicionales. |

Puedes agregar el paquete Aspose.Words vía la consola de NuGet:

```powershell
Install-Package Aspose.Words
```

## Paso 1: Configurar un nuevo proyecto de consola C#

Crea una aplicación de consola que generará el archivo Word. Abre una terminal y ejecuta:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

El archivo `Program.cs` generado alojará el código que se muestra en los pasos siguientes.

## Paso 2: Crear un documento en blanco y un DocumentBuilder

La primera operación es instanciar un objeto `Document`, que representa un archivo `.docx` vacío, y un `DocumentBuilder` que te permite editar el contenido del documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:**  
`Document` es el contenedor de todos los elementos de Word (párrafos, tablas, controles). `DocumentBuilder` ofrece una API fluida para insertar objetos en la posición actual del cursor sin lidiar con colecciones de nodos de bajo nivel.

## Paso 3: Insertar un control ActiveX CommandButton

Aspose.Words admite la inserción de controles ActiveX heredados mediante el método `InsertForms2OleControl`. El método requiere el tipo de control y el tamaño deseado en puntos.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Qué ocurre bajo el capó:**  
Word trata un control ActiveX como un objeto OLE (Object Linking and Embedding). La clase `Forms2OleControl` envuelve los datos OLE y expone propiedades como `Name` y `Caption`.

## Paso 4: Configurar el nombre y el título del botón

Una vez colocado el control, puedes personalizar sus propiedades en tiempo de ejecución. Asignar un `Name` significativo te ayuda a identificar el botón más tarde, mientras que `Caption` define el texto que se muestra en el botón.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Consejo profesional:**  
Si planeas manejar el evento click del botón con VBA, el `Name` se convierte en el nombre de la macro que referenciarás, por ejemplo, `Sub btnSubmit_Click()`.

## Paso 5: Guardar el documento en disco

Finalmente, escribe el documento a un archivo `.docx`. Elige una carpeta donde tengas permisos de escritura; el ejemplo usa una ruta relativa, que se resuelve al directorio de salida del proyecto.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecutar el programa genera `CommandButton.docx`. Al abrir el archivo en Microsoft Word se muestra un botón **Submit** clicable:

![Documento Word con un botón de comando Submit](/images/command-button.png "Captura de pantalla de un documento Word que contiene un botón de comando Submit creado con C#")

*Texto alternativo de la imagen (og_image_alt):* `Captura de pantalla de un documento Word que contiene un botón de comando Submit creado con C#`

## Verificando el resultado

1. Inicia Word y abre `CommandButton.docx`.  
2. Deberías ver un botón etiquetado **Submit** en el cuerpo del documento.  
3. Al pasar el cursor sobre el botón se revela el nombre `btnSubmit` en el panel **Propiedades** (pestaña Desarrollador → Propiedades).  

Si el botón no aparece, asegúrate de que la pestaña **Desarrollador** esté habilitada en Word (Archivo → Opciones → Personalizar cinta de opciones → marcar *Desarrollador*). Los controles ActiveX se ocultan cuando la pestaña está desactivada.

## Manejo de variaciones comunes y casos límite

| Situación | Ajuste recomendado |
|-----------|--------------------|
| **Tamaño de botón diferente** | Cambia los argumentos de ancho y alto en `InsertForms2OleControl`. Por ejemplo, `150, 40` crea un botón más grande. |
| **Múltiples botones** | Llama a `InsertForms2OleControl` repetidamente, moviendo el cursor del builder entre llamadas (`builder.Writeln();`). |
| **Botón sin ActiveX** | Usa `InsertFormField` para agregar un campo de formulario heredado (p. ej., una casilla de verificación) si necesitas compatibilidad con versiones antiguas de Word que bloquean ActiveX. |
| **Uso multiplataforma** | Los controles ActiveX solo funcionan en versiones de Word para Windows. Para Mac o visores basados en web, considera insertar un hipervínculo con estilo de botón. |
| **Advertencias de seguridad** | Word puede mostrar un aviso de seguridad al abrir un documento que contiene controles ActiveX. Firmar el documento con un certificado de confianza reduce esta fricción. |

## Ejemplo completo y ejecutable

A continuación tienes el programa completo que puedes copiar‑pegar en `Program.cs`. Compila y ejecuta sin modificaciones después de agregar el paquete NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada en la consola:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Abrir el archivo generado muestra el botón **Submit** listo para interactuar.

## Conclusión

Ahora sabes cómo **crear un documento Word con C#** y **agregar programáticamente controles de botón de comando** usando Aspose.Words. El proceso se reduce a inicializar un `Document`, insertar un `Forms2OleControl`, configurar sus propiedades y guardar el archivo. Desde aquí puedes:

* Añadir más controles (p. ej., casillas de verificación, campos de texto) cambiando `ControlType`.  
* Adjuntar macros VBA al botón para lógica personalizada.  
* Combinar esta técnica con otras funcionalidades de Aspose.Words como combinación de correspondencia o rellenado de plantillas.

Experimenta con diferentes tamaños, títulos y múltiples botones para adaptarlos a tu escenario de automatización. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos en tus propios proyectos.

- [Crear documento Word con encabezado y pie de página usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crear documento Word con Aspose.Words para .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Crear forma grupal en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}