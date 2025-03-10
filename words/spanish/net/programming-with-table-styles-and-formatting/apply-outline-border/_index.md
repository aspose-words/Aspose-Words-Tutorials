---
title: Aplicar borde de contorno
linktitle: Aplicar borde de contorno
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a aplicar un borde de contorno a una tabla en Word con Aspose.Words para .NET. Siga nuestra guía paso a paso para lograr un formato de tabla perfecto.
weight: 10
url: /es/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aplicar borde de contorno

## Introducción

En el tutorial de hoy, nos adentraremos en el mundo de la manipulación de documentos con Aspose.Words para .NET. En concreto, aprenderemos a aplicar un borde de contorno a una tabla en un documento de Word. Se trata de una habilidad fantástica que conviene tener en el conjunto de herramientas si trabajas con frecuencia con la generación y el formato automatizados de documentos. Así que, comencemos este viaje para que tus tablas no solo sean funcionales, sino también visualmente atractivas.

## Prerrequisitos

Antes de pasar al código, necesitarás algunas cosas:

1.  Aspose.Words para .NET: Necesita tener instalado Aspose.Words para .NET. Puede descargarlo[aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Un entorno de desarrollo adecuado como Visual Studio.
3. Conocimientos básicos de C#: una comprensión fundamental de C# le ayudará a seguir el tutorial.

## Importar espacios de nombres

Para empezar, asegúrese de haber importado los espacios de nombres necesarios. Esto es fundamental para acceder a las funcionalidades de Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Dividamos el proceso en pasos simples y manejables.

## Paso 1: Cargue el documento

Primero, necesitamos cargar el documento de Word que contiene la tabla que queremos formatear.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 En este paso, usamos el`Document` Clase de Aspose.Words para cargar un documento existente. Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real donde se almacena su documento.

## Paso 2: Acceda a la tabla

A continuación, necesitamos acceder a la tabla específica que queremos formatear. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Aquí,`GetChild` El método recupera la primera tabla del documento. Los parámetros`NodeType.Table, 0, true` asegurarnos de obtener el tipo de nodo correcto.

## Paso 3: Alinea la mesa

Ahora, alineemos la tabla al centro de la página.

```csharp
table.Alignment = TableAlignment.Center;
```

Este paso asegura que la mesa esté perfectamente centrada, dándole un aspecto profesional.

## Paso 4: Limpiar los límites existentes

Antes de aplicar nuevos límites, debemos limpiar todos los existentes.

```csharp
table.ClearBorders();
```

Limpiar los bordes garantiza que nuestros nuevos bordes se apliquen de manera limpia sin que ningún estilo antiguo interfiera.

## Paso 5: Establecer los bordes del contorno

Ahora, apliquemos los bordes de contorno verde a la tabla.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Cada tipo de borde (izquierdo, derecho, superior, inferior) se configura individualmente. Usamos`LineStyle.Single` para una linea continua,`1.5` para el ancho de línea, y`Color.Green` Para el color del borde.

## Paso 6: Aplicar sombreado de celda

Para que la tabla sea más atractiva visualmente, rellenemos las celdas con un color verde claro.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Aquí,`SetShading` Se utiliza para aplicar un color verde claro sólido a las celdas, haciendo que la tabla se destaque.

## Paso 7: Guardar el documento

Por último, guarde el documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Este paso guarda el documento con el formato aplicado. Puedes abrirlo para ver la tabla con un formato perfecto.

## Conclusión

¡Y ya está! Si sigue estos pasos, habrá aplicado con éxito un borde de contorno a una tabla en un documento de Word con Aspose.Words para .NET. Este tutorial abarcó la carga del documento, el acceso a la tabla, su alineación, la eliminación de los bordes existentes, la aplicación de nuevos bordes, la adición de sombreado de celdas y, por último, el guardado del documento. 

Con estas habilidades, puedes mejorar la presentación visual de tus tablas, haciendo que tus documentos sean más profesionales y atractivos. ¡Feliz codificación!

## Preguntas frecuentes

### ¿Puedo aplicar diferentes estilos a cada borde de la tabla?  
 Sí, puedes aplicar diferentes estilos y colores a cada borde ajustando los parámetros en el`SetBorder` método.

### ¿Cómo puedo cambiar el ancho del borde?  
 Puede cambiar el ancho modificando el tercer parámetro en el`SetBorder` método. Por ejemplo,`1.5` Establece un ancho de 1,5 puntos.

### ¿Es posible aplicar sombreado a celdas individuales?  
 Sí, puede aplicar sombreado a celdas individuales accediendo a cada celda y utilizando el`SetShading` método.

### ¿Puedo usar otros colores para los bordes y el sombreado?  
 ¡Por supuesto! Puedes utilizar cualquier color disponible en el`System.Drawing.Color` clase.

### ¿Cómo puedo centrar la tabla horizontalmente?  
 El`table.Alignment = TableAlignment.Center;` La línea en el código centra la tabla horizontalmente en la página.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
