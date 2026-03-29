---
category: general
date: 2026-03-28
description: Cómo establecer sombra en una forma en C# con Aspose.Words – agregar
  sombra a la forma, aplicar sombra y personalizar la apariencia.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: es
og_description: Cómo establecer sombra en una forma en C# rápidamente. Aprende a agregar
  sombra a la forma, aplicar sombra y ajustar el desenfoque, la distancia y el ángulo.
og_title: Cómo aplicar sombra a una forma en C# – Guía completa
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: Cómo aplicar sombra a una forma en C# – Guía paso a paso
url: /es/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer sombra en una forma en C# – Guía completa de programación

¿Alguna vez te has preguntado **cómo establecer sombra** en una forma cuando estás creando documentos Word de forma programática? No eres el único. En muchos informes, presentaciones o folletos, una sombra sutil puede hacer que un gráfico destaque sin parecer de mala calidad. ¿La buena noticia? Con Aspose.Words for .NET puedes añadir sombra a una forma con solo unas pocas líneas de código.

En este tutorial recorreremos todo el proceso: cargar un DOCX, obtener la primera forma y luego **aplicar sombra a la forma** — incluyendo color, desenfoque, distancia y ángulo. Al final tendrás un fragmento listo para ejecutar que podrás insertar en cualquier proyecto C#. Sin bibliotecas adicionales, sin magia oculta.

## Lo que necesitarás

- **Aspose.Words for .NET** (versión 23.9 o posterior) – la biblioteca que hace que la manipulación de Word sea sencilla.  
- Un entorno de desarrollo .NET (Visual Studio 2022, Rider o la CLI).  
- Un DOCX de ejemplo que ya contenga al menos una forma (un rectángulo, imagen o SmartArt sirve).  

Si te falta alguno de estos, obtén el paquete NuGet con `Install-Package Aspose.Words` y crea un archivo Word sencillo con una forma insertada manualmente—solo para la demostración.

## Paso 1: Cargar el documento (preparar para añadir sombra)

Lo primero es abrir el archivo fuente. Aquí es donde comienza la operación de **añadir sombra a la forma**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **Por qué es importante:** Cargar el documento te proporciona un objeto `Document` que posee todos los nodos, incluidas las formas. Sin él, no hay nada que modificar.

## Paso 2: Recuperar la forma objetivo (elige la correcta)

A continuación localizamos la forma que queremos estilizar. En este ejemplo obtenemos la primera forma del primer párrafo, pero puedes adaptar la consulta a cualquier colección de nodos.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **Consejo profesional:** `GetChildNodes(NodeType.Shape, true)` recorre el subárbol de forma recursiva, asegurando que no te pierdas formas anidadas como WordArt.

## Paso 3: Acceder al objeto de formato de sombra (donde vive la magia)

Cada `Shape` expone una propiedad `ShadowFormat`. Este objeto controla la visibilidad, el color, el desenfoque, la distancia y el ángulo—todos los ajustes que necesitas para **aplicar sombra a la forma**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Por qué usamos `ShadowFormat`:** Abstrae la representación XML subyacente, de modo que puedes ajustar sombras sin tratar con OpenXML crudo.

## Paso 4: Hacer visible la sombra y elegir un color (añadir sombra a la forma)

Una sombra no aparecerá hasta que establezcas `Visible` en `true`. Después, puedes elegir cualquier `System.Drawing.Color`. Aquí usamos un gris medio, pero siéntete libre de experimentar.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **Error común:** Olvidar habilitar `Visible` produce fallos silenciosos—tu forma parece sin cambios aunque hayas configurado otras propiedades.

## Paso 5: Configurar la apariencia – desenfoque, distancia y ángulo (ajuste fino del aspecto)

Ahora modelamos el impacto visual. `BlurRadius` suaviza los bordes, `Distance` aleja la sombra de la forma, y `Angle` determina la dirección de la fuente de luz.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **Caso límite:** Si estableces una distancia negativa, la sombra aparecerá *dentro* de la forma, lo que puede ser útil para efectos de relieve.

## Paso 6: Guardar el documento actualizado (ver el resultado)

Finalmente, escribe los cambios de nuevo en el disco. Puedes sobrescribir el archivo original o crear uno nuevo.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

Ejecutar el programa produce `output-with-shadow.docx`. Ábrelo en Microsoft Word y notarás que la forma seleccionada ahora tiene una sombra gris suave con un ángulo de 45°, desenfocada a 5 pts y desplazada 3 pts.

![Diagrama que muestra la sombra aplicada a una forma](https://example.com/images/shadow-diagram.png "Diagrama que muestra la sombra aplicada a una forma")

*Texto alternativo: Diagrama que muestra la sombra aplicada a una forma* – esta imagen ilustra el efecto antes/después.

## Cómo añadir sombra – Variaciones comunes y casos límite

Aunque los pasos principales son sencillos, los escenarios del mundo real a menudo requieren ajustes. A continuación se presentan algunas situaciones “qué‑pasaría‑si” que podrías encontrar.

### 1. Múltiples formas, sombras diferentes

Si tu documento contiene varios gráficos, recorre la colección de formas y asigna configuraciones de sombra únicas a cada forma.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. Sombras transparentes

Aspose.Words te permite establecer un canal alfa mediante `Color.FromArgb(alpha, r, g, b)`. Usa un alfa bajo (p. ej., 50) para un efecto sutil y semitransparente.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. Eliminar una sombra

A veces necesitas desactivar una sombra después de haberla aplicado. Simplemente establece `Visible` en `false`.

```csharp
        shadow.Visible = false;
```

### 4. Problemas de compatibilidad

Las funciones de sombra usadas aquí son compatibles con Word 2007 + (el formato DOCX). Si apuntas al formato binario más antiguo `.doc`, la sombra puede ser ignorada porque el formato carece de los elementos XML necesarios. En esos casos, considera guardar como DOCX o usar una pista visual alternativa.

## Recapitulación: lo que hemos logrado

- **Cargado** un DOCX con Aspose.Words.  
- **Obtenido** la primera forma del documento.  
- **Accedido** a su objeto `ShadowFormat`.  
- **Activado** la sombra, establecido un color, radio de desenfoque, distancia y ángulo.  
- **Guardado** un nuevo archivo que muestra visiblemente el efecto.  

Todos esos pasos juntos responden a **cómo establecer sombra** en una forma, al mismo tiempo que te muestran cómo **añadir sombra a la forma**, **aplicar sombra a la forma**, e incluso **cómo añadir sombra** en escenarios más complejos.

## Próximos pasos y temas relacionados

Ahora que dominas el estilo de sombras, quizás quieras explorar:

- **Rellenos degradados** para formas (`Shape.FillFormat.GradientFill`).  
- **Efectos de texto** como resplandor o reflexión (`TextEffect`).  
- **Inserción programática de nuevas formas** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **Exportación a PDF** manteniendo las sombras (`doc.Save("output.pdf")`).  

Cada uno de esos temas se basa en los mismos principios del modelo de objetos que usamos aquí, por lo que te sentirás como en casa.

---

*¡Feliz codificación! Si encuentras algún problema, deja un comentario abajo o consulta la documentación de la API de Aspose.Words para obtener más información.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}