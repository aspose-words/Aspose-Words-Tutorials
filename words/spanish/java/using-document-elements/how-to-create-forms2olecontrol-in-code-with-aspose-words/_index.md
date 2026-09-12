---
category: general
date: 2026-09-11
description: Aprende cómo crear forms2olecontrol en código usando Aspose.Words DocumentBuilder.
  Esta guía paso a paso cubre la inserción de botones de comando ActiveX, el uso de
  setOleClassName y el dimensionamiento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: es
lastmod: 2026-09-11
og_description: Crea forms2olecontrol en código con Aspose.Words. Sigue esta guía
  para insertar un botón de comando ActiveX, establecer su nombre de clase y ajustar
  su tamaño.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Crear forms2olecontrol en código – guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Cómo crear forms2olecontrol en código con Aspose.Words
url: /es/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear forms2olecontrol en código con Aspose.Words

Si necesita **crear forms2olecontrol en código**, esta guía le muestra exactamente cómo hacerlo usando la API Aspose.Words .NET. Ya sea que esté automatizando una plantilla que requiera un botón de comando ActiveX o simplemente quiera enriquecer un documento Word programáticamente, los pasos a continuación cubren todo, desde insertar el control hasta configurar su apariencia.

En este tutorial aprenderá a usar el **Aspose.Words DocumentBuilder** para insertar un **botón de comando ActiveX**, establecer su clase con el **método setOleClassName**, y ajustar su **tamaño Forms2OleControl**. No se requieren herramientas externas, solo un entorno de desarrollo .NET y la biblioteca Aspose.Words.

## Requisitos previos

Antes de comenzar, asegúrese de tener:

* .NET 6.0 o posterior instalado (el código también funciona con .NET Framework 4.7+)
* Una versión reciente del paquete NuGet Aspose.Words para .NET
* Familiaridad básica con C# y el concepto de controles ActiveX en documentos Word

Si falta alguno de estos, instale el paquete NuGet con:

```bash
dotnet add package Aspose.Words
```

## Qué cubre este tutorial

* Crear una instancia de `DocumentBuilder`
* Insertar un `Forms2OleControl` (el objeto subyacente para un botón de comando ActiveX)
* Asignar el nombre de clase correcto con `setOleClassName`
* Establecer el ancho y alto visual usando las propiedades del **tamaño Forms2OleControl**
* Guardar el documento y verificar el resultado

Al final de la guía tendrá un archivo Word totalmente funcional que contiene un botón clicable que podrá personalizar más o vincular a macros VBA.

---

## Cómo crear forms2olecontrol en código – paso a paso

### Paso 1: Inicializar el DocumentBuilder

La clase `DocumentBuilder` es el punto de entrada para la mayoría de las tareas de generación de documentos en Aspose.Words. Le brinda métodos para agregar texto, imágenes, tablas y, lo que es importante para este tutorial, controles OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por qué es importante:**  
`DocumentBuilder` mantiene la posición actual del cursor dentro del documento. Al crearla temprano, se asegura de que cualquier inserción posterior —como el **botón de comando ActiveX**— aparezca exactamente donde lo desea.

### Paso 2: Insertar el Forms2OleControl

El método `insertForms2OleControl` devuelve un objeto `Forms2OleControl`. Este objeto representa el marcador de posición del control OLE que Word renderizará como un botón ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Por qué es importante:**  
Sin esta llamada no puede manipular las propiedades del control. El `Forms2OleControl` devuelto le brinda acceso completo al **método setOleClassName**, atributos de tamaño y otras configuraciones específicas de OLE.

### Paso 3: Especificar la clase ActiveX con setOleClassName

Word necesita saber qué tipo de control ActiveX renderizar. El nombre de clase para un botón de comando estándar es `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Por qué es importante:**  
El método `setOleClassName` es el puente entre el marcador de posición OLE genérico y el **botón de comando ActiveX** concreto. Usar un nombre de clase incorrecto produce un objeto vacío o un error en tiempo de ejecución al abrir el documento.

### Paso 4: Ajustar el tamaño del Forms2OleControl

Un botón que es demasiado pequeño o demasiado grande se ve poco profesional. Puede controlar sus dimensiones con `setWidth` y `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Por qué es importante:**  
Estas propiedades constituyen el **tamaño Forms2OleControl**. Afectan cómo aparece el botón en la interfaz de Word y garantizan que cualquier macro adjunta tenga suficiente área clicable.

### Paso 5: Guardar el documento y probar

Después de configurar el control, guarde el documento en la ubicación que elija.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Abra `ActiveXButton.docx` en Microsoft Word. Debería ver un botón etiquetado “CommandButton1” (el título predeterminado). Al hacer clic no ocurrirá nada a menos que añada una macro VBA, pero el control en sí es totalmente funcional.

**Resultado esperado:**  

![Documento Word con un botón ActiveX insertado](/images/activeX-button.png "Captura de pantalla de un documento Word que muestra un botón ActiveX recién creado insertado mediante código")

*El texto alternativo de la imagen contiene la palabra clave principal para accesibilidad y SEO.*

---

## Entendiendo la clase ActiveX Forms2OleControl

La clase `Forms2OleControl` envuelve la infraestructura OLE de bajo nivel que Word usa para los elementos ActiveX. Hereda de `Shape`, lo que significa que también puede aplicar formato típico de formas (p. ej., bordes, rotación) si es necesario.

* **Botón de comando ActiveX** – El caso de uso más común; puede vincularlo a una macro mediante las herramientas de desarrollo de Word.
* **Método setOleClassName** – Determina qué clase COM carga Word; otros valores válidos incluyen `"Forms.TextBox.1"` y `"Forms.ComboBox.1"`.
* **Tamaño Forms2OleControl** – Controlado mediante `SetWidth`/`SetHeight`. Estos métodos aceptan puntos (1 pt = 1/72 in).

### Cuándo usar Forms2OleControl vs. Content Controls

Si solo necesita una entrada de datos simple (p. ej., un campo de texto plano), los controles de contenido integrados de Word son más ligeros. Use `Forms2OleControl` cuando requiera la funcionalidad completa de ActiveX, como manejo de eventos o interacción VBA personalizada.

---

## Configuración de propiedades adicionales (opcional)

Aunque los pasos principales son suficientes para **crear forms2olecontrol en código**, a menudo querrá afinar la apariencia o el comportamiento del botón.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Por qué es importante:**  
`SetOleData` le permite escribir valores de propiedades arbitrarios directamente en el flujo OLE. Esta es la forma más flexible de personalizar un **botón de comando ActiveX** sin recurrir a VBA.

---

## Problemas comunes y solución de problemas

| Síntoma | Causa probable | Solución |
|--------|----------------|----------|
| El botón aparece como una caja gris | Nombre de clase incorrecto pasado a `setOleClassName` | Verifique que la cadena sea exactamente `"Forms.CommandButton.1"` (sensible a mayúsculas/minúsculas) |
| El tamaño no cambia | Ancho/Alto establecidos antes de insertar el control | Siempre llame a `SetWidth`/`SetHeight` **después** de `InsertForms2OleControl` |
| El documento lanza “OLE object not found” al abrir | Falta licencia de Aspose.Words (la versión de evaluación puede limitar OLE) | Aplique una licencia válida o use la prueba gratuita con soporte OLE completo |
| La etiqueta del botón permanece “CommandButton1” | `SetOleData` no se usa o la macro no lee la propiedad | Use una macro VBA para leer la propiedad `"Caption"` o establezca la etiqueta mediante la UI de Word |

---

## Ejemplo completo y ejecutable

A continuación se muestra una aplicación de consola completa que puede copiar, pegar y ejecutar. Demuestra todo lo cubierto en este tutorial.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explicación de cada sección**

* **Directivas using** – Importa el espacio de nombres Aspose.Words necesario para `Document`, `DocumentBuilder` y `Forms2OleControl`.
* **Creación del documento** – Instancia un archivo Word vacío.
* **InsertForms2OleControl** – Coloca el control OLE en la posición actual del cursor del builder.
* **SetOleClassName** – Indica a Word que el control es un **botón de comando ActiveX**.
* **SetWidth / SetHeight** – Ajusta el **tamaño Forms2OleControl** para una apariencia profesional.
* **SetOleData (opcional)** – Demuestra cómo escribir propiedades adicionales como una etiqueta.
* **Save** – Escribe el archivo `.docx` final en disco.

Ejecute el programa (`dotnet run`) y abra `ActiveXButton.docx`. Debería ver un botón que luego podrá vincular a una macro.

---

## Conclusión

Ahora sabe cómo **crear forms2olecontrol en código** usando Aspose.Words, desde inicializar el `DocumentBuilder` hasta configurar el **botón de comando ActiveX** con `setOleClassName` y controlar su **tamaño Forms2OleControl**. Este enfoque le permite automatizar documentos Word complejos, incrustar elementos UI interactivos y mantener toda la lógica dentro

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar características adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear forma rectangular en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}