---
category: general
date: 2026-10-23
description: Aprende cómo crear un documento de Word en blanco e insertar un control
  de contenido de texto sin formato (SDT) con un marcador de posición usando C#. Incluye
  código paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert control
- plain text content control
- how to add sdt
- add placeholder to tag
language: es
lastmod: 2026-10-23
og_description: Crea un documento de Word en blanco e inserta un control de contenido
  de texto sin formato (SDT) con un marcador de posición usando C#. Sigue el ejemplo
  completo y ejecutable.
og_image_alt: Screenshot showing a blank Word document with a highlighted plain text
  content control
og_title: Crear un documento Word en blanco y añadir un control de contenido de texto
  sin formato – Guía de C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create a blank Word document and insert a plain text content
    control (SDT) with a placeholder using C#. Includes step‑by‑step code.
  headline: How to create blank Word document with a plain text content control in
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- ContentControl
- WordAutomation
title: Cómo crear un documento Word en blanco con un control de contenido de texto
  plano en C#
url: /es/java/document-manipulation/how-to-create-blank-word-document-with-a-plain-text-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word en blanco con un control de contenido de texto sin formato en C#

Si necesitas **crear un documento Word en blanco** de forma programática, esta guía te muestra exactamente cómo. Usando Aspose.Words para .NET puedes comenzar con un archivo vacío, insertar un StructuredDocumentTag (SDT) de texto sin formato, asignarle un título y agregar un marcador de posición útil, todo en unas pocas líneas de C#.

El tutorial cubre cada paso que necesitarás, desde la inicialización del documento hasta guardar el `.docx` final. Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto .NET.

## Requisitos previos

* .NET 6.0 (o posterior) instalado.
* Una referencia al paquete NuGet **Aspose.Words**.
* Un IDE como Visual Studio 2022 o Visual Studio Code.

No se requieren bibliotecas adicionales.

## Cómo crear un documento Word en blanco y agregar un control de contenido de texto sin formato

La primera tarea importante es crear un **documento Word en blanco**. Esto te brinda un lienzo limpio donde luego podrás **insertar control** elementos.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por qué funciona*: `Document()` crea una representación en memoria de un archivo Word sin páginas. `DocumentBuilder` es la clase auxiliar que te permite agregar párrafos, tablas y controles de contenido.

## Cómo insertar control usando DocumentBuilder

Ahora que el documento existe, puedes **insertar control** objetos directamente donde está posicionado el cursor. Para un control de contenido de texto sin formato, usa `InsertStructuredDocumentTag`.

```csharp
// Step 2: Insert a plain‑text StructuredDocumentTag (SDT) inline
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
```

*Explicación*:  
* `StructuredDocumentTagType.PlainText` indica a Aspose.Words que cree un **control de contenido de texto sin formato**.  
* `MarkupLevel.Inline` coloca el control dentro del párrafo actual, haciéndolo comportarse como texto normal.

## Cómo agregar título y texto de marcador de posición al SDT

Un control con un nombre claro es más fácil de localizar después, especialmente cuando necesitas enlazar datos o realizar validaciones. El paso de **agregar marcador de posición a la etiqueta** también mejora la experiencia del usuario.

```csharp
// Step 3: Give the SDT a meaningful title (used for identification)
sdt.Title = "CustomerName";

// Step 4: Add placeholder text so the user knows what to enter
sdt.AppendChild(new Run(doc, "Enter name here"));
```

*Por qué es importante*:  
* La propiedad `Title` es metadatos que puedes consultar con `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
* El marcador de posición (`Run` con “Enter name here”) aparece en gris en Word, indicando al usuario final que lo reemplace.

## Cómo guardar el documento con el SDT

Finalmente, persiste el archivo en disco. La ruta puede ser absoluta o relativa al directorio de trabajo de tu aplicación.

```csharp
// Step 5: Save the document with the SDT to a file
doc.Save("SDTExample.docx");
```

Cuando abras **SDTExample.docx** en Microsoft Word, verás una única línea que contiene un marcador de posición en gris dentro de un cuadro con borde, exactamente el **control de contenido de texto sin formato** que creaste.

### Resultado esperado

| Ubicación | Indicador visual |
|----------|------------|
| Dentro del primer párrafo | Un cuadro rectangular etiquetado “Enter name here” (marcador de posición) |

Puedes escribir un nombre directamente en el cuadro; Word tratará el texto ingresado como el contenido del SDT.

## Agregar varios controles (opcional)

Si necesitas más de un **control de contenido de texto sin formato**, repite los pasos 2‑4 con una nueva posición de `DocumentBuilder`. Por ejemplo, para agregar un campo de dirección:

```csharp
builder.Writeln(); // Move to a new paragraph
StructuredDocumentTag addressSdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
addressSdt.Title = "CustomerAddress";
addressSdt.AppendChild(new Run(doc, "Enter address here"));
```

*Consejo*: Usa `builder.Writeln()` para iniciar un nuevo párrafo antes de insertar otro SDT, manteniendo el diseño ordenado.

## Errores comunes y cómo evitarlos

| Problema | Causa | Solución |
|-------|-------|-----|
| El texto del marcador de posición desaparece después de guardar | El SDT se creó con `MarkupLevel.Block` en lugar de `Inline` | Usa `MarkupLevel.Inline` para marcadores de posición en línea |
| El título no es buscable | El título nunca se estableció o se estableció después de guardar | Establece `sdt.Title` **antes** de llamar a `doc.Save()` |
| El documento aparece vacío en Word | No se agregó contenido después de crear el documento | Asegúrate de agregar al menos un párrafo o control antes de guardar |

## Consejo profesional: Reutilizar el fragmento en un método de utilidad

Encapsular la lógica la hace reutilizable en varios proyectos:

```csharp
public static Document CreateDocumentWithPlainTextControl(string title, string placeholder)
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);

    StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, MarkupLevel.Inline);
    sdt.Title = title;
    sdt.AppendChild(new Run(doc, placeholder));

    return doc;
}

// Usage
Document myDoc = CreateDocumentWithPlainTextControl("OrderNumber", "Enter order #");
myDoc.Save("OrderForm.docx");
```

*Por qué ayuda*: El método aísla la lógica de **crear un documento Word en blanco**, permitiéndote generar múltiples plantillas con diferentes títulos y marcadores de posición sin duplicar código.

## Próximos pasos

Ahora que sabes **cómo insertar control** y **agregar marcador de posición a la etiqueta**, puedes explorar:

* Enlazar SDTs a partes XML personalizadas (`doc.CustomXmlParts`) – útil para plantillas basadas en datos.
* Convertir el documento a PDF preservando los controles de contenido.
* Usar otros valores de `StructuredDocumentTagType` como `Date`, `ComboBox` o `CheckBox` para formularios más completos.

Cada uno de estos temas se basa en el patrón central demostrado aquí.

---

**Resumen**

Este tutorial te guió a través de la creación de un **documento Word en blanco**, la inserción de un **control de contenido de texto sin formato**, la asignación de un título y la adición de un marcador de posición útil. El ejemplo completo y ejecutable puede copiarse en cualquier proyecto .NET, y el método de utilidad opcional muestra cómo escalar el enfoque. Con esta base estás listo para crear formularios y plantillas sofisticados basados en Word en C#.

---

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear nuevo documento Word e insertar control de contenido en C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Crear documento Word programáticamente – agregar control de contenido y marcador de posición](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Cómo agregar control de contenido y crear documento Word con Aspose – Completo](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}