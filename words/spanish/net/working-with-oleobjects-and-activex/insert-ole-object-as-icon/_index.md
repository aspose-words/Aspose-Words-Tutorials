---
title: Insertar objeto OLE en documento de Word como icono
linktitle: Insertar objeto OLE en documento de Word como icono
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a insertar un objeto OLE como icono en documentos de Word con Aspose.Words para .NET. Siga nuestra guía paso a paso para mejorar sus documentos.
weight: 10
url: /es/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar objeto OLE en documento de Word como icono

## Introducción

¿Alguna vez ha necesitado incrustar un objeto OLE, como una presentación de PowerPoint o una hoja de cálculo de Excel, en un documento de Word, pero deseaba que apareciera como un pequeño icono en lugar de un objeto completo? ¡Pues está en el lugar correcto! En este tutorial, le explicaremos cómo insertar un objeto OLE como icono en un documento de Word utilizando Aspose.Words para .NET. Al final de esta guía, podrá integrar sin problemas objetos OLE en sus documentos, haciéndolos más interactivos y visualmente atractivos.

## Prerrequisitos

Antes de profundizar en los detalles, cubramos lo que necesitas:

1.  Aspose.Words para .NET: Asegúrese de tener instalado Aspose.Words para .NET. Si aún no lo ha instalado, puede descargarlo desde el sitio web[Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: necesita un entorno de desarrollo integrado (IDE) como Visual Studio.
3. Conocimientos básicos de C#: será útil tener conocimientos básicos de programación en C#.

## Importar espacios de nombres

En primer lugar, debe importar los espacios de nombres necesarios. Esto es esencial para acceder a las funciones de la biblioteca Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Paso 1: Crear un nuevo documento

Para comenzar, debes crear una nueva instancia de documento de Word.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Este fragmento de código inicializa un nuevo documento de Word y un objeto DocumentBuilder que se utiliza para crear el contenido del documento.

## Paso 2: Insertar objeto OLE como icono

 Ahora, insertemos el objeto OLE como un icono.`InsertOleObjectAsIcon` Para este propósito se utiliza el método de la clase DocumentBuilder.

```csharp
builder.InsertOleObjectAsIcon("path_to_your_presentation.pptx", false, "path_to_your_icon.ico", "My embedded file");
```

Vamos a desglosar este método:
- `"path_to_your_presentation.pptx"`:Esta es la ruta al objeto OLE que desea incrustar.
- `false` : Este parámetro booleano especifica si se debe mostrar el objeto OLE como un icono. Como queremos un icono, lo configuramos como`false`.
- `"path_to_your_icon.ico"`:Esta es la ruta al archivo de icono que desea utilizar para el objeto OLE.
- `"My embedded file"`:Esta es la etiqueta que aparecerá debajo del ícono.

## Paso 3: Guardar el documento

Por último, debes guardar el documento. Elige el directorio donde quieres guardar el archivo.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
```

Esta línea de código guarda el documento en la ruta especificada.

## Conclusión

¡Felicitaciones! Aprendió a insertar un objeto OLE como ícono en un documento de Word con Aspose.Words para .NET. Esta técnica no solo ayuda a incrustar objetos complejos, sino que también mantiene su documento ordenado y profesional.

## Preguntas frecuentes

### ¿Puedo utilizar diferentes tipos de objetos OLE con este método?

Sí, puedes incrustar varios tipos de objetos OLE, como hojas de cálculo de Excel, presentaciones de PowerPoint e incluso archivos PDF.

### ¿Cómo puedo obtener una prueba gratuita de Aspose.Words para .NET?

 Puede obtener una prueba gratuita desde[Página de lanzamiento de Aspose](https://releases.aspose.com/).

### ¿Qué es un objeto OLE?

OLE (Object Linking and Embedding) es una tecnología desarrollada por Microsoft que permite incrustar y vincular documentos y otros objetos.

### ¿Necesito una licencia para usar Aspose.Words para .NET?

 Sí, Aspose.Words para .NET requiere una licencia. Puede comprarla en el sitio web[Página de compra de Aspose](https://purchase.aspose.com/buy) o conseguir uno[licencia temporal](https://purchase.aspose.com/temporary-license/) para evaluación.

### ¿Dónde puedo encontrar más tutoriales sobre Aspose.Words para .NET?

 Puede encontrar más tutoriales y documentación en[Página de documentación de Aspose](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
