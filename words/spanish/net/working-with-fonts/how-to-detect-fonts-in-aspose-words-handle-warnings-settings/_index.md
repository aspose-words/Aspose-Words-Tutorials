---
category: general
date: 2026-01-03
description: 'Cómo detectar fuentes en Aspose.Words y manejar advertencias usando
  la configuración de fuentes de Aspose: una guía paso a paso para desarrolladores.'
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: es
og_description: Cómo detectar fuentes en Aspose.Words y configurar advertencias con
  la configuración de fuentes de Aspose. Aprende el flujo de trabajo completo en minutos.
og_title: Cómo detectar fuentes en Aspose.Words – Manejar advertencias
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones
url: /es/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones

¿Alguna vez te has preguntado **cómo detectar fuentes** en un documento Word antes de que llegue a producción? No eres el único. Las fuentes faltantes pueden causar pesadillas de maquetación, y sin advertencias adecuadas podrías lanzar un PDF o DOCX roto sin siquiera darte cuenta.  

En este tutorial recorreremos **cómo detectar fuentes** usando Aspose.Words, mostraremos **cómo manejar advertencias**, y ajustaremos **la configuración de fuentes de Aspose** para que puedas **configurar advertencias** exactamente como lo necesites. Al final tendrás un fragmento listo‑para‑ejecutar que imprime cada sustitución que Aspose realiza, y sabrás cómo adaptarlo a tus propios proyectos.

## Requisitos previos

- .NET 6+ (or .NET Framework 4.6+).  
- Aspose.Words for .NET installed via NuGet (`Install-Package Aspose.Words`).  
- Un archivo Word que intencionalmente hace referencia a una fuente faltante (p. ej., *DocumentWithMissingFonts.docx*).  

Si ya los tienes, genial—¡vamos al grano!

![captura de pantalla de cómo detectar fuentes](https://example.com/detect-fonts.png "ejemplo de salida de cómo detectar fuentes")

## Cómo detectar fuentes con Aspose.Words

El primer paso es indicarle a Aspose.Words que te importan los eventos de sustitución de fuentes. Esto se logra proporcionando una devolución de llamada de advertencia personalizada a través de **la configuración de fuentes de Aspose**. La devolución de llamada recibe un objeto `WarningInfo` por cada sustitución, permitiéndote **detectar fuentes** en tiempo de ejecución.

### Paso 1: Crear una clase de devolución de llamada de advertencia

Implementa la interfaz `IWarningCallback`. Dentro del método `Warning`, filtra por `WarningType.FontSubstitution` y registra los detalles.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Consejo profesional:** La cadena `info.Description` contiene tanto el nombre de la fuente faltante como la sustituta que Aspose eligió. Puedes analizarla si necesitas un informe estructurado.

### Paso 2: Configurar LoadOptions con la configuración de fuentes de Aspose

Crea una instancia de `LoadOptions`, adjunta un nuevo objeto `FontSettings`, y asigna el `WarningCallback` al manejador que acabamos de crear. Esto indica a Aspose **cómo configurar advertencias**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Si tienes una carpeta de fuentes privada, puedes agregarla así:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Esa línea muestra otro aspecto de **la configuración de fuentes de Aspose**—controlas exactamente dónde busca Aspose fuentes antes de decidir sustituir.

### Paso 3: Cargar el documento y activar la devolución de llamada

Ahora carga el documento objetivo con `loadOptions`. A medida que Aspose analiza el archivo, cualquier fuente faltante activa el manejador de advertencias, detectando efectivamente **fuentes** sobre la marcha.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Al ejecutar el programa, verás una salida similar a:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Paso 4: (Opcional) Recopilar advertencias para uso posterior

Si necesitas almacenar los datos de sustitución para un informe, modifica el manejador para acumular los mensajes en una lista.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Luego puedes escribir `handler.Substitutions` a un archivo JSON, enviarlo a un servicio de registro, o mostrarlo en una interfaz de usuario.

### Paso 5: Verificar el resultado programáticamente

A veces deseas asegurar que *no* haya ocurrido sustitución (p. ej., en una compilación CI). Aquí tienes una verificación rápida:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Ese fragmento demuestra **cómo manejar advertencias** de forma determinista, dándote control total sobre la canalización de compilación.

## Preguntas frecuentes (y casos límite)

**¿Qué pasa si necesito ignorar ciertas sustituciones?**  
Puedes agregar lógica condicional dentro de `Warning` y simplemente devolver sin registrar las fuentes que consideres aceptables.

**¿Puedo suprimir todas las advertencias y obtener solo un resultado booleano?**  
Sí—establece `loadOptions.WarningCallback = null` y luego inspecciona `doc.FontInfo` después de cargar (aunque perderás el registro detallado).

**¿Esto funciona con la conversión a PDF?**  
Absolutamente. El mismo mecanismo de advertencia se activa cuando llamas a `doc.Save("out.pdf")`. La devolución de llamada capturará cualquier intercambio de fuentes realizado durante el paso de conversión.

**¿Hay un impacto en el rendimiento?**  
La sobrecarga es mínima—solo unas pocas llamadas de método adicionales por cada fuente faltante. Para lotes grandes, podrías querer almacenar en caché los resultados.

## Resumen: Lo que cubrimos

- **Cómo detectar fuentes** implementando un `IWarningCallback` personalizado.  
- **Cómo manejar advertencias** a través de `LoadOptions.WarningCallback`.  
- Ajustar **la configuración de fuentes de Aspose** (agregar carpetas de fuentes personalizadas, habilitar/deshabilitar advertencias).  
- **Cómo configurar advertencias** tanto para salida inmediata en consola como para análisis posterior.  

Con estas piezas en su lugar, puedes procesar documentos Word con confianza, garantizar que las fuentes faltantes se señalen y mantener tu salida consistente en todos los entornos.

## Próximos pasos

- Explora `FontSettings.SubstitutionSettings` para un control más granular (p. ej., mapear fuentes faltantes específicas a sustitutos elegidos).  
- Combina este enfoque con Aspose.PDF para generar PDFs que mantengan la tipografía exacta.  
- Automatiza la verificación de advertencias en una canalización CI/CD para bloquear lanzamientos que contengan problemas de fuentes—perfecto para equipos que **manejan advertencias** como parte de los controles de calidad.  

¿Tienes más preguntas sobre **la configuración de fuentes de Aspose** o necesitas ayuda para integrar esto en un servicio más grande? Deja un comentario abajo, ¡y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}