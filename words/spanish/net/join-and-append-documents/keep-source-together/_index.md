---
title: Mantenga la mesa unida
linktitle: Mantenga la mesa unida
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a evitar que las tablas se dividan en varias páginas usando Aspose.Words para .NET con esta guía paso a paso. Asegúrese de que los documentos de Word tengan un aspecto ordenado y profesional
weight: 10
url: /es/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantenga la mesa unida

## Introducción

Las tablas son una parte esencial de muchos documentos de Word, pero a veces puede suceder que la tabla se divida en dos páginas. Esto puede interrumpir el flujo del documento y afectar su legibilidad. ¿No sería genial si hubiera una manera de mantener toda la tabla junta en una página? Bueno, con Aspose.Words para .NET, ¡hay una solución fácil para este problema! En este tutorial, veremos cómo evitar que las tablas se dividan en varias páginas, lo que garantizará que el documento tenga un aspecto ordenado y profesional.

## Prerrequisitos

Antes de comenzar con el tutorial, asegurémonos de que tienes todo lo que necesitas para seguirlo sin problemas.

### Biblioteca Aspose.Words para .NET

En primer lugar, deberá tener instalado Aspose.Words para .NET. Se trata de una potente biblioteca que le permite trabajar con documentos de Word de forma programada.

- [Descargar Aspose.Words para .NET](https://releases.aspose.com/words/net/)

### Entorno de desarrollo

Debe tener un entorno de desarrollo configurado para ejecutar código C#, como:

- Visual Studio (cualquier versión reciente)
- .NET Framework 2.0 o posterior

### Un documento de Word con una tabla

 Necesitará un documento de Word que contenga una tabla. En este tutorial, trabajaremos con un documento de muestra llamado`"Table spanning two pages.docx"`Este archivo contiene una tabla que actualmente ocupa dos páginas.

### Licencia temporal (opcional)

 Si bien Aspose.Words viene con una prueba gratuita, es posible que desees utilizar una[licencia temporal](https://purchase.aspose.com/temporary-license/) para liberar todo el potencial de la biblioteca.

## Importar paquetes

Antes de escribir cualquier código, debemos importar los espacios de nombres necesarios para trabajar con Aspose.Words para .NET. Agregue las siguientes importaciones en la parte superior de su archivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Estos espacios de nombres le dan acceso a clases como`Document`, `Table`, `Cell`, y otros que usaremos en este tutorial.

## Paso 1: Cargue el documento

 Lo primero que debemos hacer es cargar el documento de Word que contiene la tabla. Para ello, utilizaremos el`Document` Clase de Aspose.Words. Esta clase le permite abrir y manipular archivos de Word mediante programación.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 En este fragmento de código, especificamos la ubicación de nuestro documento. Reemplazar`"YOUR DOCUMENTS DIRECTORY"` con el directorio real donde se almacena su documento.

## Paso 2: Acceda a la tabla

Una vez cargado el documento, el siguiente paso es acceder a la tabla que queremos mantener unida. En este ejemplo, asumimos que la tabla es la primera tabla del documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Esta línea de código busca la primera tabla del documento.`GetChild` El método recupera un tipo específico de nodo, que en este caso es`NodeType.Table` . El`0` indica que queremos la primera tabla y la`true`La bandera asegura que busquemos recursivamente a través de todos los nodos secundarios.

## Paso 3: Recorrer las celdas de la tabla

Ahora, debemos recorrer cada celda de la tabla. Como una tabla contiene varias filas y cada fila contiene varias celdas, iteraremos por cada celda y nos aseguraremos de que no se interrumpa en varias páginas.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Aquí,`GetChildNodes` recupera todas las celdas de la tabla y recorremos cada una de ellas.`EnsureMinimum()` El método asegura que cada celda contenga al menos un párrafo, ya que una celda vacía podría causar problemas más adelante.

## Paso 4: Establezca la propiedad KeepWithNext

 Para evitar que la tabla se divida en varias páginas, debemos configurar el`KeepWithNext` Propiedad para cada párrafo de la tabla. Esta propiedad garantiza que el párrafo permanezca junto al párrafo siguiente, lo que evita de manera efectiva los saltos de página entre ellos.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Este bucle comprueba cada párrafo dentro de cada celda. La condición garantiza que no apliquemos la`KeepWithNext`propiedad al último párrafo de la última fila. De lo contrario, la propiedad no tendría efecto ya que no hay un párrafo siguiente.

## Paso 5: Guardar el documento

 Finalmente, después de aplicar el`KeepWithNext` propiedad, necesitamos guardar el documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Esta línea guarda el documento actualizado con un nuevo nombre, conservando el archivo original. Ahora puede abrir el archivo resultante y ver que la tabla ya no está dividida en dos páginas.

## Conclusión

¡Y ya está! Si sigue estos sencillos pasos, podrá evitar fácilmente que las tablas se dividan en varias páginas de documentos de Word con Aspose.Words para .NET. Tanto si trabaja en informes, contratos u otros documentos, mantener las tablas intactas garantiza un aspecto más pulido y profesional.

La belleza de Aspose.Words es su flexibilidad y facilidad de uso, que le permiten manipular documentos de Word de forma programada sin necesidad de tener Microsoft Word instalado en su equipo. Ahora que ya sabe cómo mantener juntas las tablas, ¡explore otras funciones de la biblioteca para llevar sus habilidades de procesamiento de documentos al siguiente nivel!

## Preguntas frecuentes

### ¿Por qué mi tabla sigue dividiéndose en varias páginas después de usar este código?

 Si su mesa aún se rompe, asegúrese de haber aplicado el`KeepWithNext` propiedad correctamente. Verifique nuevamente que todos los párrafos, excepto el último de cada celda, tengan esta propiedad configurada.

### ¿Puedo mantener juntas sólo filas específicas?

 Sí, puedes aplicar selectivamente el`KeepWithNext` propiedad a filas o párrafos específicos dentro de la tabla para controlar qué partes deben permanecer juntas.

### ¿Este método funciona con tablas grandes?

En el caso de tablas muy grandes, Word puede dividirlas en varias páginas si no hay suficiente espacio para que quepan todas en una sola página. Considere ajustar el formato o los márgenes de la tabla para que se adapten a tablas más grandes.

### ¿Puedo utilizar este método con otros formatos de documentos?

¡Sí! Aspose.Words para .NET admite muchos formatos, como DOC, DOCX, PDF y otros. El mismo método funciona en todos los formatos que admiten tablas.

### ¿Es Aspose.Words para .NET una biblioteca gratuita?

 Aspose.Words para .NET ofrece una versión de prueba gratuita, pero para tener acceso completo a todas las funciones, deberá comprar una licencia. Puede explorar las opciones de licencia en la[Página de compra de Aspose](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
