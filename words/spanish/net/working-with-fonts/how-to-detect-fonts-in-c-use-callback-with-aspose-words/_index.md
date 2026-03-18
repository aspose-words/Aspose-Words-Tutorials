---
category: general
date: 2026-03-17
description: Cómo detectar fuentes en C# usando Aspose.Words y una devolución de llamada
  de advertencia. Aprende a usar la devolución de llamada para capturar sustituciones
  de fuentes faltantes al cargar documentos.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: es
og_description: Cómo detectar fuentes en C# usando Aspose.Words. Esta guía muestra
  cómo usar una devolución de llamada para capturar advertencias de fuentes faltantes
  al cargar un documento.
og_title: Cómo detectar fuentes en C# – Usar devolución de llamada con Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo detectar fuentes en C# – Usar devolución de llamada con Aspose.Words
url: /es/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

Make sure to keep them unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar fuentes en C# – Usar Callback con Aspose.Words

¿Alguna vez necesitaste **cómo detectar fuentes** en un documento Word de forma programática y te preguntaste por qué algunos caracteres se ven extraños después de la conversión? No estás solo. En muchos proyectos del mundo real —generadores de facturas, exportadores de informes o canalizaciones de procesamiento por lotes— la falta de fuentes causa fallos de diseño silenciosos que son difíciles de depurar.  

¿La buena noticia? Aspose.Words te ofrece una forma sencilla de exponer esos problemas mediante un callback de advertencia. En este tutorial verás **cómo usar callback** para capturar cada sustitución de fuente que Aspose realiza al cargar un documento, y saldrás con un ejemplo listo‑para‑ejecutar que imprime un informe claro de fuentes faltantes.

Cubrirémos:

* Los requisitos mínimos (un proyecto .NET y el paquete NuGet Aspose.Words).  
* Cómo implementar `IWarningCallback` para escuchar `WarningType.FontSubstitution`.  
* Cómo conectar el callback a `LoadOptions` y cargar un documento.  
* Cómo se ve la salida, más algunos consejos prácticos para código de producción.

Al final, podrás **detectar fuentes** automáticamente en cualquier archivo DOCX, DOC o RTF y actuar sobre la información de fuentes faltantes—ya sea registrándolas, alertando a un usuario o sustituyendo una fuente de respaldo.

---

![Cómo detectar fuentes en un documento Word usando el callback de advertencia de Aspose.Words](https://example.com/images/detect-fonts.png "cómo detectar fuentes en un documento Word")

## Lo que necesitarás

* **.NET 6.0** o posterior (el ejemplo también compila con .NET Framework 4.6+).  
* **Aspose.Words for .NET** – instálalo vía NuGet: `Install-Package Aspose.Words`.  
* Un archivo Word de muestra que deliberadamente hace referencia a una fuente que no tienes instalada (p. ej., `MissingFont.docx`).  

No se requieren bibliotecas adicionales; todo reside dentro del espacio de nombres Aspose.

---

## Cómo detectar fuentes con un callback de advertencia

### Paso 1: Crear una clase de callback de advertencia

El callback implementa `IWarningCallback`. Cuando Aspose.Words encuentra una fuente que no puede encontrar, genera un `WarningInfo` con `WarningType.FontSubstitution`. Nuestra clase simplemente escribe una línea amigable en la consola.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Por qué es importante:** Al filtrar por `WarningType.FontSubstitution` evitamos advertencias ruidosas (como características obsoletas) y mantenemos el registro centrado en el problema exacto que intentas resolver—**detectar fuentes** que no están presentes en la máquina.

### Paso 2: Conectar el callback a `LoadOptions`

`LoadOptions` te permite personalizar cómo se analiza un documento. Asignar nuestro `FontWarningCollector` a la propiedad `WarningCallback` indica a Aspose que lo invoque cada vez que se encuentre una fuente faltante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Consejo:** También puedes establecer `LoadOptions.FontSettings` aquí si deseas proporcionar una fuente de respaldo programáticamente. Ese es un escenario avanzado que mencionaremos más adelante.

### Paso 3: Cargar el documento y observar la salida

Ahora realmente cargamos el archivo. Tan pronto como Aspose analiza el documento, cualquier fuente que no pueda localizar dispara nuestro callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Salida esperada en la consola** (suponiendo que el documento hace referencia a *Comic Sans MS* que no está instalado):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Si el documento contiene varias fuentes faltantes, verás una línea por fuente—exactamente la información de **cómo detectar fuentes** que necesitas.

## Cómo usar el callback para escenarios más complejos

### Registrar en un archivo en lugar de la consola

En producción probablemente quieras un registro persistente. Cambia `Console.WriteLine` por un `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Recopilar advertencias para análisis posterior

A veces necesitas la lista de fuentes faltantes después de cargar el documento, quizás para mostrar un diálogo UI. Almacena las advertencias en un `List<string>` y expónlo:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Proveer una fuente de respaldo programáticamente

Si tienes una fuente corporativa que deseas imponer, puedes agregarla a `FontSettings` antes de cargar:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Ahora Aspose sustituye las fuentes faltantes con *Arial Unicode MS* mientras sigue informando la sustitución a través del callback. Esta es una forma práctica de **cómo usar callback** tanto para detección como para remediación automática.

## Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Cómo evitar |
|----------|----------------|--------------|
| **Olvidar referenciar `Aspose.Words.Warnings`** | La interfaz `IWarningCallback` se encuentra allí. | Agrega `using Aspose.Words.Warnings;` al inicio. |
| **Cargar un documento sin `LoadOptions`** | El cargador predeterminado sustituye silenciosamente las fuentes sin notificación. | Siempre crea una instancia de `LoadOptions` y asigna tu callback. |
| **Ejecutar en un servidor con permisos limitados** | Escribir en un archivo de registro puede lanzar `UnauthorizedAccessException`. | Usa una carpeta con permisos de escritura (p. ej., el directorio de datos de la aplicación) o mantente con colecciones en memoria. |
| **Múltiples hilos compartiendo el mismo collector** | `FontWarningCollector` no es seguro para subprocesos por defecto. | Crea un collector separado por hilo o protege la lista con un bloqueo. |
| **Suponer que el callback se dispara para fuentes incrustadas** | Las fuentes incrustadas ya están presentes en el documento; no se genera advertencia. | Si necesitas verificar la integridad de fuentes incrustadas, inspecciona `FontInfo` a través de `FontSettings`. |

## Ejemplo completo funcional (listo para copiar‑pegar)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Lo que deberías ver** (suponiendo que el archivo hace referencia a dos fuentes ausentes):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Si el archivo usa solo fuentes instaladas, la consola simplemente imprime:

```
Document loaded successfully.

No missing fonts detected.
```

## Conclusión

Hemos recorrido **cómo detectar fuentes** en un documento Word conectando un callback de advertencia personalizado en Aspose.Words. El enfoque es ligero, requiere

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}