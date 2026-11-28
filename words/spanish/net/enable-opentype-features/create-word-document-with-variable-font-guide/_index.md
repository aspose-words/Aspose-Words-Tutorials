---
category: general
date: 2026-03-19
description: Crear documento Word usando Aspose.Words y una fuente variable. Aprende
  cómo cambiar el peso de la fuente, establecer el ancho de la fuente y definir la
  variación de la fuente en C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: es
og_description: Crea un documento Word con una fuente variable usando Aspose.Words.
  Este tutorial te muestra cómo cargar la fuente, cambiar el peso de la fuente, establecer
  el ancho de la fuente y definir la variación de la fuente.
og_title: Crear documento de Word con fuente variable – Guía completa
tags:
- Aspose.Words
- C#
- Variable Font
title: Crear documento de Word con fuente variable – Guía
url: /es/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con fuente variable – Guía

¿Alguna vez necesitaste **crear un documento Word** que use una fuente variable moderna, pero no sabías por dónde empezar? No estás solo. En muchos proyectos—piensa en informes dinámicos o folletos con coherencia de marca—poder **cambiar el peso de la fuente** al vuelo es un verdadero cambio de juego.  

En este tutorial recorreremos todo el proceso: desde cargar una fuente variable en Aspose.Words, hasta establecer su peso y ancho, y finalmente guardar un DOCX que se vea exactamente como lo diseñaste. Sin referencias vagas, solo código concreto que puedes insertar en tu proyecto C# ahora mismo.

## Lo que aprenderás

- Cómo **cargar fuentes variables** en Aspose.Words usando `FontSettings`.
- La sintaxis para **definir ejes de variación de fuente** como `wght` (peso) y `wdth` (ancho).
- Formas de **establecer el ancho de la fuente** y **cambiar el peso de la fuente** en un solo `Run`.
- Consejos para solucionar problemas comunes (glifos faltantes, rutas de carpetas incorrectas, etc.).
- Un ejemplo completo y ejecutable que puedes copiar‑pegar y probar al instante.

> **Requisitos previos**: .NET 6+ (o .NET Framework 4.6+), Aspose.Words para .NET instalado vía NuGet, y un archivo de fuente variable como *RobotoFlex.ttf* colocado en una carpeta local *Fonts*.

---

## Paso 1 – Cargar la fuente variable en Aspose.Words

Primero, debemos indicarle a Aspose.Words dónde buscar nuestras fuentes personalizadas. La clase `FontSettings` hace el trabajo pesado.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Por qué es importante**: Sin registrar la carpeta, Aspose.Words recurre a las fuentes del sistema y omitirá cualquier dato de variación OpenType que intentes aplicar después. Al apuntar a un directorio específico garantizas que *RobotoFlex* (o cualquier otra fuente variable) se encuentre cada vez que se ejecute el código.

> **Consejo profesional**: Establece el segundo parámetro de `SetFontsFolder` en `true` si deseas que Aspose busque también en sub‑carpetas. Esto ayuda cuando organizas fuentes por estilo o peso.

---

## Paso 2 – Crear un nuevo documento y añadir texto de ejemplo

Ahora que el motor de fuentes sabe dónde buscar, creamos un `Document` vacío e insertamos un párrafo con un `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Qué está ocurriendo**: `Run` representa una pieza contigua de texto con formato uniforme. Al crearla primero, mantenemos la lógica de formato aislada—perfecto para aplicar más tarde diferentes ejes de variación a `Run` separados si es necesario.

---

## Paso 3 – Definir los ejes de variación deseados (Peso y Ancho)

Las fuentes variables exponen *ejes* que puedes ajustar en tiempo de ejecución. Los dos más comunes son `wght` (peso de la fuente) y `wdth` (ancho de la fuente). Aspose.Words modela esto con la colección `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Por qué estos números**: En la especificación OpenType, `wght` varía desde el peso mínimo hasta el máximo de la fuente (a menudo 100–900). Un valor de **700** equivale a una apariencia negrita. `wdth` funciona de manera similar; **100** significa el ancho predeterminado (normal), mientras que valores por debajo de 100 condensan los glifos.

> **Caso límite**: Algunas fuentes variables no admiten un eje en particular. Si proporcionas una etiqueta no soportada, Aspose la ignorará silenciosamente. Siempre verifica la especificación de la fuente (normalmente encontrada en los metadatos del archivo `.ttf` o `.otf`).

---

## Paso 4 – Aplicar la variación al Run usando el nombre de la fuente

Ahora vinculamos los datos de variación al texto real. La clase `FontInfo` contiene el nombre de la familia de la fuente y la colección de ejes.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explicación**: Al establecer `FontInfo`, evitamos la propiedad habitual `Font.Name` y entregamos al motor una configuración de fuente totalmente calificada. Esta es la única forma de indicarle a Aspose.Words que use una fuente variable con ejes personalizados.

> **Error frecuente**: Olvidar coincidir exactamente con el nombre de familia dentro del archivo de fuente (`RobotoFlex` en este ejemplo). Un error tipográfico hará que Aspose recurra a una fuente predeterminada y tu variación se perderá.

---

## Paso 5 – Guardar el documento y verificar el resultado

Finalmente, escribe el documento en disco. El DOCX generado contendrá las instrucciones de la fuente variable, que Microsoft Word (2016+) puede renderizar correctamente.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Abre el archivo resultante en Word, selecciona el texto y observa el cuadro de diálogo **Fuente**. Deberías ver *Roboto Flex* listado, y el texto aparecerá más grueso que el contenido circundante—exactamente lo que solicitó la configuración `wght = 700`.

> **Consejo de verificación**: Si el texto parece sin cambios, verifica que el archivo de fuente realmente soporte el eje `wght`. Algunas fuentes “variables” solo exponen `ital` (cursiva) o `opsz` (tamaño óptico).

---

## Opcional: Añadir más variación – Cambiar el ancho dinámicamente

Si deseas *establecer el ancho de la fuente* de forma diferente para otro párrafo, simplemente repite los pasos 3‑4 con una nueva colección `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Ahora tienes dos `Run`—uno en negrita, otro ligeramente más ancho—demostrando tanto **cambiar el peso de la fuente** como **establecer el ancho de la fuente** en el mismo documento.

---

## Ejemplo completo y funcional

Copia el fragmento a continuación en una nueva aplicación de consola (`Program.cs`) y ejecútalo. Asegúrate de que la carpeta `Fonts` contenga `RobotoFlex.ttf` (o cualquier fuente variable que prefieras).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Salida esperada**: Un archivo `VariableFont.docx` donde la frase “Variable‑weight text” aparece en negrita, gracias al eje `wght = 700`, manteniendo el ancho predeterminado.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si no se encuentra la fuente?* | Verifica la ruta de la carpeta, asegura que el nombre del archivo coincida y que el proceso tenga permisos de lectura. También puedes llamar a `fontSettings.GetFonts()` para listar las fuentes detectadas. |
| *¿Puedo combinar varios runs con variaciones diferentes?* | Por supuesto. Cada `Run` puede llevar su propio `FontInfo`. Simplemente repite los pasos 3‑4 para cada run. |
| *¿Versiones anteriores de Word admiten fuentes variables?* | Word 2016 (Build 16.0.8001) introdujo soporte básico. Si apuntas a versiones más antiguas, el documento recurrirá a la instancia estática más cercana de la fuente. |
| *¿Hay un límite de cuántos ejes puedo establecer?* | Puedes establecer cualquier número que la fuente defina. Las etiquetas comunes son `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Proveer una etiqueta no soportada simplemente no tiene efecto. |
| *¿Cómo depuro glifos faltantes?* | Usa `FontSettings.GetFontSources()` para inspeccionar las fuentes cargadas, y `FontInfo.HasGlyph(char)` para probar caracteres individuales. |

---

## Conclusión

En unos pocos pasos hemos demostrado **cómo crear documentos Word** que aprovechan el poder de las fuentes variables, permitiéndote **cambiar el peso de la fuente**, **establecer el ancho de la fuente**, **cargar archivos de fuentes variables** y **definir ejes de variación de fuente**, todo con Aspose.Words para .NET.  

La idea central es sencilla: registrar la carpeta de fuentes, describir los ejes deseados, adjuntarlos a un `Run` y guardar. Desde aquí puedes ampliar la técnica a secciones completas, tablas o incluso generar informes específicos de marca de forma programática.

**Próximos pasos**: prueba cambiar `RobotoFlex` por otra fuente variable, experimenta con el eje `ital` (cursiva), o genera una versión PDF del mismo documento usando Aspose.PDF. El mismo patrón se aplica—cargar, definir, aplicar, guardar.

¡Feliz codificación y disfruta de la flexibilidad que las fuentes variables aportan a tus proyectos de automatización de Word!

<img src="variable-font-demo.png" alt="Crear documento word con fuente variable ejemplo">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}