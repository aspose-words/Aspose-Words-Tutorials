---
title: Configuración de ancho preferida
linktitle: Configuración de ancho preferida
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a crear tablas con configuraciones de ancho absoluto, relativo y automático en Aspose.Words para .NET con esta guía paso a paso.
weight: 10
url: /es/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configuración de ancho preferida

## Introducción

Las tablas son una forma eficaz de organizar y presentar información en sus documentos de Word. Al trabajar con tablas en Aspose.Words para .NET, tiene varias opciones para configurar el ancho de las celdas de la tabla para garantizar que se ajusten perfectamente al diseño de su documento. Esta guía lo guiará a través del proceso de creación de tablas con la configuración de ancho preferida mediante Aspose.Words para .NET, centrándose en las opciones de tamaño absoluto, relativo y automático. 

## Prerrequisitos

Antes de sumergirte en el tutorial, asegúrate de tener lo siguiente:

1.  Aspose.Words para .NET: Asegúrese de tener Aspose.Words para .NET instalado en su entorno de desarrollo. Puede descargarlo[aquí](https://releases.aspose.com/words/net/).

2. Entorno de desarrollo .NET: tenga configurado un entorno de desarrollo .NET, como Visual Studio.

3. Conocimientos básicos de C#: la familiaridad con la programación en C# le ayudará a comprender mejor los fragmentos de código y los ejemplos.

4.  Documentación de Aspose.Words: consulte la[Documentación de Aspose.Words](https://reference.aspose.com/words/net/) para obtener información detallada sobre la API y lectura adicional.

## Importar espacios de nombres

Antes de comenzar a codificar, debes importar los espacios de nombres necesarios en tu proyecto de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Estos espacios de nombres proporcionan acceso a las funcionalidades principales de Aspose.Words y al objeto Table, lo que le permite manipular tablas de documentos.

Dividamos el proceso de creación de una tabla con diferentes configuraciones de ancho preferidas en pasos claros y manejables.

## Paso 1: Inicializar el documento y DocumentBuilder

Título: Creación de un nuevo documento y DocumentBuilder

 Explicación: Comience creando un nuevo documento de Word y un`DocumentBuilder` instancia. El`DocumentBuilder` La clase proporciona una forma sencilla de agregar contenido a su documento.

```csharp
// Define la ruta para guardar el documento.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crear un nuevo documento.
Document doc = new Document();

// Cree un DocumentBuilder para este documento.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aquí, especifica el directorio donde se guardará el documento e inicializa el`Document` y`DocumentBuilder` objetos.

## Paso 2: Insertar la primera celda de la tabla con ancho absoluto

Inserte la primera celda de la tabla con un ancho fijo de 40 puntos. Esto garantizará que esta celda siempre mantenga un ancho de 40 puntos independientemente del tamaño de la tabla.

```csharp
// Insertar una celda de tamaño absoluto.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

En este paso, comienza a crear la tabla e inserta una celda con un ancho absoluto.`PreferredWidth.FromPoints(40)` El método establece el ancho de la celda en 40 puntos y`Shading.BackgroundPatternColor` aplica un color de fondo amarillo claro.

## Paso 3: Insertar una celda de tamaño relativo

Inserte otra celda con un ancho que sea el 20 % del ancho total de la tabla. Este tamaño relativo garantiza que la celda se ajuste proporcionalmente al ancho de la tabla.

```csharp
// Insertar una celda de tamaño relativo (porcentaje).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

El ancho de esta celda será el 20% del ancho total de la tabla, lo que la hace adaptable a diferentes tamaños de pantalla o diseños de documentos.

### Paso 4: Insertar una celda de tamaño automático

Por último, inserte una celda que se dimensione automáticamente en función del espacio disponible restante en la tabla.

```csharp
// Insertar una celda de tamaño automático.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 El`PreferredWidth.Auto` Esta configuración permite que esta celda se expanda o contraiga según el espacio que quede después de que se hayan tenido en cuenta las demás celdas. Esto garantiza que el diseño de la tabla se vea equilibrado y profesional.

## Paso 5: Finalizar y guardar el documento

Una vez que haya insertado todas las celdas, complete la tabla y guarde el documento en la ruta especificada.

```csharp
// Guardar el documento.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Este paso finaliza la tabla y guarda el documento con el nombre de archivo "WorkingWithTables.PreferredWidthSettings.docx" en el directorio designado.

## Conclusión

Crear tablas con la configuración de ancho preferida en Aspose.Words para .NET es sencillo una vez que comprende las diferentes opciones de tamaño disponibles. Ya sea que necesite anchos de celda fijos, relativos o automáticos, Aspose.Words brinda la flexibilidad para manejar varios escenarios de diseño de tablas de manera eficiente. Si sigue los pasos descritos en esta guía, puede asegurarse de que sus tablas estén bien estructuradas y sean visualmente atractivas en sus documentos de Word.

## Preguntas frecuentes

### ¿Cuál es la diferencia entre anchos de celda absolutos y relativos?
Los anchos de celda absolutos son fijos y no cambian, mientras que los anchos relativos se ajustan según el ancho total de la tabla.

### ¿Puedo utilizar porcentajes negativos para anchos relativos?
No, los porcentajes negativos no son válidos para el ancho de celda. Solo se permiten porcentajes positivos.

### ¿Cómo funciona la función de cambio de tamaño automático?
El tamaño automático ajusta el ancho de la celda para llenar cualquier espacio restante en la tabla después de que se haya cambiado el tamaño de otras celdas.

### ¿Puedo aplicar diferentes estilos a celdas con diferentes configuraciones de ancho?
Sí, puedes aplicar varios estilos y formatos a las celdas independientemente de su configuración de ancho.

### ¿Qué sucede si el ancho total de la tabla es menor que la suma de todos los anchos de celda?
La tabla ajustará automáticamente el ancho de las celdas para que quepan dentro del espacio disponible, lo que puede provocar que algunas celdas se encojan.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
