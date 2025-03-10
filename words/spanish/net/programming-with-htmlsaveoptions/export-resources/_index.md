---
title: Recursos de exportación
linktitle: Recursos de exportación
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a exportar recursos como CSS y fuentes mientras guarda documentos de Word como HTML usando Aspose.Words para .NET. Siga nuestra guía paso a paso.
weight: 10
url: /es/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recursos de exportación

## Introducción

¡Hola, compañero entusiasta de la tecnología! Si alguna vez has tenido que convertir documentos de Word a HTML, estás en el lugar correcto. Hoy nos sumergiremos en el maravilloso mundo de Aspose.Words para .NET. Esta potente biblioteca hace que sea muy fácil trabajar con documentos de Word de manera programática. En este tutorial, repasaremos los pasos para exportar recursos, como fuentes y CSS, al guardar un documento de Word como HTML con Aspose.Words para .NET. ¡Abróchate el cinturón para un viaje divertido e informativo!

## Prerrequisitos

Antes de sumergirnos en el código, asegurémonos de que tienes todo lo que necesitas para empezar. Aquí tienes una lista de verificación rápida:

1.  Visual Studio: Asegúrese de tener Visual Studio instalado en su equipo. Puede descargarlo desde el sitio web[Sitio web de Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.Words para .NET: Necesitará la biblioteca Aspose.Words para .NET. Si aún no la tiene, obtenga una versión de prueba gratuita en[Comunicados de Aspose](https://releases.aspose.com/words/net/) o comprarlo en el[Tienda Aspose](https://purchase.aspose.com/buy).
3. Conocimientos básicos de C#: una comprensión fundamental de C# le ayudará a seguir los ejemplos de código.

¿Entendiste todo eso? ¡Genial! Pasemos a importar los espacios de nombres necesarios.

## Importar espacios de nombres

Para utilizar Aspose.Words para .NET, debe incluir los espacios de nombres pertinentes en su proyecto. A continuación, le indicamos cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Estos espacios de nombres son cruciales para acceder a las clases y métodos Aspose.Words que usaremos en nuestro tutorial.

Vamos a desglosar el proceso de exportación de recursos al guardar un documento de Word como HTML. Lo haremos paso a paso para que sea fácil de seguir.

## Paso 1: Configurar el directorio de documentos

Lo primero es lo primero: debes especificar la ruta del directorio de tus documentos. Aquí es donde se encuentra tu documento de Word y donde se guardará el archivo HTML.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su directorio.

## Paso 2: Cargue el documento de Word

 A continuación, carguemos el documento de Word que desea convertir a HTML. Para este tutorial, utilizaremos un documento llamado`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta línea de código carga el documento desde el directorio especificado.

## Paso 3: Configurar las opciones de guardado de HTML

Para exportar recursos como CSS y fuentes, debe configurar el`HtmlSaveOptions`Este paso es crucial para garantizar que su salida HTML esté bien estructurada e incluya los recursos necesarios.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://ejemplo.com/recursos"
};
```

Analicemos qué hace cada opción:
- `CssStyleSheetType = CssStyleSheetType.External`:Esta opción especifica que los estilos CSS deben guardarse en una hoja de estilo externa.
- `ExportFontResources = true`:Esto permite la exportación de recursos de fuentes.
- `ResourceFolder = dataDir + "Resources"`:Especifica la carpeta local donde se guardarán los recursos (como fuentes y archivos CSS).
- `ResourceFolderAlias = "http://example.com/resources"`:Establece un alias para la carpeta de recursos, que se utilizará en el archivo HTML.

## Paso 4: Guardar el documento como HTML

Una vez configuradas las opciones de guardado, el paso final es guardar el documento como archivo HTML. A continuación, le indicamos cómo hacerlo:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Esta línea de código guarda el documento en formato HTML, junto con los recursos exportados.

## Conclusión

¡Y ya está! Has exportado recursos con éxito mientras guardabas un documento de Word como HTML usando Aspose.Words para .NET. Con esta potente biblioteca, manejar documentos de Word de manera programática se convierte en algo muy sencillo. Ya sea que estés trabajando en una aplicación web o simplemente necesites convertir documentos para usarlos sin conexión, Aspose.Words te ayudará.

## Preguntas frecuentes

### ¿Puedo exportar imágenes junto con fuentes y CSS?
 Sí, ¡puedes! Aspose.Words para .NET también admite la exportación de imágenes. Solo asegúrate de configurar`HtmlSaveOptions` respectivamente.

### ¿Hay alguna forma de incorporar CSS en lugar de utilizar una hoja de estilo externa?
 Por supuesto. Puedes configurarlo`CssStyleSheetType` a`CssStyleSheetType.Embedded` Si prefieres estilos incrustados.

### ¿Cómo puedo personalizar el nombre del archivo HTML de salida?
 Puede especificar cualquier nombre de archivo que desee en el`doc.Save` método. Por ejemplo,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### ¿Aspose.Words admite otros formatos además de HTML?
 Sí, admite varios formatos, incluidos PDF, DOCX, TXT y más. Consulta la[documentación](https://reference.aspose.com/words/net/) para una lista completa.

### ¿Dónde puedo obtener más apoyo y recursos?
Para obtener más ayuda, visite el[Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8) También puede encontrar documentación detallada y ejemplos en[Sitio web de Aspose](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
