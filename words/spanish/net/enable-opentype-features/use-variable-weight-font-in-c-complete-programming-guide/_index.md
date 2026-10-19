---
category: general
date: 2026-06-02
description: Aprende a usar fuentes de peso variable en C# y a establecer el peso
  de la fuente programáticamente mientras cambias el código de estiramiento de fuente
  para tipografía dinámica.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: es
og_description: Utiliza fuentes de peso variable en C# para establecer el peso de
  la fuente de forma programática y cambiar el código de estiramiento de la fuente,
  habilitando tipografía dinámica en tus documentos.
og_title: Usa fuentes de peso variable en C# – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Utiliza fuentes de peso variable en C# – Guía completa de programación
url: /es/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usar Fuente de Peso Variable en C# – Guía Completa de Programación

¿Alguna vez necesitaste **usar una fuente de peso variable** en un proyecto .NET pero no estabas seguro de cómo hacer que el peso y el estiramiento respondieran a la entrada del usuario? No estás solo. En muchos escenarios de UI o generación de informes deseas que el texto se adapte—quizá un encabezado ligero que se vuelva negrita al pasar el cursor, o un párrafo que amplíe su ancho para enfatizar. La buena noticia es que con Aspose.Words puedes **establecer el peso de la fuente programáticamente** e incluso **cambiar el código de estiramiento de la fuente** sobre la marcha.

En este tutorial recorreremos un ejemplo práctico que muestra exactamente cómo cargar una fuente de peso variable, aplicar un peso personalizado y ajustar la configuración de estiramiento—todo con código C# claro que puedes copiar y pegar. Al final tendrás una aplicación de consola ejecutable que genera un PDF mostrando el efecto.

---

## Qué Necesitarás

- **Aspose.Words for .NET** (v23.12 o posterior). La biblioteca incluye soporte completo para fuentes de peso variable.
- Una carpeta que contenga al menos un archivo de fuente de peso variable, por ejemplo *RobotoFlex‑Variable.ttf*. Puedes descargarlo de Google Fonts.
- .NET 6 SDK (o cualquier versión reciente de .NET) y el IDE de tu preferencia.
- Conocimientos básicos de C#—nada complicado, solo unas cuantas líneas de código.

Eso es todo. No se requieren paquetes NuGet adicionales más allá de Aspose.Words, y no hay archivos de configuración obscuros.

---

![Ejemplo de uso de fuente de peso variable](https://example.com/variable-weight-sample.png "Demostración del uso de fuente de peso variable")

*Texto alternativo: captura de pantalla que muestra el uso de una fuente de peso variable en un documento PDF generado.*

---

## Paso 1: Configurar FontSettings y Apuntar a tu Carpeta de Fuentes  

Lo primero—Aspose.Words necesita saber dónde viven tus fuentes de peso variable. Lo haces creando un objeto `FontSettings` y adjuntando un `FolderFontSource`. La bandera `true` indica al motor que busque también en subcarpetas, lo cual es útil si mantienes varias familias de fuentes juntas.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Por qué es importante:** Sin registrar la carpeta, Aspose.Words recurre a las fuentes del sistema y omitirá los datos de peso variable incrustados en tu archivo de fuente personalizado. Este paso es la base para todo lo que sigue.

---

## Paso 2: Adjuntar FontSettings al Documento  

Ahora creamos un nuevo `Document` (o cargamos uno existente) y le indicamos que use el `FontSettings` que acabamos de preparar. Esta vinculación es lo que hace que los datos de peso variable estén disponibles para cada `Run` que añadamos después.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Si ya tienes una plantilla—por ejemplo, un archivo Word con marcadores—puedes reemplazar `new Document()` por `new Document("Template.docx")`. Los mismos `FontSettings` se aplicarán.

---

## Paso 3: Añadir un Run de Texto que Usará la Fuente de Peso Variable  

Un **Run** es la unidad más pequeña de formato de texto en Aspose.Words. Crearemos uno, lo insertaremos en un nuevo párrafo y luego cambiaremos sus atributos de fuente.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

En este punto el texto se renderizará usando la fuente predeterminada (usualmente Times New Roman). La magia ocurre cuando asignamos la familia de peso variable.

---

## Paso 4: Elegir la Familia de Fuente de Peso Variable  

Aquí es donde realmente **usamos una fuente de peso variable**. Establece `Font.Name` al nombre exacto de la familia definido dentro del archivo de fuente variable. Para Roboto Flex, el nombre es `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Si no estás seguro del nombre de la familia, abre el archivo `.ttf` en un visor de fuentes o usa el método `fontSettings.GetFonts()` para enumerar las familias disponibles.

---

## Paso 5: Establecer Peso y Estiramiento de Fuente Programáticamente  

Ahora lo esencial del tutorial: **establecemos el peso de la fuente programáticamente** y **cambiamos el código de estiramiento de la fuente**. Ambas propiedades aceptan valores enteros que se corresponden con la especificación OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Elige cualquier valor que la fuente variable admita.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). El valor predeterminado es 100 (Normal).

> **Consejo profesional:** No todas las fuentes variables exponen todo el rango. Si asignas un valor que no está soportado, el motor lo ajustará al peso o estiramiento disponible más cercano.

---

## Paso 6: Guardar el Documento y Verificar el Resultado  

Finalmente, escribe el documento en PDF (o DOCX) y ábrelo para ver el efecto. PDF es un formato excelente para la verificación visual porque el renderizado es consistente en todas las plataformas.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Al abrir *VariableWeightDemo.pdf*, deberías ver la frase “Variable‑weight text demo” renderizada en una versión ligera y ligeramente expandida de Roboto Flex. Cambia `FontWeight` a `700` y `FontStretch` a `80` y vuelve a ejecutar—observa cómo el texto se vuelve negrita y más condensado.

---

## Preguntas Frecuentes y Casos Especiales  

### ¿Qué pasa si la fuente no aparece en absoluto?  

- **FontSettings faltante**: Verifica que `doc.FontSettings = fontSettings;` se ejecute **antes** de añadir cualquier texto.
- **Nombre de familia incorrecto**: Usa `fontSettings.GetFonts()` para listar todas las familias descubiertas; copia la cadena exacta.
- **Peso/estiramiento no soportado**: Algunas fuentes variables solo admiten un subconjunto del rango 100‑900. Usa `run.Font.FontWeight = 400;` como alternativa segura.

### ¿Puedo cambiar el peso después de guardar el documento?  

Sí. El objeto `Run` es mutable, por lo que puedes ajustar `FontWeight` o `FontStretch` en cualquier momento antes del `Save` final. Si necesitas alternar pesos dinámicamente (p. ej., según la interacción del usuario), considera generar runs separados para cada estado.

### ¿Esto funciona con salida DOCX?  

Absolutamente. Los metadatos de peso variable se almacenan en el OpenXML subyacente, y las versiones modernas de Word pueden interpretarlos. Sin embargo, versiones antiguas de Word pueden ignorar la configuración de estiramiento.

---

## Ejemplo Completo Funcional  

A continuación tienes un programa de consola completo que puedes compilar y ejecutar al instante. Incluye todas las directivas `using` necesarias, manejo de errores y comentarios.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Salida esperada:** La consola muestra la ruta de guardado, y el PDF generado muestra el texto en un estilo ligero y expandido—exactamente lo que configuramos.

---

## Recapitulación  

Hemos cubierto cómo **usar una fuente de peso variable** en C# con Aspose.Words, demostrado cómo **establecer el peso de la fuente programáticamente**, y mostrado el **código para cambiar el estiramiento de la fuente** necesario para expandir o condensar los glifos. Los pasos son sencillos: configurar `FontSettings`, adjuntarlos a un `Document`, crear un `Run`, elegir la familia de peso variable y, finalmente, ajustar `FontWeight` y `FontStretch`.

---

## ¿Qué Sigue?  

- **Integración UI dinámica**: Conecta la misma lógica a una aplicación WinForms o WPF para permitir que los usuarios elijan peso/estiramiento mediante controles deslizantes.
- **Múltiples runs**: Combina varios runs con diferentes pesos en el mismo párrafo para jerarquías tipográficas ricas.
- **Ejes avanzados**: Algunas fuentes variables exponen ejes adicionales (p. ej., slant, optical size). Usa `run.Font.FontStyle` o explora `FontVariationSettings` para un control aún más fino.
- **Consejos de rendimiento**: Cachea la instancia de `FontSettings` al procesar muchos documentos para evitar escaneos repetidos de carpetas.

Siéntete libre de experimentar—sustituye *Roboto Flex* por *Inter Variable* o cualquier otra fuente OpenType variable, y observa cómo tus documentos adquieren un nuevo nivel de flexibilidad visual. ¡Feliz codificación!

## ¿Qué Deberías Aprender a Continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}