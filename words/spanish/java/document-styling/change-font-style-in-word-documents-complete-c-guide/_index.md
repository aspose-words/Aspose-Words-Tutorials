---
category: general
date: 2026-06-27
description: Cambiar el estilo de fuente en documentos de Word con C#. Aprende a establecer
  el grosor de la fuente, aplicar negrita y ajustar el ancho de la fuente para una
  tipografía precisa.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: es
og_description: Cambiar el estilo de fuente en documentos de Word con C#. Descubre
  cómo establecer el grosor de la fuente, aplicar negrita y ajustar el ancho de la
  fuente en unos pocos pasos sencillos.
og_title: Cambiar el estilo de fuente en documentos de Word – Guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Cambiar el estilo de fuente en documentos de Word – Guía completa de C#
url: /es/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cambiar estilo de fuente en documentos Word – Guía completa en C#

¿Alguna vez necesitaste **cambiar el estilo de fuente** en un archivo Word pero no estabas seguro de qué llamada a la API realmente lo logra? No estás solo—la mayoría de los desarrolladores se topan con esa barrera cuando intentan ajustar la tipografía de forma programática.  

La buena noticia es que con unas pocas líneas de C# puedes **establecer el peso de la fuente**, incluso incrementar un peso en negrita, y afinar el ancho de cada glifo. En este tutorial recorreremos un ejemplo completo y ejecutable que modifica un archivo `.docx` de principio a fin.

## Qué cubre esta guía

Comenzaremos cargando un documento existente, luego crearemos un objeto `FontSettings` que contiene un `FontVariation`. A partir de ahí **estableceremos el peso de la fuente**, **estableceremos el peso en negrita** y **ajustaremos el ancho de la fuente** antes de aplicar los cambios y guardar el resultado. Sin archivos de configuración externos, sin cadenas mágicas—solo C# puro y la biblioteca Aspose.Words. Al final podrás **modificar la fuente en documentos Word** con confianza, ya sea que estés construyendo un motor de informes o una herramienta de formato masivo.

### Requisitos previos

- .NET 6.0 o posterior (el código también compila en .NET Core)  
- Paquete NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un archivo de ejemplo `input.docx` colocado en una carpeta a la que puedas referenciar (lo llamaremos `YOUR_DIRECTORY`)  

Si ya tienes esos elementos básicos, vamos a sumergirnos.

---

## Paso 1: Cambiar estilo de fuente – Cargar el documento Word

Lo primero que debes hacer es cargar el archivo objetivo en memoria. Piensa en esto como abrir un lienzo en blanco donde luego pintarás tu nueva tipografía.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Consejo profesional:** Si ejecutas esto en un servidor sin interfaz gráfica, asegúrate de que la licencia de Aspose.Words esté configurada como prueba o que hayas aplicado un archivo de licencia correcto para evitar mensajes de marca de agua.

---

## Paso 2: Establecer peso de fuente y establecer peso en negrita

Ahora que el documento está en memoria, creamos un contenedor `FontSettings`. Este objeto es la puerta de entrada a cada ajuste a nivel de fuente que puedes realizar.  

La clase `FontVariation` te permite especificar tres atributos principales:

| Property | What it does | Typical range |
|----------|--------------|---------------|
| `Weight` | Controls how heavy the glyph appears. A value of **700** is the standard “bold”. | 100‑900 |
| `Width`  | Stretches or condenses the glyph horizontally. **100** means normal width. | 50‑200 |
| `Slant`  | Adds an italic‑like tilt. Positive numbers slant right. | -90‑90 |

A continuación **establecemos el peso de la fuente** a 700 (negrita) y también demostramos cómo podrías aumentarlo aún más si tu fuente admite un estilo “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Por qué es importante:** Establecer el **peso en negrita** directamente mediante `SetWeight` evita la necesidad de un objeto de estilo “Bold” separado, dándote un control pixel‑perfecto sobre cuán gruesos se vuelven los trazos.

---

## Paso 3: Ajustar ancho de fuente

Si alguna vez necesitaste que una fuente se vea más compacta para un titular o más espaciosa para un párrafo, estarás contento de haber llegado a este paso. La propiedad `Width` hace exactamente eso.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Error común:** No todas las tipografías respetan variaciones de ancho. Si no ves un cambio visual, verifica que la familia de fuentes que estás usando admita glifos condensados/expandidos.

---

## Paso 4: Aplicar la configuración de fuente – Modificar fuente en Word

Con nuestro `FontSettings` totalmente configurado, el salto final es indicarle al documento que lo use. Aquí es donde **modificamos la fuente en Word** a nivel de documento, afectando cada ejecución de texto que hereda el estilo predeterminado.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Si solo deseas apuntar a un párrafo o ejecución específicos, puedes obtener ese nodo y establecer su `FontSettings` individualmente. El ejemplo anterior muestra el enfoque de amplio alcance, perfecto para escenarios de formato masivo.

---

## Paso 5: Guardar y verificar los cambios

Guardar es la última, pero ciertamente no la menos importante, parte del flujo de trabajo. Después de persistir el archivo puedes abrirlo en Microsoft Word para ver el nuevo estilo en acción.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Resultado esperado

- Todo el texto del cuerpo que antes usaba la fuente predeterminada ahora aparece **en negrita** (peso 700).  
- Si experimentaste con `SetWidth(80)`, los caracteres se verán un poco más compactos; `SetWidth(120)` los expandirá.  
- Ningún otro contenido (imágenes, tablas, etc.) se altera—solo las características tipográficas de los fragmentos de texto.

Abre `output.docx` en Word, selecciona un párrafo y revisa el cuadro de diálogo **Fuente**. Verás la casilla **Negrita** marcada y la **Escala** (ancho) reflejando el valor que elegiste.

---

## Preguntas frecuentes y casos límite

### ¿Puedo cambiar la familia de fuentes al mismo tiempo?

Claro. Después de haber configurado el `FontVariation`, también puedes asignar un nuevo `FontInfo` al `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### ¿Qué pasa si solo quiero **establecer el peso en negrita** para los encabezados?

Obtén el nodo del estilo de encabezado y aplica una instancia separada de `FontSettings`:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### ¿Funciona con .NET Core en Linux?

Sí—Aspose.Words es multiplataforma. Solo asegúrate de tener instaladas las bibliotecas de tiempo de ejecución apropiadas (`libgdiplus` en algunas distribuciones) si planeas renderizar el documento a PDF más adelante.

---

## Conclusión

Acabamos de **cambiar el estilo de fuente** en un documento Word de principio a fin, cubriendo cómo **establecer el peso de la fuente**, **establecer el peso en negrita** y **ajustar el ancho de la fuente** usando C#. El ejemplo completo y ejecutable muestra cada importación requerida, creación de objetos y llamada a método, para que puedas copiar‑pegarlo en tu propio proyecto y ver la tipografía transformarse al instante.

Ahora que sabes cómo **modificar la fuente en Word**, podrías explorar temas relacionados como **incrustar fuentes personalizadas**, **aplicar degradados de color** o **crear tablas dinámicas**. Cada uno de esos se basa en la misma base `FontSettings` que usamos aquí, así que ya tienes una ventaja.

¿Tienes un escenario que no está cubierto? Deja un comentario y lo investigaremos juntos. ¡Feliz codificación—y que tus documentos siempre luzcan exactamente como los imaginas!  

![ejemplo de cambio de estilo de fuente](placeholder.png){alt="ejemplo de cambio de estilo de fuente"}

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}