---
"description": "Aprenda a configurar la configuración de reserva de fuentes en Aspose.Words para .NET. Esta guía completa garantiza que todos los caracteres de sus documentos se muestren correctamente."
"linktitle": "Establecer la configuración de reserva de fuentes"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Establecer la configuración de reserva de fuentes"
"url": "/es/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Establecer la configuración de reserva de fuentes

## Introducción

Al trabajar con documentos que contienen diversos elementos de texto, como diferentes idiomas o caracteres especiales, es fundamental garantizar que estos elementos se muestren correctamente. Aspose.Words para .NET ofrece una potente función llamada "Configuración de Retorno de Fuentes", que ayuda a definir reglas para sustituir fuentes cuando la fuente original no admite ciertos caracteres. En esta guía, exploraremos cómo configurar la configuración de retorno de fuentes con Aspose.Words para .NET en un tutorial paso a paso.

## Prerrequisitos

Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:

- Conocimientos básicos de C#: Familiaridad con el lenguaje de programación C# y el marco .NET.
- Aspose.Words para .NET: Descargar e instalar desde [enlace de descarga](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: una configuración como Visual Studio para escribir y ejecutar su código.
- Documento de muestra: Tenga un documento de muestra (por ejemplo, `Rendering.docx`) listo para probar.
- Reglas de reserva de fuentes XML: prepare un archivo XML que defina las reglas de reserva de fuentes.

## Importar espacios de nombres

Para usar Aspose.Words, debe importar los espacios de nombres necesarios. Esto permite acceder a diversas clases y métodos necesarios para el procesamiento de documentos.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Paso 1: Definir el directorio del documento

Primero, defina el directorio donde se almacena su documento. Esto es esencial para localizarlo y procesarlo.

```csharp
// La ruta al directorio de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargar el documento

Cargue su documento en un Aspose.Words `Document` objeto. Este paso le permite trabajar con el documento programáticamente.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 3: Configurar los ajustes de fuente

Crear uno nuevo `FontSettings` Objeto y carga la configuración de reserva de fuentes desde un archivo XML. Este archivo XML contiene las reglas para la reserva de fuentes.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Paso 4: Aplicar la configuración de fuente al documento

Asignar el configurado `FontSettings` al documento. Esto garantiza que se apliquen las reglas de reserva de fuentes al renderizar el documento.

```csharp
doc.FontSettings = fontSettings;
```

## Paso 5: Guardar el documento

Finalmente, guarde el documento. La configuración de reserva de fuentes se utilizará durante el proceso de guardado para garantizar una sustitución correcta de las fuentes.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Archivo XML: Reglas de reserva de fuentes

A continuación se muestra un ejemplo de cómo debe verse su archivo XML que define las reglas de reserva de fuentes:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Conclusión

Siguiendo estos pasos, podrá configurar y usar eficazmente la configuración de reserva de fuentes en Aspose.Words para .NET. Esto garantiza que sus documentos muestren todos los caracteres correctamente, incluso si la fuente original no admite ciertos caracteres. Implementar esta configuración mejorará considerablemente la calidad y la legibilidad de sus documentos.

## Preguntas frecuentes

### P1: ¿Qué es Font Fallback?

Font Fallback es una función que permite la sustitución de fuentes cuando la fuente original no admite ciertos caracteres, lo que garantiza la visualización adecuada de todos los elementos de texto.

### P2: ¿Puedo especificar varias fuentes de respaldo?

Sí, puede especificar varias fuentes de reserva en las reglas XML. Aspose.Words comprobará cada fuente en el orden especificado hasta encontrar una compatible con el carácter.

### P3: ¿Dónde puedo descargar Aspose.Words para .NET?

Puedes descargarlo desde [Página de descarga de Aspose](https://releases.aspose.com/words/net/).

### P4: ¿Cómo creo el archivo XML para las reglas de reserva de fuentes?

El archivo XML se puede crear con cualquier editor de texto. Debe seguir la estructura que se muestra en el ejemplo de este tutorial.

### Q5: ¿Hay soporte disponible para Aspose.Words?

Sí, puedes encontrar ayuda en el [Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}