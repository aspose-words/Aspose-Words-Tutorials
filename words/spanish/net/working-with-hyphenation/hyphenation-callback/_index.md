---
"description": "Aprenda a implementar la devolución de llamada de separación de palabras en Aspose.Words para .NET para mejorar el formato del documento con esta completa guía paso a paso."
"linktitle": "Devolución de llamada de separación de palabras"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Devolución de llamada de separación de palabras"
"url": "/es/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Devolución de llamada de separación de palabras


## Introducción

¡Hola! ¿Alguna vez te has encontrado con las complejidades del formato de texto, especialmente al trabajar con idiomas que requieren separación de palabras? No estás solo. La separación de palabras, aunque crucial para un diseño de texto adecuado, puede ser un poco complicada. ¿Pero sabes qué? Aspose.Words para .NET te cubre las espaldas. Esta potente biblioteca te permite gestionar el formato de texto sin problemas, incluyendo la gestión de la separación de palabras mediante un mecanismo de devolución de llamada. ¿Te intriga? Profundicemos en los detalles de cómo puedes implementar una devolución de llamada de separación de palabras con Aspose.Words para .NET.

## Prerrequisitos

Antes de ponernos manos a la obra con el código, asegurémonos de que tienes todo lo que necesitas:

1. Aspose.Words para .NET: Asegúrate de tener la biblioteca. Puedes... [Descárgalo aquí](https://releases.aspose.com/words/net/).
2. IDE: Un entorno de desarrollo como Visual Studio.
3. Conocimientos básicos de C#: comprensión de C# y .NET Framework.
4. Diccionarios de separación de palabras: diccionarios de separación de palabras para los idiomas que planea utilizar.
5. Licencia Aspose: Una licencia Aspose válida. Puede obtener una [licencia temporal](https://purchase.aspose.com/temporary-license/) Si no tienes uno.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios. Esto garantiza que nuestro código tenga acceso a todas las clases y métodos necesarios de Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Paso 1: Registrar la devolución de llamada de separación de palabras

Para empezar, necesitamos registrar nuestra llamada de separación de palabras. Aquí es donde le indicamos a Aspose.Words que use nuestra lógica de separación de palabras personalizada.

```csharp
try
{
    // Registrar la devolución de llamada de separación de palabras.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Aquí, estamos creando una instancia de nuestra devolución de llamada personalizada y asignándola a `Hyphenation.Callback`.

## Paso 2: Definir la ruta del documento

A continuación, debemos definir el directorio donde se almacenan nuestros documentos. Esto es crucial, ya que cargaremos y guardaremos documentos desde esta ruta.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real a sus documentos.

## Paso 3: Cargar el documento

Ahora, carguemos el documento que requiere separación de palabras.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Aquí estamos cargando un documento de texto en alemán. Puedes reemplazar `"German text.docx"` con el nombre de archivo de su documento.

## Paso 4: Guardar el documento

Después de cargar el documento, lo guardamos en un nuevo archivo, aplicando la devolución de llamada de separación de palabras en el proceso.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Esta línea guarda el documento como PDF con separación de palabras aplicada.

## Paso 5: Manejar la excepción del diccionario de separación de palabras faltante

A veces, puede que te encuentres con un problema de falta del diccionario de separación de palabras. Vamos a solucionarlo.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

En este bloque, capturamos la excepción específica relacionada con los diccionarios faltantes e imprimimos el mensaje.

## Paso 6: Implementar la clase de devolución de llamada de separación de palabras personalizada

Ahora, vamos a implementar el `CustomHyphenationCallback` clase que maneja la solicitud de diccionarios de separación de palabras.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Registrar diccionario para el idioma solicitado.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

En esta clase, el `RequestDictionary` Este método se llama siempre que se necesita un diccionario de separación de palabras. Comprueba el idioma y registra el diccionario apropiado.

## Conclusión

¡Y listo! Acabas de aprender a implementar una función de callback de separación de palabras en Aspose.Words para .NET. Siguiendo estos pasos, puedes asegurarte de que tus documentos tengan un formato perfecto, independientemente del idioma. Ya sea que trabajes con inglés, alemán o cualquier otro idioma, este método te permite gestionar la separación de palabras sin esfuerzo.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una poderosa biblioteca de manipulación de documentos que permite a los desarrolladores crear, modificar y convertir documentos mediante programación.

### ¿Por qué es importante la separación de palabras en el formato de un documento?
La separación de palabras mejora el diseño del texto al dividir las palabras en los lugares apropiados, lo que garantiza un documento más legible y visualmente atractivo.

### ¿Puedo utilizar Aspose.Words gratis?
Aspose.Words ofrece una prueba gratuita. Puedes obtenerla. [aquí](https://releases.aspose.com/).

### ¿Cómo puedo obtener un diccionario de separación de palabras?
Puede descargar diccionarios de separación de palabras de varios recursos en línea o crear el suyo propio si es necesario.

### ¿Qué pasa si falta un diccionario de separación de palabras?
Si falta un diccionario, el `RequestDictionary` El método lanza una excepción, que puedes manejar para informar al usuario o proporcionar una alternativa.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}