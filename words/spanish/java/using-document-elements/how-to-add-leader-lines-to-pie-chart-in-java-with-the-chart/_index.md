---
category: general
date: 2026-08-20
description: Añade líneas de guía al gráfico de pastel en Java rápidamente. Aprende
  a insertar, separar, recolorear y etiquetar las porciones usando la API de Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: es
lastmod: 2026-08-20
og_description: Añade líneas guía al gráfico de pastel en Java con un ejemplo conciso.
  Sigue esta guía para insertar, separar, recolorear y etiquetar las porciones usando
  la API de Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Añadir líneas de guía al gráfico circular en Java – guía paso a paso de
  la API de gráficos
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Cómo agregar líneas guía a un gráfico de pastel en Java con la API de gráficos
url: /es/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar líneas guía a un gráfico circular en Java con la API de Chart

Si necesitas **agregar líneas guía a un gráfico circular** en Java, esta guía te lleva paso a paso por todo el proceso. Verás cómo insertar un gráfico circular, explotar una porción para resaltarla, cambiar su color y, finalmente, habilitar líneas guía que etiqueten la porción explotada.

El ejemplo utiliza la API de Chart estándar que se encuentra en muchas bibliotecas de generación de informes Java. No se requieren herramientas externas y el código se ejecuta en cualquier entorno JDK 8+.

## Lo que lograrás

Al final de este tutorial podrás:

* Crear un `Chart` de tipo `ChartType.PIE` con un tamaño personalizado.  
* Explotar la primera porción para llamar la atención.  
* Establecer el color del sector de la porción explotada a azul.  
* **Agregar líneas guía al gráfico circular** para que la etiqueta de la porción esté claramente conectada.

Ya deberías tener un proyecto Java con la biblioteca Chart en el classpath. Si usas Maven, agrega la dependencia mostrada en la sección de requisitos previos.

## Requisitos previos

* JDK 8 o superior instalado.  
* La biblioteca Chart (p.ej., `com.example.chart:chart-api:2.5.0`).  
* Familiaridad básica con clases Java y llamadas a métodos.

---

## Cómo agregar líneas guía al gráfico circular

A continuación tienes un programa completo y ejecutable que muestra cada paso. El código está deliberadamente autocontenido para que puedas copiar, pegar y ejecutarlo sin modificaciones.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Explicación de cada paso

| Paso | Qué hace el código | Por qué es importante |
|------|-------------------|-----------------------|
| **1️⃣ Insertar un gráfico circular** | `builder.insertChart(ChartType.PIE, 400, 300)` crea un gráfico circular de 400 × 300 píxeles. | Establece el contenedor del gráfico y define sus dimensiones, lo que afecta la ubicación de las etiquetas y la longitud de las líneas guía. |
| **2️⃣ Explotar la primera porción** | `setExplosion(20)` desplaza la porción un 20 % del radio. | Una porción explotada atrae la atención del observador y hace visible la línea guía. |
| **3️⃣ Establecer color del sector** | `setSectorColor(Color.BLUE)` cambia el relleno de la porción a azul. | El contraste de color mejora la legibilidad, especialmente cuando la porción está resaltada. |
| **4️⃣ Habilitar líneas guía** | `setLeaderLines(true)` activa las líneas de conexión que enlazan la porción con su etiqueta. | Las líneas guía garantizan que la etiqueta siga siendo legible incluso cuando la porción se desplaza hacia afuera. |

La llamada `saveAsPng` es opcional pero útil para verificar el resultado visual. Después de ejecutar el programa, deberías ver una imagen similar a la que se muestra a continuación.

![Agregar líneas guía al gráfico circular](https://example.com/assets/pie-leader-lines.png "Agregar líneas guía al gráfico circular – porción explotada con color azul y líneas guía")

*Figura: Un gráfico circular donde la primera porción está explotada, coloreada en azul y conectada a su etiqueta mediante una línea guía.*

## Personalizando líneas guía (avanzado)

La llamada básica `setLeaderLines(true)` usa el estilo predeterminado de la biblioteca. Puedes controlar aún más la apariencia:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Estas opciones son útiles cuando necesitas adaptar la marca corporativa o mejorar la accesibilidad.

### Manejo de múltiples series

Si tu gráfico circular contiene más de una serie, podrías querer líneas guía solo para una porción específica. Usa el índice de la serie para apuntar al elemento correcto:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Cuando una porción no está explotada, la línea guía suele ocultarse automáticamente, pero puedes forzarla con `setLeaderLineEnabled(true)`.

## Problemas comunes y cómo evitarlos

| Problema | Síntoma | Solución |
|----------|---------|----------|
| **Líneas guía no visibles** | El gráfico se renderiza sin conectores. | Asegúrese de que la porción esté explotada (`setExplosion` > 0) o habilite explícitamente las líneas guía en la porción. |
| **Superposición de etiquetas** | Las etiquetas colisionan entre sí. | Aumente el tamaño del gráfico o establezca `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Color no aplicado** | La porción mantiene el color predeterminado. | Verifique que está apuntando al índice de serie correcto (`getSeries().get(0)`). |
| **Imagen no guardada** | `saveAsPng` lanza una excepción. | Verifique los permisos de escritura del directorio de salida y que la biblioteca soporte la exportación a PNG. |

## Listado completo del código fuente

Para mayor comodidad, aquí tienes de nuevo el archivo fuente completo, incluyendo importaciones y comentarios:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Ejecutar este programa genera `pie-with-leader-lines.png`, que muestra un gráfico circular con una porción azul explotada y líneas guía claras que apuntan a la etiqueta de la porción.

## Conclusión

Ahora sabes cómo **agregar líneas guía a un gráfico circular** en Java usando la API de Chart. El proceso consiste en insertar un `ChartType.PIE`, explotar la porción deseada, personalizar su color y habilitar líneas guía. Con las opciones de estilo opcionales puedes afinar el color de la línea, el grosor y la ubicación de la etiqueta para cumplir cualquier requisito visual.

A continuación, considera explorar temas relacionados como **explosión de gráfico circular Java**, **set sector color Chart API** y **uso de builder.insertChart** para crear visualizaciones más sofisticadas como gráficos de dona, gráficos circulares apilados o paneles interactivos.

¡Siéntete libre de experimentar con diferentes índices de porción, colores y estilos de línea guía—tus gráficos serán más informativos y visualmente atractivos con cada ajuste. Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Agregar valores de fecha y hora al eje de un gráfico](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}