---
category: general
date: 2026-02-21
description: Aprende cómo habilitar advertencias, detectar fuentes faltantes y cargar
  docx de forma segura usando Aspose.Words en C#. Sigue la guía paso a paso.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: es
og_description: Cómo habilitar advertencias, detectar fuentes faltantes y cargar correctamente
  archivos docx con Aspose.Words. Se incluye un ejemplo de código completo.
og_title: Cómo habilitar advertencias y detectar fuentes faltantes al cargar DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Cómo habilitar advertencias y detectar fuentes faltantes al cargar archivos
  DOCX
url: /es/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

Diagrama que ilustra el flujo desde la carga de un archivo DOCX hasta la captura de advertencias de sustitución de fuentes – cómo habilitar advertencias en Aspose.Words". Keep same path.

Now final shortcodes.

Let's craft final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo habilitar advertencias y detectar fuentes faltantes al cargar archivos DOCX

¿Alguna vez te has preguntado **cómo habilitar advertencias** para fuentes faltantes antes de que arruinen silenciosamente la renderización de tu documento? No estás solo: la mayoría de los desarrolladores asumen que la biblioteca simplemente “hará lo correcto”, solo para descubrir después que una fuente fue reemplazada sin dejar pista.  

En este tutorial te mostraremos exactamente **cómo habilitar advertencias**, cómo **detectar fuentes faltantes**, y la forma correcta **de cargar docx** usando Aspose.Words para .NET. Al final tendrás un ejemplo listo‑para‑ejecutar que imprime cada advertencia de sustitución de fuentes en la consola, para que nunca tengas que adivinar qué ocurrió dentro del archivo.

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7+)
- Visual Studio 2022 o cualquier IDE de C# que prefieras
- El paquete NuGet **Aspose.Words** (`Install-Package Aspose.Words`)
- Un archivo DOCX que pueda contener fuentes no instaladas en tu máquina (lo llamaremos `input.docx`)

> **Consejo profesional:** Si no tienes un archivo de prueba, simplemente abre un documento de Word que use una fuente corporativa personalizada y guárdalo como `input.docx`. Eso generará la advertencia que queremos capturar.

## Visión general de la solución

1. **Crear** un objeto `LoadOptions` con `FontSubstitutionWarnings` activado.  
2. **Cargar** el archivo DOCX usando esas opciones.  
3. **Inspeccionar** la colección `WarningCallback` en busca de entradas `FontSubstitution`.  
4. **Reaccionar** – puedes registrar, mostrar o incluso reemplazar la fuente faltante programáticamente.

A continuación desglosamos cada paso, explicamos *por qué* es importante y te proporcionamos un fragmento de código completo y ejecutable.

---

## Paso 1: Instalar Aspose.Words y configurar el proyecto

Antes de que podamos **cómo habilitar advertencias**, necesitamos la biblioteca que realmente las soporta.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

O, en la consola del Administrador de paquetes de Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **¿Por qué este paso?**  
> Sin el paquete, las clases `LoadOptions`, `Document` y la infraestructura de advertencias simplemente no existen. Añadir la referencia NuGet garantiza que estés obteniendo la última versión estable (a la fecha de este escrito, 24.5).

---

## Paso 2: Crear opciones de carga que habiliten advertencias de sustitución de fuentes

El corazón de **cómo habilitar advertencias** reside en la clase `LoadOptions`. Establecer `FontSubstitutionWarnings` a `true` indica al motor que registre cada vez que tenga que reemplazar una fuente faltante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **¿Por qué activar esta bandera?**  
> Por defecto Aspose.Words sustituye silenciosamente las fuentes faltantes por una de reserva (normalmente Arial). Eso puede provocar desplazamientos de diseño, caracteres invisibles o violaciones de la identidad corporativa. Activar la bandera te brinda total visibilidad.

---

## Paso 3: Cargar el archivo DOCX usando las opciones configuradas

Ahora que sabemos **cómo cargar docx** con advertencias activadas, realizamos la carga.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **¿Qué ocurre internamente?**  
> Mientras analiza el DOCX, Aspose.Words revisa cada elemento `<w:rFonts>`. Si la fuente especificada no está instalada, registra una advertencia `FontSubstitution` y recurre a una fuente predeterminada. Como habilitamos las advertencias, esas entradas aparecen en `document.WarningCallback.Warnings`.

---

## Paso 4: Recuperar y mostrar las advertencias de sustitución de fuentes

La propiedad `WarningCallback` contiene un `WarningInfoCollection`. Recorre la colección, filtra por `WarningType.FontSubstitution` y muestra los mensajes.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Salida esperada** (ejemplo):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **¿Qué hacer con estos mensajes?**  
> Puedes registrarlos en un archivo, mostrarlos en una interfaz de usuario o incluso activar una rutina personalizada de sustitución de fuentes. La clave es que ahora *detectas fuentes faltantes* en lugar de adivinar más tarde.

---

## Paso 5: (Opcional) Reemplazar fuentes faltantes con una reserva específica

Si dispones de una fuente corporativa que deseas imponer, puedes manejar las advertencias y reemplazarlas al vuelo.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **¿Por qué considerar esto?**  
> Garantiza consistencia visual en todos los documentos generados, lo cual es crucial para el cumplimiento de la marca.

---

## Ejemplo completo y ejecutable

A continuación tienes un único archivo C# que puedes copiar‑pegar en una aplicación de consola. Cubre todo: desde la instalación del paquete hasta la impresión de advertencias.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Ejecútalo**: `dotnet run` desde la carpeta del proyecto. Si faltan fuentes, verás las advertencias impresas y el reemplazo opcional se aplicará antes de guardar el archivo.

---

## Preguntas frecuentes

### ¿Esto funciona también con la conversión a PDF?

Sí. Después de manejar las advertencias, puedes llamar a `doc.Save("output.pdf")` y las fuentes sustituidas aparecerán en el PDF tal como lo hacen en el DOCX.

### ¿Qué pasa si necesito suprimir advertencias para una fuente específica?

Puedes filtrarlas en el bucle: simplemente omite el `WarningInfo` cuyo `Message` contenga el nombre de la fuente que deseas ignorar.

### ¿`FontSubstitutionWarnings` está disponible en versiones anteriores de Aspose.Words?

Se introdujo en la versión 20.5. Si estás atrapado en una versión más antigua, actualiza vía NuGet; el cambio de API es compatible hacia atrás.

---

## Conclusión

Hemos recorrido **cómo habilitar advertencias**, te hemos mostrado **cómo detectar fuentes faltantes** y demostrado la forma correcta **de cargar docx** con Aspose.Words manteniendo total visibilidad sobre las sustituciones de fuentes. Al inspeccionar `document.WarningCallback.Warnings` obtienes una pista de auditoría fiable—no más sustituciones silenciosas.

¿Próximos pasos? Prueba conectar la lógica de advertencias a un framework de registro como Serilog, o crea una UI que destaque las fuentes faltantes antes de entregar el documento a los usuarios. También puedes explorar la clase `FontSettings` para un control más granular de las políticas de sustitución de fuentes.

¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como lo deseas! 

![Diagrama que ilustra el flujo desde la carga de un archivo DOCX hasta la captura de advertencias de sustitución de fuentes – cómo habilitar advertencias en Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}