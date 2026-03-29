---
category: general
date: 2026-03-28
description: Cómo capturar advertencias al cargar un DOCX con Aspose.Words y obtener
  mensajes de advertencia por fuentes faltantes. Aprende a manejar fuentes faltantes
  de manera eficiente.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: es
og_description: Cómo capturar advertencias al cargar un DOCX con Aspose.Words, obtener
  los mensajes de advertencia y manejar fuentes faltantes con ejemplos de código prácticos.
og_title: Cómo capturar advertencias en Aspose.Words – Guía completa de C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo capturar advertencias en Aspose.Words – Guía completa de C#
url: /es/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar advertencias en Aspose.Words – Guía completa en C#

¿Alguna vez te has preguntado **cómo capturar advertencias** que aparecen al cargar un documento Word con Aspose.Words? Tal vez estés viendo cambios extraños de fuentes y necesites saber exactamente por qué. En resumen, puedes engancharte al sistema de advertencias de la biblioteca, **obtener mensajes de advertencia** e incluso **manejar fuentes faltantes** antes de que arruinen tu diseño.  

En este tutorial recorreremos un escenario del mundo real: cargar un DOCX, recopilar cada advertencia que emite el motor e imprimir los detalles de cualquier sustitución de fuentes que ocurra. Al final tendrás un ejemplo de código listo para ejecutar, comprenderás el “por qué” detrás de cada paso y sabrás cómo ampliar el enfoque para tus propios proyectos.

## Lo que aprenderás

- Cómo configurar `LoadOptions` para que las advertencias se capturen automáticamente.  
- La forma exacta de **obtener mensajes de advertencia** desde `WarningInfoCollection`.  
- Cómo identificar y reaccionar a **fuentes faltantes** mediante la bandera `WarningType.FontSubstitution`.  
- Consejos para solucionar casos límite, como documentos con fuentes incrustadas o carpetas de fuentes personalizadas.  

No necesitas referencias externas – todo lo que necesitas está aquí mismo.

---

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7+).  
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Un DOCX de ejemplo (`input.docx`) que carezca de algunas fuentes o use fuentes no instaladas en tu máquina.  

Eso es todo. Si ya te sientes cómodo con C# y Visual Studio, puedes copiar‑pegar el código y ejecutarlo de inmediato.

---

## Paso 1: Preparar Load Options y un Warning Callback

Lo primero que hace Aspose.Words cuando llamas a `new Document(path, loadOptions)` es analizar el archivo. Durante el análisis puede encontrarse con fuentes faltantes, características no compatibles o marcado obsoleto. Para capturar esos eventos necesitas un objeto **warning callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Por qué es importante:** Sin un callback, Aspose.Words registra silenciosamente las advertencias en la consola (o las descarta), dejándote ciego ante sustituciones de fuentes que podrían afectar el diseño. Al proporcionar una `WarningInfoCollection` dedicada, obtienes total visibilidad.

> **Consejo profesional:** Si solo te interesan las advertencias relacionadas con fuentes, puedes filtrarlas después, pero recopilar *todas* las advertencias te brinda una red de seguridad para problemas futuros.

---

## Paso 2: Cargar el documento con las opciones configuradas

Ahora que el callback está listo, carga el archivo. El constructor `Document` invocará automáticamente el callback para cualquier problema que encuentre.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**¿Qué ocurre tras bambalinas?** Aspose.Words analiza el Open XML, resuelve estilos y trata de mapear cada referencia de fuente a una fuente instalada en el sistema. Si no encuentra una coincidencia, crea una entrada `WarningInfo` del tipo `FontSubstitution`.

---

## Paso 3: Recuperar e inspeccionar las advertencias recopiladas

Una vez completada la carga, tu `warningCollector` contiene todas las advertencias que se produjeron. Extraigámoslas y centrémonos en los mensajes de sustitución de fuentes.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Salida de ejemplo** (tu consola podría mostrar algo como):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Si deseas *todas* las advertencias, simplemente elimina la condición `if` o registra `warning.Type` para cada entrada.

---

## Paso 4: Manejo de fuentes faltantes – Más allá de solo registrar

Capturar advertencias es útil, pero a menudo necesitas **manejar fuentes faltantes** programáticamente. Aquí tienes dos estrategias comunes:

### 4.1 Reemplazar fuentes faltantes con un fallback específico

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Ahora cualquier fuente faltante será sustituida por *Calibri* en lugar del fallback predeterminado de la biblioteca.

### 4.2 Incrustar una fuente sustituta dinámicamente

Si dispones de un archivo de fuente personalizado (p. ej., `MyFallback.ttf`) puedes registrarlo en tiempo de ejecución:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Este enfoque es práctico cuando distribuyes una fuente corporativa específica con tu aplicación.

> **Caso límite:** Los documentos que ya incrustan la fuente requerida ignorarán las reglas de sustitución del sistema. En ese escenario, la colección de advertencias estará vacía para esa fuente, que es precisamente lo que deseas.

---

## Paso 5: Ejemplo completo listo para copiar‑pegar

A continuación tienes un programa autocontenido que muestra todo de principio a fin. Solo reemplaza `YOUR_DIRECTORY/input.docx` con la ruta a tu archivo de prueba.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Qué esperar**

- La consola imprime cada advertencia de sustitución de fuentes, precedida de un emoji de advertencia para mayor visibilidad.  
- El DOCX de salida (`output.docx`) usa *Calibri* donde se detectó una fuente faltante.  
- No hay excepciones no controladas – el sistema de advertencias maneja elegantemente cualquier fuente desconocida.

---

## Preguntas frecuentes y respuestas

**P: ¿Esto funciona con PDFs generados desde Word?**  
R: Sí. Aspose.Words trata los PDFs como otro formato de salida. La captura de advertencias ocurre durante la fase de *carga*, por lo que es independiente de la exportación final.

**P: ¿Qué pasa si necesito capturar advertencias para **todas** las operaciones del documento (guardar, convertir, etc.)?**  
R: Puedes reutilizar la misma `WarningInfoCollection` asignándola a `Document.WarningCallback` después de instanciar el documento. Cada operación posterior añadirá nuevas entradas a la misma colección.

**P: ¿El callback de advertencias afecta al rendimiento?**  
R: De forma insignificante. La colección solo almacena objetos; a menos que proceses miles de advertencias en un bucle ajustado, no notarás ralentizaciones.

**P: ¿Cómo suprimir advertencias que no me interesan?**  
R: Implementa una clase personalizada que herede de `IWarningCallback` y filtra dentro del método `Warning`. La `WarningInfoCollection` incorporada solo almacena, no filtra.

---

## Consejos profesionales y trampas

- **Consejo profesional:** Siempre inspecciona `Warning.Description` – contiene el nombre exacto de la fuente que faltó. Esto te ayuda a decidir si debes incluir la fuente con tu aplicación.  
- **Cuidado con las fuentes incrustadas:** Si el DOCX de origen ya incrusta la fuente necesaria, Aspose.Words no emitirá una advertencia de sustitución, aunque la fuente no esté instalada localmente.  
- **Seguridad en hilos:** `WarningInfoCollection` no es segura para acceso concurrente. Si cargas varios documentos simultáneamente, asigna a cada hilo su propia colección.  
- **Comprobación de versión:** La API de advertencias es estable desde Aspose.Words 20.8. Asegúrate de usar una versión reciente para no perder tipos de advertencia más nuevos.

---

## Conclusión

Hemos cubierto **cómo capturar advertencias** de Aspose.Words, demostrado cómo **obtener mensajes de advertencia** y mostrado formas prácticas de **manejar fuentes faltantes** mediante fuentes de fallback o carpetas de fuentes personalizadas. El ejemplo completo está listo para integrarse en cualquier proyecto .NET, y los conceptos escalan a pipelines de automatización más grandes.

A continuación, podrías explorar:

- Usar `Document.WarningCallback` para capturar advertencias durante operaciones de **guardado**.  
- Registrar advertencias en un archivo o sistema de telemetría para monitorizar en producción.  
- Extender el callback para reemplazar automáticamente fuentes faltantes con tipografías específicas de la marca.

¡Siéntete libre de experimentar – cambia la fuente de fallback, agrega más documentos al lote o integra el colector de advertencias en una canalización CI que marque regresiones relacionadas con fuentes! Feliz codificación, y que tus documentos siempre se rendericen exactamente como esperas.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}