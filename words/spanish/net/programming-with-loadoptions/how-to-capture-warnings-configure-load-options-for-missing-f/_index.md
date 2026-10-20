---
category: general
date: 2026-03-30
description: cómo capturar advertencias al cargar un archivo DOCX – aprende a detectar
  fuentes faltantes, configurar la configuración de fuentes y establecer opciones
  de carga en C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: es
og_description: cómo capturar advertencias al cargar un archivo DOCX – guía paso a
  paso para detectar fuentes faltantes y configurar la configuración de fuentes en
  C#
og_title: cómo capturar advertencias – configurar opciones de carga para fuentes faltantes
tags:
- Aspose.Words
- C#
- Font management
title: Cómo capturar advertencias – configurar opciones de carga para fuentes faltantes
url: /es/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo capturar advertencias – configurar opciones de carga para fuentes faltantes

¿Alguna vez te has preguntado **cómo capturar advertencias** que aparecen cuando un documento intenta usar una fuente que no tienes instalada? Es un escenario que sorprende a muchos desarrolladores que trabajan con bibliotecas de procesamiento de texto, especialmente cuando necesitas **detectar fuentes faltantes** antes de que rompan tu canal de exportación a PDF.  

En este tutorial te mostraremos una solución práctica y lista‑para‑ejecutar que **configura la configuración de fuentes**, **establece opciones de carga** y muestra cada advertencia de sustitución en la consola. Al final sabrás exactamente cómo **manejar fuentes faltantes** de manera que tu aplicación siga siendo robusta y tus usuarios estén satisfechos.

## Lo que aprenderás

- Cómo **establecer opciones de carga** para que la biblioteca informe problemas de fuentes en lugar de sustituirlas silenciosamente.
- Los pasos exactos para **configurar la configuración de fuentes** y capturar advertencias.
- Formas de **detectar fuentes faltantes** programáticamente y reaccionar en consecuencia.
- Un ejemplo completo en C# listo para copiar y pegar que funciona con la última versión de Aspose.Words para .NET (v24.10 al momento de escribir).
- Consejos para ampliar la solución y registrar advertencias, usar fuentes personalizadas como respaldo o abortar el procesamiento cuando falten fuentes críticas.

> **Prerequisite:** Necesitas el paquete NuGet Aspose.Words para .NET instalado (`Install-Package Aspose.Words`). No se requieren otras dependencias externas.

---

## Paso 1: Importar espacios de nombres y preparar el proyecto

Primero, agrega las directivas `using` esenciales. No es solo código boilerplate; indica al compilador dónde se encuentran `LoadOptions`, `FontSettings` y `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tip:** Si usas .NET 6+ puedes habilitar declaraciones *global using* para evitar repetir estas líneas en cada archivo.

---

## Paso 2: Establecer opciones de carga y habilitar advertencias de sustitución de fuentes

El núcleo de **cómo capturar advertencias** está en el objeto `LoadOptions`. Al crear una nueva instancia de `FontSettings` y adjuntar un controlador de eventos a `SubstitutionWarning`, le indicas a la biblioteca que avise cada vez que no pueda encontrar la fuente solicitada.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Por qué es importante:** Sin la suscripción al evento, Aspose.Words recurre silenciosamente a una fuente predeterminada y nunca sabes qué glifos fueron sustituidos. Al escuchar `SubstitutionWarning`, obtienes un registro completo—crucial para entornos con requisitos de cumplimiento.

---

## Paso 3: Cargar el documento usando las opciones configuradas

Ahora que las advertencias están conectadas, carga tu DOCX (o cualquier formato compatible) con el `loadOptions` que acabas de preparar. El constructor de `Document` activará la lógica de verificación de fuentes de inmediato.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Si el archivo hace referencia, por ejemplo, a *“Comic Sans MS”* en una máquina que solo tiene *“Arial”*, verás algo como:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Esa línea se imprime directamente en la consola gracias al controlador que añadimos antes.

---

## Paso 4: Verificar y reaccionar a las advertencias capturadas

Capturar advertencias es solo la mitad de la batalla; a menudo necesitas decidir qué hacer a continuación. A continuación tienes un patrón rápido que almacena las advertencias en una lista para analizarlas después—perfecto si deseas registrarlas en un archivo o abortar la importación cuando falta una fuente crítica.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Manejo de casos límite:**  
- **Múltiples fuentes faltantes:** La lista contendrá una entrada por cada sustitución, de modo que puedes iterar y generar un informe detallado.  
- **Fuentes de respaldo personalizadas:** Si dispones de tus propios archivos de fuentes, añádelos a `FontSettings` antes de cargar: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Las advertencias mostrarán entonces la fuente de respaldo personalizada en lugar de la predeterminada del sistema.  

---

## Paso 5: Ejemplo completo (listo para copiar y pegar)

Uniendo todo, aquí tienes una aplicación de consola autocontenida que puedes compilar y ejecutar ahora mismo.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Salida esperada en la consola** (cuando el DOCX hace referencia a una fuente faltante):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Si falta una fuente *crítica* como “Times New Roman”, verás el mensaje de abortar en su lugar.

---

## Preguntas frecuentes y trampas comunes

| Pregunta | Respuesta |
|----------|-----------|
| **¿Necesito llamar a `SetFontsFolder` para capturar advertencias?** | No. El evento de advertencia funciona con las fuentes del sistema por defecto. Usa `SetFontsFolder` solo cuando quieras proporcionar fuentes de respaldo adicionales. |
| **¿Esto funciona en .NET Core / .NET 5+?** | Absolutamente. Aspose.Words 24.10 es compatible con todos los runtimes modernos de .NET. Solo asegúrate de que el paquete NuGet coincida con tu framework de destino. |
| **¿Qué pasa si quiero registrar advertencias en un archivo en lugar de la consola?** | Reemplaza `Console.WriteLine(msg);` por la llamada a tu framework de registro preferido, por ejemplo `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **¿Puedo suprimir advertencias para fuentes específicas?** | Sí. Dentro del controlador de eventos puedes filtrar: `if (e.FontName == "SomeFont") return;`. Esto brinda un control fino. |
| **¿Hay forma de tratar fuentes faltantes como errores?** | Lanza una excepción manualmente dentro del controlador cuando se cumpla una condición, o establece una bandera y aborta después de la construcción de `Document` como se muestra en el ejemplo. |

---

## Conclusión

Ahora dispones de un patrón sólido y listo para producción para **cómo capturar advertencias** que ocurren al cargar documentos con fuentes faltantes. Al **detectar fuentes faltantes**, **configurar la configuración de fuentes** y **establecer opciones de carga** de forma adecuada, obtienes total visibilidad de los eventos de sustitución de fuentes y puedes decidir si registrar, usar una fuente de respaldo o abortar.  

Da el siguiente paso integrando esta lógica en tu canal de conversión a PDF, añadiendo fuentes de respaldo personalizadas o alimentando la lista de advertencias a un sistema de monitoreo. El enfoque escala desde pequeñas utilidades hasta servicios de procesamiento de documentos de nivel empresarial.

---

### Lecturas adicionales y próximos pasos

- **Explora más características de FontSettings** – incrustar fuentes personalizadas, controlar el orden de respaldo y consideraciones de licenciamiento.  
- **Combínalo con la conversión a PDF** – después de capturar advertencias, llama a `doc.Save("output.pdf");` y verifica que el PDF use las fuentes esperadas.  
- **Automatiza pruebas** – escribe pruebas unitarias que carguen documentos con fuentes faltantes conocidas y verifica que la lista de advertencias contenga los mensajes esperados.  

Si encuentras algún problema o tienes ideas para mejorar, no dudes en dejar un comentario. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}