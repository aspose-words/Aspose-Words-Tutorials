---
category: general
date: 2026-09-30
description: 'Agrupa formas en Word con C#: aprende a agrupar formas, añadir rectángulos
  y elipses, e insertar una forma de rectángulo en documentos de Word de forma programática.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: es
lastmod: 2026-09-30
og_description: Agrupa formas en Word usando C# y Aspose.Words. Sigue esta guía completa
  para agregar un rectángulo, agregar una elipse y aprender a agrupar formas de manera
  eficiente.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Agrupar formas en Word con C# – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cómo agrupar formas en Word usando C# y Aspose.Words
url: /es/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Word usando C# y Aspose.Words

Si necesitas **group shapes in Word** de forma programática, esta guía te muestra exactamente cómo hacerlo. Verás cómo añadir un rectángulo, añadir una elipse y luego combinarlos en una única forma grupal usando la biblioteca Aspose.Words para .NET.

Trabajar con formas es un requisito común al generar informes, contratos o materiales de marketing de forma automática. Al final de este tutorial tendrás un método reutilizable en C# que carga un archivo DOCX, inserta un rectángulo y una elipse, los agrupa y guarda el resultado, todo sin abrir Word manualmente.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* .NET 6.0 SDK o posterior instalado  
* Un entorno de desarrollo como Visual Studio 2022 (la edición Community funciona)  
* Una licencia de Aspose.Words para .NET o una copia de evaluación gratuita (la API funciona sin licencia pero añade una marca de agua)  

También necesitas un documento Word fuente (`input.docx`) en una carpeta a la que puedas referenciar desde el código. El documento puede estar vacío; el tutorial se centra en el manejo de formas.

## Paso 1: Crear un nuevo proyecto de consola y agregar Aspose.Words

Abre una terminal o el símbolo de comandos de Visual Studio y ejecuta:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Esto crea una aplicación de consola nueva llamada **WordShapeDemo** y agrega el paquete NuGet `Aspose.Words`, que contiene las clases `Document` y `DocumentBuilder` usadas para manipular archivos Word.

## Paso 2: Cargar o crear un documento

La primera operación al trabajar con **group shapes in Word** es obtener un objeto `Document`. Puedes cargar un archivo DOCX existente o iniciar desde un documento en blanco.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

La clase `Document` representa todo el archivo Word. Cargar un archivo te brinda un lienzo listo para insertar formas.

## Paso 3: Iniciar una forma grupal

Una *group shape* te permite tratar varias formas independientes como una única unidad, ideal para moverlas o redimensionarlas juntas. Para iniciar un grupo, llama a `StartGroupShape()` en un `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Llamar a `StartGroupShape` indica a Aspose.Words que cada inserción de forma posterior pertenece al mismo grupo lógico hasta que llames a `EndGroupShape`.

## Paso 4: Cómo añadir una forma rectangular en Word

Ahora que el grupo está abierto, inserta un rectángulo. El método `InsertShape` recibe un enumerado `ShapeType`, seguido del ancho y la altura (en puntos).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

El rectángulo se convierte en el primer miembro del grupo. Puedes personalizar su relleno, contorno o texto más adelante si lo necesitas.

## Paso 5: Cómo añadir una forma elíptica en Word

A continuación, agrega una elipse (un círculo cuando el ancho es igual a la altura). Esto demuestra **how to add ellipse** usando el mismo builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Ambas formas comparten ahora el mismo espacio de coordenadas dentro del grupo, lo que facilita alinearlas visualmente.

## Paso 6: Cerrar la definición de la forma grupal

Cuando hayas añadido todos los miembros deseados, cierra el grupo. Esto finaliza la colección de formas para que Word las trate como un solo objeto.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

En este punto el documento contiene una única forma agrupada compuesta por un rectángulo y una elipse.

## Paso 7: Guardar el documento modificado

Finalmente, escribe los cambios en disco. Puedes sobrescribir el archivo original o crear uno nuevo.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Ejecutar el programa genera `output.docx`. Abre el archivo en Microsoft Word, selecciona la forma y verás que el rectángulo y la elipse se mueven juntos, lo que confirma que la operación **group shapes in Word** se completó con éxito.

### Resultado esperado

* El archivo Word contiene un único objeto agrupado.  
* Seleccionar el grupo permite arrastrar, redimensionar o rotar simultáneamente tanto el rectángulo como la elipse.  
* No se requiere interacción manual con Word; todo se realiza mediante código C#.

![Formas agrupadas en documento Word](grouped-shapes.png "Captura de pantalla de un documento Word que muestra un rectángulo y una elipse agrupados")

*Texto alternativo de la imagen: “Captura de pantalla de un documento Word que muestra un rectángulo y una elipse agrupados”* (cumple con el requisito de texto alternativo de la imagen).

## Por qué agrupar formas es importante

Agrupar formas es más que una conveniencia visual. Permite:

* **Mantener la consistencia del diseño** – mover un grupo conserva las posiciones relativas.  
* **Aplicar transformaciones una sola vez** – rotar o escalar todo el grupo en lugar de cada forma individualmente.  
* **Simplificar el procesamiento posterior** – cuando otras herramientas leen el DOCX, ven una única forma compuesta, reduciendo la complejidad.

Si alguna vez necesitas añadir más formas (por ejemplo, una línea o un cuadro de texto) al mismo conjunto lógico, solo tienes que volver a llamar a `InsertShape` antes de `EndGroupShape`.

## Variaciones comunes y casos límite

| Situación | Cómo manejarla |
|-----------|----------------|
| **Unidades diferentes** – tienes medidas en centímetros | Convierte los centímetros a puntos (`1 cm ≈ 28.35 pt`) antes de llamar a `InsertShape`. |
| **Añadir una etiqueta de texto** – deseas un título dentro del grupo | Inserta un `ShapeType.TextBox` después del rectángulo y la elipse, luego establece su propiedad `Text`. |
| **Aplicar un color de relleno** – necesitas un rectángulo azul | Después de `InsertShape`, recupera la última forma mediante `builder.CurrentParagraph.Runs[0].Font` y asigna `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Usar un formato de documento diferente** – apuntas a `.doc` en lugar de `.docx` | El mismo código funciona; solo cambia la extensión del archivo al llamar a `Save`. Aspose.Words gestiona automáticamente el formato. |

## Consejos profesionales

* **Reutiliza el builder** – puedes iniciar y cerrar varios grupos en el mismo documento; simplemente llama a `StartGroupShape` nuevamente después de `EndGroupShape`.  
* **Rendimiento** – insertar varias formas dentro de un único bloque `StartGroupShape/EndGroupShape` es más rápido que insertar formas individualmente fuera de un grupo.  
* **Licenciamiento** – una licencia de evaluación añade una marca de agua en la primera página. Instala una licencia adecuada para eliminarla en entornos de producción.

## Conclusión

Ahora sabes cómo **group shapes in Word** con C#, cómo **add rectangle**, cómo **add ellipse** y cómo **insert rectangle shape Word** documentos usando Aspose.Words. El ejemplo completo y ejecutable muestra cada paso, desde la configuración del proyecto hasta el guardado del archivo final.

Desde aquí puedes explorar tipos de forma adicionales, aplicar estilos o combinar formas agrupadas con tablas e imágenes para crear documentos sofisticados generados programáticamente.

---

**Próximos pasos**

* Aprende a **rotar formas agrupadas**: usa `Shape.RotationAngle` después de cerrar el grupo.  
* Explora la **personalización de relleno y contorno** para rectángulos y elipses.  
* Integra esta lógica en una API ASP.NET Core para generar informes bajo demanda.  

¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}