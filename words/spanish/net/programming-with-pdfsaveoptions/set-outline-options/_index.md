---
"description": "Aprenda a configurar opciones de contorno en un documento PDF con Aspose.Words para .NET. Mejore la navegación en PDF configurando niveles de encabezado y contornos expandidos."
"linktitle": "Establecer opciones de esquema en un documento PDF"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Establecer opciones de esquema en un documento PDF"
"url": "/es/net/programming-with-pdfsaveoptions/set-outline-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Establecer opciones de esquema en un documento PDF

## Introducción

Al trabajar con documentos, especialmente con fines profesionales o académicos, organizar el contenido eficazmente es crucial. Una forma de mejorar la usabilidad de sus documentos PDF es configurar las opciones de esquema. Los esquemas, o marcadores, permiten a los usuarios navegar por el documento eficientemente, como los capítulos de un libro. En esta guía, explicaremos cómo configurar estas opciones con Aspose.Words para .NET, garantizando que sus archivos PDF estén bien organizados y sean fáciles de usar.

## Prerrequisitos

Antes de comenzar, hay algunas cosas que deberá asegurarse de tener:

1. Aspose.Words para .NET: Asegúrate de tener Aspose.Words para .NET instalado. Si no es así, puedes... [Descargue la última versión aquí](https://releases.aspose.com/words/net/).
2. Un entorno de desarrollo .NET: necesitará un entorno de desarrollo .NET que funcione, como Visual Studio.
3. Comprensión básica de C#: estar familiarizado con el lenguaje de programación C# le ayudará a seguir fácilmente.
4. Un documento de Word: ten listo un documento de Word que convertirás en PDF.

## Importar espacios de nombres

Primero, deberá importar los espacios de nombres necesarios. Aquí es donde incluirá la biblioteca Aspose.Words para interactuar con su documento. A continuación, le explicamos cómo configurarla:

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

En el fragmento de código anterior, reemplace `"YOUR DOCUMENT DIRECTORY"` Con la ruta real al directorio de su documento. Esto le indica al programa dónde encontrar el documento de Word.

## Paso 2: Configurar las opciones de guardado de PDF

A continuación, debe configurar las opciones de guardado del PDF. Esto incluye configurar cómo se gestionarán los contornos en el PDF de salida. Utilizará el `PdfSaveOptions` clase para hacer esto.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
```

Ahora, configuremos las opciones de contorno. 

### Niveles de esquema de encabezados de conjuntos

El `HeadingsOutlineLevels` La propiedad define cuántos niveles de encabezados deben incluirse en el esquema del PDF. Por ejemplo, si se establece en 3, se incluirán hasta tres niveles de encabezados en el esquema del PDF.

```csharp
saveOptions.OutlineOptions.HeadingsOutlineLevels = 3;
```

### Establecer niveles de esquema ampliados

El `ExpandedOutlineLevels` Esta propiedad controla cuántos niveles del esquema se deben expandir por defecto al abrir el PDF. Al establecerla en 1, se expandirán los encabezados de nivel superior, ofreciendo una vista clara de las secciones principales.

```csharp
saveOptions.OutlineOptions.ExpandedOutlineLevels = 1;
```

## Paso 3: Guardar el documento como PDF

Con las opciones configuradas, está listo para guardar el documento como PDF. Utilice el `Save` método de la `Document` clase y pase la ruta del archivo y las opciones de guardado.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SetOutlineOptions.pdf", saveOptions);
```

Esta línea de código guarda su documento de Word como PDF, aplicando las opciones de esquema que configuró. 

## Conclusión

Configurar opciones de esquema en un documento PDF puede mejorar considerablemente su navegabilidad, facilitando a los usuarios encontrar y acceder a las secciones que necesitan. Con Aspose.Words para .NET, puede configurar fácilmente estos ajustes para que se ajusten a sus necesidades, garantizando que sus documentos PDF sean lo más intuitivos posible.

## Preguntas frecuentes

### ¿Cuál es el propósito de configurar opciones de esquema en un PDF?

La configuración de las opciones de esquema ayuda a los usuarios a navegar por documentos PDF grandes con mayor facilidad proporcionando una tabla de contenido estructurada y en la que se puede hacer clic.

### ¿Puedo establecer diferentes niveles de encabezado para diferentes secciones de mi documento?

No, la configuración del esquema se aplica globalmente a todo el documento. Sin embargo, puede estructurar su documento con niveles de encabezado adecuados para lograr un efecto similar.

### ¿Cómo puedo obtener una vista previa de los cambios antes de guardar el PDF?

Puedes usar visores de PDF compatibles con la navegación por esquemas para comprobar su aspecto. Algunas aplicaciones ofrecen una función de vista previa para ello.

### ¿Es posible eliminar el contorno después de guardar el PDF?

Sí, puedes eliminar los contornos usando un software de edición de PDF, pero esto no se puede lograr directamente con Aspose.Words una vez creado el PDF.

### ¿Qué otras opciones de guardado de PDF puedo configurar con Aspose.Words?

Aspose.Words ofrece varias opciones, como configurar el nivel de conformidad con PDF, incrustar fuentes y ajustar la calidad de la imagen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}