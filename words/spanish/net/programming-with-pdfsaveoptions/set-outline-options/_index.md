---
title: Establecer opciones de esquema en un documento PDF
linktitle: Establecer opciones de esquema en un documento PDF
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar opciones de esquema en un documento PDF con Aspose.Words para .NET. Mejore la navegación en PDF configurando niveles de encabezado y esquemas expandidos.
weight: 10
url: /es/net/programming-with-pdfsaveoptions/set-outline-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer opciones de esquema en un documento PDF

## Introducción

Al trabajar con documentos, especialmente con fines profesionales o académicos, es fundamental organizar el contenido de forma eficaz. Una forma de mejorar la usabilidad de los documentos PDF es configurar las opciones de esquema. Los esquemas, o marcadores, permiten a los usuarios navegar por el documento de forma eficaz, como si fueran capítulos de un libro. En esta guía, analizaremos en profundidad cómo configurar estas opciones con Aspose.Words para .NET, lo que garantiza que los archivos PDF estén bien organizados y sean fáciles de usar.

## Prerrequisitos

Antes de comenzar, hay algunas cosas que deberá asegurarse de tener:

1.  Aspose.Words para .NET: asegúrese de tener instalado Aspose.Words para .NET. Si no es así, puede[Descargue la última versión aquí](https://releases.aspose.com/words/net/).
2. Un entorno de desarrollo .NET: necesitará un entorno de desarrollo .NET que funcione, como Visual Studio.
3. Comprensión básica de C#: la familiaridad con el lenguaje de programación C# le ayudará a seguir fácilmente.
4. Un documento de Word: ten listo un documento de Word que convertirás en PDF.

## Importar espacios de nombres

En primer lugar, deberá importar los espacios de nombres necesarios. Aquí es donde incluirá la biblioteca Aspose.Words para interactuar con su documento. A continuación, le indicamos cómo configurarla:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Definir la ruta del documento

Para comenzar, deberá especificar la ruta de su documento de Word. Este es el archivo que desea convertir a PDF con opciones de esquema. 

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 En el fragmento de código anterior, reemplace`"YOUR DOCUMENT DIRECTORY"` con la ruta actual al directorio de su documento. Esto le indica al programa dónde encontrar el documento de Word.

## Paso 2: Configurar las opciones para guardar PDF

 A continuación, debe configurar las opciones de guardado del PDF. Esto incluye configurar cómo se deben manejar los contornos en la salida del PDF. Utilizará el`PdfSaveOptions` clase para hacer esto.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
```

Ahora, configuremos las opciones de esquema. 

### Establecer niveles de esquema de encabezados

 El`HeadingsOutlineLevels` La propiedad define cuántos niveles de encabezados se deben incluir en el esquema del PDF. Por ejemplo, si la establece en 3, incluirá hasta tres niveles de encabezados en el esquema del PDF.

```csharp
saveOptions.OutlineOptions.HeadingsOutlineLevels = 3;
```

### Establecer niveles de esquema ampliados

 El`ExpandedOutlineLevels`La propiedad controla cuántos niveles del esquema se deben expandir de forma predeterminada cuando se abre el PDF. Si se establece en 1, se expandirán los encabezados de nivel superior, lo que dará una vista clara de las secciones principales.

```csharp
saveOptions.OutlineOptions.ExpandedOutlineLevels = 1;
```

## Paso 3: Guardar el documento como PDF

 Con las opciones configuradas, estás listo para guardar el documento como PDF. Usa el botón`Save` método de la`Document` clase y pase la ruta del archivo y las opciones de guardado.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SetOutlineOptions.pdf", saveOptions);
```

Esta línea de código guarda su documento de Word como PDF, aplicando las opciones de esquema que usted configuró. 

## Conclusión

La configuración de opciones de esquema en un documento PDF puede mejorar enormemente su navegabilidad, lo que facilita a los usuarios encontrar y acceder a las secciones que necesitan. Con Aspose.Words para .NET, puede configurar fácilmente estos ajustes para que se ajusten a sus necesidades, lo que garantiza que sus documentos PDF sean lo más fáciles de usar posible.

## Preguntas frecuentes

### ¿Cuál es el propósito de configurar opciones de esquema en un PDF?

La configuración de las opciones de esquema ayuda a los usuarios a navegar por documentos PDF grandes con mayor facilidad al proporcionar una tabla de contenido estructurada y en la que se puede hacer clic.

### ¿Puedo establecer diferentes niveles de encabezado para diferentes secciones de mi documento?

No, la configuración del esquema se aplica de manera global a todo el documento. Sin embargo, puedes estructurar tu documento con niveles de encabezado adecuados para lograr un efecto similar.

### ¿Cómo puedo obtener una vista previa de los cambios antes de guardar el PDF?

Puede utilizar visualizadores de PDF que admitan la navegación por el esquema para comprobar cómo aparece. Algunas aplicaciones ofrecen una función de vista previa para ello.

### ¿Es posible eliminar el contorno después de guardar el PDF?

Sí, puedes eliminar los contornos usando un software de edición de PDF, pero esto no se puede lograr directamente con Aspose.Words una vez creado el PDF.

### ¿Qué otras opciones de guardado de PDF puedo configurar con Aspose.Words?

Aspose.Words ofrece varias opciones, como configurar el nivel de conformidad con PDF, incrustar fuentes y ajustar la calidad de la imagen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
