---
category: general
date: 2026-02-18
description: Aprenda cómo capturar advertencias de fuentes y detectar fuentes faltantes
  en C# usando Aspose.Words. Siga esta guía paso a paso para manejar fuentes faltantes
  de manera eficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: es
og_description: Captura advertencias de fuentes en C# y aprende a detectar fuentes
  faltantes, manejar fuentes faltantes y enumerar fuentes faltantes con un ejemplo
  de código completo.
og_title: Capturar advertencias de fuentes en C# – Guía completa
tags:
- Aspose.Words
- C#
- Font Management
title: Capturar advertencias de fuentes en C# – Guía completa de programación
url: /es/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar advertencias de fuentes en C# – Guía completa de programación

¿Alguna vez te has preguntado cómo **capturar advertencias de fuentes** cuando un documento hace referencia a una fuente que no está instalada en el servidor? No eres el único. En muchas aplicaciones empresariales, las fuentes faltantes provocan fallos de diseño, y la única forma fiable de detectarlas es escuchando las advertencias que lanza la biblioteca.  

En este tutorial te mostraremos una solución lista‑para‑ejecutar que no solo **captura advertencias de fuentes**, sino que también **detecta fuentes faltantes**, **maneja fuentes faltantes** y, además, **lista fuentes faltantes** para que puedas decidir si sustituirlas, incrustarlas o alertar al usuario. No se necesita documentación externa—solo copia, pega y ejecuta.

## Lo que aprenderás

- Cómo configurar `LoadOptions` para activar las advertencias de sustitución de fuentes.  
- El código exacto que necesitas para cargar un DOCX y extraer cada advertencia.  
- Por qué cada paso es importante, incluidas consideraciones de rendimiento.  
- Manejo de casos límite como documentos con fuentes de scripts mixtos o carpetas de fuentes personalizadas.  

**Prerequisites**: .NET 6+ (o .NET Framework 4.6+), una referencia al paquete NuGet **Aspose.Words**, y un conocimiento básico de C#. Si nunca has usado Aspose.Words antes, no te preocupes—esta guía te lleva paso a paso por cada detalle.

![Diagrama que muestra el flujo de captura de advertencias de fuentes](image.png){alt="diagrama de captura de advertencias de fuentes"}

## Capturar advertencias de fuentes – Por qué es importante

Cuando Aspose.Words carga un documento, sustituye silenciosamente cualquier fuente no disponible por una alternativa. Esa sustitución mantiene viva la operación de carga, pero el resultado visual puede quedar totalmente desalineado. Al activar la bandera **SubstitutionWarningLevel.All**, la biblioteca agrega una entrada `WarningInfo` por cada fuente faltante, lo que te permite **detecta fuentes faltantes** antes de que el documento se renderice o guarde.

> **Pro tip:** Si procesas cientos de archivos en un trabajo por lotes, registrar estas advertencias en un almacén central puede ahorrarte horas de QA manual más adelante.

## Paso 1: Configura tu proyecto

1. Abre tu IDE favorito (Visual Studio, Rider, VS Code).  
2. Crea un nuevo proyecto de consola:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Añade el paquete Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Eso es todo—sin DLLs extra, sin interop COM. La biblioteca incluye todo lo necesario para **manejar fuentes faltantes**.

## Paso 2: Prepara Load Options para Capturar Todas las Advertencias de Sustitución de Fuentes

Para que el motor **capture advertencias de fuentes**, debes indicarle que registre cada sustitución. El siguiente fragmento crea una instancia de `LoadOptions`, habilita el nivel de advertencia y (opcionalmente) apunta el motor a una carpeta que contenga fuentes personalizadas que puedas querer usar.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Por qué esto importa:**  
- `SubstitutionWarningLevel.All` garantiza que **cada** evento de fuente faltante se registre, no solo el primero.  
- Sin esta bandera, Aspose.Words sustituye silenciosamente la fuente y nunca sabrás que existe un problema.

## Paso 3: Carga el Documento Usando las Opciones Configuradas

Ahora realmente abrimos el archivo. Sustituye `DocumentWithMissingFonts.docx` por la ruta a tu documento de prueba.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Si el archivo contiene referencias a fuentes que no están en la máquina (o en la carpeta opcional que añadiste), la `document.WarningInfoCollection` se poblará.

## Paso 4: Encuentra y Muestra Cualquier Advertencia de Sustitución de Fuentes

Este es el corazón del tutorial: iterar sobre la `WarningInfoCollection` para **listar fuentes faltantes**. Filtraremos por `WarningType.FontSubstitution` y mostraremos un mensaje amigable.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Salida esperada

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Si el documento usa solo fuentes instaladas, verás la línea “✅ No missing fonts detected”.

## Paso 5: Avanzado – Cómo **manejar fuentes faltantes** programáticamente

Simplemente imprimir una lista puede ser suficiente para una herramienta de diagnóstico, pero muchos sistemas de producción necesitan **manejar fuentes faltantes** automáticamente. A continuación se presentan dos estrategias comunes:

### 5.1 Sustituir con una alternativa conocida

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Incrustar una fuente personalizada sobre la marcha

Si dispones de un archivo de fuente corporativa (`MyBrand.ttf`), puedes incrustarlo cuando se detecte una fuente faltante:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Nota:** Incrustar fuentes puede aumentar el tamaño del archivo de salida, así que evalúa el compromiso entre fidelidad y ancho de banda.

## Problemas comunes y cómo evitarlos

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| No aparecen advertencias aunque el documento se vea mal | `SubstitutionWarningLevel` no está configurado a `All` | Asegúrate de que el paso 2 establezca la bandera exactamente como se muestra |
| Las advertencias enumeran la misma fuente varias veces | El documento contiene la fuente en varios estilos | Desduplicar si solo necesitas una lista única: `fontWarnings.Select(w => w.Description).Distinct()` |
| La aplicación se bloquea con archivos DOCX grandes | Cargando con la configuración de memoria predeterminada | Usa `LoadOptions.LoadFormat` o transmite el archivo para reducir la presión de memoria |

## Ejemplo completo (Listo para copiar‑pegar)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Ejecuta el programa con `dotnet run`. Deberías ver la lista de fuentes faltantes impresa en la consola, confirmando que has **capturado advertencias de fuentes** con éxito.

## Conclusión

Ahora dispones de un patrón completo y listo para producción que **captura advertencias de fuentes**, **detecta fuentes faltantes**, **maneja fuentes faltantes** y **lista fuentes faltantes** usando Aspose.Words en C#. El enfoque es ligero, requiere solo unas pocas líneas de código y puede integrarse en cualquier canal de procesamiento existente—ya sea que

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}