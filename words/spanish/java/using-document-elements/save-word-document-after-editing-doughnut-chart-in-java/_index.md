---
category: general
date: 2026-09-11
description: Guarde el documento de Word después de editar un gráfico de rosquilla
  con Aspose.Words para Java. Aprenda cómo cambiar el tamaño del agujero de la rosquilla,
  rotar el gráfico de rosquilla y editar las propiedades del gráfico de rosquilla.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: es
lastmod: 2026-09-11
og_description: Guarde el documento Word después de editar un gráfico de rosquilla
  usando Aspose.Words para Java. Este tutorial muestra cómo cambiar el tamaño del
  agujero de la rosquilla, rotar el gráfico de rosquilla y personalizar la apariencia
  del gráfico.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Guardar documento de Word después de editar el gráfico de rosquilla – Guía
  de Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Guardar documento de Word después de editar el gráfico de rosquilla en Java
url: /es/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Guardar documento Word después de editar un gráfico de rosquilla en Java

Si necesitas **guardar documento Word** que contiene un gráfico de rosquilla personalizado, esta guía te muestra exactamente cómo hacerlo. En solo unas pocas líneas de Java puedes cambiar el agujero de la rosquilla, rotar el gráfico y luego escribir el resultado en disco.

Verás un ejemplo completo y ejecutable que usa Aspose.Words para Java, además de consejos para manejar varios gráficos, verificar tipos de nodos y evitar errores comunes. No se requieren referencias externas; todo lo que necesitas está incluido.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java 17 o superior instalado
- Maven o Gradle para gestionar dependencias
- Aspose.Words para Java (versión 23.9 o posterior) añadido a tu proyecto  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Un archivo Word (`input.docx`) que contenga un único gráfico de rosquilla

## Paso 1: Cargar el documento Word

El primer paso es abrir el archivo fuente. Este paso es esencial porque cada operación posterior trabaja sobre el objeto `Document` en memoria.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **¿Por qué?** Cargar el documento crea una representación DOM que permite recorrer formas, tablas y gráficos. Si el archivo no puede abrirse, Aspose.Words lanza una excepción, de modo que sabes inmediatamente que la ruta es incorrecta.

## Paso 2: Ubicar la forma del gráfico de rosquilla

Un gráfico se almacena dentro de un nodo `Shape`. Recuperamos la primera forma que contiene un gráfico y convertimos su renderizador a `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **¿Por qué?** Comprobar `isChart()` evita una `ClassCastException` cuando el documento contiene imágenes u otras formas antes del gráfico. Esto hace que el código sea robusto para documentos con contenido mixto.

## Paso 3: Cambiar el tamaño del agujero de la rosquilla  

Ahora editamos el agujero de la rosquilla. El método `setHoleSize` espera un porcentaje del radio del gráfico (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **¿Por qué?** Cambiar el agujero de la rosquilla (`change doughnut hole` / `change chart hole size`) permite enfatizar o des‑enfatizar el área central. Los valores fuera del rango 10‑90 % son ignorados por la API.

## Paso 4: Rotar el gráfico de rosquilla  

Para controlar dónde comienza la primera porción, establece el ángulo de la primera porción. Esto efectivamente **rota el gráfico de rosquilla**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **¿Por qué?** Rotar el gráfico es útil cuando deseas que una porción específica aparezca en la parte superior o para cumplir con una especificación de diseño.

## Paso 5: Guardar el documento actualizado  

Finalmente, escribe los cambios en un nuevo archivo. Este es el momento en que **guardas documento Word** con el gráfico editado.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Resultado esperado:** `output.docx` contiene el contenido original, pero el gráfico de rosquilla ahora tiene un agujero del 30 % y su primera porción comienza a los 45 °. Al abrir el archivo en Microsoft Word se mostrará el gráfico transformado.

## Ejemplo completo y funcional

A continuación tienes el programa completo que puedes copiar y pegar en tu IDE. Incluye todas las importaciones y el manejo de errores necesario para **editar gráfico de rosquilla** y **guardar documento Word** de forma segura.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Salida esperada

Al abrir `output.docx`:

- El agujero central del gráfico de rosquilla ocupa aproximadamente un tercio del radio del gráfico.  
- La primera porción comienza en la posición de 45 grados, desplazando todo el gráfico en sentido horario.  

Ambos cambios visuales se reflejan instantáneamente en Word.

## Variaciones comunes y casos límite

| Situación | Cómo manejarlo |
|-----------|----------------|
| **Múltiples gráficos** | Itera a través de `doc.getChildNodes(NodeType.SHAPE, true)` y filtra `shape.isChart()`; aplica `setHoleSize` / `setFirstSliceAngle` a cada `Chart`. |
| **El gráfico no es una rosquilla** | Verifica `chart.getType()`; solo llama a `setHoleSize` cuando `chart.getType() == ChartType.DOUGHNUT`. |
| **Necesitas cambiar el tamaño del agujero dinámicamente** | Calcula el porcentaje deseado en función de los valores de datos y luego llama a `setHoleSize(computedValue)`. |
| **Guardar en un stream** | Usa |

## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Save Word with Password using Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}