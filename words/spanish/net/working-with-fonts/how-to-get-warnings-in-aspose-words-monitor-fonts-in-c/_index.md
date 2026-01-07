---
category: general
date: 2026-01-06
description: Aprenda cómo obtener advertencias al cargar documentos y cómo supervisar
  fuentes usando Aspose.Words. Esta guía cubre los callbacks de advertencias y el
  seguimiento de sustitución de fuentes.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: es
og_description: ¿Cómo obtener advertencias en Aspose.Words? Sigue este tutorial paso
  a paso para monitorear fuentes y capturar mensajes de sustitución al cargar documentos.
og_title: Cómo obtener advertencias en Aspose.Words – Monitorear fuentes
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Cómo obtener advertencias en Aspose.Words – Supervisar fuentes en C#
url: /es/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo obtener advertencias en Aspose.Words – Monitorizar fuentes en C#

¿Alguna vez te has preguntado **cómo obtener advertencias** cuando un documento de Word contiene fuentes que no tienes instaladas? Es un problema frecuente: tu aplicación sustituye silenciosamente las fuentes faltantes y nunca sabes qué cambió. La buena noticia es que puedes engancharte al sistema de advertencias de Aspose.Words y **monitorizar fuentes** en tiempo real.

En este tutorial te mostraremos exactamente cómo capturar esas advertencias de sustitución de fuentes, por qué es importante y qué hacer con la información una vez que la tengas. Sin documentación externa, solo un ejemplo completo y ejecutable que puedes pegar en Visual Studio ahora mismo.

> **Consejo profesional:** Si estás construyendo una canalización de conversión de documentos, registrar las fuentes faltantes temprano te ahorra sorpresas desagradables de maquetación más adelante.

---

## Lo que necesitarás

- **Aspose.Words for .NET** (última versión; la API no ha cambiado desde v23.10)
- Un entorno de desarrollo .NET (Visual Studio, Rider o VS Code con la extensión C#)
- Un archivo de muestra `.docx` que haga referencia a una fuente que no tienes instalada (p. ej., **“NonExistentFont”**)

¡Eso es todo! No se requieren paquetes NuGet adicionales más allá de Aspose.Words.

---

## Paso 1 – Configurar un recolector de advertencias (Palabra clave principal en el encabezado)

Lo primero que necesitas es un lugar para almacenar las advertencias a medida que ocurren. Aspose.Words proporciona la propiedad `WarningCallback` en `LoadOptions` precisamente para este propósito.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Por qué es importante:**  
Cuando la biblioteca encuentra una fuente faltante, no lanza una excepción; emite un objeto `WarningInfo`. Al conectar un recolector, obtienes visibilidad total de cada evento de sustitución, lo que te permite **monitorizar fuentes** sin ensuciar tu consola con mensajes no relacionados.

---

## Paso 2 – Cargar el documento con las opciones habilitadas para advertencias

Ahora leemos realmente el archivo. Las `LoadOptions` que preparamos en el paso anterior garantizan que cualquier advertencia relacionada con fuentes se capture.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**¿Qué ocurre bajo el capó?**  
Aspose.Words analiza el archivo de Word, resuelve las fuentes y, siempre que no puede encontrar una fuente solicitada, recurre a una sustituta (normalmente Arial). La sustitución genera una advertencia `WarningType.FontSubstitution`, que se almacena en `warningCollector`.

---

## Paso 3 – Inspeccionar las advertencias recopiladas (Palabra clave principal aparece de nuevo)

Una vez cargado el documento, simplemente iteramos sobre `warningCollector` e imprimimos los mensajes de sustitución de fuentes.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Salida esperada** (suponiendo que la fuente faltante sea *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Si el documento contiene varias fuentes desconocidas, verás una línea por cada sustitución, ideal para registro o alertas.

---

## Paso 4 – Opcional: registrar o persistir la información de advertencias

En producción probablemente querrás algo más que un `Console.WriteLine`. Aquí tienes un ejemplo rápido que escribe las advertencias en un archivo JSON para análisis posterior.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Ahora dispones de un registro permanente que puedes alimentar a un panel de monitoreo o incluso desencadenar una solicitud automática de los archivos de fuentes faltantes.

---

## Paso 5 – Verificar el resultado y limpiar

Ejecuta el programa. Si ves los mensajes de sustitución, has **obtenido advertencias** con éxito y ahora estás **monitorizando fuentes** activamente. Si no aparece nada, verifica que el documento de prueba realmente haga referencia a una fuente que no está instalada en la máquina.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Un recuento de cero suele significar una de las siguientes situaciones:

1. Todas las fuentes fueron resueltas (quizá la fuente *está* instalada localmente), o
2. El documento no contenía referencias a fuentes que requirieran sustitución.

---

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparecen advertencias** | La fuente realmente existe en el sistema, o el documento usa solo fuentes incorporadas. | Cambia el nombre de la fuente en el archivo fuente a algo imposible (p. ej., `XYZ123`) y vuelve a intentarlo. |
| **Demasiadas advertencias (ruido)** | Estás cargando muchos documentos en un bucle sin limpiar el recolector. | Vuelve a crear `WarningInfoCollection` para cada documento, o llama a `warningCollector.Clear()` después de procesar. |
| **Impacto en el rendimiento** | Un registro excesivo en disco puede ralentizar el procesamiento por lotes. | Almacena las advertencias en memoria y escríbelas en bloque, o usa I/O asíncrono. |
| **Falta `using Aspose.Words.Loading;`** | La clase `LoadOptions` pertenece a ese espacio de nombres. | Añade la directiva `using` que falta, como se muestra en el Paso 1. |

---

## Ampliando la solución – Monitorizando otros tipos de advertencias

Aunque la sustitución de fuentes es la más visible, Aspose.Words puede emitir advertencias para:

- **Características obsoletas** (`WarningType.Deprecated`),
- **Posible pérdida de datos** (`WarningType.DataLoss`),
- **Formatos de archivo no compatibles** (`WarningType.UnsupportedFileFormat`).

Puedes ampliar el filtro en el Paso 3 para capturar también estos casos:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

De esa forma no solo sabes **cómo monitorizar fuentes**, sino también **cómo obtener advertencias** para cualquier escenario que tu aplicación pueda encontrar.

---

## Ejemplo completo listo para copiar y pegar

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Ejecutarlo:** Compila el proyecto, ejecútalo y verás las advertencias impresas y guardadas. Esa es la respuesta completa a **cómo obtener advertencias** y **cómo monitorizar fuentes** con Aspose.Words.

---

## Conclusión

Ahora sabes **cómo obtener advertencias** de Aspose.Words, específicamente para escenarios de sustitución de fuentes, y has aprendido **cómo monitorizar fuentes** durante el proceso de carga del documento. Al adjuntar un `WarningCallback`, iterar los objetos `WarningInfo` recopilados y, opcionalmente, persistir los datos, obtienes total transparencia sobre los eventos de fuentes faltantes, una capacidad esencial para cualquier canalización de procesamiento de documentos.

¿Próximos pasos? Prueba a ampliar el filtro de advertencias para cubrir pérdidas de datos o advertencias de características obsoletas, o integra el registro JSON en un panel de monitoreo como Grafana. El mismo patrón funciona para todos los tipos de advertencia, así que estarás bien preparado para vigilar cualquier problema que Aspose.Words te presente.

¡Feliz codificación y que tus documentos siempre se rendericen exactamente como esperas!

---

<img src="font-warnings.png" alt="cómo obtener advertencias en Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}