---
category: general
date: 2025-12-29
description: Las opciones de carga de Aspose permiten cargar archivos DOCX personalizando
  la configuración de fuentes y detectando fuentes faltantes. Aprende cómo cargar
  docx con control total.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: es
og_description: Las opciones de carga de Aspose le permiten cargar archivos DOCX mientras
  personaliza la configuración de fuentes y detecta fuentes faltantes. Aprenda cómo
  cargar docx con control total.
og_title: Opciones de carga de Aspose – Cargar DOCX con configuraciones de fuente
  personalizadas
tags:
- Aspose.Words
- C#
- Document Processing
title: Opciones de carga de Aspose – Cargar DOCX con configuraciones de fuente personalizadas
url: /es/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opciones de carga de Aspose – Cargar DOCX con configuración de fuentes personalizada

¿Alguna vez te has preguntado cómo cargar un archivo DOCX en C# sin tropezar con fuentes faltantes? No estás solo. **Aspose Load Options** te brinda el poder de controlar exactamente cómo se abre un documento Word, permitiéndote establecer configuraciones de fuentes personalizadas e incluso detectar fuentes faltantes antes de que se conviertan en un problema.

En este tutorial recorreremos todo el proceso de cargar un DOCX usando Aspose.Words, configurando **configuraciones de fuentes personalizadas**, y conectando una devolución de llamada de advertencia que te indica qué fuentes faltan. Al final podrás **cargar documentos Word** con confianza, sin importar qué fuentes haya usado el autor original.

> **Prerequisite** – Necesitas Aspose.Words para .NET (última versión) referenciado en tu proyecto y un conocimiento básico de C#. No se requieren otras bibliotecas.

## Lo que aprenderás

- Cómo crear un objeto `LoadOptions` y adjuntar una devolución de llamada de advertencia.  
- Cómo configurar `FontSettings` para **configuraciones de fuentes personalizadas**.  
- Cómo **cargar docx** y verificar que se informen las fuentes faltantes.  
- Consejos para manejar casos límite como fuentes incrustadas o carpetas de fuentes basadas en red.

## Paso 1: Instalar Aspose.Words y preparar el proyecto

Lo primero, asegúrate de que Aspose.Words esté instalado. La forma más fácil es a través de NuGet:

```bash
dotnet add package Aspose.Words
```

Una vez añadido el paquete, crea un nuevo proyecto de consola C# (o inserta el código en cualquier aplicación existente). El código que escribiremos funciona con .NET 6+ y .NET Framework 4.7.2+, así que estarás cubierto en ambos casos.

> **Pro tip:** Si estás apuntando a .NET Core, agrega `using System;` al inicio del archivo; el IDE normalmente lo insertará automáticamente.

## Paso 2: Configurar Aspose Load Options con una devolución de llamada de advertencia

Ahora llegamos al corazón del asunto—**aspose load options**. La clase `LoadOptions` te permite ajustar cómo se analiza un documento. La usaremos para:

1. Adjuntar una devolución de llamada que se dispara cada vez que el cargador no puede encontrar una fuente solicitada.  
2. Asignar una instancia de `FontSettings` que luego podrá ajustarse para **configuraciones de fuentes personalizadas**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Por qué es importante:** Sin una devolución de llamada de advertencia, Aspose sustituye silenciosamente las fuentes faltantes, lo que puede provocar sorpresas de maquetación más adelante. Al engancharte a la devolución de llamada, **detectas fuentes faltantes** temprano y puedes decidir si incrustar una alternativa o pedir al usuario que instale la tipografía ausente.

## Paso 3: Cargar el DOCX usando las opciones configuradas

Con el `LoadOptions` listo, cargar un DOCX es una sola línea. El constructor `Document` acepta la ruta al archivo y las opciones que acabamos de crear.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Si el archivo fuente hace referencia a una fuente que no está en el sistema o en la carpeta personalizada, verás una salida como:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Esa retroalimentación inmediata es invaluable cuando construyes una canalización de procesamiento por lotes que debe garantizar la fidelidad visual.

## Paso 4: Verificar el documento cargado (opcional pero útil)

Después de cargar, puede que quieras confirmar que el contenido del documento es accesible. Para una rápida comprobación, imprimamos el texto del primer párrafo.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Ejecutar el programa ahora muestra:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Paso 5: Casos límite y consejos avanzados

### 5.1 Manejo de fuentes incrustadas

Algunos archivos DOCX incrustan las fuentes requeridas directamente. Aspose.Words las usa automáticamente, por lo que no verás advertencias para ellas. Sin embargo, si deliberadamente **cargas documentos Word** que eliminan fuentes incrustadas (p. ej., después de una conversión), puede que necesites proporcionar las fuentes faltantes mediante `SetFontsFolder` como se mostró antes.

### 5.2 Usar un Memory Stream en lugar de una ruta de archivo

Si tu DOCX está en una base de datos o proviene de una solicitud HTTP, puedes cargarlo desde un `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Las mismas **aspose load options** se aplican, y la devolución de llamada de advertencia sigue funcionando.

### 5.3 Sobrescribir la sustitución de fuentes globalmente

Si prefieres reemplazar fuentes faltantes con una alternativa específica (por ejemplo, Arial), puedes añadir una regla de sustitución:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Combínalo con la devolución de llamada de advertencia para registrar el evento de sustitución y mantener tu salida consistente.

## Paso 6: Ejemplo completo funcional

A continuación tienes el programa completo, listo para copiar y pegar, que incorpora todos los pasos anteriores. Guárdalo como `Program.cs`, restaura los paquetes NuGet y ejecútalo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Salida esperada

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Si no faltan fuentes, las líneas de advertencia simplemente no aparecerán.

## Visión general visual

![ejemplo de opciones de carga de aspose](/images/aspose-load-options.png "Diagrama que muestra el flujo de trabajo de Aspose Load Options")

*El diagrama ilustra cómo **Aspose Load Options** se sitúan entre la fuente de tu archivo y el objeto `Document`, gestionando la resolución de fuentes y la detección de fuentes faltantes.*

## Conclusión

Hemos recorrido una solución completa para **aspose load options**, mostrándote exactamente **cómo cargar docx** mientras aplicas **configuraciones de fuentes personalizadas** y **detectas fuentes faltantes**. Al configurar una devolución de llamada de advertencia y, opcionalmente, apuntar a una carpeta de fuentes personalizada, obtienes total visibilidad sobre los problemas de fuentes antes de que afecten el renderizado.  

A partir de aquí puedes explorar temas relacionados como la conversión de **cargar documentos Word** a PDF, añadir marcas de agua, o procesar por lotes docenas de archivos en una carpeta. El mismo patrón—crear `LoadOptions`, adjuntar devoluciones de llamada y llamar a `new Document(...)`—funciona en toda la API de Aspose.Words.

¿Tienes preguntas sobre un caso límite específico, como el manejo de idiomas de derecha a izquierda o archivos DOCX cifrados? Deja un comentario o consulta la documentación de Aspose.Words para profundizar. ¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como deseas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}