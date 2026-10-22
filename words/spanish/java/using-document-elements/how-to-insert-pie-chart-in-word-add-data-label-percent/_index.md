---
category: general
date: 2026-07-20
description: Cómo insertar un gráfico circular en Word con Aspose.Words. Aprende a
  agregar el porcentaje de la etiqueta de datos y mostrar los porcentajes en el gráfico
  para documentos profesionales.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: es
lastmod: 2026-07-20
og_description: cómo insertar un gráfico circular en Word usando Aspose.Words. Esta
  guía muestra cómo agregar el porcentaje de la etiqueta de datos y mostrar los porcentajes
  en el gráfico en solo unas pocas líneas.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: cómo insertar un gráfico de pastel en Word – guía rápida
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: cómo insertar un gráfico de pastel en Word – agregar porcentaje a la etiqueta
  de datos
url: /es/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo insertar un gráfico circular en Word – agregar etiqueta de datos de porcentaje

¿Alguna vez te has preguntado **cómo insertar un gráfico circular** en un documento de Word sin luchar con la interfaz? No estás solo. En muchos escenarios de informes necesitas *agregar un gráfico circular a Word* y, lo que es más importante, **mostrar el porcentaje en el gráfico circular** para que los lectores comprendan instantáneamente la distribución de los datos.

En este tutorial recorreremos todo el proceso usando Aspose.Words for Java. Al final sabrás exactamente cómo **agregar etiqueta de datos de porcentaje**, **mostrar porcentajes en el gráfico**, y obtener un gráfico circular pulido que se vea correcto a la primera. Sin complementos extra, sin ajustes manuales—solo código limpio que puedes insertar en cualquier proyecto.

---

## Requisitos previos

- Java 17 (o posterior) – la versión LTS actual que Aspose.Words soporta.
- Aspose.Words for Java 24.x (la más reciente al momento de escribir, julio 2026).
- Una configuración básica de Maven o Gradle para obtener la biblioteca.
- Un IDE que prefieras (IntelliJ IDEA, Eclipse, VS Code… cualquiera sirve).

Si ya tienes esto, genial—¡vamos a sumergirnos!

---

## Paso 1: Configurar el proyecto e importar la biblioteca

Primero, agrega la dependencia de Aspose.Words a tu `pom.xml` (Maven) o `build.gradle` (Gradle). Esto te da acceso a las clases `Document`, `DocumentBuilder` y de gráficos.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Consejo profesional:** Mantén el número de versión actualizado; las versiones más recientes a menudo añaden correcciones relacionadas con gráficos que hacen que **mostrar porcentajes en el gráfico** sea más fiable.

---

## Paso 2: Crear un nuevo documento Word y un builder

El builder es tu navaja suiza para insertar contenido. Aquí creamos un documento nuevo y le adjuntamos un `DocumentBuilder`.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

¿por qué necesitamos un builder? Abstracta las estructuras OpenXML de bajo nivel, permitiéndonos centrarnos en *qué* queremos—como **agregar un gráfico circular a Word**—en lugar de *cómo* se ve el XML.

---

## Paso 3: Insertar el gráfico circular

Ahora llega el núcleo de **cómo insertar un gráfico circular**. Le pedimos al builder que coloque un gráfico circular de un tamaño específico. Las dimensiones están en puntos (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

En este punto el gráfico está vacío, pero el marcador ya está en el documento. Acabas de **agregar un gráfico circular a Word** programáticamente.

---

## Paso 4: Poblar el gráfico con datos

Un gráfico circular necesita al menos una serie de valores. Alimentémoslo con algunos datos de ejemplo que representan la cuota de mercado.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Si alguna vez necesitas múltiples series (gráficos circulares apilados, donuts, etc.) puedes llamar a `pieChart.getSeries().add()` y repetir los pasos. La misma lógica se aplica cuando deseas **mostrar porcentajes en el gráfico** para cada porción.

---

## Paso 5: **agregar etiqueta de datos de porcentaje** – mostrar los porcentajes en las porciones

Esta es la parte que la mayoría de los desarrolladores olvida: configurar las etiquetas de datos para mostrar porcentajes. Sin ello, el gráfico solo muestra números sin formato, lo que puede ser ambiguo.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

La llamada `setShowPercent(true)` indica a Aspose.Words que renderice la etiqueta como “30 %”, “45 %”, etc. Eso es exactamente cómo **mostrar el porcentaje en el gráfico circular** sin trabajo de formato adicional.

---

## Paso 6: Guardar el documento

Finalmente, escribe el documento en disco. Puedes elegir `.docx`, `.pdf` o incluso `.html`. Para esta guía nos quedaremos con el formato moderno `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Ejecuta el programa, abre `PieChartDemo.docx`, y verás un gráfico circular renderizado ordenadamente con etiquetas de porcentaje en cada porción.

---

## Resultado esperado

A continuación hay una captura de pantalla del archivo Word generado. Observa cómo cada porción muestra su participación como porcentaje—exactamente lo que queríamos al establecer **agregar etiqueta de datos de porcentaje**.

![Captura de pantalla de un documento Word que contiene un gráfico circular con etiquetas de porcentaje](/images/pie-chart-percent.png){.center width=600px alt="Captura de pantalla que muestra cómo insertar un gráfico circular en Word con etiquetas de porcentaje"}

*El texto alternativo incluye la palabra clave principal, cumpliendo tanto con SEO como con accesibilidad.*

---

## Preguntas frecuentes y manejo de casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Puedo cambiar la fuente de las etiquetas de porcentaje?** | Sí. Después de habilitar `setShowPercent(true)`, recupera el objeto `DataLabel` y ajusta su propiedad `Font` (`dataLabel.getFont().setSize(10);`). |
| **¿Qué pasa si necesito un gráfico de donut en lugar de un circular?** | Reemplaza `ChartType.PIE` por `ChartType.DOUGHNUT` en la llamada `insertChart`. La misma lógica de **agregar etiqueta de datos de porcentaje** funciona. |
| **¿Las versiones antiguas de Word (2007‑2010) muestran los porcentajes correctamente?** | Aspose.Words escribe el XML subyacente de forma independiente de la versión, por lo que los porcentajes aparecen en cualquier Word que soporte gráficos (2007+). |
| **¿Cómo agregar un título al gráfico?** | Usa `pieChart.getTitle().setText("Market Share");` antes de guardar. |
| **¿Puedo insertar el gráfico en un párrafo o celda de tabla específicos?** | Absolutamente. Mueve el `DocumentBuilder` a la ubicación deseada (`builder.moveToParagraph(index, true);` o `builder.moveToCell(table, row, column, true);`) antes de llamar a `insertChart`. |

---

## Consejos y trucos del campo

- **Consejo profesional:** Si planeas generar muchos gráficos en un bucle, reutiliza una única instancia de `DocumentBuilder`; reduce el consumo de memoria.
- **Cuidado con:** Porciones muy pequeñas (< 2 %). Aspose.Words puede omitir la etiqueta para evitar desorden; puedes forzarla con `dataLabel.setShowLabel(true);`.
- **Nota de rendimiento:** Renderizar gráficos es intensivo en CPU. Para generación masiva de informes, considera multihilo pero asegúrate de que cada hilo trabaje con su propia instancia de `Document`.
- **Verificación de versión:** El método `setShowPercent` se introdujo en Aspose.Words 22.8. Si usas una versión anterior, actualiza o calcula manualmente los porcentajes y establécelos como etiquetas personalizadas.

---

## Recapitulación

Hemos cubierto **cómo insertar un gráfico circular** en un documento Word usando Aspose.Words, te hemos mostrado cómo **agregar etiqueta de datos de porcentaje**, y demostrado la forma más sencilla de **mostrar porcentajes en el gráfico**. Con solo unas pocas líneas de Java puedes **agregar un gráfico circular a Word** y **mostrar el porcentaje en el gráfico circular**, convirtiendo números crudos en visuales instantáneamente legibles.

---

## ¿Qué sigue?

- Experimenta con otros tipos de gráficos (`BAR`, `LINE`, `AREA`) y observa cómo se aplica la misma lógica de **agregar etiqueta de datos de porcentaje**.
- Combina gráficos con tablas para informes más ricos—Aspose.Words lo hace trivial colocar un gráfico junto a una tabla de datos.
- Explora exportar el mismo documento a PDF o HTML para ver cómo se renderizan los porcentajes en los distintos formatos.
- Siéntete libre de ajustar las dimensiones, colores o fuente de datos (p. ej., una consulta a base de datos) y observa cómo tus informes Word cobran vida. Si encuentras algún problema, deja un comentario abajo—¡feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar gráfico de columnas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insertar gráfico de áreas en documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insertar un gráfico de burbujas en Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}