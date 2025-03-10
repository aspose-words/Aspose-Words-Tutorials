---
title: Reiniciar numeración de páginas
linktitle: Reiniciar numeración de páginas
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a reiniciar la numeración de páginas al unir y adjuntar documentos de Word usando Aspose.Words para .NET.
weight: 10
url: /es/net/join-and-append-documents/restart-page-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reiniciar numeración de páginas

## Introducción

¿Alguna vez ha tenido problemas para crear un documento pulido con secciones diferenciadas, cada una comenzando con la página número 1? Imagine un informe en el que los capítulos comienzan de nuevo, o una propuesta extensa con secciones separadas para el resumen ejecutivo y los apéndices detallados. Aspose.Words para .NET, una potente biblioteca de procesamiento de documentos, le permite lograr esto con delicadeza. Esta guía completa le revelará los secretos para reiniciar la numeración de páginas, lo que le permitirá crear documentos de aspecto profesional sin esfuerzo.

## Prerrequisitos

Antes de emprender este viaje, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: Descargue la biblioteca desde el sitio web oficial[Enlace de descarga](https://releases.aspose.com/words/net/) Puedes explorar una prueba gratuita[Enlace de prueba gratuito](https://releases.aspose.com/) o comprar una licencia[Enlace de compra](https://purchase.aspose.com/buy) Basado en sus necesidades.
2. Entorno de desarrollo AC#: Visual Studio o cualquier entorno que admita el desarrollo .NET funcionará perfectamente.
3. Un documento de muestra: busque un documento de Word con el que desea experimentar.

## Importación de espacios de nombres esenciales

Para interactuar con los objetos y las funcionalidades de Aspose.Words, necesitamos importar los espacios de nombres necesarios. A continuación, se explica cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Settings;
```

 Este fragmento de código importa el`Aspose.Words` espacio de nombres, que proporciona acceso a las clases de manipulación de documentos principales. Además, importamos el`Aspose.Words.Settings` espacio de nombres, que ofrece opciones para personalizar el comportamiento del documento.


Ahora, profundicemos en los pasos prácticos necesarios para reiniciar la numeración de páginas dentro de sus documentos:

## Paso 1: Cargue los documentos de origen y destino:

Definir una variable de cadena`dataDir` Para almacenar la ruta al directorio de su documento. Reemplace "DIRECTORIO DE SU DOCUMENTO" con la ubicación real.

 Crea dos`Document` objetos que utilizan el`Aspose.Words.Document` constructor. El primero (`srcDoc`) contendrá el documento fuente que contiene el contenido que se va a adjuntar. El segundo (`dstDoc`) representa el documento de destino donde integraremos el contenido de origen con la numeración de páginas reiniciada.

```csharp
string dataDir = @"C:\MyDocuments\"; // Reemplazar con su directorio actual
Document srcDoc = new Document(dataDir + "source.docx");
Document dstDoc = new Document(dataDir + "destination.docx");
```

## Paso 2: Configurar el salto de sección:

 Acceder a la`FirstSection` propiedad del documento fuente (`srcDoc`) para manipular la sección inicial. Se reiniciará la numeración de páginas de esta sección.

 Utilice el`PageSetup` propiedad de la sección para configurar su comportamiento de diseño.

 Establecer el`SectionStart` propiedad de`PageSetup` a`SectionStart.NewPage`Esto garantiza que se cree una nueva página antes de que el contenido de origen se agregue al documento de destino.

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.NewPage;
```

## Paso 3: Habilitar el reinicio de la numeración de páginas:

 Dentro del mismo`PageSetup` objeto de la primera sección del documento fuente, establezca el`RestartPageNumbering`propiedad a`true`Este paso crucial le indica a Aspose.Words que inicie nuevamente la numeración de páginas para el contenido adjunto.

```csharp
srcDoc.FirstSection.PageSetup.RestartPageNumbering = true;
```

## Paso 4: Anexar el documento fuente:

Ahora que el documento de origen está preparado con la configuración de numeración y salto de página deseada, es momento de integrarlo en el documento de destino.

 Emplea el`AppendDocument` método del documento de destino (`dstDoc`) para agregar sin problemas el contenido de origen.

Pase el documento fuente (`srcDoc` ) y un`ImportFormatMode.KeepSourceFormatting` argumento de este método. Este argumento conserva el formato original del documento fuente cuando se adjunta.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Paso 5: Guardar el documento final:

 Por último, utilice el`Save` método del documento de destino (`dstDoc`) para almacenar el documento combinado con la numeración de páginas reiniciada. Especifique un nombre de archivo y una ubicación adecuados para el documento guardado.

```csharp
dstDoc.Save(dataDir + "final_document.docx");
```

## Conclusión

En conclusión, dominar los saltos de página y la numeración en Aspose.Words para .NET le permitirá crear documentos pulidos y bien estructurados. Al implementar las técnicas descritas en esta guía, podrá integrar sin problemas el contenido con la numeración de páginas reiniciada, lo que garantizará una presentación profesional y fácil de leer. Recuerde que Aspose.Words ofrece una gran cantidad de funciones adicionales para la manipulación de documentos.

## Preguntas frecuentes

### ¿Puedo reiniciar la numeración de páginas en medio de una sección?

 Lamentablemente, Aspose.Words para .NET no admite directamente el reinicio de la numeración de páginas dentro de una sola sección. Sin embargo, puede lograr un efecto similar creando una nueva sección en el punto deseado y configurando`RestartPageNumbering` a`true` para esa sección.

### ¿Cómo puedo personalizar el número de página de inicio después de un reinicio?

 Si bien el código proporcionado inicia la numeración desde 1, puede personalizarlo. Utilice el`PageNumber` propiedad de la`HeaderFooter` objeto dentro de la nueva sección. Al configurar esta propiedad, podrá definir el número de página inicial.

### ¿Qué sucede con los números de página existentes en el documento fuente?

Los números de página existentes en el documento de origen no se verán afectados. Solo se reiniciará la numeración del contenido añadido en el documento de destino.

### ¿Puedo aplicar diferentes formatos de numeración (por ejemplo, números romanos)?

 ¡Por supuesto! Aspose.Words ofrece un amplio control sobre los formatos de numeración de páginas. Explore`NumberStyle` propiedad de la`HeaderFooter` objeto para elegir entre varios estilos de numeración como números romanos, letras o formatos personalizados.

### ¿Dónde puedo encontrar más recursos o ayuda?

 Aspose ofrece un portal de documentación completo[Enlace de documentación](https://reference.aspose.com/words/net/) que profundiza en las funciones de numeración de páginas y otras características de Aspose.Words. Además, su foro activo[Enlace de soporte](https://forum.aspose.com/c/words/8) Es una gran plataforma para conectarse con la comunidad de desarrolladores y buscar ayuda con desafíos específicos.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
