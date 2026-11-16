---
category: general
date: 2026-11-15
description: Aprende cómo traducir texto con Google en C#. Este tutorial muestra un
  ejemplo de Google Translate, manejando varios idiomas y buenas prácticas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: es
lastmod: 2026-11-15
og_description: Cómo traducir texto con Google en C# usando un ejemplo completo de
  Google Translate. Sigue este tutorial para traducir varios idiomas de forma segura.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Cómo traducir texto con la API de Google Translate en C# – tutorial rápido
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Cómo traducir texto con la API de Google Translate en C# – guía paso a paso
url: /es/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo traducir texto con la API de Google Translate en C# – guía paso a paso

Si necesitas **cómo traducir texto** en una aplicación .NET, la API de Google Cloud Translation ofrece una solución fiable y agnóstica al idioma. En este tutorial verás un **ejemplo de Google Translate** que traduce una cadena simple, se amplía para **traducir varios idiomas**, y sigue las mejores prácticas para claves de API y manejo de errores.

Obtendrás un programa de consola C# listo para ejecutar, una comprensión clara de **traducir texto con Google**, y la confianza para adaptar el código a proyectos más grandes.

## Qué cubre este tutorial

* Configurar un proyecto de Google Cloud y obtener una clave de API.  
* Instalar el paquete NuGet `Google.Cloud.Translation.V2`.  
* Escribir código limpio y reutilizable que **cómo traducir texto** usando el SDK oficial.  
* Ampliar la solución para **traducir varios idiomas** en una sola llamada.  
* Problemas comunes y consejos para implementaciones de nivel producción.

### Requisitos previos

* .NET 6.0 SDK o posterior (el código se compila con .NET Core y .NET Framework).  
* Una cuenta de Google Cloud con la **API de Cloud Translation** habilitada.  
* Familiaridad básica con C# y aplicaciones de consola.  

---

## Paso 1: Instalar la biblioteca cliente de Google Cloud Translation

La biblioteca cliente oficial abstrae las llamadas HTTP y maneja la autenticación por ti.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Ejecutar el comando agrega el paquete `Google.Cloud.Translation.V2` a tu proyecto, dándote acceso a la clase `TranslationClient` utilizada a lo largo de esta guía.

> **Por qué este paso es importante** – Usar el SDK evita la construcción manual de solicitudes, reduce errores y garantiza que estés alineado con la última versión de la API de Google.

## Paso 2: Crear un asistente de traducción reutilizable

Encapsular la lógica de traducción en una clase estática hace que el código sea reutilizable y aísla el manejo de la clave de API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Por qué devolvemos un diccionario** – Cuando necesitas **traducir varios idiomas**, organizar los resultados por código de idioma facilita el procesamiento posterior.

## Paso 3: Construir la aplicación de consola que usa el asistente

A continuación se muestra un `Program.cs` completo que demuestra tanto una traducción de texto único como una traducción por lotes.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Salida esperada en la consola**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **¿Por qué los bloques try/catch?** – Los errores de red, los límites de cuota o una clave de API inválida generan excepciones. Manejarlo de forma elegante mejora la experiencia del usuario y mantiene estable tu aplicación.

## Paso 4: Asegurar tu clave de API

Incrustar la clave de API en el código, como se muestra arriba, es aceptable para una demostración rápida pero no para producción. Sigue estas prácticas:

* Almacena la clave en una variable de entorno (`GOOGLE_API_KEY`) y léela en tiempo de ejecución:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Usa **Google Application Default Credentials** en lugar de una clave de API al ejecutar en Google Cloud (App Engine, Cloud Run, etc.).
* Restringe la clave a la API de Translation en la consola de Google Cloud y limita su uso a direcciones IP o referenciadores específicos.

## Paso 5: Ampliar la solución para escenarios del mundo real

### Detección de idioma

Si necesitas conocer el idioma de origen, el objeto de respuesta contiene `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Traducir documentos grandes

La API admite hasta 30 KB por solicitud. Para textos más extensos, divide el contenido en fragmentos, traduce cada fragmento y luego concatena los resultados. Mantén los límites de oración intactos para evitar frases torpes.

### Limitación de velocidad y cuotas

Google impone límites de solicitudes por minuto. Implementa una política de reintentos con retroceso exponencial para respetar los límites de cuota y evitar errores `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Preguntas comunes y casos límite

**Q: ¿Puedo traducir una página HTML completa?**  
A: Sí. Usa el parámetro `Format` (`"text"` o `"html"`) al llamar a `TranslateText`. El SDK expone esto mediante la sobrecarga de `TranslateText` que acepta un `TranslateTextRequest`.

**Q: ¿Qué pasa si un idioma no está soportado?**  
A: La API devuelve un error. Valida los códigos de idioma contra la lista devuelta por `client.ListSupportedLanguages()` antes de hacer una solicitud.

**Q: ¿La API cobra por carácter?**  
A: Google factura por carácter traducido. Estima los costos usando la página de precios y considera almacenar en caché traducciones frecuentes.

## Conclusión

Ahora sabes **cómo traducir texto** en C# usando la API oficial de Google Translate. El tutorial cubrió un **ejemplo de Google Translate**, demostró **traducir varios idiomas**, y resaltó prácticas listas para producción como la seguridad de la clave de API y el manejo de errores. Al reutilizar el asistente `Translator`, puedes integrar la traducción en cualquier servicio .NET, aplicación de escritorio o microservicio.

**Próximos pasos**

- Explora el **tutorial de Google Translate** para funciones avanzadas como glosarios y modelos personalizados.  
- Combina este código con ASP.NET Core para crear una API web multilingüe.  
- Experimenta con la traducción por lotes de archivos CSV para automatizar pipelines de localización.

¡Feliz codificación y disfruta creando aplicaciones accesibles globalmente!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [traducir docx a francés con Aspose.Words y Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Cómo guardar documento Word traducido en C# con Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Traducir cadena a español en C# con Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}