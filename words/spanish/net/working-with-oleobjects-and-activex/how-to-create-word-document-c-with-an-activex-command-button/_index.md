---
category: general
date: 2026-10-26
description: Aprende cómo crear un documento de Word en C# y agregar un botón ActiveX
  programáticamente. Esta guía paso a paso cubre la inserción de un botón de comando,
  ocultarlo en tiempo de diseño y guardar el archivo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: es
lastmod: 2026-10-26
og_description: Crear documento de Word en C# y agregar programáticamente un botón
  ActiveX. Sigue este tutorial completo para incrustar un botón de comando que solo
  aparece en tiempo de ejecución.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Crear un documento Word en C# con un botón de comando ActiveX – guía completa
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Cómo crear un documento Word en C# con un botón de comando ActiveX
url: /es/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word C# con un botón de comando ActiveX

Si necesitas **create Word document C#** que contenga un botón interactivo, esta guía te muestra exactamente cómo. Al final de las dos primeras frases conocerás el enfoque general, y los pasos siguientes te guiarán a través de cada línea de código que debes escribir.

Aprenderás cómo agregar un botón ActiveX, ocultarlo durante el diseño y hacerlo visible solo cuando el usuario abra el archivo. El tutorial también cubre problemas comunes como advertencias de seguridad y compatibilidad de versiones, para que puedas distribuir documentos fiables.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior instalado  
* Una copia con licencia de **Aspose.Words for .NET** (la versión de prueba gratuita sirve para experimentación)  
* Familiaridad básica con C# y Visual Studio (cualquier IDE que soporte .NET sirve)  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words`.

## Paso 1: Crear un Word document C# e inicializar el DocumentBuilder

El primer paso es instanciar un objeto `Document` y un `DocumentBuilder`. El `Document` representa todo el archivo .docx, mientras que el `DocumentBuilder` ofrece métodos fluidos para agregar contenido.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Por qué es importante:** Sin un `DocumentBuilder` tendrías que manipular el DOM OpenXML manualmente, lo que es propenso a errores y más difícil de leer. El builder abstrae esos detalles y garantiza un archivo Word bien formado.

## Paso 2: Cómo agregar un botón ActiveX – insertar un control CommandButton

Ahora insertamos un **control ActiveX CommandButton** en una ubicación específica. El rectángulo define la posición del botón (X, Y) y su tamaño (ancho, alto) en puntos.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Por qué es importante:** `InsertForms2OleControl` es el único método de Aspose.Words que crea un verdadero objeto ActiveX OLE. El valor enum `Forms2OleControlType.CommandButton` indica a Word que incruste un botón clicable en lugar de un contenedor OLE genérico.

## Paso 3: Agregar programáticamente el botón de comando – ocultarlo hasta tiempo de ejecución

Word trata cualquier forma insertada como visible por defecto. Para mantener el botón invisible mientras diseñas la plantilla, establece la propiedad `Hidden` en la forma que el builder acaba de crear.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Por qué es importante:** Establecer `Hidden = true` evita que el botón desordene la vista de diseño. Cuando el documento se abre en Word, el entorno de tiempo de ejecución revela automáticamente el control, preservando la experiencia de usuario prevista.

## Paso 4: Guardar el archivo – crear documento Word con botón de comando

Finalmente, escribe el documento en disco. Elige una ruta a la que tu aplicación pueda escribir y usa la extensión `.docx` para garantizar compatibilidad moderna.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Por qué es importante:** Guardar como `.docx` garantiza que el control ActiveX incrustado cumpla con el estándar Office Open XML, que es compatible con Word 2007 y versiones posteriores. Si necesitas soporte para el legado `.doc`, reemplaza la extensión y usa `SaveFormat.Doc`.

## Ejemplo completo funcional

Juntando todo, aquí está el programa completo que puedes copiar, pegar y ejecutar:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Salida esperada:** Después de ejecutar el programa, abre `C:\Temp\ActiveX.docx` en Microsoft Word. Verás un documento en blanco; el botón no es visible en modo de diseño. Pulsa **Alt + F9** para alternar los códigos de campo, luego haz clic en el área del botón—Word mostrará el control ActiveX y podrás interactuar con él (p. ej., doble clic para ver sus propiedades).

## Casos límite y consejos de buenas prácticas

| Situación | Qué observar | Solución recomendada |
|-----------|--------------|----------------------|
| **El usuario desactiva ActiveX** | Word puede mostrar una advertencia de seguridad o bloquear el control. | Indique a los usuarios finales que habiliten “ActiveX controls” en el Centro de confianza, o proporcione una alternativa con macro firmada. |
| **Documento abierto en Word Online** | Word Online no soporta ActiveX; el botón será omitido. | Utiliza un hipervínculo de respaldo o un control de contenido si necesitas compatibilidad en la nube. |
| **Configuraciones de DPI diferentes** | El tamaño del rectángulo puede aparecer más grande o más pequeño en pantallas de alta DPI. | Usa `GraphicsUnit.Point` (el predeterminado) y prueba en configuraciones de DPI comunes (96 dpi, 120 dpi). |
| **Múltiples botones** | La llamada `GetChildNodes(NodeType.Shape, true)[0]` solo recupera la primera forma. | Itera sobre `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` y establece `Hidden` para cada forma que agregues. |
| **Formato .doc heredado** | Algunas propiedades de ActiveX se pierden al guardar como `.doc`. | Prefiere `.docx` a menos que tengas un requisito estricto de legado. |

**Consejo profesional:** Después de insertar el botón, puedes asignar una macro a su propiedad `OnAction` mediante la interfaz de Word. Esto te permite definir un comportamiento de clic personalizado sin escribir código C# adicional.

## Preguntas frecuentes

* **¿Funciona esto con .NET Core?**  
  Sí. Aspose.Words for .NET es totalmente compatible con .NET 5, .NET 6 y versiones posteriores. Simplemente referencia el mismo paquete NuGet.

* **¿Puedo cambiar el texto del botón después de que se genere el documento?**  
  El texto establecido en `InsertForms2OleControl` se convierte en el texto predeterminado en tiempo de diseño. Los usuarios pueden editarlo en Word, pero también puedes actualizar el texto programáticamente accediendo a las propiedades del objeto OLE mediante la API `Shape.OleFormat`.

* **¿Qué pasa si necesito un tamaño diferente para el botón?**  
  Ajusta los valores de `RectangleF`. Los dos primeros parámetros son las coordenadas X y Y; los últimos dos son el ancho y alto en puntos (1 pt = 1/72 pulgada).

## Conclusión

Ahora sabes cómo **create Word document C#** y **agregar programáticamente un botón de comando** usando Aspose.Words. El tutorial cubrió la inicialización del documento, la inserción de un botón ActiveX, su ocultación hasta tiempo de ejecución y el guardado del archivo final. Con estos bloques de construcción puedes incrustar controles interactivos en cualquier plantilla Word que generes.

A continuación, explora temas relacionados como el manejo de eventos **how to add ActiveX button**, el estilo **create command button word** con VBA, y **programmatically add command button** a documentos existentes. Extender este patrón a casillas de verificación, cuadros combinados u objetos OLE personalizados sigue los mismos pasos—solo cambia el valor del enum `Forms2OleControlType`.

Comienza a experimentar: reemplaza el texto, ajusta la posición o encadena varios controles. Cuanto más practiques, más fluido serás al entregar documentos Word ricos e interactivos desde C#. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo agregar un botón de comando programáticamente en un documento Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Cómo agregar un botón ActiveX en un documento Word con Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Crear documento Word con botón ActiveX – Guía C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}