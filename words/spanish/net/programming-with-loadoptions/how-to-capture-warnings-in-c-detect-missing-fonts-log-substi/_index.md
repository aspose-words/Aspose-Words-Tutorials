---
category: general
date: 2026-04-04
description: Aprenda a capturar advertencias, detectar fuentes faltantes y registrar
  eventos de sustitución usando Aspose.Words LoadOptions en C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: es
og_description: Cómo capturar advertencias, detectar fuentes faltantes y registrar
  eventos de sustitución usando Aspose.Words LoadOptions en C#.
og_title: Cómo capturar advertencias en C# – Detectar fuentes faltantes y registrar
  sustituciones
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Cómo capturar advertencias en C# – Detectar fuentes faltantes y registrar sustituciones
url: /es/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar advertencias en C# – Detectar fuentes faltantes y registrar sustituciones

¿Alguna vez te has preguntado **cómo capturar advertencias** que aparecen al cargar un documento Word con fuentes faltantes? No estás solo. En muchos proyectos reales, las fuentes se pierden durante la migración y el reemplazo silencioso puede romper tu diseño. ¿La buena noticia? Aspose.Words te ofrece una forma limpia de escuchar esas advertencias, detectar fuentes faltantes e incluso registrar cada sustitución para que puedas corregir la causa más adelante.

En este tutorial recorreremos una solución completa, lista para ejecutar, que muestra **cómo capturar advertencias**, demuestra **cómo detectar fuentes faltantes** y explica **cómo registrar eventos de sustitución**. Al final, tendrás un manejador de advertencias reutilizable, un objeto `LoadOptions` totalmente configurado y una salida de consola de ejemplo que podrás verificar.

> **Prerequisite:** Necesitas Aspose.Words for .NET (v24.x o posterior) instalado vía NuGet y un entorno básico de desarrollo en C# (Visual Studio 2022 o VS Code funcionan bien).

---

## Cómo capturar advertencias al cargar documentos

El núcleo de la solución es una clase que implementa `IWarningCallback`. Aspose.Words llama a este callback automáticamente para cada advertencia generada durante la carga del documento, incluidas las advertencias de sustitución de fuentes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> Al filtrar por `WarningType.FontSubstitution` evitamos el desorden de advertencias no relacionadas (como características obsoletas). Esto mantiene el registro centrado en el problema exacto que te importa: fuentes faltantes.

---

## Detectar fuentes faltantes con Aspose.Words

Cuando un documento hace referencia a una fuente que no está instalada en la máquina, Aspose.Words sustituye la más cercana y genera una advertencia. Nuestro manejador anterior capturará cada ocurrencia, detectando efectivamente **fuentes faltantes**.

Para verlo en acción, necesitamos configurar `LoadOptions` y adjuntar el manejador:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** Si prefieres recopilar advertencias para procesarlas después (por ejemplo, escribirlas en un archivo), reemplaza `Console.WriteLine` con código que añada el mensaje a una `List<string>`.

---

## Cómo registrar eventos de sustitución

Registrar es tan simple como dirigir la salida de la advertencia a un almacenamiento persistente. A continuación tienes un ejemplo rápido que escribe cada advertencia de sustitución en un archivo de texto llamado `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> Los registros persistentes te permiten auditar problemas de fuentes a lo largo de múltiples ejecuciones, automatizar alertas o alimentar los datos en una verificación de pipeline de compilación.

---

## Ejemplo completo funcional

Uniendo todo, aquí tienes una aplicación de consola autocontenida que puedes copiar, pegar y ejecutar. Demuestra **cómo capturar advertencias**, **detecta fuentes faltantes** y **cómo registrar sustituciones** en un solo paso.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Salida esperada en la consola

Si `input.docx` hace referencia a una fuente que no está instalada, verás algo como:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Si cambias a `FileLoggingWarningHandler`, las mismas líneas aparecerán dentro de `font-warnings.log` con marcas de tiempo.

![salida de consola de captura de advertencias](image-placeholder.png)

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito capturar *todas* las advertencias, no solo las de sustitución de fuentes?

Simplemente elimina la comprobación `if (info.Type == WarningType.FontSubstitution)`. El callback recibirá cada tipo de advertencia (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, etc.). Luego puedes ramificar según `info.Type` para manejar cada caso de forma diferente.

### ¿Esto funciona con PDFs o solo con documentos Word?

`LoadOptions` e `IWarningCallback` forman parte de Aspose.Words, por lo que se aplican a formatos compatibles con Word (`.docx`, `.doc`, `.rtf`, `.html`). Para PDFs deberías usar los mecanismos de advertencia propios de Aspose.PDF.

### ¿Cómo puedo suprimir advertencias en lugar de registrarlas?

Establece `LoadOptions.WarningCallback = null` o implementa el callback pero deja el cuerpo del método vacío. La biblioteca seguirá realizando la sustitución de forma silenciosa.

### ¿Qué hay de la seguridad en entornos multihilo?

La instancia del callback se invoca en el mismo hilo que carga el documento, por lo que no necesitas sincronización adicional a menos que compartas el manejador entre cargas paralelas. En ese caso, protege los recursos compartidos (por ejemplo, el archivo de registro) con un bloqueo o usa colecciones concurrentes.

---

## Conclusión

Hemos cubierto **cómo capturar advertencias** de Aspose.Words, te hemos mostrado **cómo detectar fuentes faltantes** y explicado **cómo registrar eventos de sustitución** para su análisis posterior. Al conectar una simple implementación de `IWarningCallback` a `LoadOptions`, obtienes total visibilidad sobre los problemas relacionados con fuentes sin ensuciar tu base de código.

¿Próximos pasos? Prueba a extender el registrador para enviar correos electrónicos, integrarlo con Azure Monitor o instalar automáticamente fuentes faltantes en un servidor de compilación. También puedes explorar otros tipos de advertencia: `WarningType.DegradedDocument` puede alertarte sobre características que no sobrevivieron al proceso de conversión.

¿Tienes más preguntas sobre el manejo de fuentes o Aspose.Words en general? Deja un comentario o abre un nuevo tema en los foros de Aspose. ¡Feliz codificación y que tus documentos siempre se rendericen con la tipografía correcta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}