---
category: general
date: 2026-11-15
description: Aprenda cómo insertar una forma en un documento de Word y agrupar varias
  formas con Aspose.Words DocumentBuilder. Incluye ejemplos de inserción de forma
  rectangular e inserción de múltiples formas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: es
lastmod: 2026-11-15
og_description: Cómo insertar una forma en un archivo de Word usando Aspose.Words.
  Esta guía cubre la agrupación de múltiples formas, la inserción de una forma rectangular
  y la adición de múltiples formas de manera eficiente.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Cómo insertar una forma y agrupar varias formas con DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Cómo insertar una forma y agrupar varias formas usando DocumentBuilder en C#
url: /es/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo insertar una forma y agrupar varias formas usando DocumentBuilder en C#

Si necesitas saber **cómo insertar una forma** en un documento Word con Aspose.Words, esta guía te muestra los pasos exactos. También aprenderás cómo **agrupar varias formas** para que se comporten como un solo objeto, y cómo **insertar una forma rectangular** junto a otros gráficos.

La automatización de documentos a menudo requiere agregar varios gráficos —gráficos, logotipos, llamadas— manteniéndolos organizados. Al final de este tutorial podrás **insertar múltiples formas**, colocarlas dentro de un grupo y guardar un diseño limpio y reutilizable.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior instalado  
* Visual Studio 2022 (o cualquier IDE de C#)  
* Una licencia de Aspose.Words for .NET o una clave de evaluación gratuita  
* Familiaridad básica con C# y la clase `DocumentBuilder` de Aspose.Words  

No necesitas ninguna otra biblioteca de terceros; todo lo necesario forma parte de Aspose.Words.

## Paso 1: Instalar Aspose.Words vía NuGet

Abre tu proyecto en Visual Studio y ejecuta el siguiente comando en la consola del Administrador de paquetes:

```powershell
Install-Package Aspose.Words
```

El paquete incluye las clases `DocumentBuilder`, `Shape` y `GroupShape` que se usan a lo largo de este tutorial.

## Paso 2: Crear una instancia de DocumentBuilder – la base para **cómo insertar forma**

La primera línea de código ejecutable es crear un `DocumentBuilder`. Este objeto te brinda acceso directo al árbol del documento, permitiéndote colocar formas exactamente donde lo desees.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Por qué es importante*: `DocumentBuilder` mantiene un cursor (el “punto de inserción”). Cada llamada posterior a `Insert...` usa ese cursor, por lo que más adelante lo movemos dentro de un `GroupShape` para mantener todas las formas juntas.

## Paso 3: **Insertar forma rectangular** – el primer gráfico que agregarás

Un rectángulo es un marcador de posición común para tablas, imágenes o llamadas. Usa `InsertShape` con `ShapeType.Rectangle` y especifica el ancho y la altura en puntos (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

El rectángulo aparece en la ubicación actual del cursor. Puedes personalizar su relleno, estilo de línea o texto más adelante si lo necesitas.

## Paso 4: Insertar otra forma – una elipse para variar visualmente

Agregar más de una forma demuestra **insertar múltiples formas**. La elipse se situará después del rectángulo en el flujo del documento.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

En este punto el documento contiene dos formas independientes. Si mueves el cursor o añades texto, las formas permanecen donde fueron insertadas.

## Paso 5: **Agrupar varias formas** para que actúen como una sola unidad

Agrupar es esencial cuando necesitas mover, rotar o formatear varios gráficos juntos. El siguiente código crea un `GroupShape`, mueve el cursor del builder dentro de él y luego inserta nuevamente las mismas formas —esta vez se convierten en hijos del grupo.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### ¿Por qué usar un grupo?

* **Transformación de un solo punto** – rota o cambia el tamaño de todo el grupo con una sola llamada.  
* **Organización lógica** – el árbol del documento Word refleja el agrupamiento, facilitando ediciones posteriores.  
* **Diseño consistente** – mover el grupo mantiene intactas las posiciones relativas de sus hijos.

### Añadiendo más formas – ampliando **insertar múltiples formas** dentro del grupo

Puedes seguir llamando a `InsertShape` mientras el cursor permanece dentro del `GroupShape`. Por ejemplo, para agregar un triángulo:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Cada llamada respeta el contexto del grupo, por lo que el triángulo se convierte automáticamente en parte del mismo conjunto agrupado.

## Paso 6: Guardar el documento y verificar el resultado

Después de colocar todas las formas, persiste el documento en un archivo `.docx`. Al abrir el archivo en Microsoft Word (o cualquier visor compatible) deberías ver dos formas separadas seguidas de un conjunto agrupado que contiene el mismo rectángulo, elipse y triángulo.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Resultado esperado

* **Primeras dos formas** – un rectángulo y una elipse colocados de forma independiente en la página.  
* **Bloque agrupado** – un rectángulo, una elipse y un triángulo que se mueven juntos al hacer clic en cualquiera de ellos en Word.

Puedes probar el agrupamiento seleccionando cualquier forma dentro del grupo; Word resaltará toda la colección, confirmando que la operación **agrupar varias formas** se realizó con éxito.

## Problemas comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| Las formas aparecen fuera de la página prevista | El cursor del builder no se movió dentro del `GroupShape` antes de insertar. | Siempre llama a `builder.MoveTo(group)` **antes** de cualquier llamada a `InsertShape` que pertenezca al grupo. |
| El grupo desaparece después de guardar | El grupo se insertó sin añadirse a la colección de nodos del documento. | Usa `builder.InsertNode(group)` inmediatamente después de crear el `GroupShape`. |
| Tamaño inesperado por la DPI del documento | Aspose.Words usa puntos; si piensas en píxeles puedes obtener dimensiones desajustadas. | Convierte píxeles a puntos (`points = pixels * 72 / 96`) o trabaja directamente en puntos. |
| Las formas se superponen sin querer | No se estableció una posición explícita; Word las coloca secuencialmente. | Define `Shape.Left` y `Shape.Top` después de la inserción para controlar la ubicación exacta. |

**Consejo profesional:** Después de agrupar, puedes obtener la colección `Shapes` del grupo (`group.Shapes`) para iterar, renombrar o aplicar formato masivo.

## Paso 7: Extender el ejemplo – ¿qué sigue?

Ahora que sabes **cómo insertar forma**, **insertar forma rectangular** y **agrupar varias formas**, puedes explorar:

* **Animar formas agrupadas** – establecer propiedades de rotación o volteo en el grupo.  
* **Aplicar estilos** – usar `Shape.FillColor`, `Shape.LineFormat` o `Shape.TextBox` para añadir etiquetas.  
* **Exportar a PDF** – el mismo diseño agrupado se renderiza correctamente al llamar a `doc.Save("output.pdf")`.  

Todas estas extensiones reutilizan el mismo flujo de trabajo con `DocumentBuilder`, manteniendo tu código limpio y mantenible.

## Conclusión

Este tutorial demostró **cómo insertar una forma** en un documento Word con Aspose.Words, cómo **insertar una forma rectangular** y cómo **agrupar varias formas** para que se comporten como un solo objeto. Siguiendo el código paso a paso, puedes insertar de forma fiable **múltiples formas**, organizarlas en grupos y producir documentos de calidad profesional de manera programática.

Siéntete libre de experimentar con diferentes tipos de forma, colores y transformaciones de grupo. Cuando estés listo, integra este patrón en soluciones de generación de informes o plantillas más amplias para automatizar diseños de documentos complejos. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}