---
category: general
date: 2026-04-02
description: Cómo detectar fuentes en documentos C# usando Aspose.Words. Aprende a
  configurar la configuración de fuentes y manejar fuentes faltantes de manera eficiente.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: es
og_description: Cómo detectar fuentes en documentos C# usando Aspose.Words. Esta guía
  le muestra cómo configurar la configuración de fuentes y manejar fuentes faltantes.
og_title: Cómo detectar fuentes en C# – Guía completa
tags:
- C#
- Aspose.Words
- Document Processing
title: Cómo detectar fuentes en C# – Guía completa
url: /es/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar fuentes en C# – Guía completa

¿Alguna vez te has preguntado **cómo detectar fuentes** que faltan o son sustituidas al cargar un documento Word en .NET? No eres el único—los desarrolladores constantemente se topan con el problema cuando un documento hace referencia a una fuente que no está instalada en el servidor. La buena noticia es que Aspose.Words te brinda una forma limpia y programática de detectar esas ausencias.

En este tutorial recorreremos un ejemplo práctico que no solo muestra **cómo detectar fuentes**, sino que también demuestra cómo **configurar la configuración de fuentes** y **manejar fuentes faltantes** de forma elegante. Al final tendrás un fragmento listo para ejecutar que imprime cada advertencia de sustitución de fuentes, para que puedas registrar, alertar o reemplazar fuentes según sea necesario.

---

## Lo que necesitarás

- **Aspose.Words for .NET** (la última versión funciona mejor; el código a continuación está dirigido a .NET 6+)
- Un entorno de desarrollo .NET (Visual Studio, Rider o VS Code)
- Un archivo de muestra `.docx` que haga referencia a una fuente que no tienes instalada (ideal para pruebas)

No se requieren paquetes NuGet adicionales más allá de Aspose.Words, y la solución funciona en Windows, Linux y macOS.

---

## Paso 1: Instalar y Referenciar Aspose.Words

Primero, agrega la biblioteca a tu proyecto. El comando NuGet es sencillo:

```bash
dotnet add package Aspose.Words
```

> **Consejo profesional:** Si estás en un servidor CI, fija la versión del paquete para evitar cambios inesperados que rompan el código.

---

## Paso 2: Configurar la configuración de fuentes (y preparar las opciones de carga)

Antes de abrir un documento, puedes indicarle a Aspose.Words dónde buscar fuentes de respaldo. Esta es la parte de **configurar la configuración de fuentes** que evita que el motor reemplace silenciosamente fuentes que quizás no quieras.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

¿Por qué molestarse? Si el documento hace referencia a *Comic Sans* pero tu servidor solo tiene *Calibri*, Aspose.Words sustituirá *Calibri* y generará una advertencia. Al configurar la ruta de búsqueda, reduces sorpresas no deseadas.

---

## Paso 3: Cargar el documento con las opciones preparadas

Ahora realmente abrimos el archivo. Las `LoadOptions` que construimos en el paso anterior se pasan directamente al constructor `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Si el archivo no se encuentra o está corrupto, se lanza una excepción—por lo que podrías envolver esto en un try/catch en código de producción.

---

## Paso 4: Analizar las advertencias del documento en busca de sustituciones de fuentes

Aspose.Words recopila una lista de advertencias mientras analiza. Entre ellas, `FontSubstitutionWarning` te indica exactamente qué fuente fue reemplazada.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

La colección `Warnings` también puede contener otros elementos (p. ej., `DocumentStructureWarning`). Filtrar por `FontSubstitutionWarning` asegura que solo informemos del escenario **manejar fuentes faltantes** que nos interesa.

---

## Paso 5: Juntar todo – Un ejemplo completo y ejecutable

A continuación se muestra el programa completo. Copia‑pega en una nueva aplicación de consola y ejecútalo; verás cada fuente faltante impresa en la consola.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Salida esperada** (ejemplo):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Si el documento usa solo fuentes que existen en la máquina, verás la línea “No font substitutions detected” en su lugar.

---

## Casos límite y preguntas frecuentes

### ¿Qué pasa si el documento no contiene **advertencias** en absoluto?

Eso simplemente significa que cada fuente referenciada se encontró en las carpetas de búsqueda que configuraste. La bandera `anySubstitutions` en el ejemplo cubre este caso.

### ¿Puedo **registrar** advertencias en un archivo en lugar de la consola?

Absolutamente. Reemplaza las llamadas a `Console.WriteLine` por un logger de tu elección (Serilog, NLog, etc.). El objeto `WarningInfo` también expone `WarningType` y `WarningMessage` si necesitas más detalle.

### ¿Cómo puedo **ignorar** ciertas fuentes, como una fuente de marca corporativa que nunca debe ser sustituida?

Puedes añadir una regla de sustitución personalizada:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Ahora Aspose.Words solo reemplazará *MyBrandFont* con las alternativas listadas, y seguirás recibiendo una advertencia que podrás actuar.

### ¿Esto funciona en contenedores **Linux**?

Sí—solo asegúrate de montar una carpeta con los archivos `.ttf`/`.otf` requeridos y apunta `SetFontsFolder` a ella. Aspose.Words no depende de fuentes instaladas por el SO.

---

## Visión general visual

![diagrama de cómo detectar fuentes](detect-fonts.png "Diagrama que muestra los pasos para detectar fuentes en un documento")

*Texto alternativo de la imagen:* **cómo detectar fuentes** diagrama que ilustra la configuración, carga e inspección de advertencias.

---

## Resumen – Lo que hemos aprendido

- **Cómo detectar fuentes** que faltan o son sustituidas usando advertencias de Aspose.Words.  
- Cómo **configurar la configuración de fuentes** para apuntar a carpetas de fuentes personalizadas y establecer una alternativa predeterminada.  
- Estrategias para **manejar fuentes faltantes**, desde el registro hasta reglas de sustitución personalizadas.

Todo esto cabe en una aplicación de consola compacta y autocontenida que puedes incorporar a cualquier solución .NET.

---

## Próximos pasos y temas relacionados

- **Incrustar fuentes** directamente en el documento de salida para evitar sustituciones futuras (`SaveOptions` con `EmbedFullFonts`).  
- **Reemplazo programático de fuentes** – reemplazar fuentes faltantes con una alternativa específica antes de guardar.  
- **Ajuste de rendimiento** – almacenar en caché `FontSettings` al procesar muchos documentos en lote.  

Si te interesan esos temas, busca *configure font settings* y *handle missing fonts*—te llevarán a análisis más profundos sobre la gestión de fuentes con Aspose.Words.

¡Feliz codificación! ¿Tienes un caso extraño de fuentes? Deja un comentario y lo resolveremos juntos.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}