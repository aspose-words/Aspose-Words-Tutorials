---
category: general
date: 2026-08-04
description: Cambiar el separador de notas al pie en C# usando Aspose.Words – aprende
  cómo editar el separador de notas al pie y cambiar el separador de notas finales
  en documentos de Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: es
lastmod: 2026-08-04
og_description: Cambiar el separador de notas al pie en C# con Aspose.Words. Esta
  guía muestra cómo editar el separador de notas al pie, personalizar el separador
  de notas finales y guardar el documento actualizado.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Cambiar el separador de notas al pie en C# – guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Cambiar el separador de notas al pie en C# usando Aspose.Words
url: /es/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cambiar el separador de notas al pie en C# usando Aspose.Words

Si necesitas **cambiar el separador de notas al pie** en un documento Word, este tutorial te guía paso a paso con Aspose.Words para .NET. Ya sea que quieras reemplazar la línea predeterminada por un símbolo, o aplicar un estilo diferente a los separadores de notas finales, el código a continuación cubre todo el flujo de trabajo.

También aprenderás cómo **editar el separador de notas al pie** y la operación relacionada **cambiar el separador de notas finales**, de modo que el mismo documento pueda tener un estilo coherente tanto para notas al pie como para notas finales. No se requieren herramientas externas, solo unas pocas líneas de C#.

## Lo que lograrás

* Cargar un archivo *.docx* existente que contenga notas al pie y notas finales.  
* Acceder a los nodos separadores de notas al pie, continuaciones de notas al pie y notas finales.  
* Reemplazar el carácter separador (por ejemplo, cambiar la línea predeterminada por un asterisco).  
* Guardar el documento modificado sin perder ningún otro contenido.  

El tutorial asume que tienes un conocimiento básico de C# y que has instalado el paquete NuGet **Aspose.Words** (versión 24.9 o posterior).  

---

## Requisitos previos

| Requisito | Razón |
|-------------|--------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Entorno de ejecución requerido para Aspose.Words |
| Aspose.Words for .NET library | Proporciona las APIs `Document` y `FootnoteOptions` |
| An input Word file (`input.docx`) with at least one footnote or endnote | Un archivo Word de entrada (`input.docx`) con al menos una nota al pie o nota final que demuestre el cambio de separador |

Puedes agregar Aspose.Words a tu proyecto con el siguiente comando CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Paso 1: Cargar el documento que contiene notas al pie

La primera operación es leer el archivo fuente en un objeto `Document`. Este objeto representa todo el archivo Word en memoria y te brinda acceso a todos sus nodos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Por qué es importante:** Cargar el documento es el punto de entrada para cualquier manipulación. Si el archivo no se encuentra, Aspose.Words lanza una `FileNotFoundException`, así que asegúrate de que la ruta sea correcta antes de continuar.

---

## Paso 2: Acceder a los nodos separadores de notas al pie y notas finales

`Document.FootnoteOptions` expone tres nodos separadores:

* `Separator` – la línea que aparece después de la colección de notas al pie en la primera página.  
* `ContinuationSeparator` – la línea que se usa cuando las notas al pie continúan en la página siguiente.  
* `EndnoteSeparator` – la línea que separa el texto principal de la lista de notas finales.

Obtienes estos nodos como objetos genéricos `Node`, y luego los conviertes a `Run` para modificar el texto.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Por qué es importante:** Estos nodos son los únicos lugares donde reside el carácter separador visual. Cambiar cualquier otro nodo (p.ej., un párrafo normal) no afectará el formato de las notas al pie.

---

## Paso 3: Cambiar el carácter del separador de notas al pie

El requisito más común es reemplazar la línea predeterminada por un símbolo como un asterisco (`*`). Dado que el separador se almacena como un `Run`, puedes modificar de forma segura su propiedad `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Por qué es importante:** Editar directamente `Run.Text` actualiza la representación visual en el documento final sin afectar el resto del contenido de la nota al pie. El mismo patrón se puede usar para aplicar cualquier cadena, incluidos símbolos Unicode.

---

## Paso 4: Cambiar el separador de notas finales (opcional)

Si también necesitas **cambiar el separador de notas finales**, el proceso es similar al cambio de la nota al pie. Reemplaza el texto de `endnoteSeparator` con el carácter que desees.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Por qué es importante:** Las notas finales a menudo tienen un estilo diferente al de las notas al pie. Proporcionar un separador independiente te permite mantener la consistencia visual con las directrices de diseño de tu documento.

---

## Paso 5: Guardar el documento modificado

Después de todas las modificaciones, persiste los cambios usando `Document.Save`. Puedes sobrescribir el archivo original o escribir en una nueva ubicación.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Por qué es importante:** `Save` escribe la representación en memoria en el disco, preservando todos los demás elementos (estilos, imágenes, tablas) sin cambios.

---

## Ejemplo completo y ejecutable

Juntando todas las piezas, aquí tienes una aplicación de consola autónoma que demuestra todo el flujo de trabajo:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Resultado esperado:** Abre *ModifiedSeparators.docx* en Microsoft Word. La línea del separador de notas al pie en la parte inferior de la primera página de notas al pie será ahora un solo asterisco (`*`). Si el documento contiene notas finales, la línea que separa el texto principal de la lista de notas finales aparecerá como un guion (`-`). Todo el demás contenido (texto, imágenes, tablas) permanece intacto.

---

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si el documento no tiene notas al pie?** | `FootnoteOptions.Separator` todavía devuelve un nodo `Run`, pero su texto puede estar vacío. El código verifica de forma segura el tipo de nodo antes de modificarlo. |
| **¿Puedo usar una cadena de varios caracteres (p.ej., "***")?** | Sí. La propiedad `Run.Text` acepta cualquier cadena, incluidos caracteres Unicode. |
| **¿Cambiar el separador afecta la numeración existente de notas al pie?** | No. El separador es independiente del esquema de numeración. |
| **¿Necesito disponer del objeto `Document`?** | `Document` implementa `IDisposable` implícitamente a través de `Node`. En una aplicación de consola de corta duración es opcional, pero para servicios de larga ejecución puedes envolverlo en un bloque `using`. |
| **¿Cómo funciona esto con .NET Core vs .NET Framework?** | La API es idéntica en ambos entornos; solo importa la versión del framework objetivo (debe ser compatible con el paquete Aspose.Words). |

**Consejo profesional:** Si necesitas aplicar diferentes separadores para distintas secciones, puedes iterar a través de `doc.GetChildNodes(NodeType.Footnote, true)` y ajustar individualmente la propiedad `Separator` de cada nota al pie. Esto es más avanzado pero útil para documentos complejos.

---

## Conclusión

Ahora sabes cómo **cambiar el separador de notas al pie** y **cambiar el separador de notas finales** en un archivo Word usando Aspose.Words para C#. La guía cubrió cargar el documento, acceder a los nodos separadores relevantes, modificar su texto y guardar el resultado, todo en un único programa autónomo.

A partir de aquí puedes explorar temas relacionados como **editar el estilo del separador de notas al pie**, personalizar la numeración de notas al pie, o aplicar formato condicional basado en el diseño de página. El mismo patrón (obtener un nodo, convertir a `Run`, modificar `Text`) funciona para muchos otros escenarios de procesamiento de Word.

¡Feliz codificación, y siéntete libre de experimentar con diferentes símbolos o incluso incrustar imágenes como separadores para lograr un diseño de documento verdaderamente único!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Procesamiento de Word con notas al pie y notas finales](/words/english/net/working-with-footnote-and-endnote/)
- [Obtener separador de estilo de párrafo en documento Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insertar separador de estilo de documento en Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}