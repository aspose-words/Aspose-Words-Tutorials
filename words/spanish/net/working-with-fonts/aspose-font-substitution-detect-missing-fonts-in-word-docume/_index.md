---
category: general
date: 2026-04-05
description: Guía de sustitución de fuentes de Aspose para detectar fuentes faltantes
  al cargar un documento de Word. Aprende a configurar la configuración de fuentes
  y a manejar las fuentes faltantes de manera eficiente.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: es
og_description: Guía de sustitución de fuentes de Aspose para detectar fuentes faltantes
  al cargar un documento de Word. Aprende a configurar la configuración de fuentes
  y a manejar las fuentes faltantes de manera eficiente.
og_title: Sustitución de fuentes Aspose – Detectar fuentes faltantes en documentos
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: Sustitución de fuentes Aspose – Detectar fuentes faltantes en documentos Word
url: /es/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sustitución de fuentes Aspose – Detectar fuentes faltantes en documentos Word

¿Alguna vez te has encontrado con un archivo Word que se ve perfecto en una máquina pero muestra extraños cambios de fuente en otra? Ese es el clásico problema de **aspose font substitution**, y normalmente significa que faltan algunas fuentes en el sistema de destino. En este tutorial te mostraremos, paso a paso, cómo **detectar fuentes faltantes** al **cargar un documento Word**, cómo **configurar la configuración de fuentes**, y qué hacer para **manejar fuentes faltantes** de forma elegante.

Recorreremos un ejemplo completo y ejecutable en C#, explicaremos por qué cada línea es importante e incluso te mostraremos la salida de consola que deberías obtener. Al final podrás detectar sustituciones de fuentes en el momento en que se carga un documento, sin necesidad de adivinar.

## Lo que aprenderás

- Cómo habilitar el recopilador diagnóstico de Aspose.Words para advertencias de fuentes.  
- El código exacto necesario para **cargar un documento Word** con **configuración de fuentes** personalizada.  
- Cómo iterar sobre objetos `WarningInfo` para enumerar cada fuente sustituida.  
- Consejos para suprimir advertencias no deseadas o proporcionar fuentes de respaldo.  
- Un ejemplo listo para ejecutar que puedes copiar y pegar en Visual Studio.

### Requisitos previos

- .NET 6.0 o posterior (la API funciona igual en .NET Framework).  
- Aspose.Words para .NET (paquete NuGet `Aspose.Words`).  
- Un archivo Word que haga referencia a una fuente que no tienes instalada (p. ej., `MissingFont.docx`).  

Si tienes todo eso, vamos a sumergirnos.

## Paso 1 – Habilitar el recopilador diagnóstico (Configurar la configuración de fuentes)

Primero lo primero: Aspose.Words solo registra advertencias de sustitución de fuentes si se lo indicas. Esto se hace creando un objeto `FontSettings` y asignándolo a una instancia de `LoadOptions`. Piensa en esto como encender las “luces de depuración” para el manejo de fuentes.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**¿Por qué?**  
Sin un objeto `FontSettings` el recopilador de advertencias permanece silencioso, y nunca sabrás qué fuentes fueron sustituidas. Al inicializarlo vacío permitimos que Aspose use las fuentes predeterminadas del sistema *y* haga un seguimiento de cualquier sustitución.

> **Consejo profesional:** Si sabes que una carpeta específica contiene fuentes corporativas, indica esa carpeta a `FontSettings` con `SetFontsFolder("ruta")`. Eso puede reducir la cantidad de advertencias de fuentes faltantes.

## Paso 2 – Cargar el documento con las opciones configuradas (Cargar documento Word)

Ahora que el recopilador está activo, carga tu archivo `.docx` usando el mismo `LoadOptions`. Este es el momento en que Aspose escanea el documento, busca cada referencia de fuente y decide si se necesita una sustitución.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**¿Por qué es importante?**  
Si simplemente llamas a `new Document("MissingFont.docx")`, se aplicarían los ajustes predeterminados *y* la lista de advertencias permanecería vacía. Pasar `loadOptions` garantiza que el recopilador diagnóstico esté conectado al proceso de carga.

## Paso 3 – Recuperar y mostrar advertencias de sustitución de fuentes (Detectar fuentes faltantes)

Después de que el documento está en memoria, Aspose almacena cualquier advertencia en `document.WarningCallback.Warnings`. Recorre esa colección, filtra por `WarningType.FontSubstitution` y muestra la descripción. Cada descripción te indica qué fuente faltaba y cuál se utilizó en su lugar.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Salida esperada de la consola**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

![Salida de consola que muestra advertencias de sustitución de fuentes Aspose](/images/aspose-font-substitution-console.png)

*Texto alternativo de la imagen:* sustitución de fuentes Aspose – salida de consola que enumera las fuentes sustituidas

## Paso 4 – Opcional: Personalizar el comportamiento de sustitución (Manejar fuentes faltantes)

A veces no solo quieres saber *que* ocurrió una sustitución, sino controlar *cómo* ocurre. Aspose.Words te permite registrar una regla personalizada `IFontSubstitutionRule`. A continuación hay un ejemplo rápido que fuerza a cualquier fuente faltante a usar `Tahoma` como respaldo.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**¿Cuándo usarías esto?**  
Si estás generando PDFs para un servicio web y sabes que todos los clientes pueden renderizar `Tahoma`, forzar el respaldo garantiza consistencia visual sin tener que distribuir decenas de archivos de fuentes.

## Ejemplo completo funcional (Todos los pasos combinados)

Aquí tienes el programa completo que puedes pegar en un nuevo proyecto de consola. Compila tal cual, asumiendo que has instalado el paquete NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Ejecuta el programa, observa la consola y verás cada evento de fuente faltante impreso. A partir de ahí puedes decidir si instalar las fuentes faltantes, incrustarlas o mantener el respaldo.

## Preguntas frecuentes

**P: ¿Esto funciona con la conversión a PDF?**  
Sí. Cuando luego llames a `doc.Save("output.pdf")`, cualquier fuente que haya sido sustituida durante la carga será la que se incruste en el PDF. Por lo tanto, capturar las advertencias temprano te ayuda a evitar cambios de fuente inesperados en el PDF final.

**P: ¿Qué pasa si tengo muchos documentos para procesar?**  
Envuelve la lógica de carga en un bloque try‑catch y reutiliza una única instancia de `FontSettings` para varios documentos. Eso reduce la sobrecarga y mantiene activo el recopilador de advertencias para cada archivo.

**P: ¿Puedo suprimir completamente las advertencias?**  
Puedes establecer `loadOptions.WarningCallback = null;` antes de cargar, pero perderás la capacidad de **detectar fuentes faltantes**, lo cual usualmente no es lo que deseas.

## Conclusión

Hemos cubierto todo lo que necesitas para dominar la **aspose font substitution**: habilitar el recopilador diagnóstico, cargar un archivo Word con **configuración de fuentes** personalizada, extraer la lista de fuentes faltantes e incluso sobrescribir la regla de sustitución predeterminada para **manejar fuentes faltantes** a tu manera. Con solo unas pocas líneas de C# obtienes una visibilidad completa de los problemas de fuentes que de otro modo estarían ocultos tras sutiles cambios de diseño.

¿Próximos pasos? Intenta incrustar las fuentes originales en el documento con `FontSettings.SetFontsFolder` o explora `FontSourceBase` para cargar fuentes desde una base de datos. También podrías experimentar con la colección `Document.BuiltInStyle` para ver cómo se propagan los cambios de fuente a nivel de estilo.

¿Tienes más preguntas sobre Aspose.Words o la gestión de fuentes? Deja un comentario, explora la documentación oficial de Aspose o crea un nuevo proyecto y juega con el código anterior. ¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como deseas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}