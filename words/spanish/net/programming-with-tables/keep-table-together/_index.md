---
title: Mantenga la mesa unida
linktitle: Mantenga la mesa unida
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a evitar que las tablas se dividan en varias páginas en documentos de Word con Aspose.Words para .NET. Siga nuestra guía para mantener documentos legibles y profesionales.
weight: 10
url: /es/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantenga la mesa unida

## Introducción

¿Alguna vez te has sentido frustrado cuando una tabla de tu documento de Word se divide en dos páginas? ¡Es como si la información que habías organizado cuidadosamente de repente decidiera tomarse un descanso a mitad de camino! Mantener las tablas juntas en una página es crucial para la legibilidad y la presentación. Ya sea para un informe, una propuesta de proyecto o simplemente un documento personal, tener las tablas divididas puede ser bastante molesto. Por suerte para nosotros, Aspose.Words para .NET tiene una forma ingeniosa de resolver este problema. En este tutorial, repasaremos los pasos para mantener tus tablas intactas y con un aspecto impecable. ¡Vamos a profundizar!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: si aún no lo ha instalado, puede descargarlo desde[aquí](https://releases.aspose.com/words/net/).
2. Un documento de Word con una tabla: trabajaremos con un documento de muestra que tiene una tabla que abarca varias páginas.
3. Conocimientos básicos de C#: este tutorial asume que tienes un conocimiento básico de programación en C#.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto nos dará acceso a las clases y métodos que necesitamos de Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Dividamos el proceso en pasos sencillos y fáciles de entender. Comenzaremos cargando nuestro documento y terminaremos guardando el documento actualizado donde la tabla permanece unida.

## Paso 1: Cargue el documento

 Para trabajar con un documento de Word, primero debemos cargarlo. Usaremos el`Document` clase para esto.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Paso 2: Acceda a la tabla

A continuación, debemos obtener la tabla que queremos mantener unida. Supondremos que es la primera tabla del documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Paso 3: Establezca KeepWithNext para los párrafos

 Para evitar que la tabla se divida en varias páginas, debemos configurar el`KeepWithNext` propiedad para cada párrafo de la tabla, excepto los últimos párrafos de la última fila.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Paso 4: Guardar el documento

Por último, guardamos el documento actualizado. Esto aplicará los cambios y garantizará que la tabla permanezca unida en una sola página.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusión

¡Y ya está! Con solo unas pocas líneas de código, puede evitar que las tablas se dividan en las distintas páginas de sus documentos de Word. Esta solución simple pero efectiva garantiza que sus tablas permanezcan ordenadas y profesionales, mejorando la legibilidad de sus documentos. Aspose.Words para .NET facilita la gestión de estos problemas de formato, lo que le permite centrarse en crear contenido excelente.

## Preguntas frecuentes

### ¿Puedo mantener varias tablas juntas usando este método?  
Sí, puedes aplicar la misma lógica a varias tablas iterando a través de cada tabla en tu documento.

### ¿Qué pasa si mi tabla es demasiado grande para caber en una página?  
Si una tabla es demasiado grande para caber en una sola página, se extenderá de todas formas a varias páginas. Este método garantiza que las tablas más pequeñas permanezcan intactas sin dividirse.

### ¿Hay alguna manera de automatizar esto para todas las tablas de un documento?  
 Sí, puede recorrer todas las tablas de su documento y aplicar las`KeepWithNext` propiedad a cada párrafo.

### ¿Necesito una licencia paga para Aspose.Words para .NET?  
Puedes comenzar con una prueba gratuita desde[aquí](https://releases.aspose.com/), pero para una funcionalidad completa, se recomienda una licencia paga.

### ¿Puedo aplicar otro formato a la tabla y mantenerla unida?  
¡Por supuesto! Puedes formatear tu tabla como necesites y asegurarte de que se mantenga unida en una sola página.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
