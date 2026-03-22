---
category: general
date: 2026-03-22
description: Guardar documento de Word y detectar fuentes faltantes con Aspose.Words.
  Aprende a rastrear fuentes faltantes y capturar errores de fuentes en C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: es
og_description: Guardar documento de Word y detectar fuentes faltantes en C#. Esta
  guía muestra cómo rastrear fuentes faltantes y capturar errores de fuentes mediante
  una devolución de llamada de advertencia.
og_title: Guardar documento Word – Detectar fuentes faltantes con Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Guardar documento Word – Detectar fuentes faltantes con Aspose.Words
url: /es/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar documento de Word – Detectar fuentes faltantes con Aspose.Words

¿Alguna vez necesitaste **save word document** pero no estabas seguro de si algunas de las fuentes internas sobrevivirían al proceso de ida y vuelta? Sucede más a menudo de lo que piensas, especialmente cuando los documentos viajan entre máquinas con diferentes bibliotecas de fuentes. ¿La buena noticia? Aspose.Words te brinda una forma incorporada de **detect missing fonts** mientras **save word document**, de modo que puedes registrar, advertir o incluso reemplazarlas antes de que el archivo llegue a la pantalla del usuario.

En este tutorial recorreremos un ejemplo completo, listo para ejecutar, que no solo guarda un documento de Word sino que también **tracks missing fonts** y **captures font errors** usando un manejador de advertencias personalizado. Al final sabrás exactamente por qué el callback de advertencias es importante, cómo conectarlo y cómo se ve la salida de consola cuando ocurre una sustitución. Sin contenido extra, solo el código que puedes insertar en un proyecto .NET ahora mismo.

> **Prerequisitos**  
> • .NET 6 (o cualquier versión reciente de .NET Framework) instalado  
> • Visual Studio 2022 o tu IDE favorito  
> • Una copia con licencia de **Aspose.Words for .NET** (la versión de prueba gratuita sirve para pruebas)  

Si los tienes, comencemos.

---

## Guardar documento de Word y detectar fuentes faltantes

La idea principal es simple: antes de llamar a `Document.Save`, asigna un objeto que implemente `IWarningCallback` a `Document.WarningCallback`. Aspose.Words invocará este objeto para cada advertencia que encuentre, incluidas las advertencias de **font substitution** que ocurren cuando el documento fuente hace referencia a una fuente que tu sistema no puede encontrar.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Lo que verás:**  
Si `input.docx` hace referencia a una fuente que no está instalada, la consola imprimirá algo como:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Esa línea te indica exactamente qué fuente faltaba y qué usó Aspose.Words en su lugar, perfecto para **captures font errors** antes de distribuir el archivo.

---

## Rastrear fuentes faltantes con un callback de advertencias (Paso a paso)

### 1️⃣ Instalar Aspose.Words

Abre la consola de NuGet de tu proyecto y ejecuta:

```bash
dotnet add package Aspose.Words
```

Esto descarga la última versión estable (actualmente 24.10). Mantener la biblioteca actualizada garantiza que obtengas las últimas capacidades de **detect missing fonts** y correcciones de errores.

### 2️⃣ Definir el manejador de advertencias

¿Por qué necesitamos una clase separada? Implementar `IWarningCallback` te permite centralizar toda la lógica de advertencias en un solo lugar. También podrías registrar en un archivo, enviar telemetría o lanzar una excepción si una fuente faltante es un error crítico para tu flujo de trabajo.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Consejo profesional:** Si necesitas **track missing fonts** en varios documentos, almacena los mensajes en una `List<string>` dentro del manejador y expónla después para generar informes.

### 3️⃣ Cargar tu documento fuente

El constructor `Document` puede aceptar una ruta de archivo, un stream o incluso bytes crudos. En la mayoría de los casos lo apuntarás a un `.docx` que recibiste de un usuario u otro sistema.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Si el archivo es grande, considera usar `LoadOptions` para habilitar la carga diferida, lo que reduce la presión de memoria.

### 4️⃣ Adjuntar el callback

Asigna la instancia a `doc.WarningCallback`. A partir de este punto, cada advertencia (incluidas las sustituciones de fuentes) pasará por tu manejador.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Guardar el documento

Ahora puedes llamar a `Save` con seguridad. El manejador de advertencias se ejecuta **synchronously** durante la operación de guardado, por lo que verás la salida inmediatamente.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Si prefieres guardar en un formato diferente (PDF, HTML, etc.), el mismo mecanismo de advertencias funciona: Aspose.Words seguirá informando fuentes faltantes antes de la conversión.

---

## Capturar errores de fuentes – Casos límite comunes

Aunque el flujo básico cubre la mayoría de los escenarios, los proyectos del mundo real a menudo encuentran algunos problemas. A continuación se presentan algunas variaciones que podrías encontrar y cómo manejarlas.

### Fuente faltante en un encabezado/pie de página

Los encabezados y pies de página son nodos separados, pero el sistema de advertencias los trata igual que el texto del cuerpo. No se necesita código adicional; el callback se disparará también para esas fuentes. Solo asegúrate de cargar el documento completo (el comportamiento predeterminado lo hace).

### Múltiples sustituciones en un documento

Si un documento usa varias fuentes desconocidas, el manejador se llamará una vez por sustitución. Para evitar inundar la consola, podrías deduplicar los mensajes:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Convertir advertencias en excepciones

A veces una fuente faltante es un factor decisivo. Lanza una excepción dentro del manejador para abortar el guardado:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Recuerda envolver `doc.Save` en un bloque `try/catch` para manejar la excepción de forma adecuada.

---

## Verificar el resultado – Qué esperar

Después de que el guardado se complete, abre `output.docx` en Microsoft Word (o cualquier visor compatible). Deberías ver el mismo diseño visual que el original, pero las fuentes sustituidas aparecerán como el fallback que observaste en la consola. Para verificar, puedes:

1. Abrir **Archivo → Opciones → Avanzado → Mostrar contenido del documento → Usar calidad de borrador** – esto obliga a Word a revelar cualquier sustitución de fuentes oculta.  
2. Usar el cuadro de diálogo **Reemplazar fuentes** de Word (`Ctrl+Shift+F`) para ver qué fuentes están realmente incrustadas.

Si todo coincide, has **saved word document** con éxito mientras **detect missing fonts** y **captures font errors**. 🎉

---

## Ejemplo completo funcional (listo para copiar y pegar)

A continuación se muestra el programa completo que puedes insertar en un nuevo proyecto de aplicación de consola. Simplemente reemplaza `YOUR_DIRECTORY` con una ruta de carpeta real en tu máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Salida esperada en la consola** (ejemplo):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Esa es toda la historia: sin pasos ocultos, sin documentación externa que debas buscar.

---

## Conclusión

Hemos demostrado cómo **save word document** mientras detectas activamente **detect missing fonts**, **track missing fonts**, y **captures font errors** usando el callback de advertencias de Aspose.Words. Al conectar una pequeña implementación de `IWarningCallback`, obtienes total visibilidad de las sustituciones de fuentes al guardar, dándote la oportunidad de registrar, reemplazar o abortar según sea necesario.  

¿Listo para el siguiente desafío? Intenta ampliar el manejador para escribir advertencias en un registro JSON estructurado, o combínalo con Aspose.PDF para convertir el mismo documento preservando la información de fuentes. También podrías explorar incrustar fuentes faltantes directamente en el archivo de salida—Aspose.Words soporta la incrustación de fuentes mediante `LoadOptions.FontSettings`.  

Pruébalo, ajusta el código a tu flujo de trabajo y cuéntanos cómo te funciona. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}