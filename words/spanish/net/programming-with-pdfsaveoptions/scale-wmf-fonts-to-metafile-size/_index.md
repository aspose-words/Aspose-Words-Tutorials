---
"description": "Guía paso a paso para reducir el tamaño de PDF con escala de fuentes wmf al tamaño de metarchivo al convertir a PDF con Aspose.Words para .NET."
"linktitle": "Reducir el tamaño de un PDF con la función Escalar fuentes WMF al tamaño de un metarchivo"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Reducir el tamaño de un PDF con la función Escalar fuentes WMF al tamaño de un metarchivo"
"url": "/es/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reducir el tamaño de un PDF con la función Escalar fuentes WMF al tamaño de un metarchivo

## Introducción

Al trabajar con archivos PDF, especialmente aquellos generados a partir de documentos de Word que contienen gráficos WMF (metarchivo de Windows), la gestión del tamaño puede ser crucial. Una forma de controlar el tamaño del PDF es ajustar la representación de las fuentes WMF en el documento. En este tutorial, exploraremos cómo reducir el tamaño de un PDF escalando las fuentes WMF al tamaño del metarchivo con Aspose.Words para .NET.

## Prerrequisitos

Antes de continuar con los pasos, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET: Asegúrese de tener instalada la biblioteca Aspose.Words. De lo contrario, puede... [Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: este tutorial asume que tiene configurado un entorno de desarrollo .NET (como Visual Studio) donde puede escribir y ejecutar código C#.
3. Comprensión básica de la programación .NET: será útil estar familiarizado con los conceptos básicos de programación .NET y la sintaxis de C#.
4. Documento de Word con gráficos WMF: Necesitará un documento de Word con gráficos WMF. Puede usar su propio documento o crear uno para probar.

## Importar espacios de nombres

Primero, debe importar los espacios de nombres necesarios en su proyecto de C#. Esto le dará acceso a las clases y métodos necesarios para trabajar con Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Cargue el documento de Word

Para comenzar, cargue el documento de Word que contiene los gráficos WMF. Esto se hace usando el `Document` clase de Aspose.Words.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Cargar el documento
Document doc = new Document(dataDir + "WMF with text.docx");
```

Aquí, `dataDir` es un marcador de posición para la ruta del directorio de su documento. Creamos una instancia de `Document` Clase pasando la ruta al archivo de Word. Esto carga el documento en memoria, listo para su posterior procesamiento.

## Paso 2: Configurar las opciones de representación de metarchivos

A continuación, debe configurar las opciones de representación del metarchivo. En concreto, configure `ScaleWmfFontsToMetafileSize` propiedad a `false`Esto controla si las fuentes WMF se escalan para que coincidan con el tamaño del metarchivo.

```csharp
// Crear una nueva instancia de MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

El `MetafileRenderingOptions` La clase proporciona opciones sobre cómo se representan los metarchivos (como WMF). Al configurar `ScaleWmfFontsToMetafileSize` a `false`, le está indicando a Aspose.Words que no escale las fuentes según el tamaño del metarchivo, lo que puede ayudar a reducir el tamaño general del PDF.

## Paso 3: Establecer las opciones para guardar el PDF

Ahora, configure las opciones de guardado del PDF para usar las opciones de renderizado de metarchivos que acaba de configurar. Esto le indica a Aspose.Words cómo gestionar los metarchivos al guardar el documento como PDF.

```csharp
// Crear una nueva instancia de PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

El `PdfSaveOptions` La clase permite especificar varias configuraciones para guardar el documento como PDF. Al asignar las opciones previamente configuradas `MetafileRenderingOptions` hacia `MetafileRenderingOptions` propiedad de `PdfSaveOptions`, se asegura de que el documento se guarde de acuerdo con la configuración de representación de metarchivo deseada.

## Paso 4: Guardar el documento como PDF

Finalmente, guarde el documento de Word como PDF con las opciones de guardado configuradas. Esto aplicará todos los ajustes, incluidas las opciones de renderizado de metarchivos, al PDF de salida.


```csharp
// Guardar el documento como PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

En este paso, el `Save` método de la `Document` La clase se utiliza para exportar el documento a un archivo PDF. Se especifica la ruta donde se guardará el PDF, junto con la `PdfSaveOptions` que incluyen la configuración de representación del metarchivo.

## Conclusión

Al escalar las fuentes WMF al tamaño de un metarchivo, puede reducir significativamente el tamaño de sus archivos PDF generados a partir de documentos de Word. Esta técnica ayuda a optimizar el almacenamiento y la distribución de documentos sin comprometer la calidad del contenido visual. Seguir los pasos descritos anteriormente garantiza que sus archivos PDF sean más manejables y eficientes en tamaño.

## Preguntas frecuentes

### ¿Qué es WMF y por qué es importante para el tamaño de PDF?

WMF (Metarchivo de Windows) es un formato gráfico utilizado en Microsoft Windows. Puede contener datos vectoriales y de mapa de bits. Dado que los datos vectoriales se pueden escalar y manipular, es importante gestionarlos correctamente para evitar archivos PDF innecesariamente grandes.

### ¿Cómo afecta el escalado de fuentes WMF al tamaño de metarchivo al PDF?

Escalar las fuentes WMF al tamaño de metarchivo puede ayudar a reducir el tamaño general del PDF al evitar la representación de fuentes de alta resolución que podría aumentar el tamaño del archivo.

### ¿Puedo utilizar otros formatos de metarchivo con Aspose.Words?

Sí, Aspose.Words admite varios formatos de metarchivo, incluido EMF (Enhanced Metafile), además de WMF.

### ¿Esta técnica es aplicable a todos los tipos de documentos de Word?

Sí, esta técnica se puede aplicar a cualquier documento de Word que contenga gráficos WMF, ayudando a optimizar el tamaño del PDF generado.

### ¿Dónde puedo encontrar más información sobre Aspose.Words?

Puede explorar más sobre Aspose.Words en el [Documentación de Aspose.Words](https://reference.aspose.com/words/net/)Para descargas, pruebas y soporte, visite el [Página de descarga de Aspose.Words](https://releases.aspose.com/words/net/), [Comprar Aspose.Words](https://purchase.aspose.com/buy), [Prueba gratuita](https://releases.aspose.com/), [Licencia temporal](https://purchase.aspose.com/temporary-license/), y [Apoyo](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}