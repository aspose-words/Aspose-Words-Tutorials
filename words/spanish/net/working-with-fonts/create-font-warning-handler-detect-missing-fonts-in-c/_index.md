---
category: general
date: 2026-02-12
description: Crear un manejador de advertencias de fuentes para detectar fuentes faltantes
  y rastrear fuentes ausentes en Aspose.Words. Aprende a registrar advertencias de
  forma eficiente.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: es
og_description: Crea un controlador de advertencias de fuentes en C# para detectar
  fuentes faltantes y aprende cómo registrar advertencias cuando Aspose.Words sustituye
  fuentes.
og_title: Crear manejador de advertencias de fuentes – Detectar fuentes faltantes
tags:
- Aspose.Words
- C#
- Document Processing
title: Crear manejador de advertencias de fuentes – Detectar fuentes faltantes en
  C#
url: /es/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear controlador de advertencias de fuentes – Detectar fuentes faltantes en C#

¿Alguna vez necesitaste **crear un controlador de advertencias de fuentes** porque un documento de Word sustituyó silenciosamente una fuente que no esperabas? No eres el único. Cuando Aspose.Words carga un DOCX que hace referencia a una fuente ausente en el servidor, recurre silenciosamente a una fuente predeterminada, dejando tu diseño sutilmente roto.  

En este tutorial te mostraremos exactamente cómo **detectar fuentes faltantes**, **rastrear fuentes faltantes**, y **cómo registrar advertencias** para que puedas identificar esas sustituciones antes de que te causen problemas. Al final tendrás un controlador de advertencias reutilizable que imprime cada evento de sustitución de fuente en la consola (o en cualquier registrador que prefieras). Sin misterios, solo código claro y accionable.

## Requisitos previos

- .NET 6.0 o posterior (la API es la misma para .NET Framework 4.6+)
- Aspose.Words for .NET instalado (`dotnet add package Aspose.Words`)
- Un archivo Word que haga referencia a una fuente no instalada en tu máquina (p. ej., `MissingFont.docx`)

Si ya los tienes, genial—¡vamos allá!

## Paso 1: Configurar LoadOptions con una devolución de llamada de advertencia  

Lo primero que haces cuando quieres **crear un controlador de advertencias de fuentes** es indicarle a Aspose.Words que dispare una devolución de llamada cada vez que encuentre un problema. `LoadOptions` es el contenedor de esa configuración.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Por qué es importante:**  
`LoadOptions` es el único lugar donde puedes conectar un `IWarningCallback`. Sin él, Aspose.Words registrará advertencias internamente pero nunca las verás. Al asignar `FontWarningHandler` obtenemos control total sobre lo que ocurre cuando se sustituye una fuente faltante.

## Paso 2: Implementar la clase FontWarningHandler  

Ahora realmente **creamos el controlador de advertencias de fuentes**. La clase implementa `IWarningCallback` y recibe un objeto `WarningInfo` por cada advertencia que genera Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explicación:**  
- `info.Type` indica la categoría de la advertencia. Nos interesan los `WarningType.FontSubstitution` porque son los que señalan una fuente faltante.  
- `info.Description` contiene un mensaje legible como *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Al escribir en `Console.WriteLine` **registramos advertencias** al instante. En una aplicación real podrías reemplazarlo por `ILogger`, un escritor de archivos o un servicio de telemetría.

> **Consejo profesional:** Si necesitas recopilar todas las fuentes faltantes para un informe posterior, guarda `info.Description` en una `List<string>` en lugar de imprimirlo.

## Paso 3: Cargar el documento usando los LoadOptions configurados  

Con la devolución de llamada en su lugar, cargar un documento disparará automáticamente nuestro controlador cada vez que falte una fuente.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Lo que verás:**  
Al ejecutar el programa se imprimirá algo similar a:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Esa línea confirma que has **detectado fuentes faltantes** y ahora estás **rastreando fuentes faltantes** en tiempo real.

## Paso 4: Verificar que el controlador funciona con diferentes escenarios  

Es fácil asumir que el controlador solo funciona para archivos DOCX, pero Aspose.Words admite muchos formatos. Prueba cargando un PDF que haga referencia a una fuente incrustada, o un archivo `.doc` más antiguo. La misma devolución de llamada se dispara para cualquier formato que pase por la canalización de resolución de fuentes.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Si el PDF hace referencia a una fuente que no está instalada, obtendrás la misma salida en la consola. Esto demuestra que tu solución **crear controlador de advertencias de fuentes** es independiente del formato.

## Paso 5: Extender el controlador – Registrar en un archivo  

La salida en consola es útil para demostraciones, pero el código de producción suele escribir en un archivo de registro. Aquí tienes un ajuste rápido.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Ahora, cada vez que se sustituya una fuente, el mensaje se añadirá a `font-warnings.log`. Esto cubre la parte de **cómo registrar advertencias** del requerimiento y te brinda un historial persistente.

## Paso 6: Juntar todo – Ejemplo completo y ejecutable  

A continuación tienes el programa completo que puedes copiar y pegar en una aplicación de consola. No falta nada; solo reemplaza la ruta del archivo por tu propio documento.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Resultado esperado:**  

- La consola imprime cada línea de sustitución.  
- `font-warnings.log` contiene ahora un registro con marca de tiempo de cada evento de fuente faltante.  
- El archivo `output.pdf` se crea usando las fuentes sustituidas, asegurando que la conversión se complete aunque las fuentes originales no estén disponibles.

## Preguntas frecuentes y casos límite  

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si quiero ignorar ciertas fuentes?* | Dentro de `Warning`, verifica `info.Description` para el nombre de la fuente y `return;` temprano para las fuentes que consideres aceptables. |
| *¿El controlador se disparará para fuentes incrustadas?* | No—las fuentes incrustadas siempre están disponibles para el documento, por lo que no se genera una advertencia de sustitución. |
| *¿Puedo capturar otros tipos de advertencia (p. ej., problemas de resolución de imágenes)?* | Por supuesto. Elimina la condición `if (info.Type == WarningType.FontSubstitution)` o añade bloques `if` adicionales para `WarningType.ImageResolution`. |
| *¿El controlador es seguro para subprocesos?* | La implementación predeterminada escribe en un archivo sin sincronización. Para escenarios multihilo, envuelve las escrituras en un lock o usa un registrador concurrente. |

## Próximos pasos  

Ahora que sabes **cómo registrar advertencias** para fuentes faltantes, podrías:

- **Detectar fuentes faltantes** durante un proceso de importación por lotes y generar un informe resumido.  
- **Rastrear fuentes faltantes** en varios documentos y enviar una alerta por correo cuando una fuente en particular aparezca con frecuencia.  
- **Integrar con un sistema de monitoreo** (p. ej., Azure Application Insights) para visualizar tendencias de sustitución de fuentes a lo largo del tiempo.  

Todas estas extensiones se basan en la misma base `IWarningCallback` que creamos.

---

*¡Feliz codificación! Si te encuentras con particularidades—tal vez una carpeta de fuentes personalizada o un recurso compartido en red—deja un comentario abajo. La comunidad (y yo) estamos siempre dispuestos a ayudarte a afinar tu estrategia de advertencias de fuentes.* 

![crear controlador de advertencias de fuentes ejemplo](image-placeholder.png "crear controlador de advertencias de fuentes ejemplo")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}