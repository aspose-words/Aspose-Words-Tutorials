---
title: Especificar la fuente predeterminada al renderizar
linktitle: Especificar la fuente predeterminada al renderizar
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a especificar una fuente predeterminada al representar documentos de Word con Aspose.Words para .NET. Garantice una apariencia uniforme de los documentos en todas las plataformas.
weight: 10
url: /es/net/working-with-fonts/specify-default-font-when-rendering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Especificar la fuente predeterminada al renderizar

## Introducción

Garantizar que los documentos de Word se representen correctamente en distintas plataformas puede ser un desafío, especialmente cuando se trata de compatibilidad de fuentes. Una forma de mantener una apariencia uniforme es especificar una fuente predeterminada al representar los documentos en PDF u otros formatos. En este tutorial, exploraremos cómo establecer una fuente predeterminada con Aspose.Words para .NET, para que sus documentos se vean bien sin importar dónde se visualicen.

## Prerrequisitos

Antes de sumergirnos en el código, veamos lo que necesitarás seguir junto con este tutorial:

- Aspose.Words para .NET: Asegúrate de tener instalada la última versión. Puedes descargarla[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro entorno de desarrollo .NET.
- Conocimientos básicos de C#: este tutorial asume que se siente cómodo con la programación en C#.

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios. Estos le permitirán acceder a las clases y métodos necesarios para trabajar con Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ahora, desglosemos el proceso de especificar una fuente predeterminada en pasos fáciles de seguir.

## Paso 1: Configurar el directorio de documentos

En primer lugar, defina la ruta al directorio de documentos. Allí se almacenarán los archivos de entrada y salida.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Cargue su documento

A continuación, cargue el documento que desea renderizar. En este ejemplo, utilizaremos un archivo llamado "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 3: Configurar los ajustes de fuente

 Crear una instancia de`FontSettings` y especifique la fuente predeterminada. Si no se puede encontrar la fuente definida durante la representación, Aspose.Words utilizará la fuente más cercana disponible en la máquina.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";
```

## Paso 4: Aplicar la configuración de fuente al documento

Asigne las opciones de fuente configuradas a su documento.

```csharp
doc.FontSettings = fontSettings;
```

## Paso 5: Guardar el documento

Por último, guarda el documento en el formato que desees. En este caso, lo guardaremos como PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SpecifyDefaultFontWhenRendering.pdf");
```

## Conclusión

Si sigue estos pasos, podrá asegurarse de que sus documentos de Word se representen con una fuente predeterminada específica, manteniendo la coherencia en distintas plataformas. Esto puede resultar especialmente útil para documentos que se comparten ampliamente o que se visualizan en sistemas con disponibilidad de fuentes variable.


## Preguntas frecuentes

### ¿Por qué especificar una fuente predeterminada en Aspose.Words?
Especificar una fuente predeterminada garantiza que su documento aparezca consistente en diferentes plataformas, incluso si las fuentes originales no están disponibles.

### ¿Qué sucede si no se encuentra la fuente predeterminada durante la renderización?
Aspose.Words utilizará la fuente más cercana disponible en la máquina para mantener la apariencia del documento lo más fiel posible.

### ¿Puedo especificar varias fuentes predeterminadas?
 No, solo puede especificar una fuente predeterminada. Sin embargo, puede manejar la sustitución de fuentes para casos específicos utilizando el`FontSettings` clase.

### ¿Aspose.Words para .NET es compatible con todas las versiones de documentos de Word?
Sí, Aspose.Words para .NET admite una amplia gama de formatos de documentos de Word, incluidos DOC, DOCX, RTF y más.

### ¿Dónde puedo obtener ayuda si tengo problemas?
 Puede obtener soporte de la comunidad y los desarrolladores de Aspose en[Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
