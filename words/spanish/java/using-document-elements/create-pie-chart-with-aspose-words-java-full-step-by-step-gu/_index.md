---
category: general
date: 2026-07-16
description: Crear un gráfico circular en Java usando Aspose.Words. Aprende a agregar
  líneas guía, mostrar la leyenda del gráfico y separar una porción en un solo tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: es
lastmod: 2026-07-16
og_description: Crea un gráfico circular en Java usando Aspose.Words. Esta guía muestra
  cómo agregar líneas guía, mostrar la leyenda del gráfico y separar una porción,
  brindándote una visualización pulida en minutos.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Crear gráfico de pastel con Aspose.Words Java – Tutorial completo de formato
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Crear gráfico de pastel con Aspose.Words Java – Guía completa paso a paso
url: /es/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear gráfico circular con Aspose.Words Java – Guía completa paso a paso

¿Alguna vez te has preguntado cómo **crear un gráfico circular** programáticamente en Java sin luchar contra APIs de dibujo de bajo nivel? No eres el único. Muchos desarrolladores necesitan una visual rápida para informes, paneles o documentos automatizados, y recurren a Aspose.Words porque se encarga del trabajo pesado.  

En este tutorial recorreremos un ejemplo completo, listo para ejecutar, que no solo **crea un gráfico circular**, sino que también te muestra cómo **añadir líneas guía**, **mostrar la leyenda del gráfico** y hasta **explotar una porción** para resaltarla. Al final tendrás un archivo `.docx` que luce lo suficientemente pulido como para impresionar a un cliente.

> **Resultado rápido:** El fragmento de código a continuación funciona tal cual con Aspose.Words for Java 23.9 (o cualquier versión posterior). Sin dependencias extra, solo el JAR.

## Lo que aprenderás

- Configurar un documento Word en blanco con `DocumentBuilder`.
- Insertar un **gráfico circular** de tamaño personalizado.
- Usar la función **explode slice** para resaltar un punto de datos.
- Habilitar **líneas guía** para que la porción explotada permanezca conectada a la etiqueta.
- Activar la **leyenda del gráfico** para que los lectores identifiquen instantáneamente cada porción.
- Guardar el resultado en un archivo `.docx` que puedes abrir en Microsoft Word o LibreOffice.

**Requisitos previos** – Necesitarás:

1. Java 17 (o posterior) instalado.
2. Aspose.Words for Java JAR en tu classpath.
3. Un IDE básico o editor de texto—IntelliJ IDEA, Eclipse, VS Code, lo que prefieras.

Ahora, vamos al detalle.

## Paso 1: Inicializar el Documento y el Builder – Preparando para **crear gráfico circular**

Primero, necesitamos un lienzo de documento limpio. `Document` representa todo el archivo Word, mientras que `DocumentBuilder` es el asistente que nos permite añadir contenido.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Por qué es importante:** Comenzar con un `Document` nuevo garantiza que no haya estilos ocultos u objetos residuales que puedan interferir con la renderización del gráfico.

## Paso 2: Insertar el **gráfico circular** – El tamaño importa

Aspose.Words hace que la inserción de un gráfico sea una sola línea. Aquí solicitamos un gráfico circular de 400 × 300 puntos—aproximadamente 5.5 × 4.2 pulgadas en una pantalla típica.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Consejo profesional:** Si necesitas un tamaño diferente, simplemente cambia los dos argumentos numéricos. La API trabaja en puntos, donde 72 puntos = 1 pulgada.

## Paso 3: **Cómo explotar una porción** – Resaltando un punto de datos clave

Explotar una porción la saca del resto del círculo, atrayendo la mirada del lector. El método `setExplosion` recibe un entero que representa la distancia en puntos.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **¿Qué pasa si tienes varias series?** Puedes llamar a `setExplosion` en cualquier índice de serie (`get(1)`, `get(2)`, …) para explotar diferentes porciones.

## Paso 4: **Añadir líneas guía** y **mostrar la leyenda del gráfico** – Conectando los puntos

Cuando una porción está explotada, la etiqueta puede alejarse. Las líneas guía mantienen la etiqueta atada, preservando la legibilidad. Al mismo tiempo, una leyenda ofrece una clave rápida para todas las porciones.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **¿Por qué habilitar líneas guía?** Sin ellas, la etiqueta podría aparecer flotando, confundiendo a los usuarios sobre a qué porción pertenece.  
> **¿Necesitas una posición de leyenda personalizada?** Usa `chart.getLegend().setPosition(LegendPosition.TOP)` o cualquier otro valor del enum.

## Paso 5: Guardar el Documento – El paso final de **crear gráfico circular**

Finalmente, persistimos el documento en disco. Ajusta la ruta a una carpeta donde tengas permiso de escritura.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Ejecuta el programa, abre el `PieChartDemo.docx` generado, y deberías ver un gráfico circular bien formateado con la primera porción explotada, líneas guía y una leyenda visible.

![Ejemplo de gráfico circular que muestra una porción explotada y la leyenda](pie-chart-example.png){: .center-image alt="Ejemplo de creación de gráfico circular con porción explotada, líneas guía y leyenda"}

### Resultado esperado

Al abrir el archivo Word, el gráfico se verá aproximadamente así:

- Un gráfico circular de 400 × 300 pt.
- La primera porción está desplazada 10 pt.
- Una línea guía delgada conecta la porción explotada con su etiqueta.
- Una leyenda bajo el gráfico enumera cada nombre de serie.

Si no ves la línea guía, verifica que `setLeaderLines(true)` se haya llamado *después* de la configuración de explosión—el orden importa.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparece la leyenda** | Se omitió `setShowLegend(true)` o se llamó sobre el objeto de gráfico incorrecto. | Asegúrate de llamar `chart.setShowLegend(true)` **después** de obtener el `Chart` desde la forma. |
| **Falta la línea guía** | La porción no se explotó, o el tipo de gráfico no soporta líneas guía. | Solo `ChartType.PIE` (o `PIE_3D`) soporta líneas guía. Llama primero a `setExplosion`, luego a `setLeaderLines(true)`. |
| **La porción no se mueve** | Valor de explosión demasiado bajo (0‑2 pt). | Incrementa el entero, por ejemplo `setExplosion(10)` o un valor mayor para un efecto más dramático. |
| **El gráfico se ve distorsionado** | Usar un tamaño no cuadrado (ancho ≠ alto) puede aplastar el círculo. | Mantén ancho y alto iguales o cercanos; 400 × 300 funciona pero 400 × 400 da un círculo perfecto. |

## Ajustes avanzados (Opcional)

Si deseas ir más allá de lo básico, considera:

- **Colores personalizados**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Etiquetas de datos**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Efecto 3‑D**: Reemplaza `ChartType.PIE` por `ChartType.PIE_3D`.

Estas opciones te permiten afinar el aspecto visual para que coincida con las directrices de la marca corporativa.

## Recapitulación – Lo que logramos

Comenzamos con un documento Word en blanco, **creamos un gráfico circular**, **explotamos la primera porción**, **añadimos líneas guía** y **mostramos la leyenda del gráfico**. Todo el flujo cabe en un método `main` conciso, lo que facilita su integración en pipelines de generación de informes más grandes.

## Próximos pasos

- **Añadir más series**: Poblar el gráfico con datos reales provenientes de una base de datos o CSV.
- **Exportar a PDF**: Usa `doc.save("output.pdf", SaveFormat.PDF);` para generar una versión PDF.
- **Combinar con otras formas**: Inserta tablas, imágenes u otros gráficos para un informe completo.

Si te interesa explorar otros tipos de gráficos—columna, barra, línea—simplemente reemplaza `ChartType.PIE` por el enum correspondiente y sigue los mismos pasos de formato.

---

*¡Feliz creación de gráficos!* No dudes en dejar un comentario si algo no funcionó como esperabas, o comparte cómo personalizaste la posición de la leyenda. Tu feedback nos ayuda a todos a crear mejores documentos automatizados.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}