---
title: Cambiar las tabulaciones de la tabla de contenidos en un documento de Word
linktitle: Cambiar las tabulaciones de la tabla de contenidos en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a cambiar las tabulaciones de la tabla de contenidos en documentos de Word con Aspose.Words para .NET. Esta guía paso a paso le ayudará a crear una tabla de contenidos de aspecto profesional.
weight: 10
url: /es/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cambiar las tabulaciones de la tabla de contenidos en un documento de Word

## Introducción

¿Alguna vez te preguntaste cómo darle vida a la tabla de contenido (TOC) en tus documentos de Word? Tal vez quieras que las tabulaciones se alineen perfectamente para darle un toque profesional. ¡Estás en el lugar correcto! Hoy profundizaremos en cómo puedes cambiar las tabulaciones de la TOC usando Aspose.Words para .NET. Quédate y te prometo que te irás con todo el conocimiento para que tu TOC luzca elegante y ordenado.

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo lo que necesitas:

1.  Aspose.Words para .NET: puedes[Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Visual Studio o cualquier IDE compatible con C#.
3. Un documento de Word: específicamente, uno que contenga una tabla de contenidos.

¿Entendiste todo eso? ¡Genial! ¡Vamos allá!

## Importar espacios de nombres

Lo primero es lo primero: deberás importar los espacios de nombres necesarios. Esto es como preparar tus herramientas antes de comenzar un proyecto.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dividamos este proceso en pasos sencillos y fáciles de entender. Repasaremos cómo cargar el documento, modificar las tabulaciones de la tabla de contenidos y guardar el documento actualizado.

## Paso 1: Cargue el documento

¿Por qué? Necesitamos acceder al documento de Word que contiene la tabla de contenidos que queremos modificar.

¿Cómo? A continuación, se incluye un fragmento de código sencillo para comenzar:

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Cargue el documento que contiene la tabla de contenidos
Document doc = new Document(dataDir + "Table of contents.docx");
```

Imagina que tu documento es como un pastel y que estamos a punto de agregarle un poco de glaseado. El primer paso es sacar el pastel de la caja.

## Paso 2: Identificar los párrafos de la tabla de contenidos

¿Por qué? Necesitamos identificar los párrafos que componen la tabla de contenidos. 

¿Cómo? Recorrer los párrafos y comprobar sus estilos:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Párrafo de TOC encontrado
    }
}
```

Piense en ello como si estuviera escaneando una multitud para encontrar a sus amigos. Aquí, buscamos párrafos con formato de entradas de índice.

## Paso 3: Modificar las tabulaciones

¿Por qué? Aquí es donde ocurre la magia. Al cambiar las tabulaciones, la tabla de contenidos tiene un aspecto más ordenado.

¿Cómo? Elimine la tabulación existente y agregue una nueva en una posición modificada:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Es como ajustar los muebles de tu sala de estar hasta que quede perfecto. Estamos ajustando esas pestañas para lograr la perfección.

## Paso 4: Guardar el documento modificado

¿Por qué? Para garantizar que todo su arduo trabajo se guarde y pueda verse o compartirse.

¿Cómo? Guarda el documento con un nuevo nombre para mantener intacto el original:

```csharp
// Guardar el documento modificado
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

¡Y listo! Tu índice ahora tiene las tabulaciones exactamente donde las quieres.

## Conclusión

Cambiar las tabulaciones de la tabla de contenidos en un documento de Word con Aspose.Words para .NET es muy sencillo una vez que lo analizas. Al cargar el documento, identificar los párrafos de la tabla de contenidos, modificar las tabulaciones y guardar el documento, puedes lograr un aspecto elegante y profesional. Recuerda que la práctica hace al maestro, así que sigue experimentando con diferentes posiciones de tabulación para obtener el diseño exacto que deseas.

## Preguntas frecuentes

### ¿Puedo modificar las tabulaciones para diferentes niveles de TOC por separado?
Sí, puedes. Solo tienes que comprobar cada nivel de TOC específico (Toc1, Toc2, etc.) y realizar los ajustes correspondientes.

### ¿Qué pasa si mi documento tiene varias tablas de contenidos?
El código escanea todos los párrafos con estilo TOC, por lo que modificará todos los TOC presentes en el documento.

### ¿Es posible agregar varias tabulaciones en una entrada de TOC?
 ¡Por supuesto! Puedes agregar tantas tabulaciones como necesites ajustando el`para.ParagraphFormat.TabStops` recopilación.

### ¿Puedo cambiar la alineación de las tabulaciones y el estilo del líder?
Sí, puedes especificar diferentes alineaciones y estilos de líder al agregar una nueva tabulación.

### ¿Necesito una licencia para usar Aspose.Words para .NET?
 Sí, necesita una licencia válida para usar Aspose.Words para .NET más allá del período de prueba. Puede obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/) o[Compra uno](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
