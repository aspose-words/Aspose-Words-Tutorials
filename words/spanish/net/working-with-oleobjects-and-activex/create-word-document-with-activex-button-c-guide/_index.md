---
category: general
date: 2026-07-19
description: Crear documento de Word usando Aspose.Words C# y aprender cómo agregar
  un botón de comando ActiveX, establecer el tamaño del botón e insertar el botón
  programáticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: es
lastmod: 2026-07-19
og_description: Crea un documento Word con Aspose.Words C# e incrusta un botón de
  comando ActiveX en segundos. Sigue la guía paso a paso para establecer el tamaño
  del botón e insertarlo fácilmente.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Crear documento de Word con botón ActiveX – Tutorial de C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Crear documento de Word con botón ActiveX – Guía de C#
url: /es/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con botón ActiveX – Guía completa en C#

¿Alguna vez te has preguntado cómo **crear documento Word** que contenga un botón ActiveX funcional? Tal vez estés automatizando un informe y necesites un control “Aprobar” clicable dentro del archivo. En este tutorial recorreremos exactamente eso—usando Aspose.Words para .NET para añadir un botón de comando ActiveX, establecer su tamaño e insertarlo donde lo necesites.  

Si alguna vez te has preguntado *cómo añadir activex* sin abrir Word manualmente, estás en el lugar correcto. Al final tendrás un ejemplo ejecutable, una explicación clara de cada paso y consejos para manejar problemas comunes.

## Lo que aprenderás

- Cómo configurar Aspose.Words en un proyecto C#  
- El código exacto para **crear documento Word** e incrustar un botón de comando ActiveX  
- Formas de **establecer tamaño del botón** y personalizar su texto y nombre  
- El método correcto para **insertar botón de comando** y **cómo insertar botón** en cualquier ubicación del documento  
- Consideraciones de casos límite (versión de Word, limitaciones de plataforma, advertencias de seguridad)

### Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7+).  
- Una licencia válida de Aspose.Words para .NET (o una clave de evaluación gratuita).  
- Visual Studio 2022 (o cualquier IDE que prefieras).  
- Familiaridad básica con C# y programación orientada a objetos.

No se requieren otras bibliotecas de terceros.

---

## Paso 1: Crear documento Word – Configuración del proyecto

Antes de poder **insertar botón de comando**, necesitamos un archivo Word en blanco con el que trabajar. Este paso también muestra el patrón clásico de “**crear documento Word**” usando Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por qué es importante:** `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` rastrea la posición actual del cursor. Todas las inserciones posteriores (incluido nuestro control ActiveX) se realizan en relación con este builder.

---

## Paso 2: Cómo añadir ActiveX – Construir el control CommandButton

Ahora que el documento existe, abordemos la parte de **cómo añadir activex**. Aspose.Words expone la clase `Forms2OleControl` para objetos ActiveX. Aquí crearemos un botón de comando y configuraremos sus propiedades, incluido el requisito de **establecer tamaño del botón**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Consejo profesional:** El tamaño se mide en puntos (1 punto = 1/72 de pulgada). Ajusta los valores para que encajen en tu diseño; para un botón típico de barra de herramientas, 120 × 30 funciona bien.

---

## Paso 3: Insertar botón de comando – El núcleo de **Insertar botón de comando**

Con el control listo, ahora **insertamos botón de comando** en el documento en la ubicación actual del builder. Puedes mover el builder a cualquier parte (p. ej., después de un párrafo) antes de llamar a este método.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Si necesitas **cómo insertar botón** en un marcador específico, simplemente mueve el builder primero:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **¿Qué ocurre tras bambalinas?** Aspose.Words escribe los flujos de objetos OLE necesarios dentro del paquete .docx, de modo que Word pueda renderizar el botón sin macros adicionales.

---

## Paso 4: Guardar el documento – Finalizando el ciclo de **Crear documento Word**

El paso final es sencillo: persistir el archivo en disco. Esto completa el ciclo de **crear documento Word**, incrustar el ActiveX y guardar.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Abre el archivo resultante en Microsoft Word (solo Windows). Deberías ver un botón clicable con la etiqueta “Click Me”. Al pulsarlo se activará la Acción predeterminada de un CommandButton—no ocurre nada a menos que adjuntes código VBA, pero el control es totalmente funcional.

> **Salida esperada:** Un archivo .docx con una sola página, un botón centrado en el punto de inserción, de tamaño 120 × 30 pt, con el texto “Click Me”.  
> ![Botón ActiveX insertado en un documento Word](placeholder-image.png)  
> *Texto alternativo de la imagen:* **Botón ActiveX insertado en un documento Word usando C#** (coincide con `og_image_alt`).

---

## Paso 5: Casos límite, seguridad y buenas prácticas

### Limitaciones de plataforma
- Los controles ActiveX solo se ejecutan en la versión de Windows de Word. Si tu audiencia incluye usuarios de macOS o Word Online, el botón aparecerá como una imagen estática.
- Algunos entornos corporativos deshabilitan ActiveX por seguridad; puede que necesites firmar el documento o indicar a los usuarios que habiliten el contenido.

### Interacción con VBA (opcional)
Si deseas que el botón ejecute una macro, tendrás que añadir un proyecto VBA al documento después de guardarlo. Aspose.Words no genera código VBA automáticamente, pero puedes usar la API `Document.VbaProject` para inyectarlo.

### Colisiones de nombres
Siempre asigna a cada control un `Name` único. Reutilizar el mismo nombre puede causar errores en tiempo de ejecución cuando Word intente resolver el control.

### Consejo de rendimiento
Al insertar muchos controles, reutiliza una única instancia de `DocumentBuilder` y evita llamar a `doc.Save` dentro de un bucle. Agrupa las inserciones y guarda una sola vez al final.

---

## Ejemplo completo y funcional

Juntando todo, aquí tienes un programa listo para copiar y pegar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Ejecuta el programa, abre el archivo guardado y verás el botón exactamente donde estaba posicionado el builder.

---

## Conclusión

Acabamos de **crear documento Word** desde cero, aprendimos **cómo añadir activex** configurando un `Forms2OleControl`, dominamos las propiedades de **establecer tamaño del botón**, y demostramos la forma correcta de **insertar botón de comando** y **cómo insertar botón** en cualquier punto del archivo.  

Con una sola muestra de código ahora tienes una base sólida para una automatización de Word más rica—ya sea que estés construyendo plantillas con formularios interactivos, generando contratos que requieran la aceptación del usuario, o simplemente añadiendo algunos controles útiles a un informe.

### ¿Qué sigue?

- **Estilizar el botón** – cambiar fuentes, colores o añadir una imagen de fondo.  
- **Adjuntar macros VBA** – hacer que el botón realice cálculos o lance programas externos.  
- **Combinar con otros controles** – casillas de verificación, listas desplegables o incluso hojas de cálculo Excel incrustadas.  

Siéntete libre de experimentar, y si encuentras algún obstáculo, deja un comentario abajo. ¡Feliz codificación y disfruta automatizando Word con Aspose.Words!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}