---
"description": "Aprenda a actualizar la propiedad \"Última hora guardada\" en documentos de Word con Aspose.Words para .NET. Siga nuestra guía detallada paso a paso."
"linktitle": "Actualizar la última propiedad guardada"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Actualizar la última propiedad guardada"
"url": "/es/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Actualizar la última propiedad guardada

## Introducción

¿Alguna vez te has preguntado cómo controlar la propiedad "Última hora guardada" en tus documentos de Word mediante programación? Si trabajas con varios documentos y necesitas mantener sus metadatos, actualizar la propiedad "Última hora guardada" puede ser muy práctico. Hoy te guiaré en este proceso usando Aspose.Words para .NET. ¡Prepárate y adentrémonos en el tema!

## Prerrequisitos

Antes de pasar a la guía paso a paso, hay algunas cosas que necesitarás:

1. Aspose.Words para .NET: Asegúrate de tener Aspose.Words para .NET instalado. Si no lo tienes, puedes... [Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: Un entorno de desarrollo como Visual Studio.
3. Conocimientos básicos de C#: será útil comprender los conceptos básicos de la programación en C#.

## Importar espacios de nombres

Para empezar, asegúrese de importar los espacios de nombres necesarios a su proyecto. Esto le permitirá acceder a las clases y métodos necesarios para manipular documentos de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ahora, desglosemos el proceso en pasos sencillos. Cada paso le guiará en el proceso de actualizar la propiedad "Última hora guardada" en su documento de Word.

## Paso 1: Configure su directorio de documentos

Primero, debe especificar la ruta al directorio de su documento. Aquí se almacena el documento existente y se guardará el documento actualizado.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real a su directorio.

## Paso 2: Cargue su documento de Word

A continuación, cargue el documento de Word que desea actualizar. Puede hacerlo creando una instancia del archivo `Document` clase y pasando la ruta de su documento.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Asegúrese de que el documento nombrado `Document.docx` está presente en el directorio especificado.

## Paso 3: Configurar las opciones de guardado

Ahora, crea una instancia de la `OoxmlSaveOptions` Esta clase le permite especificar opciones para guardar su documento en formato Office Open XML (OOXML). Aquí, configurará `UpdateLastSavedTimeProperty` a `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Esto le dice a Aspose.Words que actualice la propiedad de la última hora de guardado del documento.

## Paso 4: Guardar el documento actualizado

Por último, guarde el documento utilizando el `Save` método de la `Document` clase, pasando la ruta donde desea guardar el documento actualizado y las opciones de guardado.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Esto guardará el documento con la propiedad de hora de último guardado actualizada.

## Conclusión

¡Listo! Siguiendo estos pasos, puedes actualizar fácilmente la propiedad "Última hora guardada" de tus documentos de Word con Aspose.Words para .NET. Esto es especialmente útil para mantener la precisión de los metadatos en tus documentos, lo cual puede ser crucial para los sistemas de gestión documental y otras aplicaciones.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca para crear, editar y convertir documentos de Word en aplicaciones .NET.

### ¿Por qué debería actualizar la propiedad de la última hora guardada?
Actualizar la propiedad de la última hora guardada ayuda a mantener metadatos precisos, lo cual es esencial para el seguimiento y la gestión de documentos.

### ¿Puedo actualizar otras propiedades usando Aspose.Words para .NET?
Sí, Aspose.Words para .NET le permite actualizar varias propiedades del documento, como título, autor y asunto.

### ¿Aspose.Words para .NET es gratuito?
Aspose.Words para .NET ofrece una prueba gratuita, pero para disfrutar de todas sus funciones, se requiere una licencia. Puede obtener una licencia. [aquí](https://purchase.aspose.com/buy).

### ¿Dónde puedo encontrar más tutoriales sobre Aspose.Words para .NET?
Puede encontrar más tutoriales y documentación [aquí](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}