---
category: general
date: 2025-12-29
description: Aprenda a establecer DPI al convertir Word a PNG con Aspose.Words. Este
  tutorial paso a paso también cubre la exportación de PNG en alta resolución y la
  configuración de la resolución de la imagen.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: es
og_description: Cómo establecer DPI al convertir Word a PNG usando Aspose.Words. Sigue
  esta guía para exportar PNG de alta resolución y controlar la resolución de la imagen.
og_title: Cómo establecer DPI al convertir Word a PNG – Guía completa de C#
tags:
- Aspose.Words
- C#
- Image Export
title: Cómo establecer DPI al convertir Word a PNG – Guía completa de C#
url: /es/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer DPI al convertir Word a PNG – Guía completa en C#

¿Alguna vez te has preguntado **cómo establecer DPI** mientras conviertes un documento Word a PNG? Tal vez necesites capturas nítidas para una presentación, o estés generando recursos imprimibles que deben verse perfectos a 300 dpi. Sea cual sea el caso, estás en el lugar correcto. En este tutorial recorreremos la conversión de un `.docx` multipágina a imágenes PNG de alta resolución usando Aspose.Words, y te mostraremos exactamente cómo definir la resolución de la imagen para que el resultado no quede borroso.

También incluiremos consejos sobre **convert word to png**, **save word as png**, y cómo lograr una **high resolution png export** sin complicaciones. No se requieren documentos externos, solo un ejemplo autocontenido y ejecutable que puedes copiar y pegar en Visual Studio.

---

## Qué necesitarás

- **Aspose.Words for .NET** (última versión, por ejemplo, 24.9).  
- .NET 6+ (o .NET Framework 4.7.2+) – cualquier runtime reciente funciona.  
- Un archivo Word (`MultiPage.docx`) que quieras convertir a PNG.  
- Un entorno de desarrollo – Visual Studio, Rider o VS Code sirven.

Eso es todo. No necesitas paquetes NuGet adicionales más allá de Aspose.Words.

---

## Paso 1: Cargar el documento Word

Lo primero es obtener una representación en memoria del archivo Word. La clase `Document` lo hace por nosotros.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Por qué es importante:** Cargar el documento nos da acceso a su `PageCount`, que necesitaremos más adelante cuando indiquemos a Aspose que exporte **todas las páginas** como PNG.

---

## Paso 2: Configurar ImageSaveOptions con la DPI

Ahora le decimos a Aspose que queremos salida PNG *y* especificamos la DPI. Las propiedades `ImageHorizontalResolution` e `ImageVerticalResolution` son donde ocurre la magia.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Consejo profesional:** 300 dpi es el estándar de facto para gráficos listos para imprimir. Si solo necesitas calidad para pantalla, 96 dpi reducirá drásticamente el tamaño del archivo.

---

## Paso 3: Guardar todas las páginas como un solo PNG mosaico (o archivos separados)

Aspose permite agrupar cada página en un enorme PNG mosaico **o** escribir cada página en su propio archivo. El ejemplo a continuación muestra el enfoque *único mosaico*, pero el `PageSavingCallback` que añadimos ya garantiza que se crearán archivos separados si cambias la bandera `ExportImagesAsSeparateFiles`.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Si prefieres un archivo por página, simplemente establece:

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

y la devolución de llamada se encargará de nombrar cada `Page_#.png`.

---

## Paso 4: Verificar la salida

Después de ejecutar el código, abre `Pages.png` (o los archivos `Page_#.png` generados) en cualquier visor de imágenes. Deberías ver imágenes nítidas y de alta resolución que coinciden con el diseño de las páginas originales de Word.

- **Comprobación de resolución:** Clic derecho → Propiedades → Detalles → DPI horizontal / DPI vertical → debe indicar **300**.  
- **Comprobación de tamaño:** A 300 dpi, una página A4 típica (8.27 in × 11.69 in) se convierte aproximadamente en 2481 × 3508 píxeles – perfecto para impresión.

---

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Salida borrosa** | DPI dejada en el valor predeterminado (96) | Establece explícitamente `ImageHorizontalResolution` **y** `ImageVerticalResolution`. |
| **Páginas faltantes** | `PageSet` solo cubre un subconjunto | Usa `new PageSet(0, multiPageDoc.PageCount - 1)` para incluir todas las páginas. |
| **Colisiones de nombres de archivo** | No se definió la devolución de llamada | Proporciona un `PageSavingCallback` que genere nombres únicos. |
| **Tamaño de archivo grande** | 600 dpi o más sin necesidad | Elige la DPI más baja que aún cumpla con tu requisito de calidad. |
| **Errores de memoria insuficiente** con documentos enormes | Exportar un PNG mosaico masivo | Cambia a `ExportImagesAsSeparateFiles = true` para escribir cada página individualmente. |

---

## Avanzado: Exportar a diferentes variantes de PNG

A veces necesitas un **fondo transparente** o una **profundidad de color distinta**. Aspose.Words admite esos ajustes mediante `PngOptions` dentro de `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

También puedes combinar esto con la configuración de DPI anterior para obtener una **high resolution png export** lista tanto para web como para impresión.

---

## Ejemplo completo y funcional

A continuación tienes el programa completo, listo para copiar y pegar. Solo reemplaza `YOUR_DIRECTORY` con la ruta real en tu máquina.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Ejecuta el programa y obtendrás una **high resolution PNG export** de cada página, cada una con la DPI exacta que configuraste.

---

## Preguntas frecuentes

**P: ¿Esto funciona con archivos `.doc` antiguos?**  
R: Absolutamente. Aspose.Words abstrae el formato, por lo que el mismo código maneja `.doc`, `.docx`, `.rtf` e incluso `.odt`.

**P: ¿Puedo exportar a JPEG en lugar de PNG?**  
R: Sí – solo cambia `SaveFormat.Png` a `SaveFormat.Jpeg` y ajusta `JpegOptions` si es necesario.

**P: ¿Qué pasa si necesito 600 dpi para un póster grande?**  
R: Establece `ImageHorizontalResolution = 600` y `ImageVerticalResolution = 600`. Vigila el uso de memoria; valores de DPI altos inflan rápidamente las dimensiones en píxeles.

**P: ¿Hay una forma de procesar por lotes muchos archivos Word?**  
R: Envuelve la lógica anterior en un bucle `foreach (var file in Directory.GetFiles(folder, "*.docx"))`. Recuerda disponer de cada instancia de `Document` o reutilizar un solo objeto `ImageSaveOptions` para mayor eficiencia.

---

## Conclusión

Hemos cubierto **cómo establecer DPI** al **convertir Word a PNG** usando Aspose.Words, abordado los matices de una **high resolution PNG export**, y te hemos proporcionado un fragmento de código listo para ejecutar que **save word as png** con control preciso de la resolución de la imagen. Ajustando `ImageHorizontalResolution`, `ImageVerticalResolution` y, opcionalmente, `PngOptions`, puedes generar gráficos listos para imprimir o activos ligeros para la web con total confianza.

¿Prximos pasos? Experimenta con diferentes valores de DPI, cambia a exportación de archivos separados, o combina este flujo de trabajo con una canalización PDF‑a‑PNG para un manejo de documentos aún más amplio. Los mismos principios se aplican cuando **set image resolution png** para otros formatos, así que ahora estás preparado para enfrentar una amplia gama de escenarios de exportación de imágenes.

¡Feliz codificación y que tus PNGs siempre sean ultra‑nítidos!

![Cómo establecer DPI al convertir Word a PNG – ejemplo de salida](/images/how-to-set-dpi-word-to-png.png "cómo establecer dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}