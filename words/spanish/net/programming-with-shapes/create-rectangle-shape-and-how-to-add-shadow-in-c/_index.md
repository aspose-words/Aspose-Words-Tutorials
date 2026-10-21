---
category: general
date: 2026-04-04
description: Crear una forma rectangular en C# con Aspose.Words y aprender cómo agregar
  sombra, aplicar desenfoque a la sombra y hacer la sombra transparente – guía paso
  a paso.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: es
og_description: Crea una forma rectangular en C# con Aspose.Words. Aprende cómo agregar
  sombra, aplicar desenfoque a la sombra y hacerla transparente en un tutorial conciso.
og_title: Crear forma rectangular y cómo agregar sombra en C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear forma de rectángulo y cómo agregar sombra en C#
url: /es/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma de rectángulo y cómo añadir sombra en C#

¿Alguna vez necesitaste **crear una forma de rectángulo** en un documento de Word pero no sabías cómo darle una sombra sutil? No estás solo. En muchos escenarios de informes o branding, un simple rectángulo con una sombra suave y semitransparente puede darle al diseño un aspecto pulido sin mucho esfuerzo.

En este tutorial recorreremos **cómo crear un documento** usando Aspose.Words, luego mostraremos **cómo añadir sombra**, **aplicar desenfoque a la sombra**, e incluso **hacer la sombra transparente**. Al final tendrás un fragmento de C# listo para ejecutar que produce un archivo *.docx* con un rectángulo bien sombreado, todo en pocos minutos.

## Lo que necesitarás

- .NET 6 o posterior (la API también funciona con .NET Framework 4.6+)
- Aspose.Words for .NET (la prueba gratuita sirve para este ejemplo)
- Un editor de código – Visual Studio, VS Code, Rider, lo que prefieras
- Conocimientos básicos de C# – nada complicado, solo la capacidad de ejecutar una aplicación de consola

Si ya cuentas con eso, podemos pasar directamente a la solución.

## Paso 1 – Cómo crear documento e inicializar el lienzo

Lo primero: necesitas un objeto `Document` vacío. Piensa en él como una hoja en blanco que Aspose.Words convertirá luego en un archivo de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

¿Por qué instanciamos `Document` en lugar de cargar una plantilla? Empezar desde cero garantiza que no haya estilos o secciones ocultas que interfieran con nuestro rectángulo. También mantiene el tamaño del archivo diminuto, un buen hábito cuando generas muchos documentos en un bucle.

## Paso 2 – Crear forma de rectángulo (el núcleo de nuestra palabra clave principal)

Ahora realmente **creamos una forma de rectángulo**. La clase `Shape` es flexible; le indicas el tipo (Rectangle), el tamaño y cómo debe ajustarse al texto circundante.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Observa el uso de la sintaxis de inicializador de objetos: es concisa y reduce la probabilidad de olvidar establecer una propiedad más adelante. El rectángulo se ubicará dentro del primer párrafo, que añadiremos en el siguiente paso.

## Paso 3 – Cómo añadir sombra y personalizar su aspecto

Añadir una sombra no es solo una línea; tienes varias propiedades que ajustar. Aquí es donde entran en juego las palabras clave secundarias **aplicar desenfoque a la sombra** y **hacer la sombra transparente**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Una nota rápida sobre los números: `BlurRadius` de 5 produce un difuminado suave; aumentarlo a 10 da un aspecto más tenue, o reducirlo a 2 para un borde más definido. El valor de `Transparency` varía de 0 (opaco) a 1 (invisible). Ajústalo según los requisitos de contraste de tu marca.

### Consejo profesional

Si alguna vez necesitas una sombra coloreada (por ejemplo, un azul corporativo), simplemente reemplaza `Color.DarkGray` por `Color.FromArgb(80, 0, 120, 215)`. El primer argumento es el canal alfa – mantenlo bajo para sutileza.

## Paso 4 – Insertar la forma en el documento

Con el rectángulo y su sombra listos, ahora lo colocamos en el primer párrafo del documento. Este paso asegura que la forma aparezca en la parte superior del archivo.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

¿Por qué el primer párrafo? Es un valor predeterminado seguro que funciona incluso cuando el documento está completamente vacío. Si tienes una ubicación específica (p. ej., después de un encabezado), localizarías ese nodo e insertarías la forma allí.

## Paso 5 – Guardar el archivo y verificar el resultado

Finalmente, persistimos el documento en disco. Puedes elegir cualquier ruta que desees; solo asegúrate de que la carpeta exista.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Al abrir *ShadowRectangle.docx* en Microsoft Word, deberías ver un rectángulo de 200 × 100 puntos con una sombra gris‑oscura, ligeramente difuminada, 30 % transparente, desplazada tres puntos a la derecha y hacia abajo. El efecto es sutil pero aporta profundidad a diseños que de otro modo serían planos.

![crear forma de rectángulo con sombra en Aspose.Words](https://example.com/placeholder-image.png "crear forma de rectángulo con sombra en Aspose.Words")

*Texto alternativo de la imagen:* **crear forma de rectángulo con sombra en Aspose.Words** – la imagen muestra el documento final con el rectángulo sombreado.

## Variaciones comunes y casos límite

### Cambiar el color de la sombra dinámicamente

Si tu aplicación admite temas, podrías obtener el color de la sombra desde un archivo de configuración:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Hacer que la forma no sea en línea

A veces deseas que el rectángulo flote sobre el texto. Cambia `WrapType` a `WrapType.Square` y establece `RelativeHorizontalPosition` en `RelativeHorizontalPosition.Margin` para mayor control.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Manejo de múltiples páginas

Si necesitas un rectángulo en cada página, recorre `doc.Sections` y agrega una forma clonada al primer párrafo de cada sección. Recuerda llamar a `rect.Clone(true)` para duplicar también la configuración de la sombra.

## Recapitulación – Lo que logramos

- **Creaste una forma de rectángulo** usando Aspose.Words
- **Cómo añadir sombra** con color, desplazamiento, desenfoque y transparencia
- Demostraste **aplicar desenfoque a la sombra** y **hacer la sombra transparente**
- Guardaste un archivo de Word que puedes abrir al instante

Todo esto se logró con solo unas cuantas líneas, demostrando que los ajustes visuales sofisticados no siempre requieren bibliotecas gráficas pesadas.

## ¿Qué sigue?

- Experimenta con otros `ShapeType`s (Ellipse, Cloud, etc.) y observa cómo se comportan las sombras.
- Combina el rectángulo con cuadros de texto para crear llamadas etiquetadas.
- Profundiza en **cómo crear documento** a partir de plantillas que ya contengan marcadores de posición para formas, y luego pópualas programáticamente.

Siéntete libre de ajustar el radio de desenfoque, el color o la transparencia hasta que la sombra se vea perfecta para tu lenguaje de diseño. La API es indulgente, y los cambios son visibles al instante cuando vuelves a ejecutar la aplicación de consola.

¡Feliz codificación, y que tus documentos siempre tengan ese toque extra de profundidad!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}