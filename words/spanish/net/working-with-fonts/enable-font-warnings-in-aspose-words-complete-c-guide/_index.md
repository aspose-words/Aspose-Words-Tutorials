---
category: general
date: 2026-04-01
description: Habilite las advertencias de fuentes al cargar documentos Word con Aspose.Words.
  Aprenda cómo capturar eventos de sustitución de fuentes usando LoadOptions y Configuración
  de fuentes en C#.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: es
og_description: Habilite las advertencias de fuentes al cargar documentos Word con
  Aspose.Words. Este tutorial le muestra cómo capturar eventos de sustitución de fuentes
  en C#.
og_title: Activar advertencias de fuentes en Aspose.Words – Guía completa de C#
tags:
- Aspose.Words
- C#
- Font Management
title: Activar advertencias de fuentes en Aspose.Words – Guía completa de C#
url: /es/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar advertencias de fuentes en Aspose.Words – Guía completa de C# 

¿Alguna vez te has preguntado por qué un documento de Word se ve diferente de repente después de cargarlo programáticamente? **Enable Font Warnings** y sabrás al instante cuándo Aspose.Words sustituye una fuente faltante por una alternativa. En este tutorial recorreremos un ejemplo práctico que no solo captura esas sustituciones sino que también explica *por qué* ocurren.

Cubrirémos todo lo que necesitas para comenzar: el paquete NuGet requerido, la configuración exacta de `LoadOptions` y una salida de consola ordenada que te indica qué fuentes fueron reemplazadas. Al final tendrás un patrón sólido y reutilizable para **C# document processing** que funciona con cualquier versión de Aspose.Words.

## Lo que aprenderás

- Cómo crear una instancia de `LoadOptions` que rastree los cambios de fuentes.  
- El propósito del evento `SubstitutionWarning` y cómo suscribirse.  
- Un ejemplo de código completo y ejecutable que imprime advertencias claras en la consola.  
- Consejos para manejar casos límite, como documentos que solo contienen fuentes estándar.  

No se requiere experiencia previa con Aspose.Words, solo una familiaridad básica con C# y .NET.

---

![texto alternativo: diagrama de advertencias de fuentes que muestra el flujo de eventos cuando se sustituye una fuente faltante.](placeholder-image.png "Diagrama de advertencias de fuentes")

## Paso 1: Configurar LoadOptions y habilitar advertencias de fuentes

Lo primero que necesitas es un objeto `LoadOptions`. Este contenedor le indica a Aspose.Words cómo tratar el archivo que estás a punto de cargar. Al asignar una nueva instancia de `FontSettings` abres la puerta a eventos relacionados con fuentes.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Por qué es importante:**  
Si omites la asignación de `FontSettings`, Aspose.Words seguirá sustituyendo fuentes faltantes, pero no recibirás ninguna notificación. El mecanismo de advertencia reside dentro de `FontSettings`, por lo que inicializarlo es *crucial* para nuestro objetivo.

> **Consejo profesional:** También puedes apuntar `FontSettings` a una carpeta de fuentes personalizada usando `SetFontsFolder`. Eso reduce la cantidad de advertencias que verás, porque Aspose.Words puede encontrar realmente las tipografías faltantes.

## Paso 2: Suscribirse al evento SubstitutionWarning (sustitución de fuentes)

Ahora que el objeto `FontSettings` existe, nos conectamos a su evento `SubstitutionWarning`. Este evento se dispara **cada vez** que Aspose.Words reemplaza una fuente solicitada por otra.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Por qué es importante:**  
Sin este escuchador no tendrías visibilidad del proceso de sustitución. La línea de consola te brinda una pista de auditoría rápida, lo cual es especialmente útil durante compilaciones automatizadas o al generar PDFs para industrias con alta normativa.

> **Pregunta frecuente:** *¿Qué pasa si quiero suprimir las advertencias?*  
> Puedes simplemente desvincular el manejador o establecer `FontSettings.SubstitutionWarning += null;`. Sin embargo, mantener las advertencias suele ser la ruta más segura porque las sustituciones silenciosas pueden provocar fallos de diseño.

## Paso 3: Cargar tu documento con opciones configuradas (procesamiento de documentos C#)

Con el sistema de advertencias listo, cargar el documento es sencillo. Pasa la instancia de `LoadOptions` al constructor `Document`, y Aspose.Words hará el resto.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Por qué es importante:**  
El objeto `LoadOptions` es el puente entre el archivo bruto y la infraestructura de advertencias. Si lo omites, el documento se carga silenciosamente y cualquier fuente faltante se sustituye sin dejar rastro.

> **Caso límite:** Algunos documentos incrustan los archivos de fuente exactos que necesitan. En ese escenario no aparecerá ninguna advertencia porque Aspose.Words encuentra la fuente incrustada. El código anterior sigue funcionando; simplemente verás una salida de consola vacía.

## Paso 4: Verificar la salida y errores comunes

Ejecuta el programa desde una línea de comandos o el depurador de tu IDE. Si el documento fuente contiene una fuente que no está instalada en la máquina (o no está disponible en la carpeta de fuentes personalizada), verás líneas como:

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Si no se imprime nada, puede ser que:

1. Todas las fuentes fueron encontradas, **o**  
2. El manejador `SubstitutionWarning` no se adjuntó correctamente (verifica nuevamente el Paso 2).

### ¿Por qué ocurren las sustituciones de fuentes?

- **Fuente del sistema faltante:** El SO no tiene la tipografía solicitada.  
- **Formato de fuente no compatible:** Aspose.Words puede leer TrueType y OpenType, pero no todos los formatos propietarios.  
- **Restricciones de licencia:** Algunas fuentes comerciales bloquean la incrustación, obligando a un sustituto.  

Entender el *por qué* te ayuda a decidir si debes incluir las fuentes faltantes con tu aplicación o ajustar el estilo del documento.

## Bonus: Controlar la fuente de sustitución

Si deseas que cada fuente faltante recurra a una familia específica (por ejemplo, “Calibri”), puedes establecer una regla de sustitución global:

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

Ahora la consola seguirá advirtiéndote, pero el resultado visual será consistente en todas las fuentes faltantes.

---

## Resumen

- **Enable Font Warnings** creando un `LoadOptions` con una nueva `FontSettings`.  
- Conectar el evento `SubstitutionWarning` para obtener alertas en tiempo real cada vez que se sustituya una fuente.  
- Cargar tu documento usando las opciones configuradas y, opcionalmente, guardarlo como PDF para ver el efecto visual.  
- Diagnosticar por qué ocurrió una sustitución y, si es necesario, forzar una fuente de sustitución específica.  

Acabas de añadir una red de seguridad a tu flujo de trabajo de **Aspose.Words** que evita cambios de diseño silenciosos. A continuación, podrías explorar **font settings** como `DefaultFontName` o profundizar en las opciones de **document rendering** para afinar la salida PDF.

---

### ¿Qué probar a continuación?

- **Explorar otras características de FontSettings**: `SetFontsFolder`, `LoadFontSources` y `DefaultFontName`.  
- **Combinar advertencias con frameworks de registro** (Serilog, NLog) para diagnósticos de nivel producción.  
- **Experimentar con diferentes formatos de documento** (`.doc`, `.rtf`, `.html`) para ver cómo cada uno maneja fuentes faltantes.  

¿Tienes preguntas o un caso curioso? Deja un comentario abajo, ¡y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}