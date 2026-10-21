---
category: general
date: 2026-09-21
description: Aprende a generar una plantilla de documento, rellenar una plantilla
  de Word y reemplazar marcadores de posición en un archivo DOCX usando C# – guía
  paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: es
lastmod: 2026-09-21
og_description: Genera una plantilla de documento en C# rellenando una plantilla de
  Word, sustituyendo los marcadores de posición y guardando un archivo DOCX completado.
  Sigue esta guía completa.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Generar plantilla de documento en C# – rellenar archivos DOCX con datos
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Cómo generar una plantilla de documento y rellenarla con datos en C#
url: /es/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo generar una plantilla de documento y completarla con datos en C#

Si necesitas **generar plantillas de documento** que puedan reutilizarse para facturas, contratos o informes, esta guía te muestra exactamente cómo hacerlo. Aprenderás a **poblar plantillas de Word** sustituyendo los marcadores de posición por valores reales y, finalmente, **rellenar plantillas docx** de forma programática.

Crear una plantilla reutilizable elimina la copia‑pega manual y garantiza la consistencia en todos los documentos generados. Los pasos a continuación funcionan con cualquier archivo `.docx` que contenga tokens de marcador de posición simples como `{{Name}}`.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Visual Studio 2022 (o cualquier IDE que prefieras)  
* El paquete NuGet **Aspose.Words for .NET** – proporciona la clase `Document` usada en el ejemplo  

Puedes agregar el paquete con el siguiente comando:

```bash
dotnet add package Aspose.Words
```

## Paso 1: Preparar la plantilla de Word

Crea un documento de Word (`Template.docx`) que contenga marcadores de posición donde debe aparecer la información dinámica. Una convención común es usar llaves dobles:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Guarda el archivo en una carpeta a la que puedas referenciar desde el código, por ejemplo `C:\Docs\Template.docx`.

## Paso 2: Cargar el documento plantilla

La primera acción programática es cargar la plantilla en memoria. El constructor `Document` lee el archivo y construye un modelo de objetos que puedes manipular.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Por qué es importante:** Cargar el archivo crea una copia limpia cada vez, de modo que la plantilla original permanece intacta para ejecuciones futuras.

## Paso 3: Reemplazar los marcadores de posición con datos reales

Aspose.Words ofrece un método sencillo `Range.Replace` que escanea el documento en busca de una cadena específica y la sustituye. Envuelve la llamada en un método auxiliar para mantener el flujo principal ordenado.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Cómo funciona:** `Range.Replace` recorre cada párrafo, celda de tabla, encabezado y pie de página, asegurando que todas las apariciones del token se actualicen. Esta es la forma más fiable de **cómo reemplazar marcadores de posición** en un archivo DOCX.

### Manejo de múltiples ocurrencias y tokens ausentes

* Si un marcador de posición aparece más de una vez, `Replace` actualiza todas las instancias automáticamente.  
* Si un marcador de posición está ausente, el método simplemente no hace nada—no se lanza ninguna excepción.  
* Para documentos grandes, puedes mejorar el rendimiento desactivando `doc.UpdateFields()` hasta que se completen todos los reemplazos.

## Paso 4: Guardar el documento completado

Una vez que todos los marcadores de posición se hayan reemplazado, escribe el resultado en un nuevo archivo. Mantener la salida separada preserva la plantilla original para ejecuciones futuras.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Resultado:** `FilledTemplate.docx` ahora contiene el contenido personalizado:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Paso 5: Verificar la salida (opcional)

Si deseas confirmar programáticamente que los reemplazos se realizaron correctamente, puedes leer el archivo guardado y buscar los valores esperados:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

Ejecutar el paso de verificación imprime `true` cuando el marcador de posición se reemplazó correctamente.

## Problemas comunes y consejos de buenas prácticas

| Problema | Por qué ocurre | Solución recomendada |
|----------|----------------|----------------------|
| **Los marcadores de posición contienen espacios extra** | `"{{ Name }}"` no coincide con `"{{Name}}"`. | Mantén los tokens sin espacios en blanco, o recorta ambos lados antes del reemplazo. |
| **Word agrega formato oculto** | Word puede almacenar el marcador dividido en varios *runs*, lo que hace que `Replace` no lo detecte. | Usa `Document.Range.Replace` con `FindReplaceOptions` configurado con `MatchCase = false` y `FindWholeWordsOnly = false`. |
| **Documentos grandes provocan lentitud** | Reemplazar tokens uno por uno desencadena un escaneo completo del documento cada vez. | Agrupa los reemplazos en una sola pasada llamando a `Range.Replace` para cada token antes de guardar. |
| **Guardar en una carpeta de solo lectura** | `doc.Save` lanza una `UnauthorizedAccessException`. | Asegúrate de que el directorio de destino tenga permisos de escritura, o elige una ruta accesible para el usuario (p. ej., `%TEMP%`). |

## Ejemplo completo funcionando

A continuación se muestra el programa completo, autocontenido, que puedes copiar, pegar y ejecutar.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Salida esperada en la consola**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Abre `FilledTemplate.docx` en Microsoft Word para ver el texto personalizado.

## Conclusión

Ahora sabes cómo **generar plantillas de documento**, **poblar plantillas de Word** y **rellenar plantillas docx** mediante **cómo reemplazar marcadores de posición** con datos reales. El enfoque funciona con cualquier número de marcadores y escala a documentos grandes cuando sigues los consejos de buenas prácticas.

### ¿Qué sigue?

* **Tablas dinámicas:** Usa `DocumentBuilder` para insertar filas basadas en colecciones.  
* **Secciones condicionales:** Oculta o muestra partes de la plantilla con campos `IF`.  
* **Exportación a PDF:** Llama a `doc.Save("output.pdf")` para crear una versión PDF del documento completado.  

Experimenta con estas variantes para construir un motor de generación de documentos completo para facturas, contratos o cualquier informe repetible.

---


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Generate Word Document](/words/english/java/word-processing/generate-word-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}