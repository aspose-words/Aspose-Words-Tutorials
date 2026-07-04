---
category: general
date: 2026-06-24
description: Cómo usar IWarningCallback para detectar fuentes faltantes en documentos
  Aspose.Words. Aprende un ejemplo completo y ejecutable y las mejores prácticas.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: es
og_description: Cómo usar IWarningCallback para detectar fuentes faltantes en Aspose.Words.
  Sigue la guía paso a paso para una solución completa y lista para producción.
og_title: Cómo usar IWarningCallback – Detectar fuentes faltantes
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo usar IWarningCallback – Detectar fuentes faltantes con Aspose.Words
url: /es/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo usar IWarningCallback – Detectar fuentes faltantes con Aspose.Words

Cómo usar **IWarningCallback** es esencial cuando trabajas con Aspose.Words y necesitas **detectar fuentes faltantes** en un archivo DOCX. En esta guía recorreremos un ejemplo completo, listo para copiar y pegar, que muestra exactamente cómo usar IWarningCallback para capturar advertencias de sustitución de fuentes, por qué es importante y qué hacer una vez que las hayas capturado.

Si alguna vez has abierto un documento y has visto texto distorsionado porque una fuente personalizada no estaba instalada, conoces la frustración. Al final de este tutorial tendrás una forma fiable de exponer esos problemas programáticamente, registrarlos o incluso aplicar una fuente de respaldo automáticamente.

## Lo que aprenderás

- El propósito de **IWarningCallback** y cuándo usarlo.  
- Cómo implementar un recopilador de advertencias personalizado que aísle los eventos de **detect missing fonts**.  
- Cómo conectar el recopilador a **LoadOptions** para que cada carga de documento sea monitorizada.  
- Verificar la salida y manejar casos extremos (múltiples fuentes faltantes, advertencias silenciosas, etc.).  

### Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.6+).  
- Aspose.Words para .NET instalado vía NuGet (`Install-Package Aspose.Words`).  
- Un archivo DOCX que haga referencia a una fuente que no esté presente en la máquina (p. ej., `DocumentWithMissingFont.docx`).  

No se requieren bibliotecas adicionales; todo vive dentro de Aspose.Words.

---

## Cómo usar IWarningCallback para detectar fuentes faltantes en Aspose.Words

A continuación se muestra el **programa completo y ejecutable**. Cópialo en un nuevo proyecto de consola, ajusta la ruta del archivo y ejecútalo. Verás la salida en consola para cada advertencia de fuente faltante.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Salida esperada

Si `DocumentWithMissingFont.docx` hace referencia a una fuente llamada *“MyFancyFont”* que no está instalada, verás algo como:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Cada línea con el prefijo **[Missing Font]** es generada por nuestra implementación de **IWarningCallback**, demostrando que hemos **detectado fuentes faltantes** con éxito.

---

## Paso 1: Implementar la interfaz IWarningCallback

¿Por qué necesitamos una clase personalizada? Aspose.Words genera **advertencias** por diversas razones—problemas de formato, características obsoletas y, lo más importante para nosotros, sustitución de fuentes. Al implementar `IWarningCallback`, obtenemos un punto de enganche que recibe cada advertencia en el momento en que ocurre. Filtrar por `WarningType.FontSubstitution` aísla el escenario específico en el que una fuente falta.

**Consejo profesional:** Si necesitas capturar *todas* las advertencias para diagnóstico, simplemente elimina la comprobación `if` y registra cada `info.Type`.

---

## Paso 2: Conectar la devolución de llamada a LoadOptions

`LoadOptions` es la puerta de entrada que indica a Aspose.Words cómo tratar el documento entrante. Asignar `WarningCallback` a una instancia de nuestro recopilador garantiza que la devolución de llamada esté activa durante toda la operación de carga. Puedes reutilizar el mismo objeto `LoadOptions` para varios documentos, lo cual es útil en tuberías de procesamiento por lotes.

**Pregunta frecuente:** *¿Qué pasa si cargo un documento sin especificar LoadOptions?*  
Respuesta: Aspose.Words seguirá generando advertencias internamente, pero sin una devolución de llamada se descartan silenciosamente, y pierdes la oportunidad de **detect missing fonts**.

---

## Paso 3: Cargar un documento y capturar advertencias de fuentes faltantes

El constructor `Document` que recibe una ruta de archivo y `LoadOptions` realiza el trabajo pesado. A medida que el archivo se analiza, cualquier fuente faltante activa nuestro método `FontWarningCollector.Warning`. La salida en consola prueba que el mecanismo funciona.

**Caso extremo:** Un solo documento puede hacer referencia a varias fuentes ausentes. La devolución de llamada se dispara una vez por cada fuente faltante, por lo que verás múltiples líneas—perfecto para crear un informe completo.

---

## ¿Por qué usar IWarningCallback en lugar de comprobaciones manuales de fuentes?

Podrías escanear manualmente las propiedades `Run.Font` del documento después de cargarlo, pero eso requeriría que el documento se cargara con éxito primero—algo que falla si la fuente está completamente indisponible. El sistema de advertencias funciona **antes** de que ocurra cualquier sustitución, dándote una visión real de lo que falta.

Además, la devolución de llamada se ejecuta **como parte del pipeline de carga**, lo que permite abortar temprano, reemplazar fuentes sobre la marcha o registrar diagnósticos detallados sin pasadas adicionales sobre el árbol del documento.

---

## Manejar múltiples fuentes faltantes de forma elegante

Si anticipas muchas fuentes faltantes, considera agregarlas a una colección:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Después de la carga, puedes iterar sobre `MissingFonts` y, por ejemplo, escribirlas en un archivo CSV para el equipo de diseño.

---

## Bonus: Registrar advertencias en un archivo

La salida en consola está bien para demostraciones, pero el código de producción suele registrar en un almacén persistente. Sustituye la llamada `Console.WriteLine` por algo como:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Ahora dispones de una pista de auditoría que puede revisarse más tarde, cumpliendo con requisitos de cumplimiento.

---

## Conclusión

Hemos cubierto **cómo usar IWarningCallback** para **detect missing fonts** en Aspose.Words, desde la implementación de la devolución de llamada hasta su integración en `LoadOptions` y el manejo de las advertencias resultantes. Este enfoque te brinda información en tiempo real sobre problemas relacionados con fuentes, permitiéndote registrar, reemplazar o alertar a los usuarios antes de que el documento se renderice.

Próximos pasos que podrías explorar:

- **Fuentes de respaldo:** asignar programáticamente una fuente predeterminada cuando ocurre una sustitución.  
- **Procesamiento por lotes:** iterar sobre una carpeta de documentos, reutilizando el mismo `AggregatingFontCollector`.  
- **Retroalimentación al usuario:** mostrar advertencias de fuentes faltantes en una UI en lugar de la consola.

Pruébalo en tu propio proyecto—no más texto misterioso y distorsionado, solo diagnósticos claros y accionables. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo cargar DOCX y detectar fuentes faltantes – Guía completa en C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cómo usar LoadOptions en Aspose.Words – Guía completa](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}