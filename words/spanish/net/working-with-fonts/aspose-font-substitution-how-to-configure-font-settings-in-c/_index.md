---
category: general
date: 2026-03-27
description: 'Sustitución de fuentes Aspose fácil: aprenda a configurar los ajustes
  de fuentes, capturar advertencias y manejar fuentes faltantes en sus aplicaciones
  .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: es
og_description: Domina la sustitución de fuentes de Aspose configurando la configuración
  de fuentes y manejando fuentes faltantes con una devolución de llamada de advertencia.
  Guía completa de C#.
og_title: Sustitución de fuentes Aspose – Configurar ajustes de fuentes en C#
tags:
- Aspose.Words
- C#
- Font Management
title: Sustitución de fuentes Aspose – Cómo configurar la configuración de fuentes
  en C#
url: /es/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sustitución de fuentes Aspose – Guía completa para configurar la configuración de fuentes

¿Alguna vez te has encontrado con un documento que de repente cambia tu tipografía personalizada por algo genérico? Eso es **aspose font substitution** haciendo su trabajo—reemplazando fuentes faltantes con la coincidencia más cercana que puede encontrar. Es útil, pero si necesitas saber *exactamente* qué fuente se sustituyó, debes acceder al sistema de advertencias de la biblioteca y configurar la configuración de fuentes tú mismo.

En este tutorial recorreremos un escenario del mundo real: cargar un DOCX que hace referencia a una fuente que no tienes, capturar el evento de sustitución y imprimir un mensaje amigable en la consola. Al final estarás cómodo con **configure font settings**, configurando un **Aspose.Words warning callback**, y ampliando el ejemplo para adaptarlo a cualquier flujo de trabajo.

> **Lo que necesitarás**  
> • .NET 6+ (o .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (último NuGet)  
> • Un DOCX que haga referencia a una fuente faltante (lo llamaremos `MissingFont.docx`)  

¡Vamos a sumergirnos!

---

## Paso 1: Instalar Aspose.Words y preparar el proyecto

Antes de escribir cualquier código, asegúrate de que el paquete Aspose.Words esté referenciado:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Usa la última versión estable; a partir de marzo 2026 es 23.11.0. Las versiones más recientes mejoran los algoritmos de coincidencia de fuentes y añaden tipos de advertencia adicionales.

Crea una nueva aplicación de consola (o inserta el código en un proyecto existente) y agrega las directivas `using` habituales:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Estos espacios de nombres nos dan acceso a `Document`, `LoadOptions` y a las clases relacionadas con fuentes que necesitaremos.

---

## Paso 2: Configurar Font Settings con LoadOptions

El corazón del control de **aspose font substitution** vive en `LoadOptions.FontSettings`. Al proporcionar un objeto `FontSettings` vacío le decimos a Aspose que use sus rutas de búsqueda predeterminadas *y* que informe cualquier sustitución mediante una callback de advertencia.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

¿Por qué no confiar solo en los valores predeterminados? Porque adjuntar una callback de advertencia (paso siguiente) solo funciona cuando la propiedad `FontSettings` no es nula. Esta pequeña línea nos brinda un punto de enganche en el proceso de sustitución sin cambiar el comportamiento real de búsqueda de fuentes.

---

## Paso 3: Adjuntar una callback de advertencia para capturar sustituciones

Aspose.Words implementa la interfaz `IWarningCallback`. Cada vez que ocurre algo notable—como una fuente faltante—llama a nuestro método `Warning`. Implementaremos un manejador pequeño que filtre `WarningType.FontSubstitution` y muestre la descripción.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Y aquí está el manejador propiamente dicho:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Por qué es importante** – Sin la callback, Aspose sustituye fuentes silenciosamente y nunca sabrás cuál se utilizó. La callback hace el proceso transparente, lo cual es esencial para informes de cumplimiento o para depurar problemas de maquetación.

---

## Paso 4: Cargar el documento usando las opciones configuradas

Ahora finalmente cargamos el documento, pasando el `loadOptions` que acabamos de preparar. Si el archivo fuente hace referencia a una fuente que no está instalada, nuestro manejador se activará.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Reemplaza `YOUR_DIRECTORY` con la ruta real donde se encuentra `MissingFont.docx`. Cuando ejecutes el programa, deberías ver una salida similar a:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Esa línea te indica exactamente qué fuente faltaba y qué fuente de respaldo eligió Aspose.

---

## Paso 5: (Opcional) Ajustar finamente las rutas de búsqueda de fuentes

Si dispones de una carpeta privada con fuentes corporativas, puedes indicarle a Aspose dónde buscar antes de que recurra a las fuentes del sistema. Este es un uso avanzado de **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Establecer `recursive: true` hace que Aspose escanee también las subcarpetas. Ahora la biblioteca intentará primero tus fuentes privadas, reduciendo la probabilidad de sustituciones no deseadas.

---

## Ejemplo completo y funcional

Juntando todo, aquí tienes el programa completo, listo para ejecutarse:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Salida esperada** (cuando se encuentre una fuente faltante):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Si todas las fuentes están presentes, el programa se ejecuta silenciosamente (sin advertencias) y aún así genera el PDF.

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito *evitar* la sustitución por completo?

Establece `FontSettings.SubstitutionSettings` a `null` o usa `FontSettings.FontSubstitutionSettings` para controlar el comportamiento. Por ejemplo:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Ahora Aspose lanzará una excepción en lugar de sustituir silenciosamente, la cual puedes capturar y manejar.

### ¿Esto funciona con otros formatos de archivo (p. ej., .doc, .rtf)?

Absolutamente. El mismo objeto `LoadOptions` puede pasarse a cualquier constructor de `Document` que acepte una ruta de archivo. La callback de advertencia se activará para todos los formatos que dependan de fuentes.

### ¿Puedo capturar el nombre exacto de la fuente de respaldo?

Sí. La cadena `info.Description` contiene tanto la fuente faltante como la de reemplazo. Si necesitas el nombre programáticamente, puedes analizarla o usar el objeto `FontInfo` (disponible en versiones más recientes).

### ¿Cómo se comporta esto en un entorno multihilo?

`FontSettings` **no** es seguro para hilos. Crea un `LoadOptions` separado (con su propio `FontSettings`) por hilo, o protege el acceso con un bloqueo (`lock`).

---

## Conclusión

Hemos cubierto todo lo que necesitas para dominar **aspose font substitution** y **configure font settings** en una aplicación C#:

1. Instala Aspose.Words y agrega las declaraciones `using` necesarias.  
2. Crea un objeto `LoadOptions` con un `FontSettings` nuevo.  
3. Adjunta un `IWarningCallback` personalizado para exponer los eventos de sustitución.  
4. Carga el documento, dejando que la callback informe cualquier fuente faltante.  
5. (Opcional) Amplía la ruta de búsqueda o desactiva la sustitución por completo.

Con este patrón puedes registrar fuentes faltantes para cumplimiento, alertar a los usuarios en una UI, o incrustar automáticamente fuentes de respaldo antes de publicar. A continuación, podrías explorar **políticas de sustitución de fuentes de Aspose.Words** o integrar el flujo de trabajo en una canalización de procesamiento de documentos más grande.

¡Feliz codificación, y que tus documentos siempre se rendericen con la tipografía correcta!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}