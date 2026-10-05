---
category: general
date: 2026-01-05
description: Cómo capturar fuentes rápidamente y manejar fuentes faltantes usando
  Aspose.Words. Aprende una solución paso a paso con código C# completo.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: es
og_description: Cómo capturar fuentes en Aspose.Words y manejar fuentes faltantes.
  Sigue esta guía detallada para una implementación confiable en C#.
og_title: Cómo capturar fuentes en Aspose.Words – Tutorial completo
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo capturar fuentes en Aspose.Words – Guía completa
url: /es/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar fuentes en Aspose.Words – Guía completa

¿Alguna vez te has preguntado **cómo capturar fuentes** al cargar un documento Word con Aspose.Words? No eres el único. Las fuentes faltantes pueden causar sutiles fallos de diseño, y sin una advertencia adecuada es posible que nunca lo notes hasta que el PDF final se vea mal. En este tutorial te mostraremos exactamente cómo capturar fuentes **y** manejar fuentes faltantes para que tu salida se mantenga pixel‑perfecta.

Recorreremos un escenario del mundo real, configuraremos una devolución de llamada de advertencia y te daremos un ejemplo de C# listo para ejecutar. Al final sabrás por qué es importante, cómo implementarlo y qué vigilar cuando las fuentes desaparecen de tu entorno.

## Qué aprenderás

- Cómo configurar **LoadOptions** para escuchar advertencias relacionadas con fuentes.  
- El papel de **IWarningCallback** y **WarningInfo** en Aspose.Words.  
- Consejos prácticos para solucionar problemas y registrar fuentes faltantes.  
- Un ejemplo de código completo y autónomo que puedes pegar en Visual Studio y ejecutar al instante.

**Requisitos previos:** .NET 6+ (o .NET Framework 4.7.2+), Aspose.Words para .NET instalado vía NuGet, y una familiaridad básica con C#. No se requieren otras bibliotecas.

---

## Paso 1: Configurar Load Options para capturar fuentes

Lo primero que necesitamos es una instancia de **LoadOptions**. Este objeto indica a Aspose.Words cómo comportarse al leer un documento. Al asignar un **IWarningCallback** personalizado podemos interceptar cualquier advertencia de sustitución de fuentes que ocurra durante el proceso de carga.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Por qué es importante:**  
Aspose.Words sustituye silenciosamente las fuentes faltantes por una predeterminada a menos que le pidas que lo notifique. Al conectar una devolución de llamada, **capturamos** la información de fuentes justo en el momento de la carga, dándonos la oportunidad de registrar, reemplazar o incluso abortar la operación.

> **Consejo profesional:** Mantén `loadOptions` como una variable reutilizable si procesas muchos documentos en lote. Evita recrear la misma devolución de llamada una y otra vez.

---

## Paso 2: Cargar el documento con las opciones configuradas

Ahora que la devolución de llamada está en su lugar, cargamos el documento. El constructor **Document** acepta la ruta y los **LoadOptions** que acabamos de configurar.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Si falta alguna fuente, Aspose.Words generará una advertencia que nuestro `FontWarningCollector` recibirá. El documento en sí seguirá cargándose, pero tendrás un registro claro de qué fuentes fueron sustituidas.

---

## Paso 3: Implementar FontWarningCollector – Manejar fuentes faltantes

El corazón de **cómo capturar fuentes** reside en la clase `FontWarningCollector`. Implementa `IWarningCallback` y filtra solo los eventos `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explicación:**  
- `info.Type` nos indica la categoría de la advertencia. Al comprobar `FontSubstitution` **manejamos fuentes faltantes** sin saturar la salida con mensajes no relacionados (p. ej., funciones obsoletas).  
- `info.Description` contiene un mensaje legible por humanos como “Font 'Comic Sans MS' was substituted with 'Arial'.” Este es exactamente el dato que necesitas para auditar tu inventario de fuentes.

> **Cuidado:** Si necesitas detener el procesamiento cuando falta una fuente crítica, lanza una excepción dentro del bloque `if` en lugar de solo imprimir.

---

## Paso 4: Verificar la salida – Qué esperar

Ejecuta el programa desde una consola o tu IDE. Por cada fuente faltante, verás una línea como:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Si todas las fuentes están presentes, la devolución de llamada permanecerá silenciosa y el documento se cargará sin incidentes. Ahora puedes continuar con seguridad guardando, convirtiendo o imprimiendo el documento, confiado en que has **capturado** la información de fuentes.

---

## Paso 5: Ejemplo completo funcional (Todas las piezas juntas)

A continuación se muestra el programa completo, listo para copiar y pegar. Incluye las directivas using, la implementación de la devolución de llamada y una pequeña demostración de guardar el documento cargado como PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Ejecutando el código:**  
1. Crea un nuevo proyecto de consola (`dotnet new console -n FontCaptureDemo`).  
2. Añade el paquete Aspose.Words (`dotnet add package Aspose.Words`).  
3. Reemplaza el `Program.cs` generado con el fragmento anterior.  
4. Coloca un DOCX que intencionalmente haga referencia a una fuente que no tengas (p. ej., “Papyrus”).  
5. Ejecuta (`dotnet run`). Observa la consola para los mensajes de sustitución y luego abre `output.pdf` para verificar el diseño.

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito la lista de fuentes faltantes más adelante?

Almacena los mensajes en un `List<string>` dentro de `FontWarningCollector` y expónlo mediante una propiedad. Así podrás escribir la lista en un archivo de registro después de procesar muchos documentos.

### ¿Funciona con archivos encriptados o protegidos con contraseña?

Sí, pero también debes proporcionar la contraseña mediante `LoadOptions.Password`. La devolución de llamada de advertencia funciona igual una vez que el documento está descifrado.

### ¿Puedo reemplazar una fuente faltante con una alternativa personalizada?

Absolutamente. Dentro del método `Warning` puedes llamar a `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Esto garantiza que la sustitución sea determinista.

### ¿Afectará esto al rendimiento?

La sobrecarga es mínima—básicamente una llamada a método por advertencia. En un lote de miles de documentos el impacto es insignificante comparado con el coste de I/O de cargar cada archivo.

## Conclusión

Hemos cubierto **cómo capturar fuentes** en Aspose.Words, te hemos mostrado cómo **manejar fuentes faltantes** con una devolución de llamada de advertencia limpia, y te hemos entregado un ejemplo completo y ejecutable. Al incorporar este patrón en tu canal de procesamiento de documentos nunca volverás a sorprenderte con sustituciones silenciosas de fuentes.

¿Listo para el siguiente paso? Intenta ampliar el colector para escribir registros en JSON, integrarlo con un panel de monitoreo, o incrustar automáticamente las fuentes faltantes en el PDF de salida. Las posibilidades son infinitas, y ahora tienes una base sólida.

¡Feliz codificación! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}