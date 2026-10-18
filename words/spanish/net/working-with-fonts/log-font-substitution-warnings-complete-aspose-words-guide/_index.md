---
category: general
date: 2026-01-14
description: Registra advertencias de sustitución de fuentes al cargar documentos
  Word con Aspose.Words. Aprende a detectar fuentes faltantes y cómo capturarlas en
  C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: es
og_description: Registra advertencias de sustitución de fuentes al cargar documentos
  Word con Aspose.Words. Descubre cómo detectar fuentes faltantes y capturarlas en
  C#.
og_title: Advertencias de sustitución de fuentes del registro – Guía completa de Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Registro de advertencias de sustitución de fuentes – Guía completa de Aspose.Words
url: /es/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registro de advertencias de sustitución de fuentes – Guía completa de Aspose.Words

Registrar advertencias de sustitución de fuentes es esencial cuando necesitas garantizar que un documento Word se vea exactamente igual después de ser cargado por Aspose.Words. Si alguna vez te has preguntado cómo **detectar fuentes faltantes** o quieres saber **cómo capturar fuentes faltantes**, estás en el lugar correcto.  

En este tutorial recorreremos un escenario del mundo real, te mostraremos el código C# completo y explicaremos por qué cada línea es importante. Al final podrás registrar cada evento de sustitución de fuentes y actuar en consecuencia—sin advertencias misteriosas que queden sin resolver.

![Ejemplo de registro de advertencias de sustitución de fuentes](/images/font-warnings.png "Captura de pantalla que muestra la salida de consola del registro de advertencias de sustitución de fuentes")

## Lo que aprenderás

- Cómo configurar `LoadOptions` para que Aspose.Words genere advertencias tipadas para la sustitución de fuentes.  
- Los pasos exactos para **detectar fuentes faltantes** durante la carga del documento.  
- Una forma limpia de **capturar fuentes faltantes** y escribirlas en tu propio registro o sistema de monitoreo.  
- Manejo de casos límite (p. ej., cuando un documento contiene una fuente que no está instalada en el servidor).  

### Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+).  
- Una licencia válida de Aspose.Words para .NET (o la prueba gratuita).  
- Familiaridad básica con C# y aplicaciones de consola.  

Si ya los tienes, vamos a sumergirnos.

## Paso 1 – Configurar LoadOptions para generar advertencias tipadas

El corazón de la solución está en `LoadOptions.FontSubstitutionWarning`. Al cambiarlo a `RaiseTypedWarnings` le indicas a Aspose.Words que dispare un evento **cada vez** que no pueda encontrar la fuente exacta que solicitaste.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Por qué es importante:**  
> El comportamiento predeterminado intercambia silenciosamente una fuente faltante por la coincidencia más cercana, lo que puede provocar fallos de diseño que nunca esperas. Generar advertencias tipadas te brinda total visibilidad.

## Paso 2 – Suscribirse al evento de advertencia

Ahora nos enganchamos a `loadOptions.FontSubstitutionWarning`. La lambda recibe un objeto `e` que nos indica exactamente qué fuente faltó y cuál se utilizó en su lugar.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Si ejecutas esto en un servidor web, reemplaza `Console.WriteLine` por un registrador estructurado (Serilog, NLog, etc.) para que puedas consultar los datos más tarde.

## Paso 3 – Cargar el documento usando las opciones configuradas

Con el mecanismo de advertencia en su lugar, simplemente carga el documento como lo harías normalmente. El evento se dispara automáticamente para cada fuente faltante.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Salida esperada de la consola

Si `input.docx` hace referencia a una fuente llamada *MyFancyFont* que no está instalada, verás:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Cada línea corresponde a un evento de **detectar fuentes faltantes**, brindándote un registro completo.

## Paso 4 – Manejo de casos límite y escenarios avanzados

### 4.1 Cuando no ocurre sustitución

A veces un documento solo usa fuentes del sistema que ya están presentes. En ese caso el evento de advertencia nunca se dispara, y obtendrás una consola limpia sin salida. Eso es una buena señal—tu entorno ya tiene todas las fuentes requeridas.

### 4.2 Capturando advertencias para análisis posterior

Si necesitas almacenar las advertencias para un informe nocturno, recógelas en una lista:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Después de cargar, puedes serializar `missingFonts` a JSON, escribir a una base de datos o enviar por correo un resumen.

### 4.3 Trabajando con PDFs u otros formatos

El mismo enfoque de `LoadOptions` funciona para llamadas `Load` en PDFs, RTF e incluso archivos HTML. Simplemente pasa la misma instancia de opciones, y Aspose.Words generará advertencias para cualquier fuente que no pueda coincidir.

## Paso 5 – Verificar el resultado programáticamente

Si prefieres una prueba automatizada en lugar de observar la consola, verifica que la lista contenga las entradas esperadas:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Este fragmento demuestra **cómo capturar fuentes faltantes** en código, no solo en registros.

## Errores comunes y cómo evitarlos

| Error | Por qué ocurre | Solución |
|-------|----------------|----------|
| Olvidar establecer `RaiseTypedWarnings` | El valor predeterminado es `DoNotRaise`, por lo que no se disparan eventos. | Establecer explícitamente `FontSubstitutionWarning` como se muestra en el Paso 1. |
| Usar `Console.WriteLine` en una aplicación web | La salida de consola desaparece en IIS/ASP.NET Core. | Cambiar a un registrador persistente (p. ej., Serilog). |
| Cargar un documento con una ruta relativa | El directorio de trabajo puede diferir en tiempo de ejecución. | Usar rutas absolutas o `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorar `SubstitutedFontName` | Pierdes información sobre qué fuente alternativa se eligió. | Siempre registra tanto `FontName` como `SubstitutedFontName`. |

## Bonus: Automatizando la instalación de fuentes

Si controlas el entorno de despliegue, puedes pre‑instalar las fuentes faltantes usando un script de PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Ejecutar esto antes de que inicie tu aplicación elimina la mayoría de las advertencias de **detectar fuentes faltantes** por completo.

## Conclusión

Hemos cubierto todo lo que necesitas para **registrar advertencias de sustitución de fuentes** al cargar documentos Word con Aspose.Words. Configurando `LoadOptions`, suscribiéndote al evento de advertencia y, opcionalmente, persistiendo los resultados, puedes detectar fuentes faltantes de manera fiable y entender **cómo capturar fuentes faltantes** para cualquier proyecto .NET.

Toma el código, ajusta el registrador para que se adapte a tu stack, y nunca volverás a sorprenderte con un intercambio silencioso de fuentes. Los siguientes pasos podrían incluir:

- Integrar la lista de advertencias con tu pipeline CI/CD para fallar compilaciones cuando falten fuentes críticas.  
- Extender el enfoque para monitorear el uso de fuentes en una flota de documentos.  
- Explorar la API `FontSettings` de Aspose.Words para proporcionar fuentes alternativas personalizadas.

¿Tienes preguntas o un escenario complicado? Deja un comentario y solucionemos el problema juntos. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}