---
title: Establecer carpetas de fuentes
linktitle: Establecer carpetas de fuentes
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar carpetas de fuentes personalizadas en Aspose.Words para .NET con esta guía completa paso a paso. Perfecta para desarrolladores que buscan mejorar las fuentes de los documentos.
weight: 10
url: /es/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer carpetas de fuentes

## Introducción

¡Hola! ¿Estás listo para sumergirte en el mundo de las fuentes personalizadas en Aspose.Words para .NET? Comencemos. Este tutorial te guiará a través del proceso de configuración de carpetas de fuentes personalizadas, lo que garantizará que tus documentos se vean exactamente como quieres. Ya seas un desarrollador experimentado o recién estés comenzando, esta guía te guiará en cada paso. ¡Así que, hagamos que esas fuentes se vean fabulosas!

## Prerrequisitos

Antes de comenzar, asegurémonos de que tienes todo lo que necesitas:

-  Aspose.Words para .NET: puedes[descargar](https://releases.aspose.com/words/net/) Hazlo si aún no lo has hecho.
- Visual Studio: cualquier versión funcionará, pero la última es siempre la mejor.
- Un documento: para este tutorial, utilizaremos un documento de Word. Puedes crear uno propio o utilizar uno existente.
- Fuentes personalizadas: tenga preparadas algunas fuentes personalizadas. Las usaremos para demostrar cómo configurar carpetas de fuentes.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Esto es esencial para acceder a las clases y métodos que necesitamos de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Con estos espacios de nombres importados, estamos listos para comenzar a configurar nuestras carpetas de fuentes personalizadas.

## Paso 1: Defina su directorio de documentos

 Comencemos por definir la ruta al directorio de su documento. Aquí es donde se almacena su documento de Word. Usaremos una variable llamada`dataDir` para almacenar esta ruta.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real a su directorio. Esto es crucial porque Aspose.Words necesitará saber dónde encontrar su documento.

## Paso 2: Establecer fuentes de fuentes

 A continuación, debemos configurar las fuentes de fuentes. Aquí es donde le indicamos a Aspose.Words dónde encontrar nuestras fuentes personalizadas. Vamos a utilizar el`FontSettings.DefaultInstance.SetFontsSources` método para lograr esto.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Esto es lo que estamos haciendo:

- SystemFontSource: Esto le indica a Aspose.Words que utilice las fuentes predeterminadas del sistema.
-  FolderFontSource: Aquí es donde especificamos la carpeta que contiene nuestras fuentes personalizadas. Reemplazar`"C:\\MyFonts\\"` con la ruta a su directorio de fuentes personalizadas.`true` El parámetro indica que también deben incluirse los subdirectorios.

## Paso 3: Cargue su documento

Ahora que hemos configurado nuestras fuentes, es hora de cargar el documento con el que queremos trabajar. Usaremos el`Document` clase de Aspose.Palabras para esto.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Asegúrese de que`"Rendering.docx"` es el nombre de su documento de Word. Si su documento tiene un nombre diferente, asegúrese de actualizarlo como corresponda.

## Paso 4: Guarde su documento como PDF

 Por último, guardemos nuestro documento como PDF para ver las fuentes personalizadas en acción. Usaremos el`Save` método de la`Document` clase.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Esto guardará su documento como PDF en el directorio especificado, utilizando las fuentes personalizadas que configuramos anteriormente.

## Conclusión

¡Y ya está! Has configurado correctamente carpetas de fuentes personalizadas en Aspose.Words para .NET y has guardado tu documento como PDF con esas fuentes personalizadas. Genial, ¿verdad? Personalizar las fuentes puede marcar una gran diferencia en la apariencia de tus documentos y ahora sabes exactamente cómo hacerlo. ¡Que disfrutes codificando!

## Preguntas frecuentes

### ¿Cómo instalo Aspose.Words para .NET?

 Puede[descargar](https://releases.aspose.com/words/net/) la última versión de Aspose.Words para .NET desde el sitio web.

### ¿Puedo utilizar varias carpetas de fuentes personalizadas?

 Sí, puedes agregar varios`FolderFontSource` instancias a la`SetFontsSources`Método para utilizar fuentes de diferentes directorios.

### ¿Es necesario incluir fuentes del sistema?

Incluir fuentes del sistema es opcional, pero se recomienda para garantizar que todas las fuentes estándar estén disponibles.

### ¿Qué tipos de archivos admite Aspose.Words?

Aspose.Words admite una amplia gama de formatos de archivos, incluidos DOCX, DOC, PDF, TXT, HTML y muchos más.

### ¿Cómo puedo obtener una licencia temporal para Aspose.Words?

 Puedes obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/) desde el sitio web de Aspose para probar las funciones completas de Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
