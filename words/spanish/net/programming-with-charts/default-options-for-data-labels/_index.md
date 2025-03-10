---
title: Establecer opciones predeterminadas para las etiquetas de datos en un gráfico
linktitle: Establecer opciones predeterminadas para las etiquetas de datos en un gráfico
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar opciones predeterminadas para las etiquetas de datos en un gráfico con Aspose.Words para .NET. Siga nuestra guía paso a paso para crear y personalizar gráficos sin esfuerzo.
weight: 10
url: /es/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer opciones predeterminadas para las etiquetas de datos en un gráfico

## Introducción

¡Hola! ¿Estás emocionado por sumergirte en el mundo de la automatización de documentos? Hoy, vamos a explorar cómo usar Aspose.Words para .NET para crear documentos impresionantes mediante programación. Aspose.Words es una biblioteca poderosa que te permite manipular documentos de Word con facilidad y, en este tutorial, nos centraremos en configurar opciones predeterminadas para las etiquetas de datos en un gráfico. Ya seas un desarrollador experimentado o un novato, esta guía te guiará paso a paso para que puedas comenzar a trabajar en poco tiempo.

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo lo que necesitas para seguir este tutorial. Aquí tienes una lista de verificación rápida:

- Visual Studio o cualquier otro IDE compatible con .NET: aquí es donde escribirás y ejecutarás tu código.
-  Aspose.Words para .NET: puedes[Descargue la última versión](https://releases.aspose.com/words/net/) e instálelo en su proyecto.
- Conocimientos básicos de programación en C#: si bien esta guía está dirigida a principiantes, será útil tener un poco de familiaridad con C#.
- .NET Framework instalado: asegúrese de tener .NET Framework configurado en su máquina.
-  Una licencia temporal para Aspose.Words: Consigue una[aquí](https://purchase.aspose.com/temporary-license/) para desbloquear la funcionalidad completa.

¡Una vez que hayas cumplido con estos requisitos previos, estaremos listos para comenzar!

## Importar espacios de nombres

Lo primero es lo primero: configuremos nuestro proyecto e importemos los espacios de nombres necesarios. Estos espacios de nombres son fundamentales para acceder a la funcionalidad de Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Paso 1: Crear un nuevo documento


 El viaje comienza creando un nuevo documento e inicializando un`DocumentBuilder` . El`DocumentBuilder` La clase proporciona un conjunto de métodos para manipular el contenido del documento fácilmente.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crear un nuevo documento
Document doc = new Document();

// Inicializar DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Explicación

 En este paso, configuramos el documento y el generador que usaremos para insertar y dar formato a nuestro contenido.`dataDir` La variable contiene la ruta donde guardaremos nuestro documento final.

## Paso 2: Insertar un gráfico

 A continuación, agregaremos un gráfico circular a nuestro documento.`InsertChart` método de la`DocumentBuilder` La clase hace que esto sea súper fácil.

```csharp
// Insertar un gráfico circular
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Acceder al objeto gráfico
Chart chart = shape.Chart;
```

### Explicación

Aquí, estamos insertando un gráfico circular en nuestro documento.`InsertChart` El método requiere el tipo de gráfico, el ancho y la altura como parámetros. Después de insertar el gráfico, accedemos al objeto gráfico para manipularlo más.

## Paso 3: Personaliza la serie de gráficos

Ahora, borraremos todas las series existentes en el gráfico y agregaremos nuestra serie personalizada. Esta serie representará nuestros puntos de datos.

```csharp
// Borrar series de gráficos existentes
chart.Series.Clear();

// Añadir nueva serie al gráfico
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Explicación

En este paso, nos aseguramos de que nuestro gráfico esté vacío borrando cualquier serie preexistente. Luego, agregamos una nueva serie con categorías y valores personalizados, que se mostrarán en nuestro gráfico circular.

## Paso 4: Establecer opciones predeterminadas para las etiquetas de datos

Las etiquetas de datos son fundamentales para que el gráfico sea informativo. Configuraremos opciones para mostrar porcentajes y valores, y personalizaremos el separador.

```csharp
// Acceda a la colección de etiquetas de datos
ChartDataLabelCollection labels = series.DataLabels;

// Establecer opciones de etiqueta de datos
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Explicación

 Aquí, estamos accediendo a la`DataLabels`Propiedad de nuestra serie para personalizar la apariencia y la información que se muestra en cada etiqueta de datos. Hemos optado por mostrar tanto el porcentaje como el valor, ocultar las líneas guía y establecer un separador personalizado.

## Paso 5: Guardar el documento

Por último, guardaremos nuestro documento en el directorio especificado. Este paso garantiza que todos los cambios se escriban en un archivo.

```csharp
// Guardar el documento
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Explicación

 En este último paso, guardamos nuestro documento usando el`Save` método. El documento se guardará en el directorio especificado por`dataDir`, con el nombre "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Conclusión

¡Y ya está! Ha creado con éxito un documento de Word con un gráfico circular personalizado utilizando Aspose.Words para .NET. Esta potente biblioteca facilita la automatización de la creación y manipulación de documentos, lo que le permite ahorrar tiempo y esfuerzo. Ya sea que esté generando informes, facturas o cualquier otro tipo de documento, Aspose.Words lo tiene cubierto.

 Siéntete libre de explorar el[Documentación de Aspose.Words](https://reference.aspose.com/words/net/) Para más funciones y ejemplos. ¡Que disfrutes codificando!

## Preguntas frecuentes

### ¿Puedo utilizar Aspose.Words gratis?
Puedes utilizar Aspose.Words de forma gratuita con un[licencia temporal](https://purchase.aspose.com/temporary-license/) o explorar sus funciones utilizando el[prueba gratis](https://releases.aspose.com/).

### ¿Cómo puedo obtener soporte para Aspose.Words?
 Puede obtener ayuda a través de[Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).

### ¿Puedo agregar otros tipos de gráficos?
 Sí, Aspose.Words admite varios tipos de gráficos, como gráficos de barras, de líneas y de columnas.[documentación](https://reference.aspose.com/words/net/) Para más detalles.

### ¿Aspose.Words es compatible con .NET Core?
 Sí, Aspose.Words es compatible con .NET Core. Puede encontrar más información en[documentación](https://reference.aspose.com/words/net/).

### ¿Cómo puedo comprar una licencia para Aspose.Words?
 Puede comprar una licencia en[Tienda Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
