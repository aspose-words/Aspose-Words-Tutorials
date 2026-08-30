---
category: general
date: 2026-04-28
description: Cómo establecer sombra en una forma rápidamente. Aprende cómo agregar
  sombra a la forma, establecer el color de la sombra y personalizar la sombra de
  la forma con Aspose.Words para .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: es
og_description: Cómo establecer sombra en una forma en C# con Aspose.Words. Guía paso
  a paso que cubre agregar sombra a la forma, establecer el color de la sombra y personalizar
  la sombra de la forma.
og_title: Cómo aplicar sombra a una forma en C# – Guía completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Cómo aplicar sombra a una forma en C# – Añade sombra a la forma fácilmente
url: /es/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer sombra en una forma en C# – Añade sombra a la forma fácilmente

¿Alguna vez te has preguntado **cómo establecer sombra** en una forma sin tener que bucear en interminables documentos de API? No estás solo. Muchos desarrolladores se topan con un muro cuando necesitan una sombra sutil para que un diagrama destaque, pero no encuentran un ejemplo claro que muestre *qué* hacer y *por qué*.

En este tutorial recorreremos el proceso de añadir sombra a una forma, cambiar el color de la sombra y afinar su difuminado, desplazamiento y transparencia, todo usando Aspose.Words para .NET. Al final tendrás un fragmento listo para ejecutar que podrás insertar en cualquier proyecto C#, además de varios consejos para personalizar la sombra de la forma en escenarios más complejos.

> **Nota:** El código funciona con Aspose.Words 22.9 o posterior y requiere .NET 6+ (o .NET Framework 4.7.2+).  

![Forma con sombra personalizada](shape-shadow.png "Forma con sombra personalizada")

## Qué aprenderás

- **Añadir sombra a la forma** programáticamente a la primera forma de un documento Word.  
- **Establecer el color de la sombra** a cualquier `System.Drawing.Color`.  
- **Personalizar la sombra de la forma** ajustando el radio de difuminado, los desplazamientos y la transparencia.  
- Cómo manejar múltiples formas y restablecer la configuración de sombra si es necesario.  

Sin herramientas externas, sin macros de Visual Basic—solo C# puro.

---

## Requisitos previos

| Requisito | Por qué es importante |
|-------------|----------------|
| **Aspose.Words para .NET** (paquete NuGet `Aspose.Words`) | Proporciona las clases `Document`, `Shape` y `ShadowFormat` usadas en el ejemplo. |
| **SDK de .NET 6** (o .NET Framework 4.7.2) | Garantiza compatibilidad con la última superficie de API. |
| **Un archivo .docx** con al menos una forma (p. ej., un rectángulo o una imagen) | El tutorial manipula la *primera* forma; puedes crear una en Word si no tienes una. |

Instala la biblioteca con:

```bash
dotnet add package Aspose.Words
```

---

## Paso a paso: Cómo establecer sombra en una forma

### 1. Cargar el documento Word

Comenzamos abriendo el archivo `.docx`. El constructor `Document` lee el archivo en memoria, dándonos acceso total a sus nodos.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **¿Por qué?** Cargar el documento es la base—sin ello no puedes recorrer el árbol de formas.

### 2. Obtener la primera forma (o cualquier forma que necesites)

Aspose.Words almacena las formas como nodos de tipo `NodeType.SHAPE`. El método `GetChild` nos permite obtener la forma *n‑ésima*; aquí tomamos el índice 0, es decir, la primera forma.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Consejo profesional:** Si necesitas **añadir sombra a la forma** en una forma específica, reemplaza el índice por el valor adecuado o itera a través de `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. Acceder al objeto de formato de sombra

Cada `Shape` tiene una propiedad `ShadowFormat` que expone todas las configuraciones relacionadas con la sombra.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

Ahora podemos comenzar a ajustar la sombra.

### 4. Establecer el radio de difuminado – suavizando los bordes

Un radio de difuminado mayor hace que la sombra se vea más difusa. El valor está en puntos (1 pt ≈ 1/72 pulgada).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **¿Cuándo ajustarlo?** Si tu forma es pequeña, un difuminado de 2–3 pt puede ser suficiente; para banners grandes, aumenta a 8–10 pt.

### 5. Definir los desplazamientos horizontal y vertical

Los desplazamientos controlan qué tan lejos se desplaza la sombra de la forma. Valores positivos mueven la sombra a la derecha/abajo; valores negativos la mueven a la izquierda/arriba.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. Ajustar la transparencia (opacidad)

`Transparency` varía de `0.0` (totalmente opaco) a `1.0` (completamente invisible). Un valor alrededor de `0.3` brinda un aspecto sutil y semitransparente.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. Elegir un color de sombra – **establecer color de sombra** a cualquier `System.Drawing.Color`

Puedes escoger cualquier color predefinido o crear uno personalizado con valores RGB.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

Si prefieres una sombra negra clásica, simplemente usa `Color.Black`.

### 8. Guardar el documento modificado

Finalmente, persiste los cambios. Puedes sobrescribir el archivo original o escribir en una nueva ubicación.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## Ejemplo completo (Todos los pasos en un solo bloque)

Copia y pega lo siguiente en el método `Main` de una aplicación de consola. Compila tal cual, siempre que el paquete NuGet esté instalado.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Resultado esperado:** Abre `output_with_shadow.docx` en Word; la primera forma ahora muestra una sombra azul suave, desplazada 3 pt, con un difuminado sutil y un 30 % de transparencia.

---

## Variaciones comunes y casos límite

### Añadir sombras a *todas* las formas

Si tu documento contiene varios diagramas, quizá quieras recorrer cada forma:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### Restablecer una sombra

A veces una forma ya tiene una sombra que necesitas eliminar. Establece `ShadowFormat.Visible` a `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### Usar un color personalizado con alfa (semitransparente)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### Nota de compatibilidad

La API `ShadowFormat` es estable en todas las versiones de Aspose.Words, pero versiones anteriores (< 19.1) utilizaban campos de `ShadowFormat` con convenciones de nombres ligeramente diferentes. Siempre apunta al paquete NuGet más reciente para obtener los mejores resultados.

---

## Consejos profesionales para una sombra pulida

- **Equilibra difuminado y desplazamiento:** Un difuminado intenso con un desplazamiento pequeño puede parecer “luminoso” en lugar de una sombra real. Experimenta con `BlurRadius` × `DistanceX/Y`.
- **Alinea con el tema del documento:** Si el archivo Word usa un tema oscuro, una sombra clara (`Color.White`) puede crear un sutil efecto de elevación.
- **Rendimiento:** Cambiar sombras en cientos de formas puede añadir unos pocos milisegundos por forma. Agrupa la operación si procesas informes grandes.
- **Pruebas:** Abre el `.docx` resultante tanto en Word de escritorio como en Word Online para asegurar que la sombra se renderiza de forma consistente.

---

## Conclusión

Acabamos de cubrir **cómo establecer sombra** en una forma usando C#. Siguiendo los ocho pasos anteriores puedes **añadir sombra a la forma**, **establecer el color de la sombra** y **personalizar completamente la sombra de la forma** para que coincida con cualquier lenguaje de diseño. El ejemplo es autónomo, funciona de inmediato y te brinda una base sólida para extender la lógica a múltiples formas, colores dinámicos o incluso parámetros definidos por el usuario.

¿Listo para el próximo desafío? Prueba combinar esta técnica con **rotación de forma**, o genera un informe completo donde cada gráfico reciba su propia sombra de marca. Las posibilidades son infinitas, y el código que acabas de aprender es una plataforma perfecta.

Si encontraste útil esta guía, siéntete libre de darle una estrella al repositorio, dejar un comentario o compartir tus propios trucos de ajuste de sombras abajo. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}