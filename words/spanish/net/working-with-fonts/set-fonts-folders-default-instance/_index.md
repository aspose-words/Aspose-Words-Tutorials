---
title: Establecer carpetas de fuentes como instancia predeterminada
linktitle: Establecer carpetas de fuentes como instancia predeterminada
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar carpetas de fuentes para la instancia predeterminada en Aspose.Words para .NET con este tutorial paso a paso. Personalice sus documentos de Word sin esfuerzo.
weight: 10
url: /es/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer carpetas de fuentes como instancia predeterminada

## Introducción

¡Hola, colega programador! Si trabajas con documentos de Word en .NET, probablemente sepas lo importante que es que las fuentes sean las correctas. Hoy, veremos cómo configurar carpetas de fuentes para la instancia predeterminada usando Aspose.Words para .NET. Imagina tener todas tus fuentes personalizadas a tu alcance, haciendo que tus documentos se vean exactamente como los imaginas. Suena genial, ¿verdad? ¡Comencemos!

## Prerrequisitos

Antes de profundizar en los detalles, asegurémonos de que tienes todo lo que necesitas:
-  Aspose.Words para .NET: Asegúrese de tener instalada la biblioteca. Si no es así, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro IDE compatible con .NET.
- Conocimientos básicos de C#: Debe sentirse cómodo con la programación en C#.
- Carpeta de fuentes: un directorio que contiene sus fuentes personalizadas.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto ayuda a acceder a las clases y métodos necesarios para configurar la carpeta de fuentes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Dividamos el proceso en pasos simples y digeribles.

## Paso 1: Definir el directorio de datos

Todo gran viaje comienza con un paso, y el nuestro comienza con la definición del directorio donde se almacena su documento. Allí es donde Aspose.Words buscará su documento de Word.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Aquí, reemplace`"YOUR DOCUMENT DIRECTORY"` con la ruta actual al directorio de su documento. Aquí es donde se encuentra su documento de origen y donde se guardará el resultado.

## Paso 2: Establezca la carpeta de fuentes

 Ahora, vamos a indicarle a Aspose.Words dónde encontrar sus fuentes personalizadas. Esto se hace configurando la carpeta de fuentes mediante el comando`FontSettings.DefaultInstance.SetFontsFolder` método.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 En esta línea,`"C:\\MyFonts\\"` es la ruta a la carpeta de fuentes personalizadas. El segundo parámetro,`true`, indica que las fuentes en esta carpeta deben escanearse recursivamente.

## Paso 3: Cargue su documento

 Una vez configurada la carpeta de fuentes, el siguiente paso es cargar el documento de Word en Aspose.Words. Esto se hace mediante el comando`Document` clase.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Aquí,`dataDir + "Rendering.docx"` Se refiere a la ruta completa de su documento de Word. Asegúrese de que su documento se encuentre en el directorio especificado.

## Paso 4: Guardar el documento

El paso final es guardar el documento después de configurar la carpeta de fuentes. Esto garantiza que las fuentes personalizadas se apliquen correctamente en el documento resultante.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Esta línea guarda el documento como PDF con las fuentes personalizadas aplicadas. El archivo de salida se ubicará en el mismo directorio que el documento de origen.

## Conclusión

¡Y ya está! Configurar carpetas de fuentes para la instancia predeterminada en Aspose.Words para .NET es muy fácil si lo divides en pasos simples. Si sigues esta guía, podrás asegurarte de que tus documentos de Word se vean exactamente como quieres, con todas tus fuentes personalizadas en su lugar. ¡Así que adelante, pruébalo y haz que tus documentos brillen!

## Preguntas frecuentes

### ¿Puedo configurar varias carpetas de fuentes?
 Sí, puedes configurar varias carpetas de fuentes mediante el uso de`SetFontsFolders` método que acepta una matriz de rutas de carpetas.

### ¿Qué formatos de archivos admite Aspose.Words para guardar documentos?
Aspose.Words admite varios formatos, incluidos DOCX, PDF, HTML, EPUB y más.

### ¿Es posible utilizar fuentes en línea en Aspose.Words?
No, Aspose.Words actualmente solo admite archivos de fuentes locales.

### ¿Cómo puedo asegurarme de que mis fuentes personalizadas estén incrustadas en el PDF guardado?
 Al configurar el`FontSettings` correctamente y asegurándose de que las fuentes estén disponibles, Aspose.Words las incrustará en la salida PDF.

### ¿Qué sucede si no se encuentra una fuente en la carpeta especificada?
Aspose.Words utilizará una fuente alternativa si no se encuentra la fuente especificada.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
