---
category: general
date: 2026-04-21
description: Crear documento de Word con un rectángulo con estilo y sombra. Aprende
  cómo agregar sombra, insertar una forma de rectángulo, establecer el color de la
  sombra y más en C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: es
og_description: Crea un documento de Word y agrega una forma de rectángulo con sombra
  en C#. Sigue esta guía para establecer fácilmente el color de la sombra, el desenfoque
  y los desplazamientos.
og_title: Crear documento de Word con rectángulo sombreado – Paso a paso
tags:
- Aspose.Words
- C#
- Document Automation
title: Crear documento de Word con rectángulo sombreado – Guía completa
url: /es/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word con rectángulo sombreado – Guía completa

¿Alguna vez necesitaste **crear documento de Word** que se vea un poco más pulido que una página de texto simple? Tal vez estés creando una plantilla de informe o un folleto y un rectángulo sencillo con una sombra sutil sea la solución. En este tutorial recorreremos exactamente eso: cómo insertar una forma de rectángulo, activar la sombra y personalizar su color, difuminado y desplazamientos, todo con C# y Aspose.Words.

También cubriremos **cómo agregar sombra** de una manera que funcione tanto si apuntas a Word 2016, 2019 o la última versión de Office 365. Al final tendrás un archivo *.docx* listo para guardar que muestra un rectángulo con sombra bien sombreada, y comprenderás el “por qué” detrás de cada propiedad que configuras.

## Requisitos previos

- .NET 6 (o cualquier versión reciente de .NET Framework)  
- Paquete NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)  
- Familiaridad básica con la sintaxis de C#  
- Un IDE como Visual Studio (pero cualquier editor sirve)

No se requieren bibliotecas adicionales; todo lo demás reside dentro de Aspose.Words.

## Paso 1 – Inicializar el Document y el Builder (Crear documento de Word)

Para **crear documento de Word** programáticamente comienzas con la clase `Document`. El `DocumentBuilder` es tu pincel; te permite agregar texto, formas y otros elementos.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*¿Por qué es importante?* El objeto `Document` representa todo el archivo .docx. Sin él no tienes dónde adjuntar el rectángulo o su sombra.

## Paso 2 – Insertar una forma de rectángulo (Insertar forma de rectángulo)

Ahora realmente **insertamos forma de rectángulo**. El método `InsertShape` recibe un enum `ShapeType`, además del ancho y alto en puntos.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Consejo profesional:* 1 punto ≈ 1/72 pulgada, por lo que 200 pts son aproximadamente 2.78 pulgadas de ancho. Ajusta estos números para que se adapten a tu diseño.

## Paso 3 – Activar la sombra (Cómo agregar sombra)

Las sombras están desactivadas por defecto. Cambia la bandera `Visible` para activarla.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*¿Qué está pasando?* Cuando `Visible` es true, Word renderizará una sombra paralela basada en las demás propiedades que configures a continuación.

## Paso 4 – Personalizar la apariencia de la sombra (Establecer color de sombra, difuminado, desplazamientos)

Aquí es donde **estableces el color de la sombra**, el radio de difuminado y los desplazamientos X/Y. Siéntete libre de experimentar: diferentes valores te darán un resplandor suave, una sombra profunda o incluso un efecto “flotante”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*¿Por qué estos números?* Un difuminado de 5 pts brinda un borde suave y difuso, mientras que un desplazamiento de 4 pts mueve la sombra hacia abajo‑derecha, imitando una fuente de luz desde la esquina superior‑izquierda. Cambia `Color` a `Color.Black` para un contraste más fuerte, o usa `Color.FromArgb(128, 0, 0, 0)` para un negro semitransparente.

### Casos límite y variaciones

- **Sin difuminado:** Establece `Blur = 0` para una sombra nítida y de bordes duros.  
- **Desplazamientos negativos:** Usa `OffsetX = -4` para mover la sombra a la izquierda.  
- **Formas diferentes:** Las mismas propiedades de sombra funcionan para círculos, triángulos o incluso formas dibujadas a mano—simplemente cambia `ShapeType` en el Paso 2.  
- **Compatibilidad:** Aspose.Words escribe los datos de sombra en formato Office Open XML, que funciona en Word 2010‑2021 y Office 365.

## Paso 5 – Guardar el documento (Crear documento de Word)

Finalmente, persiste el archivo en disco. Puedes elegir cualquier formato compatible (`.docx`, `.pdf`, `.odt`, …) pero para esta guía nos quedaremos con el formato clásico de Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Cuando abras **ShadowRectangle.docx** en Microsoft Word verás un rectángulo gris con una sombra sutil y difuminada desplazada hacia la esquina inferior‑derecha—exactamente lo que programamos.

### Resultado esperado

- Un archivo *.docx* de una sola página.  
- Un rectángulo de 200 pt × 100 pt centrado donde estaba el cursor cuando se llamó a `InsertShape`.  
- Una sombra gris que aparece 4 pts a la derecha y 4 pts abajo, con un difuminado de 5 pts.

Si la forma parece descentrada, puedes mover el cursor con `builder.MoveTo` antes de insertar, o ajustar las propiedades `Left` y `Top` de la forma después de la inserción.

## Preguntas frecuentes y solución de problemas

**Q: La sombra no aparece en Word.**  
A: Asegúrate de que `ShadowFormat.Visible` sea `true`. También verifica que estés usando una versión reciente de Aspose.Words (la función de sombra se añadió en la versión 20.3).  

**Q: ¿Puedo aplicar un degradado a la sombra?**  
A: No directamente a través de `ShadowFormat`. La interfaz de Word admite sombras degradadas, pero el esquema Open XML (que sigue Aspose.Words) solo expone sombras de color sólido. Tendrías que editar el XML subyacente manualmente, lo cual es un escenario más avanzado.  

**Q: ¿Qué pasa si necesito un rectángulo transparente con solo una sombra?**  
A: Establece `rectangle.FillColor = Color.Transparent;` después de la inserción. La sombra seguirá renderizándose porque es independiente del relleno.

## Consejos profesionales para código de producción

- **Reutilizar el builder:** Si estás agregando múltiples formas, mantén la misma instancia de `DocumentBuilder`; crear una nueva para cada forma genera una sobrecarga innecesaria.  
- **Guardados por lotes:** Guarda una sola vez después de todas las modificaciones; I/O frecuente ralentiza la generación de documentos grandes.  
- **Manejo de errores:** Envuelve todo el bloque en un `try / catch` y registra las excepciones de `Aspose.Words`; a menudo contienen números de línea útiles si la plantilla del documento está corrupta.

## Próximos pasos (Temas relacionados)

- **Cómo agregar sombra** a imágenes o cuadros de texto (uso similar de `ShadowFormat`).  
- **Insertar forma de rectángulo** dentro de una celda de tabla para estilo de celda personalizado.  
- **Crear rectángulo en Word** usando el XML nativo de Word (para quienes prefieren Open XML sin procesar).  
- **Establecer color de sombra** dinámicamente según la entrada del usuario o los colores del tema.

Experimenta con diferentes colores, radios de difuminado y desplazamientos—quizá un resplandor azul suave para un informe corporativo, o una sombra negra profunda para un folleto dramático. Las posibilidades son infinitas, y los cambios de código son mínimos.

---

### Resumen rápido

- **Creamos un documento de Word** desde cero.  
- **Insertamos una forma de rectángulo** y activamos su sombra.  
- **Establecimos el color de la sombra**, el difuminado y los desplazamientos para lograr un aspecto profesional.  
- Guardamos el archivo, listo para su distribución.

Ahora tienes una base sólida para añadir estilo visual a cualquier proyecto de automatización de Word. ¿Tienes más ideas? Deja un comentario y sigamos la conversación. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}