---
category: general
date: 2026-05-23
description: Establezca la devolución de llamada de advertencia de Aspose para capturar
  advertencias de sustitución de fuentes en Aspose.Words. Aprenda sobre LoadOptions,
  FontSettings y la implementación de IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: es
og_description: Establezca la devolución de llamada de advertencia de Aspose para
  monitorizar la sustitución de fuentes en Aspose.Words. Este tutorial muestra LoadOptions,
  FontSettings y la implementación del manejador de advertencias.
og_title: Establecer la devolución de llamada de advertencia en Aspose – Guía paso
  a paso
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Establecer la devolución de llamada de advertencia en Aspose – Guía completa
  para la carga de documentos Word
url: /es/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# establecer callback de advertencia aspose – Guía completa para la carga de documentos Word

¿Alguna vez te has preguntado cómo **establecer callback de advertencia aspose** para no perder nunca una alerta de sustitución de fuentes? No estás solo. Cuando un DOCX hace referencia a una fuente que no está instalada, Aspose.Words la sustituye silenciosamente, y sin un callback adecuado es posible que nunca sepas que algo cambió.

En este tutorial recorreremos un ejemplo completo y ejecutable que muestra exactamente cómo capturar esas advertencias. Al final entenderás **Aspose.Words LoadOptions**, cómo configurar **FontSettings**, y por qué implementar **IWarningCallback** es la manera más limpia de mantenerte informado. Sin rodeos, solo el código que puedes incorporar a un proyecto .NET hoy mismo.

## Lo que aprenderás

- Cómo **establecer callback de advertencia aspose** en una instancia de `LoadOptions`.  
- El papel de **Aspose.Words LoadOptions** al abrir un documento.  
- Configurar el manejo de **sustitución de fuentes Aspose** con `FontSettings`.  
- Escribir una implementación personalizada de **IWarningCallback** para registrar problemas de fuentes.  
- Cargar un documento de forma segura siguiendo las mejores prácticas de **carga de documentos Aspose**.

### Requisitos previos

- .NET 6.0 o superior (el código también funciona en .NET Framework 4.5+).  
- Una licencia válida de Aspose.Words para .NET o una clave de prueba.  
- Visual Studio, Rider o cualquier editor de C# que prefieras.  
- Un DOCX de ejemplo (`fontTest.docx`) que haga referencia a una fuente faltante (opcional pero útil).

> **Consejo profesional:** Si no tienes un DOCX con fuente faltante, simplemente cambia el nombre de una fuente en el estilo del documento y observa cómo se dispara la advertencia.

---

## Cómo establecer callback de advertencia aspose para la carga de documentos

A continuación tienes el programa completo y autocontenido. Guárdalo como `Program.cs`, restaura los paquetes NuGet y ejecútalo. La consola imprimirá cada advertencia de sustitución de fuentes que Aspose.Words genere al cargar el archivo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Salida esperada en la consola

Si `fontTest.docx` hace referencia a una fuente que no está instalada, verás algo como:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Si todas las fuentes están presentes, la única línea impresa será *Document loaded successfully*—sin advertencias, sin ruido.

![ejemplo de establecer callback de advertencia aspose](image.png "ejemplo de establecer callback de advertencia aspose")

---

## Entendiendo LoadOptions en Aspose.Words

`LoadOptions` es la puerta de entrada a cada ajuste que puedes hacer en la **carga de documentos Aspose**. Permite:

1. **Especificar un `FontSettings` personalizado** – útil cuando tu aplicación incluye sus propias fuentes.  
2. **Adjuntar un callback de advertencia** – exactamente lo que hicimos para capturar sustituciones de fuentes.  
3. Controlar la detección del formato del documento, el manejo de contraseñas y más.

Como `LoadOptions` se pasa al constructor de `Document`, la configuración se aplica **una sola vez**, justo en el momento en que el archivo se analiza. Por eso podemos garantizar que nuestro manejador de advertencias verá cada sustitución antes de que el documento se construya en memoria.

### Cuándo usar un LoadOptions personalizado

- **Procesamiento por lotes** de muchos archivos donde deseas una estrategia de registro uniforme.  
- **Servicios en la nube** que necesitan reportar fuentes faltantes al llamador.  
- **Pipelines de pruebas** que verifican que los documentos cumplan con una política corporativa de fuentes.

---

## Configurando FontSettings para la sustitución de fuentes Aspose

El objeto `FontSettings` controla cómo Aspose.Words resuelve las fuentes. Por defecto busca en las carpetas de fuentes del sistema y, si no encuentra, recurre a sustitutos incorporados. Puedes afinar este comportamiento:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Estas líneas son opcionales para el escenario básico de “establecer callback de advertencia aspose”, pero ilustran cómo puedes **reducir** el número de advertencias de sustitución proporcionando las fuentes correctas de antemano.

---

## Implementando IWarningCallback para advertencias de sustitución de fuentes

La interfaz `IWarningCallback` es diminuta—solo un método `Warning`. Sin embargo te brinda **control total** sobre cómo se manejan las advertencias:

- **Registrar en un archivo** en lugar de la consola.  
- **Recopilar advertencias** en una lista para análisis posterior.  
- **Lanzar excepciones** para advertencias críticas (p. ej., cuando falta una fuente obligatoria).

Aquí tienes un ejemplo rápido que almacena las advertencias en un `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Luego podrías inspeccionar `handler.Messages` después de cargar el documento para decidir si abortar el procesamiento.

---

## Cargando un documento con manejo de advertencias personalizado (flujo completo)

Uniendo todo, el patrón final que probablemente reutilizarás se ve así:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Este fragmento demuestra el flujo de **carga de documentos Aspose** que usarás en producción: configurar, cargar y luego reaccionar. El patrón escala sin problemas, ya sea que proceses un solo archivo o recorras miles.

---

## Preguntas frecuentes y casos límite

**¿Qué pasa si el documento está protegido con contraseña?**  
Añade `Password = "secret"` al inicializador de `LoadOptions`. El callback de advertencia sigue funcionando una vez que el archivo se descifra.

**¿El callback se dispara para otros tipos de advertencia?**  
Sí—`WarningInfo.Type` puede ser `DocumentStructure`, `UnsupportedFileFormat`, etc. En nuestro ejemplo filtramos `FontSubstitution`, pero puedes registrar todo eliminando la condición `if`.

**¿Afecta esto al rendimiento?**  
De forma insignificante. El callback se invoca solo cuando ocurre una advertencia, lo cual es mucho menos frecuente que los pasos normales de análisis.

**¿Puedo desactivar la sustitución de fuentes por completo?**  
Puedes establecer `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` pero entonces Aspose.Words lanzará una excepción por fuentes faltantes en lugar de sustituirlas.

---

## Conclusión

Ahora sabes exactamente cómo **establecer callback de advertencia aspose** para monitorizar eventos de sustitución de fuentes durante el procesamiento con **Aspose.Words LoadOptions**. Configurando `FontSettings`, implementando un `IWarningCallback` ligero y cargando el documento con esas opciones, obtienes visibilidad total sobre cualquier cambio de fuente que Aspose realice tras bambalinas.

A partir de aquí podrías:

- Extender el manejador de advertencias para escribir en un servicio de registro central.  
- Combinar el callback con una estrategia personalizada de sustitución de fuentes.  
- Utilizar el patrón al construir una API en la nube que valide documentos subidos por clientes.

Pruébalo con tus propios archivos DOCX, ajusta `FontSettings` y observa cómo la consola te indica exactamente qué fuentes fueron sustituidas. ¡Feliz codificación, y que tus documentos siempre se rendericen como esperas!

## Tutoriales relacionados

- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Habilitar advertencias de sustitución de fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cómo establecer LoadOptions en Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}