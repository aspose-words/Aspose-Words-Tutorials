---
category: general
date: 2026-01-08
description: Cree un documento de Word en blanco y aprenda cómo agregar sombra a una
  forma rectangular. Inserte archivos de Word con formas y añada sombra a la forma
  en C# usando Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: es
og_description: Crea un documento Word en blanco y descubre cómo agregar sombra a
  una forma rectangular usando C#. Código completo, explicaciones y consejos.
og_title: Crear documento de Word en blanco – Añadir forma de rectángulo con sombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento de Word en blanco con forma de rectángulo sombreado – Guía
  paso a paso
url: /es/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco con forma de rectángulo con sombra – Tutorial completo

¿Alguna vez necesitaste **crear documentos Word en blanco** de forma programática y luego adornarlos con un bonito rectángulo con sombra? No eres el único. Muchos desarrolladores se topan con un obstáculo cuando descubren que insertar formas y aplicar efectos no es tan sencillo como escribir texto.  

En esta guía recorreremos todo el proceso —desde crear un `.docx` vacío hasta **cómo agregar sombra** a un objeto **rectangle shape word**, y finalmente **insertar shape word** contenido con un pulido efecto **add shape shadow**. Al final tendrás un fragmento listo para usar que funciona con la última versión de Aspose.Words para .NET.

---

## Lo que necesitarás

- **Aspose.Words for .NET** (v24.10 o más reciente) – la biblioteca que impulsa todo lo siguiente.  
- Un entorno de desarrollo .NET (Visual Studio, Rider o la CLI `dotnet`).  
- Conocimientos básicos de C# – si puedes escribir “Hello World”, estás listo.  

No se requieren paquetes NuGet adicionales; todo reside dentro de `Aspose.Words` y `System.Drawing`.

---

## Paso 1: Crear un documento Word en blanco

Lo primero es crear un objeto `Document` vacío. Piensa en él como un lienzo nuevo, como al abrir manualmente un archivo Word nuevo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Por qué es importante:*  
Una instancia de `Document` representa todo el archivo Word. Comenzar con uno en blanco te brinda control total sobre cada elemento que agregarás después, desde párrafos hasta formas.

---

## Paso 2: Definir una forma de rectángulo (Rectangle Shape Word)

Ahora necesitamos una forma con la que trabajar. Un rectángulo es la geometría más simple y funciona bien para banners, marcadores de posición o maquetas de UI simples.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Por qué es importante:*  
Configurar `Width` y `Height` te permite controlar la huella visual de la forma. `ShapeType.Rectangle` indica a Aspose que renderice una caja clásica, perfecta para demostrar **add shape shadow** más adelante.

---

## Paso 3: Aplicar una sombra a la forma (How to Add Shadow)

Las sombras añaden profundidad, haciendo que un rectángulo plano parezca un objeto físico. Aspose.Words expone una propiedad `Shadow` donde puedes ajustar color, distancia, desenfoque y transparencia.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Por qué es importante:*  
Cada propiedad influye en la pista visual:

- **Enabled** – sin esto, los demás ajustes se ignoran.  
- **Color** – elige un tono que coincida con el tema de tu documento.  
- **Distance** – valores mayores alejan más la sombra.  
- **BlurRadius** – números mayores hacen la sombra más suave.  
- **Transparency** – ajusta finamente la opacidad para mayor sutileza.

Siéntete libre de experimentar; para un efecto dramático, aumenta `Distance` a `10` y establece `Transparency` en `0.5`.

---

## Paso 4: Insertar la forma en el documento (Insert Shape Word)

Con el rectángulo listo, necesitamos un lugar para colocarlo. El sitio más sencillo es el primer párrafo del cuerpo del documento.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Por qué es importante:*  
`FirstSection.Body.FirstParagraph` siempre está presente en un `Document` nuevo. Al agregar la forma aquí, garantizas que la forma aparezca en la parte superior del archivo, útil para encabezados o banners de título.

Si necesitas insertar la forma en otro lugar, puedes localizar un `Paragraph` o `Run` específico y usar `InsertAfter` o `InsertBefore`.

---

## Paso 5: Guardar el archivo Word

El paso final es persistir el documento en memoria en el disco. Elige una carpeta a la que tengas acceso de escritura y asigna al archivo un nombre significativo.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Por qué es importante:*  
Llamar a `Save` escribe un archivo `.docx` totalmente compatible. Ábrelo en Microsoft Word, LibreOffice o cualquier visor, y verás un rectángulo con una sombra gris suave, exactamente lo que configuramos.

---

## Ejemplo completo funcionando

A continuación tienes el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye todas las directivas `using`, la creación de la forma, la configuración de la sombra, la inserción y el guardado.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Salida esperada:**  
Abre `ShadowedRectangle.docx` y verás un rectángulo gris claro centrado en la parte superior de la página con una sombra sutil desplazada 5 pts. Sin texto adicional, solo la forma, exactamente lo que produce el código.

---

## Preguntas comunes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Reemplaza `ShapeType.Rectangle` por cualquier otro valor del enum `ShapeType` (`Ellipse`, `Triangle`, `Star`, etc.). Las propiedades de sombra funcionan de la misma manera.

### ¿Puedo agregar múltiples sombras?

Aspose.Words solo admite una sombra por forma. Si necesitas efectos en capas, crea dos formas superpuestas con diferentes configuraciones de sombra.

### ¿Cómo funciona esto en .NET Core?

La misma API funciona en .NET 6/7/8. Solo asegúrate de referenciar el paquete **Aspose.Words.NETCore** (o el paquete estándar, que ahora es multiplataforma).

### ¿`System.Drawing` sigue siendo compatible en Linux?

`System.Drawing.Common` es solo para Windows a partir de .NET 6. Para proyectos multiplataforma, usa `Aspose.Drawing` (un NuGet separado) o mantente con los colores definidos por `Aspose.Words`.

### ¿Qué pasa con el escalado DPI?

Las dimensiones de la forma están en puntos (1 pt = 1/72 pulgada). Si necesitas un tamaño exacto en píxeles para un DPI específico, calcula los puntos como `pixels * 72 / dpi`.

---

## Consejos profesionales y trampas

- **Consejo profesional:** Configura `rectangleShape.WrapType = WrapType.Inline;` si deseas que la forma fluya con el texto en lugar de flotar sobre él.  
- **Cuidado con:** Olvidar habilitar la sombra (`Enabled = true`). Los demás ajustes se ignorarán silenciosamente.  
- **Nota de rendimiento:** Añadir muchas formas en un bucle ajustado puede ser lento. Agrúpalas en una sola `Section` y llama a `document.UpdatePageLayout()` una vez al final.  
- **Verificación de versión:** La API de sombra se introdujo en Aspose.Words 20.2. Si usas una versión anterior, actualiza para evitar propiedades faltantes.

---

## Conclusión

Hemos **creado un documento Word en blanco**, construido una **rectangle shape word**, aprendido **cómo agregar sombra**, y finalmente **insertado shape word** contenido con un pulido efecto **add shape shadow**, todo usando Aspose.Words para .NET.  

El fragmento es completamente ejecutable, funciona en Windows y .NET multiplataforma, y puede ampliarse a otras formas, colores o incluso GIFs animados. A continuación, podrías explorar agregar texto dentro del rectángulo, aplicar rellenos degradados o generar un informe completo con múltiples formas estilizadas.

¿Tienes más ideas? Prueba cambiar la sombra gris por una azul, aumenta el desenfoque para un aspecto etéreo, o combina varias formas en un logotipo personalizado. El cielo es el límite, y ahora tienes los bloques de construcción para hacerlo.

¡Feliz codificación, y que tus documentos siempre luzcan nítidos (con la cantidad justa de sombra)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}