---
category: general
date: 2026-01-11
description: Habilite las advertencias de sustitución de fuentes para detectar fuentes
  faltantes en sus documentos .NET. Aprenda cómo obtener el nombre de la fuente faltante
  y enumerar las fuentes faltantes con Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: es
og_description: Habilite advertencias de sustitución de fuentes en Aspose.Words para
  detectar fuentes faltantes, obtener el nombre de la fuente faltante y enumerar las
  fuentes faltantes en sus documentos.
og_title: Habilitar advertencias de sustitución de fuentes – Tutorial paso a paso
  de C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Habilitar advertencias de sustitución de fuentes en Aspose.Words – Guía completa
url: /es/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar advertencias de sustitución de fuentes – Guía completa

¿Alguna vez te has preguntado por qué un documento de Word se ve ligeramente diferente después de cargarlo en un servidor? Lo más probable es que una fuente que usó el autor original no esté disponible en tu máquina, y Aspose.Words la sustituyó silenciosamente por la más cercana. **Habilita las advertencias de sustitución de fuentes** y sabrás al instante qué fuentes faltan, con qué se reemplazaron y cómo actuar sobre esa información.

En este tutorial recorreremos un ejemplo práctico, de extremo a extremo, que muestra cómo **detectar fuentes faltantes**, obtener el **nombre de la fuente faltante**, e incluso **enumerar fuentes faltantes** para generar informes. Sin rodeos, solo una solución clara que puedes incorporar en cualquier proyecto .NET hoy mismo.

---

## Lo que aprenderás

- Cómo configurar `LoadOptions` para que Aspose.Words emita advertencias detalladas.
- El código exacto necesario para cargar un documento y enumerar las advertencias relacionadas con fuentes.
- Formas de extraer el nombre de la fuente faltante y su sustitución, y luego generar un informe ordenado.
- Consejos para manejar casos extremos, como documentos con decenas de fuentes faltantes o carpetas de fuentes personalizadas.

### Requisitos previos

- .NET 6+ (el código también funciona con .NET Framework 4.7+)
- Aspose.Words para .NET 23.10 o superior (puedes obtenerlo desde NuGet)
- Un archivo DOCX de ejemplo que haga referencia a una fuente que no tengas instalada (lo llamaremos `MissingFont.docx`)

Si ya cuentas con esos elementos, vamos a sumergirnos.

---

## Paso 1: Configurar LoadOptions para habilitar advertencias de sustitución de fuentes  

Lo primero que debes hacer es indicarle a Aspose.Words que te importan las fuentes faltantes. Por defecto, la biblioteca solo registra advertencias internamente. Establecer `SubstitutionWarningLevel` a `Typical` (o `All` para la salida más detallada) activa el mecanismo.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Por qué es importante:**  
Cuando `SubstitutionWarningLevel` está configurado, cada vez que Aspose.Words no puede encontrar una fuente referenciada agrega un `FontSubstitutionWarning` a la colección `Warnings` del documento. Esa colección es la única forma fiable de **detectar fuentes faltantes** sin analizar el documento manualmente.

> **Consejo profesional:** Si estás procesando un lote de documentos y quieres estar absolutamente seguro de capturar cada sustitución, usa `FontSubstitutionWarningLevel.All`. Es un poco más ruidoso, pero garantiza que ninguna advertencia se escape.

---

## Paso 2: Cargar el documento usando las opciones configuradas  

Ahora que el sistema de advertencias está listo, carga tu DOCX con el `LoadOptions` que acabamos de preparar. La ruta puede ser absoluta o relativa; solo asegúrate de que el archivo exista.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**¿Qué ocurre tras bambalinas?**  
Aspose.Words analiza el XML del documento, resuelve cada elemento `<w:font>` y verifica el catálogo de fuentes del sistema (más cualquier carpeta personalizada que hayas añadido a `FontSettings`). Cuando no puede localizar una fuente, registra una advertencia, exactamente lo que necesitamos para **enumerar fuentes faltantes** más adelante.

---

## Paso 3: Recorrer las advertencias y extraer los detalles de las fuentes faltantes  

Con el documento en memoria, la colección `Warnings` contiene cada `FontSubstitutionWarning`. Iteraremos sobre ella, filtraremos por el tipo correcto y generaremos un informe amigable.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Salida esperada** (suponiendo que el documento fuente hace referencia a `MyCustomFont` que no está instalado):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Observa cómo cada entrada te brinda tanto el **nombre de la fuente faltante** (`MyCustomFont`) como la alternativa (`Arial`). Esa es exactamente la información que necesitas para decidir si incrustar la fuente original, solicitar al autor un reemplazo o simplemente aceptar la sustitución.

---

## Paso 4: Opcional – Recopilar los datos en una lista para procesamiento posterior  

Si necesitas exportar el informe a CSV, enviarlo a una API, o simplemente conservarlo en memoria para más tarde, puedes almacenar las advertencias en una lista fuertemente tipada.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Ahora tienes **enumerar fuentes faltantes** en un formato que cualquier sistema downstream puede consumir. Ya sea que alimentes un panel de control o generes un registro de auditoría, los datos están listos.

---

## Paso 5: Manejo de casos extremos y errores comunes  

### Múltiples fuentes faltantes en una sola ejecución  

Las plantillas corporativas grandes a menudo hacen referencia a decenas de fuentes personalizadas. La colección de advertencias puede volverse considerable, pero el patrón de iteración mostrado arriba escala linealmente, por lo que el rendimiento no es un problema. Solo recuerda mantener la salida legible—agrupando por página o estilo puede ser útil si necesitas un análisis más profundo.

### Carpetas de fuentes personalizadas  

Si almacenas fuentes en un directorio no estándar (por ejemplo, un recurso compartido en red), indica a Aspose.Words dónde buscarlas:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Configurar esto *antes* de cargar el documento le da a la biblioteca la oportunidad de encontrar las fuentes, lo que puede eliminar algunas advertencias por completo.

### Suprimir advertencias específicas  

A veces sabes que una sustitución particular es aceptable (por ejemplo, una fuente decorativa que no te importa reemplazar). Puedes filtrarlas después de la recopilación:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Compatibilidad de versiones  

El enumerado `FontSubstitutionWarningLevel` ha sido estable desde Aspose.Words 20.12. Si utilizas una versión anterior, puede que necesites actualizar para acceder a la funcionalidad de nivel de advertencia.

---

## Ejemplo completo y funcional  

A continuación tienes el programa completo, listo para ejecutar, que incorpora todos los pasos anteriores. Pégalo en un nuevo proyecto de consola, agrega el paquete NuGet de Aspose.Words y apunta `docPath` a un documento que haga referencia a una fuente faltante.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Al ejecutar este programa **habilitarás las advertencias de sustitución de fuentes**, **detectarás fuentes faltantes**, **obtenerás el nombre de la fuente faltante** y **enumerarás fuentes faltantes** tanto en la consola como en un archivo CSV.

---

## Conclusión  

Acabamos de cubrir todo lo necesario para **habilitar advertencias de sustitución de fuentes** en Aspose.Words, desde la configuración inicial hasta la extracción de una lista limpia de fuentes faltantes. Siguiendo los pasos anteriores podrás auditar tus documentos, garantizar la fidelidad visual y evitar sorpresas desagradables al renderizar en un servidor.

A continuación, podrías explorar:

- **Incrustar fuentes faltantes** directamente en el PDF o DOCX de salida (usa `FontSettings.EmbeddedFonts`).
- **Automatizar la instalación de fuentes** en agentes de compilación basándote en el informe generado.
- **Integrar con pipelines CI** para que fallen las compilaciones cuando falten fuentes críticas.

Pruébalos y convertirás un simple sistema de advertencias en un flujo de trabajo completo de gestión de fuentes.

¡Feliz codificación, y que todas tus fuentes sean encontradas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}