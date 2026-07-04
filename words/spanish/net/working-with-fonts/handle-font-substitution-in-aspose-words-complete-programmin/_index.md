---
category: general
date: 2026-06-17
description: Gestiona la sustitución de fuentes en Aspose.Words y detecta rápidamente
  las fuentes faltantes con este tutorial paso a paso para desarrolladores .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: es
og_description: Gestione la sustitución de fuentes en Aspose.Words y aprenda a detectar
  fuentes faltantes en sus documentos con ejemplos de código claros.
og_title: Gestionar la sustitución de fuentes en Aspose.Words – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Manejar la sustitución de fuentes en Aspose.Words – Guía completa de programación
url: /es/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manejo de la sustitución de fuentes en Aspose.Words – Guía completa de programación

¿Alguna vez te has preguntado cómo **manejar la sustitución de fuentes** cuando un documento Word hace referencia a una fuente que no está instalada en el servidor? No estás solo. En muchas aplicaciones del mundo real —piense en generadores de facturas o servicios de informes automáticos— las fuentes faltantes provocan sustituciones silenciosas que arruinan el diseño.  

La buena noticia es que Aspose.Words te ofrece un sistema de advertencias incorporado que te permite **detectar fuentes faltantes** y reaccionar de la manera que desees. En este tutorial recorreremos el registro de un manejador de advertencias, la carga de un documento y la extracción de los eventos exactos de sustitución de fuentes que necesitas conocer. Al final también verás cómo responder a la clásica pregunta “**cómo detectar fuentes faltantes**?” con código limpio y listo para producción.

## Qué cubre este tutorial

* Configurar Aspose.Words para generar advertencias por cada sustitución de fuente.  
* Capturar esas advertencias en un manejador personalizado para que puedas registrar, reemplazar o abortar.  
* Usar los datos capturados para **detectar fuentes faltantes** antes de que el documento se guarde o renderice.  
* Consejos para solucionar casos límite —como cuando se elige una fuente de respaldo de forma silenciosa.  
* Un ejemplo completo y ejecutable que puedes insertar en cualquier aplicación de consola .NET.

> **Requisitos previos** – Necesitarás un SDK .NET reciente (6.0+ funciona bien), una licencia válida de Aspose.Words para .NET (o una clave de evaluación temporal) y un DOCX de muestra que haga referencia intencionalmente a una fuente que no tengas instalada. No se requieren otras bibliotecas de terceros.

---

## ## Manejo de la sustitución de fuentes con un manejador de advertencias personalizado

Aspose.Words genera un objeto `WarningInfo` cada vez que no puede encontrar una fuente solicitada. Por defecto esas advertencias se ignoran, por lo que a menudo nunca notas una sustitución. Para **manejar la sustitución de fuentes**, sustituyes el manejador de advertencias predeterminado por uno que realmente haga algo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Por qué funciona esto

* `FontSettings.DefaultWarningHandler` es una propiedad estática global; una vez que la estableces, **todas** las operaciones de Aspose.Words en el AppDomain actual usan tu delegado.  
* El `WarningInfoCollectionHandler` recibe un objeto `WarningInfo` que contiene `WarningType` y una `Description` legible por humanos. Filtrar por `WarningType.FontSubstitution` garantiza que solo veas los eventos que te interesan.  
* Llamar a `doc.Save` obliga a la biblioteca a resolver todas las fuentes, momento en el que se disparan las advertencias. Si solo necesitas inspeccionar el documento sin guardarlo, puedes llamar a `doc.UpdatePageLayout()` en su lugar.

**Salida esperada en la consola** (suponiendo que la fuente faltante sea “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Esa línea es tu prueba de que la biblioteca **detectó fuentes faltantes** y eligió una alternativa.

---

## ## Detectar fuentes faltantes antes de renderizar

A veces deseas detener el proceso por completo si falta una fuente requerida —quizá porque las guías de marca exigen una tipografía exacta. El manejador de advertencias puede ampliarse para recopilar todos los mensajes de fuentes faltantes en una lista, y luego tomar una decisión.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Cómo esto responde a “cómo detectar fuentes faltantes”

* La lista `missingFonts` actúa como un registro de cada evento de sustitución.  
* Después de `UpdatePageLayout`, puedes inspeccionar la lista y decidir si continuar, registrar o lanzar una excepción.  
* Este patrón funciona para cualquier formato de salida (PDF, HTML, imágenes) porque el sistema de advertencias es independiente del formato.

---

## ## Consejo avanzado: Reemplazar fuentes faltantes con un sustituto específico

Si dispones de una fuente corporativa que debe usarse, puedes indicarle a Aspose.Words que reemplace cualquier fuente faltante con tu sustituto automáticamente. Esto es útil cuando deseas que el documento *siga* siendo aceptable sin procesamiento manual posterior.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Coloca el fragmento anterior **antes** de cargar el documento. Ahora cualquier fuente faltante —sin importar su nombre original— será intercambiada por “Calibri” (o “Arial” si Calibri no está presente). Seguirás recibiendo la advertencia, pero el documento se renderizará con la fuente que controlas.

---

## ## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Las advertencias desaparecen después de la primera llamada** | La propiedad estática `DefaultWarningHandler` se sobrescribe más adelante en la aplicación. | Establece el manejador **una sola vez** al iniciar la aplicación, o guarda una referencia y vuelve a asignarla si la cambias. |
| **Solo se informa la primera fuente faltante** | Algunas API agrupan advertencias; necesitas llamar a `UpdatePageLayout` o `Save` para vaciar la cola. | Fuerza una actualización de diseño o guarda en el formato que pretendes generar. |
| **La sustitución sigue ocurriendo incluso después de abortar** | El manejador de advertencias se ejecuta *después* de que la sustitución ya ha ocurrido. | Usa el manejador para **registrar** y luego lanza una excepción para detener el procesamiento posterior. |
| **Fuentes faltantes en contenedores Linux** | Linux a menudo carece del catálogo de fuentes de Windows, lo que genera muchas sustituciones. | Monta las fuentes necesarias en el contenedor o usa `FontSettings.SetFontsFolder` para apuntar a un directorio de fuentes personalizado. |

---

## ## Detectar sustitución de fuentes en un escenario Web API

Si sirves documentos a través de ASP.NET Core, probablemente no quieras escribir en la consola. En su lugar, recopila las advertencias y devuélvelas como parte de la respuesta HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Ahora la API **detecta fuentes faltantes** y devuelve una carga JSON clara antes de generar cualquier PDF. Esta es una ilustración práctica de “cómo detectar fuentes faltantes” en un servicio de nivel producción.

---

## ## Probar tu implementación

1. **Crea un DOCX de prueba** que haga referencia a una fuente que sepas que no está en la máquina (por ejemplo, “Comic Sans MS” en una imagen Docker mínima).  
2. Ejecuta la aplicación de consola o el endpoint API.  
3. Verifica que la consola (o la respuesta HTTP) enumere la advertencia de sustitución.  
4. Opcionalmente, abre el PDF resultante y revisa las propiedades de la fuente —Aspose.Words debería mostrar la fuente de respaldo que configuraste.

Si ves la advertencia pero el PDF aún usa una fuente inesperada, revisa el orden de `SubstitutionSettings`; la primera coincidencia gana.

---

## ## Conclusión

Hemos cubierto todo lo necesario para **manejar la sustitución de fuentes** en Aspose.Words, desde registrar un manejador de advertencias hasta detectar programáticamente **fuentes faltantes** e incluso reemplazarlas con una tipografía corporativa. Al aprovechar el sistema de advertencias incorporado obtienes visibilidad total sobre cada evento “fuente no encontrada”, lo que responde directamente a la pregunta “**cómo detectar fuentes faltantes**?” que todo desarrollador se plantea al automatizar la generación de documentos.

¿Qué sigue? Prueba combinar esta lógica con **carga dinámica de fuentes** (`FontSettings.SetFontsFolder`) para admitir fuentes subidas por el usuario en tiempo real, o extiende el manejador de advertencias para escribir entradas en un servicio de registro central como Serilog. Cuanto más instrumentes el manejo de fuentes, más fiable será tu canal de documentos.

¿Tienes un escenario de sustitución de fuentes complicado que te está dando problemas? Deja un comentario abajo y solucionemoslo juntos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}