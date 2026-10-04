---
category: general
date: 2026-10-04
description: Aprende cómo separar una porción en un gráfico de Word, separar una porción
  de un gráfico circular y cambiar el tamaño de un gráfico de rosquilla con un ejemplo
  de Java paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: es
lastmod: 2026-10-04
og_description: Cómo separar una porción en un gráfico de Word y personalizar gráficos
  de pastel o de rosquilla con Java. Sigue el ejemplo completo para modificar el gráfico
  en Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Cómo separar una porción en un gráfico de Word – guía completa de Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Cómo separar una porción en un gráfico de Word y personalizar su apariencia
url: /es/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo explotar una porción en un gráfico de Word y personalizar su apariencia

Si necesitas **cómo explotar una porción** en un gráfico de Word, esta guía te muestra exactamente cómo hacerlo. Ya sea que estés preparando una presentación de ventas o un informe financiero, explotar una porción de un gráfico circular o ajustar el agujero de un gráfico de rosquilla puede hacer que los datos más importantes destaquen. En las siguientes secciones también aprenderás a **modificar gráficos en Word**, **explotar una porción de gráfico circular**, **cambiar el tamaño del agujero de la rosquilla** y **personalizar documentos de Word con gráficos** usando Aspose.Words for Java.

Terminarás este tutorial con un programa Java completo, listo para ejecutar, que carga un archivo `.docx`, explota la primera porción de un gráfico circular, cambia el tamaño del agujero de la rosquilla y guarda el resultado. No se requieren scripts externos ni edición manual.

## Prerrequisitos

- Java 17 o posterior instalado en tu máquina de desarrollo.  
- Maven 3.6+ (o Gradle) para gestionar dependencias.  
- Biblioteca Aspose.Words for Java (la prueba gratuita funciona para desarrollo).  
- Un documento Word (`input.docx`) que contenga al menos un gráfico (circular o rosquilla).

## Paso 1: Añadir Aspose.Words a tu proyecto

Si usas Maven, agrega la siguiente dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Para Gradle, coloca esto en `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Consejo profesional:** Mantén tu versión de la biblioteca actualizada; las versiones más recientes añaden soporte para tipos de gráficos adicionales y mejoran el rendimiento.

## Paso 2: Cargar el documento Word que contiene un gráfico

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Por qué es importante:** Cargar el documento crea una representación en memoria que Aspose.Words puede recorrer. Sin este objeto no puedes acceder a los nodos del gráfico.

## Paso 3: Recuperar el primer gráfico del documento

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explicación:** `NodeType.SHAPE` cubre todos los objetos de dibujo, incluidos los gráficos. El argumento `true` indica a Aspose que busque recursivamente, asegurando que se encuentre el primer gráfico aunque esté anidado dentro de una tabla.

## Paso 4: Explotar la primera porción de un gráfico circular

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Cómo funciona:** El método `setExplosion` recibe un valor numérico que determina qué tan lejos se desplaza la porción del centro. Un valor de `20` es visualmente perceptible sin romper el diseño del gráfico.

## Paso 5: Ajustar el tamaño del agujero de la rosquilla para un gráfico de rosquilla

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Por qué ayuda:** Un agujero de rosquilla más grande puede mejorar la legibilidad cuando tienes muchos puntos de datos. El método `setDoughnutHoleSize` espera un porcentaje (0‑100).

## Paso 6: Guardar el documento modificado

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Resultado esperado

- La primera porción del primer gráfico circular se desplaza hacia afuera, haciéndola sobresalir.  
- Si el gráfico es una rosquilla, el agujero central se expande al 40 % del radio del gráfico.  
- El archivo resultante `PieChart.docx` puede abrirse en Microsoft Word, LibreOffice o cualquier visor compatible, mostrando los cambios visuales que aplicaste programáticamente.

## Ejemplo completo y ejecutable

A continuación tienes todo el programa en un solo bloque. Cópialo en `ChartExploder.java`, ajusta las rutas de archivo y ejecútalo con `mvn compile exec:java` (o la configuración de ejecución de tu IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Ejecutar este código **modificará gráficos en Word**, **explotará una porción de gráfico circular** y **cambiará el tamaño de la rosquilla** automáticamente.

## Preguntas frecuentes y casos especiales

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si el documento contiene varios gráficos?* | El ejemplo apunta al **primer** gráfico (`NodeType.SHAPE, 0`). Para trabajar con otros gráficos, cambia el índice o itera a través de `doc.getChildNodes(NodeType.SHAPE, true)` y filtra por `shape.getChart() != null`. |
| *¿Puedo explotar una porción que no sea la primera?* | Sí. Accede a la serie deseada mediante `chart.getSeries().get(seriesIndex)` y llama a `setExplosion(value)`. Los índices comienzan en cero. |
| *¿Funciona con archivos Word 2007‑2021?* | Aspose.Words soporta `.doc`, `.docx`, `.dot` y `.dotx`. El mismo código funciona en todas las versiones porque la biblioteca abstrae el formato del archivo. |
| *¿Qué ocurre si el gráfico es de barras o de líneas?* | `setExplosion` y `setDoughnutHoleSize` solo se aplican a gráficos de tipo circular. El código omite esas operaciones de forma segura cuando el tipo de gráfico es diferente. |
| *¿Necesito una licencia para Aspose.Words?* | Una licencia de evaluación gratuita elimina el límite de 30 días pero añade una marca de agua. Para producción, adquiere una licencia para quitar la marca de agua y desbloquear la funcionalidad completa. |

## Conclusión

Ahora sabes **cómo explotar una porción** en un gráfico de Word, cómo **modificar gráficos en Word** y cómo **cambiar el tamaño de la rosquilla** usando Aspose.Words for Java. El ejemplo completo muestra el flujo completo—desde cargar un documento, localizar el gráfico, aplicar ajustes visuales, hasta guardar el resultado—para que puedas integrar estos pasos en cualquier canal de generación de informes o documentos.

**Próximos pasos**

- Explora otras personalizaciones de gráficos, como cambiar colores, añadir etiquetas de datos o cambiar el tipo de gráfico (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Combina esta lógica con Aspose.PDF para generar una versión PDF del mismo informe.  
- Automatiza el proceso para un lote de documentos recorriendo los archivos en un directorio.

¡Siéntete libre de experimentar con diferentes valores de explosión o porcentajes de agujero de rosquilla para que coincidan con tus guías de diseño! Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}