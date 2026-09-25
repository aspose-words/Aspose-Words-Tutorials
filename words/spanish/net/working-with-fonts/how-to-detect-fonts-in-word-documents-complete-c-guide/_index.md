---
category: general
date: 2026-02-24
description: Cómo detectar fuentes en un documento de Word usando Aspose.Words. Aprende
  a establecer una devolución de llamada y cargar el documento de Word con un ejemplo
  completo de código.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: es
og_description: Cómo detectar fuentes en un documento de Word usando una devolución
  de llamada de advertencia. Esta guía muestra cómo establecer la devolución de llamada
  y cargar un documento de Word con Aspose.Words.
og_title: Cómo detectar fuentes en documentos de Word – Tutorial paso a paso en C#
tags:
- C#
- Aspose.Words
- Document Processing
title: Cómo detectar fuentes en documentos de Word – Guía completa de C#
url: /es/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar fuentes en documentos Word – Guía completa en C#

¿Alguna vez te has preguntado **cómo detectar fuentes** que faltan al cargar un archivo Word? Tal vez te hayas encontrado con un documento que se ve bien en el editor, pero el PDF que generas cambia algunas tipografías tras bambalinas. Ese es un síntoma clásico de sustitución de fuentes, y detectarlo a tiempo puede evitarte desagradables sorpresas de maquetación.

En este tutorial recorreremos una solución práctica: usar **Aspose.Words** para cargar un `.docx`, adjuntar un callback de advertencia, y **cómo establecer el callback** que informa cada sustitución de fuente. Al final no solo sabrás **cómo detectar fuentes** programáticamente, sino que también comprenderás **cómo establecer el callback** correctamente y **cargar documento Word** de forma segura, todo en un único ejemplo ejecutable en C#.

> **Qué obtendrás**
> * Un ejemplo de código completo, listo para copiar y pegar  
> * Explicación paso a paso de cada línea  
> * Consejos para manejar casos límite como múltiples fuentes faltantes o carpetas de fuentes personalizadas  
> * Salida de consola esperada para que puedas verificar que todo funciona

---

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona con .NET Core)  
- Paquete NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)  
- Un archivo Word que intencionalmente hace referencia a una fuente que no tienes instalada (p. ej., `MissingFont.docx`)  
- Visual Studio, Rider o cualquier editor que prefieras

No se necesitan otras bibliotecas; todo lo demás forma parte del runtime estándar de .NET.

---

## Cómo detectar fuentes en un documento Word

### Paso 1: Crear Load Options y adjuntar un Warning Callback

Lo primero que hacemos es indicarle a Aspose.Words que queremos ser notificados sobre cualquier problema que surja al cargar el archivo. Aquí es donde **cómo establecer el callback** entra en juego.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Por qué es importante:**  
`LoadOptions` es la puerta de entrada para personalizar el proceso de carga. Al asignar una instancia de `FontWarningCollector` a `WarningCallback`, Aspose.Words invocará nuestro método `Warning` cada vez que reemplace una fuente faltante por una alternativa. Esto es el núcleo de **cómo detectar fuentes** que no están presentes en la máquina.

---

### Paso 2: Preparar la instancia de LoadOptions

Ahora instanciamos `LoadOptions` y conectamos nuestro callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Consejo profesional:** Si necesitas controlar *dónde* Aspose busca fuentes de reemplazo, también puedes establecer `loadOptions.FontSettings` aquí. Es útil cuando tienes una carpeta de fuentes privada en el servidor.

---

### Paso 3: Cargar el documento Word

Con las opciones listas, finalmente **cargamos el documento Word**. Este es el momento en que Aspose analiza el DOCX y, si faltan fuentes, nuestro callback se dispara.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**¿Qué ocurre internamente?**  
Aspose.Words lee las partes XML del DOCX, resuelve cada referencia `<w:font>` y verifica la colección de fuentes del sistema. Cada vez que una referencia no puede satisfacerse, sustituye la primera fuente alternativa coincidente y genera una advertencia `FontSubstitution`.

---

### Paso 4: Verificar la salida

Ejecuta el programa y observa la consola. Por cada fuente faltante verás una línea como:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Si el documento no contiene fuentes faltantes, la consola permanecerá silenciosa, lo que significa que **cómo detectar fuentes** no encontró coincidencias.

---

### Paso 5: Ejemplo completo funcional (aplicación de consola)

A continuación tienes un `Program.cs` autónomo que puedes colocar en un nuevo proyecto de consola. Incluye todas las piezas que discutimos más un pequeño ayudante para mantener la ventana de la consola abierta al depurar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Salida de consola esperada** (ejemplo):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Si reemplazas `MissingFont.docx` con un archivo que solo usa fuentes instaladas, verás solo la línea “Press any key…”, confirmando que la lógica de detección funciona como se espera.

---

## Preguntas frecuentes y casos límite

### ¿Qué pasa si necesito capturar *todas* las advertencias, no solo la sustitución de fuentes?

Simplemente elimina la condición `if (info.Type == WarningType.FontSubstitution)`. El objeto `WarningInfo` contiene un enum `Type` que puedes usar en otros escenarios (p. ej., `DocumentStructure`, `ImageLoading`).

### ¿Puedo registrar las advertencias en un archivo en lugar de la consola?

Por supuesto. Reemplaza `Console.WriteLine` por cualquier llamada a un framework de registro (`Serilog`, `NLog`, etc.). El callback se ejecuta en el mismo hilo que carga el documento, así que asegúrate de que tu logger sea seguro para hilos.

### ¿Cómo se comporta esto en una aplicación web?

En ASP.NET Core normalmente inyectarías una implementación singleton de `IWarningCallback` y la pasarías mediante `LoadOptions`. Recuerda evitar escribir directamente en el flujo de respuesta; registra en una base de datos o en una colección en memoria que luego puedas exponer mediante un endpoint API.

### ¿Qué pasa con fuentes personalizadas almacenadas en una carpeta no del sistema?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Ahora Aspose.Words buscará en `C:\MyCustomFonts` antes de recurrir a las fuentes del sistema operativo, reduciendo la cantidad de advertencias de sustitución que ves.

---

## Resumen visual

![Detectar la advertencia de callback de fuentes en Aspose.Words](/images/font-warning-callback.png "Cómo detectar fuentes usando un callback de advertencia")

*La captura de pantalla muestra la salida de consola cuando se sustituye una fuente faltante. El texto alternativo contiene la palabra clave principal para SEO.*

---

## Conclusión

Ahora tienes un patrón sólido y listo para producción para **cómo detectar fuentes** en cualquier archivo Word que cargues con Aspose.Words. Al **cómo establecer el callback** obtienes información en tiempo real sobre tipografías faltantes o sustituidas, y has aprendido la forma adecuada de **cargar documento Word** manteniendo tu código limpio y mantenible.

¿Próximos pasos? Intenta extender el callback para recopilar advertencias en una lista y luego mostrarlas en una UI o en un informe automatizado. También podrías explorar `FontSettings.SubstitutionSettings` para controlar *qué* fuentes se eligen como sustitutos.

Siéntete libre de experimentar: cambia el documento, agrega más fuentes faltantes o integra la lógica en una canalización de procesamiento de documentos más grande. Si encuentras algún problema, deja un comentario abajo o envíame un mensaje en GitHub.

¡Feliz codificación, y que tus documentos siempre se rendericen con las fuentes que esperas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}