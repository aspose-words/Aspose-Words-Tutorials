---
category: general
date: 2025-12-31
description: Capture advertencias de fuentes en Aspose.Words para detectar fuentes
  faltantes y enumerar las fuentes faltantes en su aplicación .NET. Aprenda una solución
  paso a paso en C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: es
og_description: Captura advertencias de fuentes en Aspose.Words para detectar fuentes
  faltantes y enumerarlas. Guía completa de C# con código y consejos.
og_title: Capturar advertencias de fuentes – Detectar y enumerar fuentes faltantes
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Capturar advertencias de fuentes – Detectar y enumerar fuentes faltantes
url: /es/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar advertencias de fuentes – Detectar y enumerar fuentes faltantes

¿Alguna vez necesitaste **capturar advertencias de fuentes** al cargar un documento Word pero no sabías cómo exponer los detalles de las fuentes faltantes? No estás solo. En muchos proyectos del mundo real, las fuentes faltantes causan fallos de diseño, y sin advertencias adecuadas terminas persiguiendo errores fantasma.  

En este tutorial te mostraremos cómo **detectar fuentes faltantes** y **enumerar fuentes faltantes** usando Aspose.Words para .NET. Al final tendrás un fragmento de C# listo para ejecutar que imprime cada advertencia de sustitución, para que puedas registrar, alertar o incluso reemplazar fuentes automáticamente.

---

## Por qué es importante capturar advertencias de fuentes

Cuando Aspose.Words abre un DOCX que hace referencia a una fuente no instalada en el servidor, sustituye silenciosamente una alternativa. El documento se ve bien, pero la fidelidad visual se ve comprometida—piensa en el logotipo corporativo renderizado con la tipografía incorrecta.  

Capturar esas advertencias te permite:

* **Mantener la consistencia de la marca** – sabes exactamente qué fuentes faltan.
* **Automatizar la remediación** – reemplazar fuentes faltantes programáticamente.
* **Auditar el cumplimiento** – generar informes para revisiones legales o de diseño.

En resumen, **capturar advertencias de fuentes** es la primera línea de defensa contra la sustitución silenciosa de fuentes.

---

## Configurar LoadOptions para detectar fuentes faltantes

La clave para exponer las advertencias es la propiedad `LoadOptions.FontSubstitutionWarning`. Por defecto está establecida en `None`, lo que significa que Aspose.Words descarta los mensajes. Cambiarla a `All` indica a la biblioteca que registre cada evento de sustitución.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Consejo profesional:** Si ya tienes una carpeta de fuentes personalizada, asígnala a `FontSettings.SetFontsFolder("path")` antes de cargar el documento. De esa manera puedes **detectar fuentes faltantes** que no están en el directorio del sistema.

---

## Cargar el documento y enumerar fuentes faltantes

Ahora que los `LoadOptions` están listos, el siguiente paso es cargar el archivo Word. El constructor acepta el objeto de opciones, y cualquier sustitución se registrará en la `WarningInfoCollection` del documento.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Si el archivo hace referencia a fuentes que no están disponibles, cada fuente faltante genera una entrada `WarningInfo`. Puedes **enumerar fuentes faltantes** iterando sobre esa colección.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Una salida típica se ve así:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Cada línea te indica exactamente qué fuente faltaba, cumpliendo con el requisito de **enumerar fuentes faltantes**.

---

## Leer e interpretar la WarningInfoCollection

La `WarningInfoCollection` puede contener diferentes tipos de advertencias (p. ej., `DocumentStructure`, `ImageLoading`). Para centrarse únicamente en problemas de fuentes, filtra por `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

¿Por qué filtrar? Porque un documento grande también puede generar advertencias sobre imágenes corruptas o características no compatibles. Al reducir la colección evitas el ruido y mantienes la salida de **capturar advertencias de fuentes** limpia.

---

## Ejemplo completo – Capturar advertencias de fuentes en acción

A continuación se muestra el programa completo y autónomo que puedes insertar en cualquier proyecto de consola .NET. Demuestra cada paso, desde la configuración de `LoadOptions` hasta la impresión de una lista ordenada de fuentes faltantes.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Salida esperada en la consola**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Si el documento no contiene fuentes faltantes verás:

```
All referenced fonts are available – no warnings captured.
```

---

## Casos límite comunes y cómo manejarlos

| Situación | Por qué ocurre | Solución recomendada |
|-----------|----------------|----------------------|
| **El documento usa una fuente OpenType incrustada** | Aspose.Words puede leer fuentes incrustadas, pero solo si el archivo no está corrupto. | Verifica el DOCX en Word primero; vuelve a incrustar la fuente si es necesario. |
| **Gran número de advertencias** (p. ej., más de 200 fuentes faltantes) | Las importaciones masivas de sistemas heredados a menudo hacen referencia a una amplia paleta de fuentes. | Procesa las advertencias por lotes: guárdalas en una base de datos y luego ejecuta un script de instalación de fuentes. |
| **La WarningInfoCollection está vacía** | O el documento tiene todas las fuentes, o `FontSubstitutionWarning` se dejó en `None`. | Verifica nuevamente la configuración de tus `LoadOptions` y asegúrate de estar cargando la ruta de archivo correcta. |
| **Fuentes personalizadas ubicadas en un recurso compartido de red** | La latencia de la red puede causar tiempos de espera durante la búsqueda de fuentes. | Precarga las fuentes en `FontSettings` usando `SetFontsFolder` y establece `CacheFontData = true`. |

---

## Ilustración de la imagen

![ejemplo de captura de advertencias de fuentes](https://example.com/images/capture-font-warnings.png "ejemplo de captura de advertencias de fuentes")

*La captura muestra una ejecución en consola donde se informan dos fuentes faltantes.*

---

## Próximos pasos – Más allá del informe simple

Ahora que puedes **capturar advertencias de fuentes**, considera automatizar la remediación:

1. **Sustitución automática de fuentes** – Reemplaza fuentes faltantes con una alternativa aprobada por la empresa modificando `FontSettings.SubstitutionSettings`.
2. **Registro en un sistema de monitoreo** – Envía los mensajes de advertencia a Serilog, ELK o Azure Application Insights.
3. **Informes para usuarios** – Genera un resumen en HTML o PDF para que los diseñadores revisen qué fuentes necesitan ser instaladas.

Todas estas extensiones se basan en la misma base que cubrimos: configurar `LoadOptions`, cargar el documento y leer `WarningInfoCollection`.

---

## Conclusión

Acabas de aprender cómo **capturar advertencias de fuentes** en Aspose.Words, **detectar fuentes faltantes** y **enumerar fuentes faltantes** con una salida limpia y amigable para la consola. El enfoque es sencillo, requiere solo unas pocas líneas de C# y funciona con cualquier versión de .NET que soporte Aspose.Words 23.x o posterior.

Pruébalo con un DOCX de ejemplo que haga referencia a una fuente que hayas desinstalado deliberadamente: verás las advertencias aparecer de inmediato. A partir de ahí, puedes decidir si instalar las tipografías faltantes, sustituirlas programáticamente o simplemente registrar el problema para revisarlo más tarde.

¡Feliz codificación, y que tus documentos siempre se rendericen con las fuentes correctas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}