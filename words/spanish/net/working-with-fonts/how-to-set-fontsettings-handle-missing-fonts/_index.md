---
category: general
date: 2026-05-29
description: Aprende cómo configurar FontSettings en Aspose.Words y manejar las fuentes
  faltantes de forma elegante. Guía paso a paso con código completo y buenas prácticas.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: es
og_description: Cómo configurar FontSettings en Aspose.Words y manejar fuentes faltantes
  rápidamente. Sigue esta guía para obtener una solución completa y ejecutable.
og_title: Cómo configurar FontSettings – Gestionar fuentes faltantes
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Cómo configurar FontSettings – Manejar fuentes faltantes
url: /es/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo configurar FontSettings – Manejar fuentes faltantes

¿Alguna vez te has preguntado **cómo configurar FontSettings** al trabajar con Aspose.Words y de repente te encuentras con un documento que hace referencia a una fuente que no tienes instalada? Es un problema frecuente, especialmente al procesar archivos suministrados por el cliente en un servidor que solo tiene un conjunto mínimo de fuentes. ¿La buena noticia? Puedes detectar esas ausencias y **manejar fuentes faltantes** sin que tu aplicación se bloquee o genere PDFs feos.

En este tutorial recorreremos un escenario real: cargar un DOCX que solicita “Calibri” mientras que tu contenedor Linux solo incluye “DejaVu Sans”. Verás exactamente cómo configurar FontSettings, suscribirte a las advertencias de sustitución y proporcionar fuentes de respaldo para que el documento se renderice tal como el autor lo diseñó. Sin rodeos, solo el código que puedes incorporar a tu proyecto hoy.

## Requisitos previos

- .NET 6.0 o posterior (la API funciona igual en .NET Framework 4.7+)
- Aspose.Words para .NET 23.10 o superior (el nombre del paquete NuGet es `Aspose.Words`)
- Un entorno básico de desarrollo en C# (Visual Studio, Rider o VS Code)

Si tienes todo eso, vamos a sumergirnos.

## Paso 1: Crear FontSettings y escuchar eventos de sustitución

El núcleo de la solución es el objeto `FontSettings`. Al adjuntar un manejador a su evento `FontSubstitutionWarning` obtendrás un informe en tiempo real cada vez que Aspose.Words tenga que reemplazar una tipografía faltante.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Por qué es importante:**  
Cuando el motor no puede localizar *Calibri*, podría recurrir silenciosamente a *Arial*. Al escuchar la advertencia, mantienes un registro de auditoría transparente, ideal para depuración o informes de cumplimiento.

> **Consejo profesional:** Si ejecutas esto en un servidor CI, redirige la salida a un archivo de registro para que puedas revisar qué fuentes faltaron después de una ejecución por lotes.

## Paso 2: Adjuntar FontSettings a LoadOptions

`LoadOptions` es la puerta de enlace para controlar cómo se analiza un documento. Al asignar el `FontSettings` que acabamos de configurar, cada carga posterior de `Document` respetará nuestra lógica de sustitución.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**¿Qué ocurre internamente?**  
Durante el constructor de `Document`, Aspose.Words lee el XML del DOCX, resuelve las referencias de fuentes y—si no se encuentra una fuente—dispara la advertencia que configuramos antes. Sin este gancho, nunca sabrías que se realizó una sustitución.

## Paso 3: Cargar el documento y (opcionalmente) definir fuentes de respaldo

Ahora finalmente cargamos el archivo en memoria. Si ya dispones de una carpeta de fuentes de respaldo (p. ej., un directorio de fuentes OpenType que se envía con tu aplicación), indica a `FontSettings` dónde buscar. Este paso es opcional pero suele ser la forma más limpia de *manejar fuentes faltantes*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Alerta de caso límite:**  
Si el documento contiene una fuente personalizada incrustada como flujo binario, Aspose.Words la usará automáticamente—no se necesita sustitución. La advertencia solo se dispara para fuentes del sistema *faltantes*.

### Verificando el resultado

Después de cargar, quizá quieras guardar el documento como PDF o Word para confirmar que todo se ve correctamente.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Al ejecutar el programa, la consola mostrará líneas como:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Si ves estos mensajes, has **manejado fuentes faltantes** con éxito y sabes exactamente qué sustituciones se realizaron.

## Paso 4: Avanzado – Reglas personalizadas de sustitución de fuentes (Opcional)

A veces necesitas un mapeo determinista, p. ej., siempre reemplazar *Times New Roman* por *Liberation Serif*. Puedes lograrlo con `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**¿Por qué molestarse?**  
Las reglas explícitas te dan control sobre la tipografía, garantizando la consistencia de la marca en los PDFs generados, especialmente cuando produces material de marketing.

## Problemas comunes y cómo evitarlos

| Problema | Síntoma | Solución |
|----------|----------|----------|
| **No warning output** | Crees que las fuentes están bien pero el documento se ve mal. | Asegúrate de que `FontSubstitutionWarning` esté adjunto **antes** de cargar el documento. |
| **Fallback folder not scanned** | Las sustituciones siguen recurriendo a los valores predeterminados del sistema. | Llama a `SetFontsFolder(path, true)` con el segundo argumento `true` para recorrer sub‑carpetas. |
| **Performance hit on large batches** | Cargar 10k documentos se vuelve lento. | Cachea una única instancia de `FontSettings` y reutilízala en las cargas; evita recrearla cada vez. |
| **Embedded fonts ignored** | Esperabas que se usara una fuente incrustada personalizada, pero ocurre una sustitución. | Verifica que el DOCX de origen realmente incruste la fuente (revisa en Word → Archivo → Información → Fuentes). |

## Ejemplo completo y funcional

A continuación tienes el programa completo, listo para copiar y pegar. Demuestra todo, desde el manejo de eventos hasta el guardado del PDF final.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Salida esperada en la consola** (ejemplo):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Ejecuta el programa, abre `Output.pdf` y verás el texto renderizado con las fuentes de respaldo—sin cuadros de glifos faltantes, sin bloqueos.

## Conclusión

Ahora tienes un patrón sólido y listo para producción para **cómo configurar FontSettings** en Aspose.Words y **manejar fuentes faltantes** de forma elegante. Al conectar el evento `FontSubstitutionWarning`, apuntar a un directorio de fuentes de respaldo y (si es necesario) definir reglas explícitas de sustitución, obtienes total visibilidad y control sobre la tipografía en pipelines de documentos automatizados.

¿Qué sigue? Prueba agregar una colección de fuentes personalizada para tipografías específicas de la marca, o explora la API `FontSourceBase` para cargar fuentes desde una base de datos o almacenamiento en la nube. Los mismos principios se aplican—simplemente conecta una fuente diferente a `FontSettings`.

¿Tienes preguntas sobre casos límite, como manejar scripts de derecha a izquierda o fuentes de emojis? Deja un comentario abajo, ¡y feliz codificación!

## ¿Qué deberías aprender a continuación?

- [Cómo capturar fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cómo cargar DOCX y detectar fuentes faltantes – Guía completa en C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}