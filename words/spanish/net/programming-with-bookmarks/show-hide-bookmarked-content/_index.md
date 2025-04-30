---
"description": "Aprenda a mostrar y ocultar contenido marcado en documentos de Word usando Aspose.Words para .NET con esta guía detallada paso a paso."
"linktitle": "Mostrar y ocultar contenido marcado en un documento de Word"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Mostrar y ocultar contenido marcado en un documento de Word"
"url": "/es/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mostrar y ocultar contenido marcado en un documento de Word

## Introducción

¿Listo para sumergirte en el mundo de la manipulación de documentos con Aspose.Words para .NET? Tanto si eres desarrollador y buscas automatizar tareas con documentos como si simplemente te interesa la gestión programática de archivos de Word, estás en el lugar adecuado. Hoy exploraremos cómo mostrar y ocultar contenido marcado en un documento de Word con Aspose.Words para .NET. Esta guía paso a paso te convertirá en un experto en el control de la visibilidad del contenido mediante marcadores. ¡Comencemos!

## Prerrequisitos

Antes de entrar en materia, hay algunas cosas que necesitarás:

1. Visual Studio: Cualquier versión compatible con .NET.
2. Aspose.Words para .NET: Descárgalo [aquí](https://releases.aspose.com/words/net/).
3. Comprensión básica de C#: si puedes escribir un programa simple "Hola mundo", estás listo para comenzar.
4. Un documento de Word con marcadores: utilizaremos un documento de muestra con marcadores para este tutorial.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios. Esto nos asegura tener todas las herramientas necesarias para nuestra tarea.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Con estos espacios de nombres en su lugar, estamos todos listos para comenzar nuestro viaje.

## Paso 1: Configuración de su proyecto

Muy bien, comencemos configurando nuestro proyecto en Visual Studio.

### Crear un nuevo proyecto

Abra Visual Studio y cree un proyecto de aplicación de consola (.NET Core). Llámelo con un nombre llamativo, como "BookmarkVisibilityManager".

### Añadir Aspose.Words para .NET

Necesitarás agregar Aspose.Words para .NET a tu proyecto. Puedes hacerlo mediante el Administrador de paquetes NuGet.

1. Vaya a Herramientas > Administrador de paquetes NuGet > Administrar paquetes NuGet para la solución.
2. Busca "Aspose.Words".
3. Instalar el paquete.

¡Genial! Ahora que nuestro proyecto está configurado, procedamos a cargar nuestro documento.

## Paso 2: Carga del documento

Necesitamos cargar el documento de Word que contiene los marcadores. Para este tutorial, usaremos un documento de ejemplo llamado "Bookmarks.docx".

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Este fragmento de código establece la ruta al directorio de su documento y carga el documento en el `doc` objeto.

## Paso 3: Mostrar/ocultar contenido marcado

Ahora viene la parte divertida: mostrar u ocultar el contenido según los marcadores. Crearemos un método llamado `ShowHideBookmarkedContent` Para manejar esto.

Este es el método que alternará la visibilidad del contenido marcado:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Desglose del método

- Recuperación de marcadores: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` recupera el marcador
- Recorrido de nodos: recorremos los nodos dentro del marcador.
- Alternar visibilidad: si el nodo es un `Run` (una serie de texto contiguos), lo configuramos `Hidden` propiedad.

## Paso 4: Aplicación del método

Con nuestro método en funcionamiento, apliquémoslo para mostrar u ocultar contenido según un marcador.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Esta línea de código ocultará el contenido dentro del marcador llamado "MyBookmark1".

## Paso 5: Guardar el documento

Por último, guardemos nuestro documento modificado.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Esto guarda el documento con los cambios que hemos realizado.

## Conclusión

¡Y listo! Acabas de aprender a mostrar y ocultar el contenido marcado en un documento de Word con Aspose.Words para .NET. Esta potente herramienta facilita la manipulación de documentos, ya sea para automatizar informes, crear plantillas o simplemente modificar archivos de Word. ¡Que disfrutes programando!

## Preguntas frecuentes

### ¿Puedo alternar entre varios marcadores a la vez?
Sí, puedes llamar al `ShowHideBookmarkedContent` método para cada marcador que desee alternar.

### ¿Ocultar contenido afecta la estructura del documento?
No, ocultar contenido solo afecta su visibilidad. El contenido permanece en el documento.

### ¿Puedo utilizar este método para otros tipos de contenido?
Este método activa y desactiva específicamente las ejecuciones de texto. Para otros tipos de contenido, deberá modificar la lógica de recorrido del nodo.

### ¿Aspose.Words para .NET es gratuito?
Aspose.Words ofrece una prueba gratuita [aquí](https://releases.aspose.com/), pero se requiere una licencia completa para su uso en producción. Puedes adquirirla. [aquí](https://purchase.aspose.com/buy).

### ¿Cómo puedo obtener ayuda si encuentro problemas?
Puede obtener soporte de la comunidad Aspose [aquí](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}