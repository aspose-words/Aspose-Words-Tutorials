---
category: general
date: 2026-03-06
description: Crear una forma rectangular en Word y añadir sombra a la forma con Aspose.Words.
  Aprende cómo insertar un rectángulo en Word y cómo agregar sombra a la forma en
  C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: es
og_description: Crear una forma rectangular en Word y añadir sombra a la forma con
  Aspose.Words. Guía paso a paso sobre cómo insertar un rectángulo en Word y cómo
  agregar sombra a la forma.
og_title: Crear forma rectangular con sombra en Word usando Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crear forma de rectángulo con sombra en Word usando Aspose.Words
url: /es/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular con sombra en Word usando Aspose.Words

¿Alguna vez necesitaste **create rectangle shape** en un documento de Word pero no estabas seguro de cómo darle ese aspecto pulido? No estás solo—la mayoría de los desarrolladores se topan con el mismo problema cuando intentan añadir un toque visual a los documentos automatizados. ¿La buena noticia? Con Aspose.Words para .NET puedes tanto **create rectangle shape** como **add shape shadow** en solo unas pocas líneas de C#.

En este tutorial recorreremos paso a paso **how to insert rectangle in Word**, luego mostraremos **how to add shadow to shape** para que destaque en la página. Al final tendrás un `Shadow.docx` listo‑para‑guardar que podrás abrir en Word y ver un rectángulo con tono gris y una sombra difusa. Sin archivos de imagen adicionales, sin ajustes manuales—solo código.

## Lo que aprenderás

- Las declaraciones exactas de C# necesarias para **create rectangle shape** con Aspose.Words.  
- Cómo habilitar y configurar una sombra usando el objeto `Shadow`.  
- Por qué cada propiedad es importante (p. ej., `Transparency`, `Blur`, `Angle`).  
- Problemas comunes (unidades, compatibilidad de versiones) y soluciones rápidas.  
- Un programa completo, listo para copiar y pegar, que puedes ejecutar hoy.

### Requisitos previos

- .NET 6+ (o .NET Framework 4.7+).  
- Aspose.Words para .NET 23.10 o posterior (el paquete NuGet es `Aspose.Words`).  
- Un conocimiento básico de C# y Visual Studio (o cualquier IDE que prefieras).  

Si ya los tienes, vamos directamente al grano.

---

## Paso 1: Configurar el proyecto e importar espacios de nombres

Primero, crea una nueva aplicación de consola (o reutiliza una existente) y agrega el paquete NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Ahora incluye los espacios de nombres requeridos en tu `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Consejo profesional:** Si estás apuntando a .NET 6+, puedes habilitar directivas `using` globales para evitar repetir estas líneas en cada archivo.

---

## Paso 2: **Create rectangle shape** en un documento Word en blanco

Comenzaremos con un nuevo objeto `Document` y un `DocumentBuilder` para manipularlo. El método `InsertShape` del builder es donde ocurre la magia.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

¿por qué 200 × 100 puntos? En Word, un punto equivale a 1/72 de pulgada, por lo que el rectángulo resulta aproximadamente 2.8 × 1.4 pulgadas—suficientemente grande para notarse pero no abrumador. Puedes cambiar estos números según tu diseño; solo recuerda que se miden en **points**, no en píxeles.

---

## Paso 3: **Add shape shadow** – configurando el aspecto

Ahora que tenemos un rectángulo, vamos a darle una sombra gris sutil. El objeto `Shadow` pertenece al `Shape` y expone varias propiedades útiles.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Qué hace cada propiedad

| Property | Efecto | Valores típicos |
|----------|--------|----------------|
| **Enabled** | Activa o desactiva la sombra | `true` o `false` |
| **Color** | Color base de la sombra | Cualquier `System.Drawing.Color` |
| **Transparency** | Opacidad (0 = sólido, 1 = invisible) | 0.0 – 1.0 |
| **Blur** | Suavidad del borde | 0 – 10 (más alto = más suave) |
| **Distance** | Espacio entre la forma y la sombra | 0 – 20 puntos |
| **Angle** | Dirección de la luz aparente | 0 – 360 grados |
| **Size** | Escala de la sombra respecto a la forma | 0 – 200 % |

> **¿Por qué preocuparse por estos ajustes?**  
> Ajustar finamente la sombra te permite cumplir con las directrices de la identidad corporativa (p. ej., una sutil transparencia del 20 % para un aspecto profesional) sin recurrir a editores de imágenes externos.

---

## Paso 4: Guardar el documento y verificar el resultado

Finalmente, escribe el archivo en disco. Puedes elegir cualquier carpeta que desees; solo reemplaza `YOUR_DIRECTORY` con una ruta real.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Abre `Shadow.docx` en Microsoft Word y deberías ver un rectángulo gris con una suave sombra desplazada a un ángulo de 45°. Esa pista visual hace que la forma parezca “elevada” de la página—exactamente lo que esperarías de un informe o factura pulida.

---

## Ejemplo completo en funcionamiento

A continuación se muestra el programa completo que puedes copiar‑pegar en `Program.cs`. No falta ninguna pieza; compila y se ejecuta tal cual.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Resultado esperado

- **Archivo:** `Shadow.docx` colocado en la carpeta de ejecución del proyecto.  
- **Visual:** Un único rectángulo centrado en la página, relleno con el blanco predeterminado, y una sombra gris desplazada 4 puntos hacia abajo‑derecha, ligeramente difuminada para un aspecto natural.

---

## Preguntas frecuentes y casos límite

### 1. ¿Qué pasa si necesito una unidad diferente (p. ej., centímetros)?

Aspose.Words funciona en puntos, pero puedes convertir centímetros a puntos con la fórmula simple:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. ¿Esto funciona con versiones anteriores de Aspose.Words?

El API `Shadow` se introdujo en la versión 14.0. Si estás en una versión anterior, deberás actualizar mediante NuGet. El resto del código (creación de formas) ha sido estable durante muchos años, por lo que no encontrarás cambios incompatibles.

### 3. ¿Puedo añadir una sombra a otras formas (p. ej., círculos)?

Absolutamente—cualquier objeto `Shape` expone una propiedad `Shadow`. Simplemente reemplaza `ShapeType.Rectangle` por `ShapeType.Ellipse` o `ShapeType.Cloud`, y luego aplica los mismos ajustes de sombra.

### 4. ¿Qué pasa si necesito una sombra coloreada (p. ej., azul para una marca)?

Intercambia `Color.Gray` por cualquier `Color` que desees:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Recuerda ajustar `Transparency` para que el color no se vuelva demasiado dominante.

---

## 🎨 Resumen visual

![crear forma rectangular con sombra en Word usando Aspose.Words](image-placeholder.png "crear forma rectangular con sombra en Word usando Aspose.Words")

*Texto alternativo: crear forma rectangular con sombra en Word usando Aspose.Words*

La captura de pantalla (marcador) muestra el documento final—solo el rectángulo y su suave sombra gris.

---

## Conclusión

Ahora sabes cómo **create rectangle shape** en un archivo Word, **add shape shadow**, y afinar cada aspecto visual usando Aspose.Words para .NET. El pequeño programa que construimos cubre todo el flujo de trabajo—desde

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}