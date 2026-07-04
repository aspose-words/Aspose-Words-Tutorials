---
category: general
date: 2026-06-02
description: cómo manejar fuentes en .NET – detectar fuentes faltantes y rastrear
  cambios de fuentes usando LoadOptions y FontSettings. Aprende una solución completa
  y ejecutable.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: es
og_description: cómo manejar fuentes en .NET – detectar fuentes faltantes y rastrear
  cambios de fuentes. Sigue esta guía paso a paso para una solución completa, lista
  para ejecutar.
og_title: cómo manejar fuentes en .NET – detectar fuentes faltantes
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: Cómo manejar fuentes en .NET – detectar fuentes faltantes
url: /es/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo manejar fuentes en .NET – detectar fuentes faltantes

¿Alguna vez te has preguntado **cómo manejar fuentes** cuando un documento de Word hace referencia a una tipografía que no está instalada en la máquina? No eres el único. Las fuentes faltantes pueden convertir un informe pulido en un desastre confuso, y sin advertencias adecuadas podrías nunca saber qué se sustituyó.  

En este tutorial te mostraremos exactamente **cómo manejar fuentes** detectando fuentes faltantes **y** rastreando los cambios de fuente en tiempo de ejecución. Al final tendrás una aplicación de consola autónoma que registra cada sustitución, para que nunca te sorprenda una misteriosa Helvetica apareciendo donde debería estar Times New Roman.

> **Lo que obtendrás:** un ejemplo de código completo, listo para copiar y pegar, una explicación de cada línea, consejos para proyectos del mundo real y una mirada rápida a casos límite que podrías encontrar.

## Requisitos previos

- .NET 6.0 o posterior (el ejemplo usa un `Program.cs` de nivel superior para mayor brevedad)  
- Aspose.Words para .NET 23.9 o más reciente – puedes obtenerlo de NuGet con `dotnet add package Aspose.Words`  
- Un documento de Word que intencionalmente hace referencia a una fuente que no tienes (p.ej., `MissingFont.docx`)  

No se requieren otras bibliotecas.

![Diagrama que muestra cómo el flujo de LoadOptions entra en FontSettings y el evento de advertencia de sustitución – ejemplo de cómo manejar fuentes en .NET](https://example.com/images/font‑handling‑flow.png "ejemplo de cómo manejar fuentes en .NET")

## Paso 1: Configurar LoadOptions con FontSettings  

Lo primero que necesitamos es un objeto `LoadOptions` que indique a Aspose.Words que vigile los problemas de fuentes.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Por qué es importante:** `LoadOptions` es el guardián cuando se lee un documento del disco. Al proporcionar un `FontSettings` personalizado obtenemos un punto de enganche en el motor interno de resolución de fuentes, que es la única forma de **detectar fuentes faltantes** antes de que el documento se renderice.

## Paso 2: Suscribirse al evento SubstitutionWarning  

Aspose.Words genera un evento `SubstitutionWarning` cada vez que no puede encontrar la fuente exacta que solicitaste. Registraremos los detalles para que puedas ver qué fuentes se solicitaron y cuáles se usaron realmente.  

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Por qué escuchamos:** Sin este escuchador nunca sabrías que ocurrió una sustitución. El evento te brinda una pista de auditoría completa, cumpliendo con el requisito de “rastrear cambios de fuente”.

## Paso 3: Cargar el documento usando nuestras opciones configuradas  

Ahora realmente leemos el archivo. Como pasamos `loadOptions`, Aspose.Words disparará el evento de advertencia para cualquier fuente faltante que encuentre.  

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Eso es todo – el documento ya está cargado, y cualquier problema de fuentes ya se ha impreso en la consola.

## Paso 4: (Opcional) Verificar las fuentes sustituidas en el documento  

Si deseas verificar doblemente qué fuentes quedaron en el PDF o DOCX final, puedes recorrer la colección de fuentes del documento:  

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Ejecutar esto después de la carga listará cada fuente que el motor decidió incrustar o referenciar. Útil cuando necesitas generar un informe para los equipos de QA.

## Ejemplo completo en funcionamiento  

Copia el bloque a continuación en un nuevo proyecto de consola (`dotnet new console`) y ejecútalo. El programa mostrará cada sustitución y luego listará las fuentes que sobrevivieron a la carga.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Salida esperada  

Si `MissingFont.docx` solicita *“Comic Sans MS”* (que no está instalada) verás algo como:  

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

La primera línea demuestra que **detectamos fuentes faltantes** y **rastreamos cambios de fuente**. La segunda línea muestra una sustitución que no era necesaria (sin advertencia, porque la fuente existía).

## Errores comunes y consejos profesionales  

| Trampa | Qué ocurre | Cómo arreglar / evitar |
|--------|------------|------------------------|
| **No se disparan eventos de advertencia** | Podrías pensar que la API está rota. | Asegúrate de *asignar* el `FontSettings` a `LoadOptions` **antes** de cargar el documento. El gancho del evento debe estar adjunto **antes** de la llamada `new Document(...)`. |
| **Las fuentes sustituidas siguen viéndose mal** | Aspose.Words recurre a una fuente genérica que no coincide con el estilo. | Proporciona una carpeta de fuentes personalizada mediante `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Esto le da al motor más opciones antes de que recurra a una fuente genérica. |
| **Impacto de rendimiento en documentos grandes** | Escanear cada fuente puede añadir unos pocos milisegundos. | Almacena en caché el objeto `FontSettings` si cargas muchos documentos consecutivamente. Reutilizar la misma instancia evita volver a leer las tablas de fuentes del sistema. |
| **La salida de consola se pierde en aplicaciones GUI** | No verás las advertencias. | Redirige el evento a un registrador (p.ej., `Serilog`) o escribe a un archivo: `File.AppendAllText("font-warnings.log", …)`. |

## Extender la solución  

- **Exportar a PDF con fuentes incrustadas** – después de cargar, llama a `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` y asegúrate de establecer `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Procesamiento por lotes** – envuelve la lógica de carga en un `foreach` sobre una carpeta de archivos DOCX. Registra las advertencias de cada archivo en un CSV para fines de auditoría.  
- **Interfaz de usuario amigable** – expón la misma lógica detrás de un botón en una aplicación WinForms/WPF, mostrando las advertencias en un `ListBox`.  

## Conclusión  

Hemos recorrido **cómo manejar fuentes** en .NET configurando `LoadOptions`, suscribiéndonos al evento `SubstitutionWarning` y finalmente cargando el documento. El ejemplo no solo **detecta fuentes faltantes**, sino que también **rastrear cambios de fuente** para que puedas auditar cada sustitución.  

Pruébalo con tus propios documentos, ajusta la ruta de la carpeta de fuentes, y nunca volverás a ser sorprendido por un intercambio inesperado de fuentes. Si encontraste útil esta guía, considera explorar temas relacionados como *“incrustar fuentes personalizadas en PDF con Aspose.Words”* o *“crear una estrategia de respaldo de fuentes para aplicaciones .NET multiplataforma.”*  

¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como lo deseas!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo cargar DOCX y detectar fuentes faltantes – Guía completa en C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cómo usar LoadOptions en Aspose.Words – Guía completa](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}