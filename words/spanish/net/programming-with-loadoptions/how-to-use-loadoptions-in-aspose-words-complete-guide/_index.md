---
category: general
date: 2026-01-10
description: Aprende a usar LoadOptions para manejar fuentes faltantes en Aspose.Words.
  Código paso a paso, consejos y mejores prácticas para una carga de documentos robusta.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: es
og_description: Cómo usar LoadOptions para manejar fuentes faltantes en Aspose.Words.
  Obtén un ejemplo completo y ejecutable con explicaciones y consejos prácticos.
og_title: Cómo usar LoadOptions en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- .NET
title: Cómo usar LoadOptions en Aspose.Words – Guía completa
url: /es/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo usar LoadOptions en Aspose.Words – Guía completa

¿Alguna vez te has preguntado **cómo usar LoadOptions** al cargar un documento Word que podría carecer de algunas fuentes? No eres el único que se rasca la cabeza por esto. En muchos proyectos del mundo real, los documentos viajan entre máquinas, y el sistema de destino a menudo no tiene los tipos de letra exactos que usó el autor. ¿El resultado? Sustituciones de fuentes inesperadas que pueden romper el diseño, ocultar caracteres importantes o simplemente verse fuera de marca.  

Afortunadamente, Aspose.Words nos brinda una forma sencilla de *manejar fuentes faltantes* exponiendo un objeto `LoadOptions` con una devolución de llamada de advertencia. En este tutorial aprenderás exactamente **cómo usar LoadOptions** para capturar esas advertencias de sustitución de fuentes, registrarlas y mantener tu canal de procesamiento robusto.

Cubriremos:

* Configurar la clase de devolución de llamada de advertencia  
* Configurar `LoadOptions` con esa devolución de llamada  
* Cargar un documento mientras se rastrean fuentes faltantes  
* Consejos para solucionar problemas y ampliar la solución  

No se necesita documentación externa—todo lo que necesitas está aquí mismo.

---

## Qué necesitarás

Antes de sumergirnos, asegúrate de tener:

* **Aspose.Words for .NET** (última versión a partir de 2026) instalado vía NuGet  
* Un entorno de desarrollo .NET (Visual Studio, Rider o VS Code)  
* Un DOCX de ejemplo que hace referencia a una fuente que no tienes instalada (lo llamaremos `input.docx`)  

Eso es todo—no se requieren bibliotecas adicionales.

---

## Paso 1 – Definir una devolución de llamada de advertencia para capturar la sustitución de fuentes

La primera pieza del rompecabezas es una clase que implementa `IWarningCallback`. Aspose.Words invocará su método `Warning` cada vez que encuentre algo notable—como una fuente faltante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Por qué esto es importante:**  
Al filtrar por `WarningType.FontSubstitution` evitamos el desorden de advertencias no relacionadas (p. ej., funciones obsoletas). La devolución de llamada te brinda control total—puedes registrar en un archivo, lanzar una excepción o incluso intentar incrustar una fuente de respaldo programáticamente.

---

## Paso 2 – Configurar LoadOptions con la devolución de llamada

Ahora que tenemos un manejador, necesitamos indicarle a Aspose.Words que lo use. Aquí es donde **cómo usar LoadOptions** en la práctica.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Consejo:** `LoadOptions` ofrece muchos otros interruptores (p. ej., `Password`, `LoadFormat`, `Encoding`). Puedes encadenarlos, pero para manejar fuentes faltantes el `WarningCallback` es la estrella del espectáculo.

---

## Paso 3 – Cargar el documento usando las opciones configuradas

Con `LoadOptions` listo, cargar el documento es sencillo. Aspose.Words invocará automáticamente la devolución de llamada para cualquier fuente que no pueda encontrar.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Salida esperada:**  

Si `input.docx` usa una fuente llamada *“GothicBold”* que no está instalada, verás algo como:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

La línea de advertencia aparece **exactamente cuando se encuentra la fuente faltante**, brindándote retroalimentación instantánea.

---

## Paso 4 – (Opcional) Continuar procesando el documento

Usualmente querrás hacer más que solo cargar el archivo. A continuación hay algunas acciones comunes después de la carga que funcionan sin problemas con nuestra configuración de advertencias.

### 4.1 Guardar el documento como PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Reemplazar fuentes faltantes con una de respaldo conocida

Si prefieres una fuente de respaldo específica (p. ej., *“Calibri”*), puedes ajustar `FontSettings` antes de guardar:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Registrar todas las advertencias en un archivo

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Estos fragmentos ilustran **cómo usar LoadOptions** más allá del caso básico, dándote flexibilidad para soluciones de nivel producción.

---

## Errores comunes y cómo **manejar fuentes faltantes** de forma elegante

| Error | Por qué ocurre | Cómo arreglar / mitigar |
|-------|----------------|--------------------------|
| **No se adjunta la devolución de llamada** | Olvidas establecer `WarningCallback`. | Siempre crea una instancia de `LoadOptions` y asigna tu manejador antes de cargar. |
| **La devolución de llamada solo imprime, nunca almacena** | En un servicio web, la salida de consola desaparece. | Reemplaza `Console.WriteLine` con un registrador (Serilog, NLog) o escribe en un almacén persistente. |
| **Múltiples fuentes faltantes, solo se informa la primera** | Tu devolución de llamada lanza una excepción en la primera advertencia. | Mantén la devolución de llamada ligera; evita lanzar excepciones a menos que realmente quieras abortar. |
| **La fuente sustituida se ve incorrecta** | La sustitución predeterminada puede elegir una fuente visualmente distinta. | Usa `FontSettings.SubstitutionSettings.FontSubstitutionRules` para priorizar tu sustituto preferido. |
| **Impacto de rendimiento en documentos enormes** | La devolución de llamada de advertencia se invoca miles de veces. | Agrupa advertencias: recógelas en una lista y procesa después de cargar, o filtra solo nombres de fuentes únicos. |

Ser consciente de estos escenarios te ayuda a **manejar fuentes faltantes** sin sorpresas.

---

## Ejemplo completo – Todas las piezas juntas

A continuación se muestra el programa completo, listo para ejecutar, que demuestra todo el flujo. Copia y pega en un proyecto de consola, agrega el paquete NuGet de Aspose.Words y funcionará de inmediato.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Ejecutar este programa** hará:

1. Imprimir cualquier advertencia de sustitución de fuentes en la consola.  
2. Guardar el diseño original como `output.pdf`.  
3. Guardar un segundo PDF (`output-with-fallback.pdf`) que fuerza la sustitución a *Calibri* o *Arial*.

---

## Preguntas frecuentes (FAQs)

**P: ¿Esto funciona para archivos DOC, RTF o HTML?**  
R: Sí. `LoadOptions` es independiente del formato; siempre que pases la ruta de archivo correcta, la devolución de llamada de advertencia se activará para fuentes faltantes en todos los formatos compatibles.

**P: ¿Puedo suprimir completamente las advertencias?**  
R: Puedes asignar una devolución de llamada sin operación (`new IWarningCallback { Warning = _ => {} }`) o establecer `LoadOptions.WarningCallback = null`. Sin embargo, perder visibilidad significa que podrías pasar por alto problemas críticos de fuentes.

**P: ¿Qué pasa si necesito reemplazar fuentes faltantes con fuentes incrustadas?**  
R: Usa `FontSettings` para incrustar un archivo de fuente sustituta (`AddFontSource`). Combínalo con las reglas de sustitución para una experiencia sin interrupciones.

**P: ¿Es segura la devolución de llamada para hilos?**  
R: La devolución de llamada puede ser invocada desde varios hilos al cargar documentos grandes en paralelo. Asegúrate de que cualquier recurso compartido (p. ej., archivos de registro) esté sincronizado.

---

## Conclusión

Hemos recorrido **cómo usar LoadOptions** en Aspose.Words para **manejar fuentes faltantes** de forma elegante. Implementando una `IWarningCallback` personalizada, adjuntándola a una instancia de `LoadOptions` y cargando tu documento con esa configuración, obtienes información en tiempo real de cualquier evento de sustitución de fuentes. A partir de ahí, puedes registrar, reemplazar o incrustar fuentes de respaldo para que tu salida se vea exactamente como se pretende.

Recuerda, los pasos clave son:

1. Implementar una devolución de llamada de advertencia que se centre en `WarningType.FontSubstitution`.  
2. Conectar la devolución de llamada a un objeto `LoadOptions`.  
3. Cargar tu documento con esas opciones.  
4. (Opcional) Aplicar reglas adicionales de sustitución de fuentes o registro según sea necesario.

Siéntete libre de experimentar—cambia el registrador de consola por uno estructurado, agrega alertas por correo electrónico para fuentes faltantes críticas, o integra este patrón en una canalización de procesamiento de documentos más grande. El enfoque escala bien tanto si manejas un solo archivo como si procesas miles en un trabajo por lotes.

¡Feliz codificación, y que tus documentos siempre se rendericen con los tipos de letra correctos!  

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}