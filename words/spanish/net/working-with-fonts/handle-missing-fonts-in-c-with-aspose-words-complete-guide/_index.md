---
category: general
date: 2026-02-26
description: Maneja fuentes faltantes en C# con Aspose.Words. Aprende a capturar advertencias
  de sustitución de fuentes, implementar IWarningCallback y mantener tus documentos
  con el aspecto correcto.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: es
og_description: Maneje fuentes faltantes en C# rápidamente. Esta guía muestra cómo
  capturar advertencias de sustitución de fuentes con Aspose.Words, implementar IWarningCallback
  y verificar los resultados.
og_title: Manejar fuentes faltantes en C# – Tutorial paso a paso de Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Manejar fuentes faltantes en C# con Aspose.Words – Guía completa
url: /es/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manejar fuentes faltantes en C# con Aspose.Words – Guía completa

¿Alguna vez necesitaste **manejar fuentes faltantes** al cargar un documento Word en C# y te preguntaste por qué la salida se ve extraña? No eres el único. Cuando un archivo fuente hace referencia a una fuente que no está instalada en la máquina, Aspose.Words sustituye silenciosamente otra, lo que puede romper tu diseño o identidad de marca.  

¿La buena noticia? Al conectar una **función de devolución de llamada de advertencia**, puedes capturar cada evento de sustitución de fuente, registrarlo y decidir si proporcionar un reemplazo. En este tutorial recorreremos todo el proceso—desde la configuración del proyecto hasta la verificación de la salida en la consola—para que nunca más te sorprenda una fuente invisible.

> **Lo que obtendrás**: Una aplicación de consola C# lista para ejecutar que informa cada fuente faltante, explica por qué ocurre la advertencia y te muestra cómo ampliar el manejador con lógica personalizada.

---

## Requisitos previos

- .NET 6.0 o posterior (el código funciona tanto en .NET Core como en .NET Framework)  
- Visual Studio 2022 (o cualquier IDE de C# que prefieras)  
- Una **licencia** de Aspose.Words para .NET (la prueba gratuita sirve para pruebas)  
- Un documento Word que haga referencia a una fuente que no tengas instalada (p. ej., *Comic Sans MS* en una máquina Linux)

Si ya cuentas con todo esto, vamos al grano.

---

## Paso 1: Crear un nuevo proyecto de consola y agregar Aspose.Words

Para mantener todo ordenado, comienza con un proyecto de consola nuevo.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Consejo**: Usa la bandera `--framework net6.0` si deseas apuntar a un runtime específico.

Esto descarga el paquete NuGet más reciente de Aspose.Words, que contiene los tipos `LoadOptions` e `IWarningCallback` que necesitaremos.

---

## Paso 2: Implementar un manejador de advertencias (IWarningCallback)

Aspose.Words genera un objeto `WarningInfo` por cada problema no crítico que encuentra al cargar un documento. Al implementar `IWarningCallback`, decides qué hacer con esas advertencias.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Por qué es importante**: Sin un manejador, las advertencias de sustitución de fuentes se ignoran silenciosamente. Al imprimirlas, obtienes visibilidad inmediata de qué fuentes faltan y qué usó Aspose.Words en su lugar.

---

## Paso 3: Configurar LoadOptions con la devolución de llamada de advertencia

Ahora vinculamos el manejador al proceso de carga del documento. `LoadOptions` permite conectar la devolución de llamada antes de que el archivo sea analizado.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Nota**: Reemplaza `YOUR_DIRECTORY` con la carpeta real que contiene tu archivo de prueba `.docx`. La instancia de `LoadOptions` debe pasarse al constructor de `Document`; de lo contrario, se activará el comportamiento silencioso predeterminado.

---

## Paso 4: Ejecutar la aplicación y verificar la salida

Compila y ejecuta:

```bash
dotnet run
```

Si el documento hace referencia a una fuente que no está en tu máquina (por ejemplo, *Papyrus*), verás algo como:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Esa única línea te indica exactamente qué fuente falta y qué fuente de reserva eligió Aspose.Words. Ahora puedes decidir incrustar la fuente faltante, cambiar el documento origen o aceptar la sustitución.

---

## Paso 5: Avanzado – Recopilar advertencias para uso posterior

A veces prefieres almacenar las advertencias en lugar de imprimirlas de inmediato. A continuación, una pequeña modificación al manejador que agrega los mensajes a una lista.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

Y actualiza `Main` en consecuencia:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Ahora dispones de una lista reutilizable que puedes escribir en un archivo de registro, enviar a un servicio de monitoreo o mostrar en una interfaz de usuario.

---

## Paso 6: Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparecen advertencias** | La devolución de llamada no se adjuntó, o el documento se cargó sin `LoadOptions`. | Asegúrate de que `LoadOptions.WarningCallback` esté configurado **antes** de llamar al constructor de `Document`. |
| **Nombre de fuente incorrecto en el mensaje** | Algunas fuentes están incrustadas en el documento; Aspose.Words informa el nombre *original*, no el incrustado. | Verifica las referencias de fuentes del archivo origen; incrustar fuentes elimina la advertencia por completo. |
| **Impacto en el rendimiento** | Recopilar advertencias para miles de documentos puede añadir sobrecarga. | Usa `Console.WriteLine` para depuración rápida; cambia a un colector solo cuando necesites los datos. |

---

## Resumen visual

![Ilustración de manejo de fuentes faltantes que muestra el flujo de la devolución de llamada de advertencia](/images/handle-missing-fonts.png "Diagrama del manejo de fuentes faltantes con Aspose.Words")

*El diagrama (texto alternativo incluye la palabra clave principal) visualiza cómo la devolución de llamada de advertencia intercepta los eventos de sustitución de fuentes durante la carga del documento.*

---

## Conclusión

Ahora sabes **cómo manejar fuentes faltantes** en C# usando Aspose.Words. Al conectar un `IWarningCallback` en `LoadOptions`, obtienes total visibilidad de cada evento de sustitución de fuente, puedes registrarlo o actuar en consecuencia y, en última instancia, garantizar que tus documentos generados mantengan el aspecto y la sensación previstos.

> **Resumen rápido**:  
> 1. Añade Aspose.Words a una aplicación de consola.  
> 2. Implementa `FontWarningHandler` (o un colector).  
> 3. Pásalo mediante `LoadOptions` al cargar el documento.  
> 4. Verifica la salida en la consola o las advertencias almacenadas.  

A partir de aquí podrías explorar **incrustar fuentes faltantes** (`FontSettings.SubstitutionSettings`) o **descargarlas automáticamente desde un servidor corporativo de fuentes**—ambas son extensiones naturales del patrón que acabamos de construir.

¿Tienes más preguntas sobre **advertencias de fuentes en Aspose.Words**, **LoadOptions en C#**, o **carga de documentos con fuentes faltantes**? ¡Deja un comentario y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}