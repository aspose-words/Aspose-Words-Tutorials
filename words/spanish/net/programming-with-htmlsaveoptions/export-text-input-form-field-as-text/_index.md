---
"description": "Aprenda a exportar campos de formulario de entrada de texto como texto simple usando Aspose.Words para .NET con esta completa guía paso a paso."
"linktitle": "Exportar campo de formulario de entrada de texto como texto"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Exportar campo de formulario de entrada de texto como texto"
"url": "/es/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportar campo de formulario de entrada de texto como texto

## Introducción

¿Te estás adentrando en el mundo de Aspose.Words para .NET? ¡Una elección fantástica! Si quieres aprender a exportar un campo de formulario de entrada de texto como texto, estás en el lugar indicado. Tanto si estás empezando como si estás perfeccionando tus habilidades, esta guía te explicará todo lo que necesitas saber. ¡Comencemos!

## Prerrequisitos

Antes de profundizar en los detalles, asegurémonos de que tienes todo lo que necesitas para seguir sin problemas:

- Aspose.Words para .NET: Descargue e instale la última versión desde [aquí](https://releases.aspose.com/words/net/).
- IDE: Visual Studio o cualquier entorno de desarrollo C#.
- Conocimientos básicos de C#: comprensión de la sintaxis básica de C# y conceptos de programación orientada a objetos.
- Documento: Un documento de Word de muestra (`Rendering.docx`) con campos de formulario de entrada de texto.

## Importar espacios de nombres

Primero, debes importar los espacios de nombres necesarios. Estos son los componentes básicos que hacen que todo funcione a la perfección.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Bien, ahora que tenemos nuestros espacios de nombres listos, ¡pasemos a la acción!

## Paso 1: Configurar el proyecto

Antes de entrar en el código, asegurémonos de que nuestro proyecto esté configurado correctamente.

## Creando el Proyecto

1. Abra Visual Studio: comience abriendo Visual Studio o su entorno de desarrollo de C# preferido.
2. Crear un nuevo proyecto: navegue a `File > New > Project`Seleccionar `Console App (.NET Core)` o cualquier otro tipo de proyecto relevante.
3. Nombre su proyecto: Dele a su proyecto un nombre significativo, algo como `AsposeWordsExportExample`.

## Añadiendo Aspose.Words

1. Administrar paquetes NuGet: haga clic derecho en su proyecto en el Explorador de soluciones y seleccione `Manage NuGet Packages`.
2. Busque Aspose.Words: en el Administrador de paquetes NuGet, busque `Aspose.Words`.
3. Instalar Aspose.Words: Haga clic en `Install` para agregar la biblioteca Aspose.Words a su proyecto.

## Paso 2: Cargue el documento de Word

Ahora que nuestro proyecto está configurado, carguemos el documento de Word que contiene los campos del formulario de ingreso de texto.

1. Especificar el directorio del documento: defina la ruta al directorio donde se almacena su documento.
2. Cargar el documento: utilice el `Document` clase para cargar su documento de Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 3: Preparar el directorio de exportación

Antes de exportar, asegurémonos de que nuestro directorio de exportación esté listo. Aquí se guardarán nuestro archivo HTML y las imágenes.

1. Definir el directorio de exportación: especifique la ruta donde se guardarán los archivos exportados.
2. Comprobar y limpiar el directorio: asegúrese de que el directorio exista y esté vacío.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Paso 4: Configurar las opciones de guardado

Aquí es donde ocurre la magia. Necesitamos configurar nuestras opciones de guardado para exportar el campo de entrada de texto como texto sin formato.

1. Crear opciones de guardado: Inicializar un nuevo `HtmlSaveOptions` objeto.
2. Establecer la opción de exportación de texto: configurar la `ExportTextInputFormFieldAsText` propiedad a `true`.
3. Establecer carpeta de imágenes: define la carpeta donde se guardarán las imágenes.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Paso 5: Guardar el documento como HTML

Por último, guardemos el documento de Word como un archivo HTML utilizando nuestras opciones de guardado configuradas.

1. Definir la ruta de salida: especifique la ruta donde se guardará el archivo HTML.
2. Guardar el documento: utilice el `Save` método de la `Document` clase para exportar el documento.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusión

¡Listo! Has exportado correctamente un campo de formulario de entrada de texto como texto sin formato con Aspose.Words para .NET. Esta guía te habrá proporcionado un método claro y paso a paso para lograrlo. Recuerda: la práctica hace al maestro, así que sigue experimentando con diferentes opciones y configuraciones para descubrir qué más puedes hacer con Aspose.Words.

## Preguntas frecuentes

### ¿Puedo exportar otros tipos de campos de formulario utilizando el mismo método?

Sí, puede exportar otros tipos de campos de formulario configurando diferentes propiedades del formulario. `HtmlSaveOptions` clase.

### ¿Qué pasa si mi documento tiene imágenes?

Las imágenes se guardarán en la carpeta de imágenes especificada. Asegúrese de configurar la `ImagesFolder` propiedad en el `HtmlSaveOptions`.

### ¿Necesito una licencia para Aspose.Words?

Sí, puedes obtener una prueba gratuita [aquí](https://releases.aspose.com/) o comprar una licencia [aquí](https://purchase.aspose.com/buy).

### ¿Puedo personalizar el HTML exportado?

¡Por supuesto! Aspose.Words ofrece varias opciones para personalizar la salida HTML. Consulta la [documentación](https://reference.aspose.com/words/net/) Para más detalles.

### ¿Es Aspose.Words compatible con .NET Core?

Sí, Aspose.Words es compatible con .NET Core, .NET Framework y otras plataformas .NET.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}