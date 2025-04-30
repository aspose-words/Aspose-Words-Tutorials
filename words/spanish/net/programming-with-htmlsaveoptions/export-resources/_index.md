---
"description": "Aprenda a exportar recursos como CSS y fuentes mientras guarda documentos de Word como HTML con Aspose.Words para .NET. Siga nuestra guía paso a paso."
"linktitle": "Recursos de exportación"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Recursos de exportación"
"url": "/es/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Recursos de exportación

## Introducción

¡Hola, amigo entusiasta de la tecnología! Si alguna vez has tenido que convertir documentos de Word a HTML, estás en el lugar indicado. Hoy nos adentramos en el maravilloso mundo de Aspose.Words para .NET. Esta potente biblioteca facilita enormemente el trabajo con documentos de Word mediante programación. En este tutorial, te explicaremos los pasos para exportar recursos, como fuentes y CSS, al guardar un documento de Word como HTML con Aspose.Words para .NET. ¡Prepárate para un viaje divertido e informativo!

## Prerrequisitos

Antes de profundizar en el código, asegurémonos de que tienes todo lo necesario para empezar. Aquí tienes una lista de verificación rápida:

1. Visual Studio: Asegúrese de tener Visual Studio instalado en su equipo. Puede descargarlo desde [Sitio web de Visual Studio](https://visualstudio.microsoft.com/).
2. Aspose.Words para .NET: Necesitará la biblioteca Aspose.Words para .NET. Si aún no la tiene, obtenga una prueba gratuita en [Lanzamientos de Aspose](https://releases.aspose.com/words/net/) o comprarlo en el [Tienda Aspose](https://purchase.aspose.com/buy).
3. Conocimientos básicos de C#: una comprensión fundamental de C# le ayudará a seguir los ejemplos de código.

¿Entendido? ¡Genial! Pasemos a importar los espacios de nombres necesarios.

## Importar espacios de nombres

Para usar Aspose.Words para .NET, debe incluir los espacios de nombres relevantes en su proyecto. Así es como se hace:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Estos espacios de nombres son cruciales para acceder a las clases y métodos Aspose.Words que usaremos en nuestro tutorial.

Analicemos el proceso de exportación de recursos al guardar un documento de Word como HTML. Lo explicaremos paso a paso para que sea fácil de seguir.

## Paso 1: Configure su directorio de documentos

Primero, debe especificar la ruta a su directorio de documentos. Aquí se encuentra su documento de Word y donde se guardará el archivo HTML.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real a su directorio.

## Paso 2: Cargue el documento de Word

continuación, carguemos el documento de Word que queremos convertir a HTML. Para este tutorial, usaremos un documento llamado `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta línea de código carga el documento desde el directorio especificado.

## Paso 3: Configurar las opciones de guardado de HTML

Para exportar recursos como CSS y fuentes, debe configurar el `HtmlSaveOptions`Este paso es crucial para garantizar que su salida HTML esté bien estructurada e incluya los recursos necesarios.

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
- `ResourceFolder = dataDir + "Resources"`: Especifica la carpeta local donde se guardarán los recursos (como fuentes y archivos CSS).
- `ResourceFolderAlias = "http://example.com/resources"`:Establece un alias para la carpeta de recursos, que se utilizará en el archivo HTML.

## Paso 4: Guardar el documento como HTML

Una vez configuradas las opciones de guardado, el último paso es guardar el documento como archivo HTML. Así es como se hace:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Esta línea de código guarda el documento en formato HTML, junto con los recursos exportados.

## Conclusión

¡Y listo! Has exportado recursos correctamente al guardar un documento de Word como HTML con Aspose.Words para .NET. Con esta potente biblioteca, gestionar documentos de Word mediante programación es pan comido. Tanto si trabajas en una aplicación web como si simplemente necesitas convertir documentos para usarlos sin conexión, Aspose.Words te ayuda.

## Preguntas frecuentes

### ¿Puedo exportar imágenes junto con fuentes y CSS?
¡Sí, puedes! Aspose.Words para .NET también admite la exportación de imágenes. Solo asegúrate de configurar `HtmlSaveOptions` respectivamente.

### ¿Hay alguna forma de incorporar CSS en lugar de utilizar una hoja de estilo externa?
Por supuesto. Puedes configurarlo. `CssStyleSheetType` a `CssStyleSheetType.Embedded` Si prefieres estilos incrustados.

### ¿Cómo puedo personalizar el nombre del archivo HTML de salida?
Puede especificar cualquier nombre de archivo que desee en el `doc.Save` método. Por ejemplo, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### ¿Aspose.Words admite otros formatos además de HTML?
Sí, admite varios formatos, como PDF, DOCX, TXT y más. Consulta la [documentación](https://reference.aspose.com/words/net/) para una lista completa.

### ¿Dónde puedo obtener más apoyo y recursos?
Para obtener más ayuda, visite el [Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8)También puede encontrar documentación detallada y ejemplos en [Sitio web de Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}