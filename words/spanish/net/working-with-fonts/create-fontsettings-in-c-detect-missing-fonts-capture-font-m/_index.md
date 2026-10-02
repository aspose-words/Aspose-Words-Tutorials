---
category: general
date: 2026-03-01
description: Cree FontSettings en C# para detectar fuentes faltantes, capturar mensajes
  de fuentes y manejar fuentes faltantes con Aspose.Words. Guía paso a paso para desarrolladores.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: es
og_description: Crea FontSettings en C# para detectar fuentes faltantes, capturar
  mensajes de fuentes y manejar fuentes faltantes usando Aspose.Words. Tutorial completo
  con código.
og_title: Crear FontSettings en C# – Detectar fuentes faltantes y capturar mensajes
  de fuentes
tags:
- Aspose.Words
- C#
- Font Management
title: Crear FontSettings en C# – Detectar fuentes faltantes y capturar mensajes de
  fuentes
url: /es/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear FontSettings en C# – Detectar fuentes faltantes y capturar mensajes de fuentes

¿Alguna vez necesitaste **create FontSettings** en un proyecto .NET pero no estabas seguro de cómo detectar fuentes que no están instaladas en la máquina de destino? No estás solo. En muchas aplicaciones del mundo real —piensa en generadores de informes automáticos o convertidores de documentos— las fuentes faltantes pueden romper silenciosamente el diseño, y no lo sabrás hasta que el PDF se vea extraño.  

¿Y si pudieras **detect missing fonts**, **capture font messages**, y **handle missing fonts** antes de que arruinen tu salida? La buena noticia es que Aspose.Words hace esto muy fácil. En este tutorial recorreremos todo el proceso, desde configurar el objeto `FontSettings` hasta conectar una devolución de llamada de advertencia que te indique exactamente qué glifos fueron sustituidos.

> **TL;DR:** Al final tendrás una aplicación de consola C# lista para ejecutar que registra cada sustitución de fuentes, permitiéndote decidir si incrustar un reemplazo o alertar al usuario.

---

## Requisitos previos

- .NET 6 SDK (o cualquier versión reciente de .NET)  
- Visual Studio 2022 o VS Code con extensiones de C#  
- Una licencia de Aspose.Words para .NET (la prueba gratuita funciona para esta demostración)  
- Un archivo DOCX de muestra que haga referencia a una fuente que no tengas instalada (p. ej., *Comic Sans MS* en una máquina Linux)  

No se requieren paquetes NuGet especiales más allá de `Aspose.Words`.

---

## Paso 1 – Instalar Aspose.Words y configurar el proyecto

Primero lo primero, crea un nuevo proyecto de consola e incorpora la biblioteca Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Si ya tienes una solución, simplemente agrega el paquete mediante la UI del Administrador de paquetes NuGet —facilita el seguimiento de versiones.

---

## Paso 2 – Crear FontSettings (Aparece la palabra clave principal aquí)

El paso **create FontSettings** es la piedra angular de cualquier flujo de trabajo relacionado con fuentes. `FontSettings` indica a Aspose.Words dónde buscar fuentes, si usar carpetas del sistema y cómo retroceder cuando algo falta.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

¿Por qué es importante? Sin un `FontSettings` configurado correctamente, el motor sustituye silenciosamente los glifos faltantes con la fuente predeterminada del sistema, y nunca verás una advertencia.

---

## Paso 3 – Conectar LoadOptions con FontSettings

`LoadOptions` te permite pasar el `FontSettings` al cargador de documentos. Este es el puente que permite al motor **detect missing fonts** durante la fase de construcción del `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Ahora, cada vez que cargues un DOCX con `loadOptions`, Aspose.Words consultará el `FontSettings` que configuramos anteriormente.

---

## Paso 4 – Adjuntar una devolución de llamada de advertencia para **Capture Font Messages**

Aspose.Words genera advertencias para una variedad de condiciones —siendo la sustitución de fuentes una de las más comunes. Al proporcionar una implementación de `IWarningCallback`, puedes **capture font messages** en tiempo real.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### La clase del manejador de advertencias

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

El campo `info.Description` contiene un mensaje legible por humanos como *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Este es exactamente el tipo de salida que necesitas para **handle missing fonts** de forma elegante.

---

## Paso 5 – Cargar el documento y dejar que la devolución de llamada haga su trabajo

Con todo conectado, cargar el documento es sencillo. Si el archivo fuente hace referencia a una fuente ausente del sistema, nuestro manejador de advertencias se activará.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Al ejecutar el programa, verás una salida en consola similar a:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Esa salida es la parte de **capture font messages** de nuestro flujo de trabajo. Puedes ampliar el manejador para registrar en un archivo, enviar telemetría o incluso abortar la conversión si faltan fuentes críticas.

---

## Paso 6 – Ejemplo completo funcional (Todas las piezas juntas)

A continuación hay un programa completo, listo para copiar y pegar. Pégalo en `Program.cs`, ajusta las rutas de archivo y ejecuta `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Salida esperada

Ejecutar el programa en una máquina que no tenga *Comic Sans MS* imprimirá algo como:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

También obtendrás `Result.pdf` que usa las fuentes sustituidas, asegurando que la conversión nunca se bloquee.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si quiero que la conversión falle en lugar de sustituir?** | Dentro de `FontSubstitutionWarningHandler`, lanza una excepción cuando `info.Description` contiene el nombre de una fuente crítica. |
| **¿Puedo incrustar una fuente de reemplazo automáticamente?** | Sí. Después de detectar una fuente faltante, puedes cargar un `FontInfo` de respaldo desde una ruta conocida y añadirlo a `fontSettings` mediante `fontSettings.SetFontsFolder`. |
| **¿Esto funciona en Linux/macOS?** | Absolutamente. `FontSettings` funciona multiplataforma; solo asegúrate de que la carpeta de respaldo contenga los archivos `.ttf` o `.otf` apropiados. |
| **¿La devolución de llamada de advertencia es segura para subprocesos?** | La devolución de llamada se ejecuta en el mismo hilo que carga el documento, por lo que no necesitas sincronización adicional para el registro en consola. En escenarios multihilo, protege los recursos compartidos. |
| **¿Cómo registro advertencias en un archivo?** | Reemplaza `Console.WriteLine` con `File.AppendAllText("font_warnings.log", ...)` o usa cualquier framework de registro (Serilog, NLog). |

---

## Consejos profesionales para el manejo de fuentes listo para producción

1. **Cache Font Lookups** – Reutilizar la misma instancia de `FontSettings` en múltiples cargas de documentos evita escaneos repetidos del sistema de archivos.  
2. **Whitelist Critical Fonts** – Si tu marca requiere una fuente específica, verifica su presencia temprano y aborta con un mensaje de error claro.  
3. **Use `SetFontFolder` Recursively** – Configurar `recursive: true` asegura que se escaneen subcarpetas, lo cual es útil cuando distribuyes una colección completa de fuentes.  
4. **Combine with `FontSubstitutionSettings`** – Puedes afinar las reglas de sustitución (p. ej., preferir fuentes con el mismo nombre de familia).  

---

## Conclusión

Acabamos de **create FontSettings**, configurar `LoadOptions` para **detect missing fonts**, adjuntar una devolución de llamada que **captures font messages**, y demostrar cómo **handle missing fonts** de manera limpia y lista para producción. Todo el flujo cabe en unas pocas docenas de líneas de C#, pero te brinda una visibilidad completa del panorama de fuentes de cualquier DOCX que proceses.

A continuación, podrías explorar:

- **Embedding fallback fonts** directamente en el PDF de salida (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** basándose en reglas de marca corporativa.  
- **Integrating with a CI pipeline** para marcar automáticamente documentos que usan fuentes no autorizadas.

Pruébalo, ajusta el manejador de advertencias a tus necesidades, y permite que tus canalizaciones de documentos se ejecuten con confianza —no más fallas misteriosas de diseño causadas por intercambios invisibles de fuentes.

¡Feliz codificación! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}