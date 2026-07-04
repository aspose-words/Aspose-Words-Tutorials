---
category: general
date: 2026-04-21
description: Aprenda a detectar fuentes, capturar advertencias, configurar la devolución
  de llamada y enumerar advertencias con Aspose.Words en C#. Guía paso a paso para
  un manejo fiable de fuentes.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: es
og_description: ¿Cómo detectar fuentes en Aspose.Words? Este tutorial le muestra cómo
  capturar advertencias, configurar una devolución de llamada y enumerar advertencias
  en C#.
og_title: Cómo detectar fuentes en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo detectar fuentes en Aspose.Words – Guía completa
url: /es/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar fuentes en Aspose.Words – Guía completa

¿Alguna vez te has preguntado **cómo detectar fuentes** que faltan al cargar un documento de Word? Es una situación que aparece más a menudo de lo que te gustaría, sobre todo al trabajar con archivos heredados o despliegues multiplataforma. En este tutorial recorreremos un ejemplo completo y ejecutable que **captura advertencias**, **configura un callback** y **enumera advertencias** para que siempre sepas qué fuentes fueron sustituidas.

Usaremos Aspose.Words para .NET (v24.9 al momento de escribir) y C# puro. Sin servicios externos, sin trucos, solo la API y unas cuantas líneas de código. Al final podrás identificar cada sustitución de fuente, registrarla e incluso decidir abortar la carga si falta una fuente crítica.  

### Lo que necesitarás
- **Aspose.Words para .NET** (instalar vía NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 o superior (el código también funciona en .NET Framework)
- Un archivo DOCX de ejemplo que haga referencia a una fuente que no esté presente en la máquina (p. ej., “MyCustomFont.ttf”)
- Visual Studio, Rider o cualquier editor de C# que prefieras

> **Consejo profesional:** Si no tienes un documento con fuentes faltantes, simplemente cambia el nombre de un archivo de fuente en tu sistema o edita el XML del DOCX para que haga referencia a una familia de fuentes inexistente.

---

## Cómo detectar fuentes con Aspose.Words

La idea principal es engancharse al sistema de advertencias de Aspose.Words. Cuando la biblioteca no puede encontrar una fuente solicitada, emite una advertencia `WarningType.FontSubstitution`. Al proporcionar una implementación personalizada de `IWarningCallback`, puedes **detectar fuentes** que fueron reemplazadas durante el proceso de carga.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Por qué funciona:** Aspose.Words llama al método `Warning` para cada problema no crítico. Al almacenar los objetos `WarningInfo` obtienes acceso completo al tipo, mensaje y contexto, que es exactamente lo que necesitas para **detectar fuentes** que fueron sustituidas.

---

## Cómo capturar advertencias al cargar un documento

Ahora que tenemos un colector, debemos indicarle a `LoadOptions` que lo use. Esta es la parte de **cómo capturar advertencias** del rompecabezas.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Caso límite:** Si cargas un documento desde un flujo (`new Document(stream, loadOptions)`), el mismo callback funciona—solo pasa el flujo en lugar de la ruta del archivo.

En este punto el documento está completamente cargado, pero cualquier advertencia de sustitución de fuente está almacenada de forma segura dentro de `warningCollector.Warnings`.

---

## Cómo enumerar advertencias y reportar sustituciones de fuentes

Finalmente, revisamos las advertencias recopiladas y **enumeramos advertencias** que son específicamente sobre sustitución de fuentes. Este paso convierte los datos crudos en un informe legible.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Salida esperada** (ejemplo):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Si el documento no contiene fuentes faltantes, el bucle simplemente no produce salida—no hay nada de qué preocuparse.

---

## Ejemplo completo (todos los pasos en un solo archivo)

A continuación tienes el programa completo que puedes copiar‑pegar en un proyecto de consola. Une **cómo detectar fuentes**, **cómo capturar advertencias**, **cómo configurar el callback** y **cómo enumerar advertencias** en un flujo cohesivo.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Ejecutar este programa** imprimirá cada fuente que Aspose.Words tuvo que reemplazar. Puedes redirigir la salida a un archivo de registro, generar una alerta o incluso abortar la carga si falta una fuente crítica.

---

## Preguntas frecuentes y trampas comunes

### ¿Qué pasa si necesito detener la carga cuando falta una fuente requerida?
Puedes inspeccionar los objetos `WarningInfo` dentro del callback y lanzar una excepción cuando aparezca un nombre de fuente concreto. La excepción abortará la carga, dándote control total.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### ¿Esto funciona con PDFs u otros formatos?
Sí. Aspose.Words utiliza la misma infraestructura de advertencias para PDFs, RTF y HTML. Solo cambia la extensión del archivo y el resto del código permanece idéntico.

### ¿Cómo puedo registrar las advertencias en un archivo en lugar de la consola?
Reemplaza `Console.WriteLine` por cualquier framework de registro que prefieras (`Serilog`, `NLog`, etc.). La clase `WarningInfo` expone `Message`, `Source` y `Exception` para registros detallados.

### ¿Esto afectará al rendimiento?
La sobrecarga es insignificante—Aspose.Words ya genera las advertencias internamente. Añadir un callback simplemente las almacena en una lista, lo que es O(n) en el número de advertencias. Para documentos típicos, el impacto está muy por debajo del 1 % del tiempo total de carga.

---

## Resumen visual

![Cómo detectar fuentes en Aspose.Words – diagrama de flujo de advertencias](https://example.com/images/font-detection-diagram.png "cómo detectar fuentes")

*Texto alternativo:* **cómo detectar fuentes** – diagrama que muestra los pasos de callback de advertencia, colección y enumeración.

---

## Conclusión

Hemos cubierto **cómo detectar fuentes** en Aspose.Words mediante **captura de advertencias**, **configuración de un callback** y **enumeración de advertencias**. El ejemplo completo muestra un patrón listo para producción que puedes incorporar en cualquier aplicación .NET.  

A continuación, podrías explorar:

- **Cómo capturar advertencias** para otros problemas (p. ej., problemas de conversión de imágenes)
- **Cómo configurar callback** para frameworks de registro personalizados
- **Cómo enumerar advertencias** en varios documentos dentro de un proceso por lotes
- Usar **Aspose.Words.Fonts.FontSettings** para proporcionar carpetas de fuentes de respaldo, lo que puede reducir el número de sustituciones desde el principio.

Pruébalo, adapta el colector a tu estilo de registro y nunca más te sorprenderá una sustitución de fuente inesperada. Si encuentras alguna peculiaridad, deja un comentario abajo—¡feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}