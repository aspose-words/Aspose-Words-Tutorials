---
category: general
date: 2026-02-28
description: Aprende a manejar advertencias de fuentes y detectar fuentes faltantes
  en Aspose.Words usando C#. Guía completa paso a paso con código completo.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: es
og_description: Maneja advertencias de fuentes en Aspose.Words y detecta fuentes faltantes
  con un ejemplo listo para ejecutar en C#. Sigue los pasos y observa la salida.
og_title: Manejar advertencias de fuentes en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- Document Loading
title: Manejar advertencias de fuentes en Aspose.Words – Detectar fuentes faltantes
url: /es/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manejar advertencias de fuentes en Aspose.Words – Detectar fuentes faltantes

¿Alguna vez necesitaste **manejar advertencias de fuentes** al cargar un documento Word y te preguntaste por qué algún texto se ve extraño? No estás solo. Las fuentes faltantes generan advertencias de sustitución que pueden corromper silenciosamente el diseño visual, y si no **detectas fuentes faltantes** nunca sabrás qué salió mal.

En este tutorial te mostraremos una forma práctica de **manejar advertencias de fuentes** usando `IWarningCallback` de Aspose.Words. Al final de la guía podrás detectar cada evento de sustitución de fuente, registrarlo e incluso decidir si abortar la carga. Sin documentación externa, solo un ejemplo listo para copiar y pegar.

## Lo que aprenderás

- Configurar un manejador de advertencias personalizado que reaccione solo a alertas de sustitución de fuentes.  
- Adjuntar el manejador a `LoadOptions` para que cada carga de documento pase por él.  
- Verificar la salida en la consola y entender qué significa cada advertencia.  

**Requisitos previos**

- .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+).  
- Aspose.Words para .NET instalado vía NuGet (`Install-Package Aspose.Words`).  
- Un archivo Word que haga referencia a una fuente no instalada en tu máquina (por ejemplo, una fuente corporativa personalizada).  

Si te falta alguno de estos, consíguelo ahora; de lo contrario, vamos al grano.

## Cómo manejar advertencias de fuentes en Aspose.Words

A continuación tienes el programa completo y ejecutable. Incluye todo, desde las sentencias `using` hasta el método `Main`, para que puedas pegarlo en una aplicación de consola y pulsar **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Salida esperada de la consola** (suponiendo que el documento usa una fuente que no tienes instalada):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Si el documento **no contiene fuentes faltantes**, la línea de advertencia nunca aparece, por lo que habrás **detectado fuentes faltantes** solo cuando era necesario.

### Por qué funciona

Aspose.Words lanza un `WarningInfo` por cada problema no crítico que encuentra al analizar un archivo. Al implementar `IWarningCallback` obtienes un punto de enganche en ese flujo. La bandera `WarningType.FontSubstitution` te indica precisamente cuándo la biblioteca tuvo que reemplazar una fuente solicitada por una alternativa. Esta es la forma más fiable de **manejar advertencias de fuentes** porque se ejecuta *durante* la carga, antes de que toques el modelo de objetos del documento.

## Detectar fuentes faltantes sin romper tu aplicación

A veces querrás tratar una fuente faltante como un error fatal—tal vez las directrices de tu marca prohíban cualquier sustitución. Puedes modificar el manejador para lanzar una excepción en lugar de solo registrar:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Ahora el bloque `try…catch` alrededor de `new Document(...)` capturará el problema, permitiéndote decidir si abortar, usar una alternativa o solicitar al usuario.

## Bonus: Visualizar advertencias en una aplicación UI

Si estás construyendo una aplicación WinForms o WPF, reemplaza `Console.WriteLine` por una llamada amigable con la UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

De esa forma, los usuarios finales verán la advertencia inmediatamente, y seguirás **manejando advertencias de fuentes** de forma consistente en todas las plataformas.

## Errores comunes y consejos profesionales

- **Error:** Olvidar establecer `WarningCallback`. El comportamiento predeterminado es ignorar las advertencias de fuentes, por lo que nunca las verás.  
  **Consejo:** Siempre crea una instancia de `LoadOptions` aunque solo necesites el manejador de advertencias. Es barato y explícito.  

- **Error:** Usar el separador de rutas incorrecto en sistemas operativos que no son Windows.  
  **Consejo:** Usa `Path.Combine` o una cadena literal cruda (`@"C:\Docs\MissingFont.docx"` funciona en Windows; en Linux usa `"/home/user/docs/MissingFont.docx"`).  

- **Error:** Suponer que la advertencia se disparará para fuentes incrustadas.  
  **Consejo:** Las fuentes incrustadas se consideran presentes, por lo que no aparece ninguna advertencia de sustitución. Prueba con fuentes realmente *faltantes* para ver el manejador en acción.  

- **Error:** Registrar en exceso cada tipo de advertencia.  
  **Consejo:** Filtra por `WarningType.FontSubstitution` como se muestra—esto mantiene la consola limpia y se centra en el escenario de **detect missing fonts**.  

## Recapitulación del ejemplo completo

Aquí tienes el programa entero nuevamente, esta vez sin comentarios para quienes prefieren una vista limpia:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Copia, pega, ejecuta—tu consola ahora **manejará advertencias de fuentes** y **detectará fuentes faltantes** automáticamente.

## Próximos pasos

- **Registrar en un archivo:** Sustituye `Console.WriteLine` por un logger (por ejemplo, NLog) para trazas de nivel producción.  
- **Procesamiento por lotes:** Recorre una carpeta de documentos, recopilando todos los eventos de sustitución de fuentes en un informe CSV.  
- **Instalación automática de fuentes:** Conecta el manejador de advertencias para descargar fuentes faltantes desde un repositorio corporativo antes de que continúe la carga.  

Cada una de estas extensiones se basa en la idea central de **manejar advertencias de fuentes** de forma limpia y reutilizable.

---

*¡Feliz codificación! Si encuentras alguna anomalía al intentar **detect missing fonts**, deja un comentario abajo. Con gusto te ayudaré a resolverlo.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}