---
category: general
date: 2026-06-27
description: Registre una devolución de llamada de advertencia en Aspose.Words para
  detectar sustituciones de fuentes y problemas de carga. Aprenda el uso paso a paso
  de LoadOptions con Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: es
og_description: Registre la devolución de llamada de advertencia en Aspose.Words para
  monitorear sustituciones de fuentes y otras advertencias de carga. Siga este tutorial
  completo para una implementación robusta.
og_title: Registrar la devolución de llamada de advertencia en Aspose.Words – Guía
  completa
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Registrar la devolución de llamada de advertencia en Aspose.Words – Guía completa
  de programación
url: /es/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar Callback de Advertencia en Aspose.Words – Guía Completa de Programación

¿Alguna vez te has preguntado cómo **registrar un callback de advertencia en Aspose.Words** para poder ver exactamente qué fuentes se sustituyen cuando se carga un documento? No estás solo. Muchos desarrolladores se topan con un problema cuando una sustitución de fuentes silenciosa arruina el diseño de un PDF o archivo Word generado.  

En este tutorial recorreremos una solución práctica que no solo registra un callback de advertencia en Aspose.Words, sino que también explica *por qué* querrías hacerlo, cómo funciona el callback internamente y qué casos límite podrías encontrar. Al final podrás registrar cada sustitución de fuente, capturar otras advertencias de carga y mantener tu canal de procesamiento de documentos transparente.

## Qué Aprenderás

- Configurar **LoadOptions** para controlar el comportamiento de carga del documento.  
- Registrar un **callback de advertencia** que se dispara para sustitución de fuentes y otros tipos de advertencia.  
- Cargar un DOCX con las opciones configuradas e interpretar la salida del callback.  
- Trampas comunes (fuentes faltantes, carpetas de fuentes personalizadas y consideraciones de rendimiento).  

**Requisitos previos:** Visual Studio 2022 (o cualquier IDE de C#), tiempo de ejecución .NET 6+ y una licencia activa de Aspose.Words (la prueba gratuita sirve para experimentar). No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

---

![Diagrama que ilustra el flujo de registro de un callback de advertencia en Aspose.Words y el manejo de advertencias de sustitución de fuentes](register-warning-callback-aspose-words.png "diagrama de registro de callback de advertencia aspose.words")

## Paso 1: Crear LoadOptions – El Punto de Entrada para el Manejo de Advertencias  

Antes de que el callback pueda dispararse, necesitas una instancia de **LoadOptions**. Piensa en ella como el panel de control que entregas a Aspose.Words cuando dices “carga este archivo, pero avísame si algo parece incorrecto”.  

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Por qué es importante:** `LoadOptions` te permite ajustar todo, desde contraseñas de cifrado hasta directorios de fuentes. Al adjuntar un callback de advertencia a este objeto, conviertes un proceso silencioso en uno observable.

## Paso 2: Registrar el Callback de Advertencia – Capturar Sustituciones de Fuente  

Ahora llega la estrella del espectáculo: el **callback de advertencia**. Registraremos un método anónimo (una lambda) que Aspose.Words invoca por cada advertencia de carga. Dentro del callback filtramos `WarningType.FontSubstitution` y mostramos un mensaje amigable.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Consejo profesional:** Si también deseas registrar imágenes faltantes o características no compatibles, agrega ramas `if` adicionales que verifiquen `args.WarningType`. Así tu **register warning callback in Aspose.Words** se convierte en una solución única para todos los diagnósticos de carga.

## Paso 3: Cargar el Documento Usando las LoadOptions Configuradas  

Con el callback conectado, el siguiente paso es simplemente cargar el documento. Pasa la instancia `loadOptions` al constructor de `Document`. Cada vez que Aspose.Words encuentre una fuente que no pueda encontrar, tu callback se disparará y escribirá en la consola.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Ejecuta el programa y verás una salida similar a:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Eso es el núcleo de **register warning callback aspose.words**: un patrón de tres pasos que puedes reutilizar en cualquier proyecto.

## Paso 4: Extender el Callback para Escenarios del Mundo Real  

### 4.1 Registrar en un Archivo en Lugar de la Consola  

En producción rara vez deseas spam en la consola. Sustituye `Console.WriteLine` por un logger (p. ej., `Serilog`, `NLog`) o escribe en un archivo de texto:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Proveer un Directorio de Fuentes Personalizado  

Si tu entorno usa fuentes corporativas, indica a Aspose.Words dónde buscar antes de que recurra a la sustitución:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Ahora el callback puede dispararse *menos* veces, porque el motor encuentra las fuentes correctas.

### 4.3 Manejar Advertencias que No Son de Fuente  

Puedes ampliar el alcance para capturar cualquier advertencia de carga:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Paso 5: Probar tu Implementación – Qué Esperar  

### 5.1 Verificar con un Documento que Tiene Fuentes Faltantes  

Crea un DOCX pequeño que haga referencia a una fuente no instalada en tu máquina (p. ej., “Comic Sans MS” en un servidor Linux). Ejecuta el cargador; deberías ver un mensaje de sustitución.  

### 5.2 Medir la Sobrecarga  

El callback añade una sobrecarga insignificante—aproximadamente unos pocos microsegundos por advertencia. Si cargas miles de documentos, podrías agrupar las entradas de registro o desactivar el callback en ejecuciones no críticas.

### 5.3 Casos Límite  

- **Múltiples sustituciones para la misma fuente:** Aspose.Words puede disparar el callback varias veces si la misma fuente faltante aparece en diferentes páginas. Desduplicar en tu logger si es necesario.  
- **Documentos Encriptados:** Si el DOCX está protegido con contraseña, también debes establecer `loadOptions.Password`. El callback seguirá disparándose después del descifrado.  
- **Carga Asíncrona:** La API es sincrónica, pero puedes envolver la llamada de carga en `Task.Run` para procesamiento en segundo plano; el callback sigue siendo seguro para hilos.

## Trampas Comunes y Cómo Evitarlas  

| Trampa | Por Qué Ocurre | Solución |
|--------|----------------|----------|
| **No hay salida en absoluto** | Callback no asignado *o* `WarningCallback` sobrescrito después. | Asegúrate de asignar el callback **una sola vez** antes de cargar, y no reasignes `loadOptions` después de la asignación. |
| **Excepción de conversión incorrecta** | Intentar convertir una advertencia que no es `FontSubstitutionWarningInfo`. | Siempre verifica `args.WarningType` antes de hacer cast. |
| **Ralentización del rendimiento** | Registro sincrónico a un destino de I/O lento. | Usa frameworks de registro asíncronos o almacena en búfer las escrituras. |
| **Fuentes personalizadas faltantes** | Carpeta de fuentes no añadida a `FontSettings`. | Añade `SetFontsFolder` como se muestra en el Paso 4.2. |

## Ejemplo Completo y Funcional – Copiar‑y‑Pegar  

A continuación tienes un programa autocontenido que puedes copiar en un nuevo proyecto de Aplicación de Consola. Demuestra todo el flujo de principio a fin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Salida esperada en la consola** (asumiendo fuentes faltantes):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Ejecuta el programa y verás exactamente qué fuentes sustituyó Aspose.Words, dándote total visibilidad del proceso de carga.

---

## Conclusión  

Acabamos de cubrir **cómo registrar un callback de advertencia en Aspose.Words**, por qué es una buena práctica para cualquier flujo de trabajo de procesamiento de documentos y cómo ampliar el patrón para registro, fuentes personalizadas y manejo más amplio de advertencias. Con solo tres líneas de código conviertes una operación de carga en una caja negra en un paso auditable y depurable—no más cambios de diseño misteriosos.

¿Qué sigue? Prueba combinar este callback con **Aspose.Words SaveOptions** para registrar advertencias tanto en carga *como* en guardado, o conecta el callback a una API web que procese cargas en tiempo real. También puedes explorar las demás palabras clave secundarias que introdujimos—como *loadoptions font substitution warning*—para afinar el rendimiento o integrarlo con un panel de monitoreo.

¿Tienes preguntas o un escenario complicado? Deja un comentario y solucionemos el problema juntos. ¡Feliz codificación, y que tus PDFs siempre se rendericen con las fuentes correctas!

## ¿Qué Deberías Aprender a Continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}