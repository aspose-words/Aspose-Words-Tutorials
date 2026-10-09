---
category: general
date: 2026-03-19
description: Aprenda cómo capturar advertencias en Aspose.Words, establecer la configuración
  de fuentes predeterminada y detectar fuentes faltantes al cargar un documento de
  Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: es
og_description: Cómo capturar advertencias en Aspose.Words, establecer la configuración
  de fuente predeterminada y detectar fuentes faltantes al cargar un documento de
  Word.
og_title: Cómo capturar advertencias – Configurar la fuente predeterminada
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo capturar advertencias – Configurar la fuente predeterminada
url: /es/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar advertencias – Configurar la fuente predeterminada

**Cómo capturar advertencias** es una necesidad común cuando trabajas con Aspose.Words, especialmente si tus documentos dependen de fuentes específicas que podrían no estar presentes en la máquina de destino. ¿Alguna vez abriste un DOCX y te preguntaste por qué el diseño se veía extraño? La respuesta a menudo está oculta en una advertencia sobre una fuente faltante.  

En esta guía recorreremos **cómo capturar advertencias** mientras **cargas un documento Word**, configuras **establecer la configuración de fuente predeterminada**, y finalmente **detectas fuentes faltantes** para que puedas reaccionar programáticamente. Sin rodeos—solo un ejemplo completo y ejecutable y el razonamiento detrás de cada línea.

> *Consejo profesional:* Capturar advertencias temprano te ahorra depurar misteriosos fallos de diseño más adelante.

---

## Lo que necesitarás

- **Aspose.Words for .NET** (última versión a partir de 2026).  
- Un entorno de desarrollo .NET (Visual Studio, Rider o VS Code).  
- Un DOCX de ejemplo que haga referencia a una fuente que *no* tienes instalada (p. ej., *Comic Sans MS* en una máquina Linux).  

Eso es todo. No se requieren paquetes NuGet adicionales más allá de Aspose.Words.

---

## Paso 1 – Entender por qué necesitas capturar advertencias

Cuando Aspose.Words analiza un documento, puede encontrarse con fuentes que no están disponibles en el host. Por defecto, la biblioteca sustituye silenciosamente una fuente de respaldo, lo que puede cambiar los saltos de línea, el espaciado e incluso hacer que el texto desaparezca.  

Usar el **WarningCallback** junto con un objeto **FontSettings** te brinda dos cosas:

1. **Visibilidad** – obtienes una entrada `WarningInfo` por cada sustitución.  
2. **Control** – puedes preconfigurar una fuente predeterminada para minimizar sorpresas visuales.

Piénsalo como instalar un “perro guardián” que grita cada vez que el motor cambia una pieza bajo el capó.

---

## Paso 2 – Configurar la fuente predeterminada

La primera palabra clave secundaria, **set default font settings**, aparece aquí mismo. Creas una instancia de `FontSettings` y, opcionalmente, la apuntas a una carpeta que contiene tus fuentes de respaldo.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **¿Por qué?**  
> Si no especificas una fuente de respaldo, Aspose.Words elige la primera fuente del sistema que coincida con el estilo, lo que puede ser muy diferente. Al establecer una predeterminada conocida, garantizas una representación consistente en todas las máquinas.

---

## Paso 3 – Preparar un Warning Callback para capturar advertencias

Ahora veremos **cómo capturar advertencias** adjuntando un `WarningInfoCollection` a las opciones de carga. Esta colección almacenará cada advertencia emitida durante el proceso de carga.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

El `WarningInfoCollection` implementa `IWarningCallback`, por lo que Aspose.Words inserta automáticamente cada advertencia en `warningInfos`. No se requiere sondeo.

---

## Paso 4 – Cargar documento Word con las opciones configuradas

Aquí es donde la segunda palabra clave secundaria, **load word document**, brilla. Pasamos tanto `FontSettings` como `WarningCallback` a través de una instancia de `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Si el documento hace referencia a una fuente que no está instalada, el callback de advertencias capturará una entrada `WarningType.FontSubstitution`.

---

## Paso 5 – Detectar fuentes faltantes a partir de las advertencias recopiladas

Finalmente, respondemos a la tercera palabra clave secundaria, **detect missing fonts**, iterando sobre las advertencias recopiladas.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Una salida típica se ve así:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Esa línea te indica exactamente qué fuente falta y qué fuente de respaldo se utilizó—información que puedes registrar, mostrar al usuario o incluso activar una rutina personalizada de instalación de fuentes.

---

## Ejemplo completo ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola. Demuestra **cómo capturar advertencias**, **configurar la fuente predeterminada**, **cargar documento Word** y **detectar fuentes faltantes** todo en un solo flujo.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Resultado esperado:** Cuando el DOCX especificado hace referencia a una fuente que no está instalada, la consola imprime una advertencia por cada sustitución. Si todas las fuentes están presentes, el bucle no produce salida.

---

## Errores comunes y casos límite

| Situación | Por qué ocurre | Cómo manejarlo |
|-----------|----------------|------------------|
| **No aparecen advertencias** even though the layout looks wrong | El documento puede estar usando *embedded* fonts, which Aspose.Words renders without substitution. | Check `Document.HasEmbeddedFonts` and consider extracting the embedded fonts if you need them on another machine. |
| **Múltiples advertencias para el

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}