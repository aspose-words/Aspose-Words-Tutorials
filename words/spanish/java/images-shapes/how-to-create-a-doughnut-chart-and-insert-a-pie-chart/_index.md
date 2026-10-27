---
category: general
date: 2026-10-26
description: Crea un gráfico de dona e inserta un gráfico de pastel en Java con código
  paso a paso. Aprende el flujo de trabajo completo para visualizaciones de gráficos
  flexibles.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: es
lastmod: 2026-10-26
og_description: Crea un gráfico de dona en Java con esta guía que también muestra
  cómo insertar un gráfico de pastel para visualizaciones flexibles.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Crear gráfico de dona e insertar gráfico de pastel – Guía de Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Cómo crear un gráfico de rosquilla e insertar un gráfico circular
url: /es/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un doughnut chart e insertar un pie chart

Si necesitas **create doughnut chart** en Java, este tutorial te guiará paso a paso. También mostraremos cómo **insert pie chart** usando la misma builder API, para que puedas cambiar entre estilos visuales sin esfuerzo. Al final de la guía tendrás un programa completo y ejecutable que produce ambos tipos de gráficos y demuestra personalizaciones comunes.

El tutorial cubre:

* Inicializar el chart builder proporcionado por la biblioteca elegida.  
* Crear un doughnut chart y configurar el tamaño del agujero.  
* Insertar un pie chart y explotar una porción para enfatizarla.  
* Consejos para manejar casos límite como series faltantes o tipos de gráfico no compatibles.

Solo necesitas un JDK reciente (8 o superior) y el JAR de la biblioteca de gráficos en tu classpath. No se requieren servicios externos.

---

## Prerequisitos

| Elemento | Razón |
|------|--------|
| Java Development Kit (JDK) 8+ | Necesario para compilar y ejecutar el ejemplo. |
| Biblioteca de gráficos (p. ej., **Aspose.Cells for Java** o **JFreeChart**) | Proporciona `ChartBuilder`, `ChartType` y los métodos de manipulación de series usados en el código. |
| Un IDE o un editor de texto | Para escribir y ejecutar el archivo fuente Java. |

Asegúrate de que el JAR de la biblioteca esté añadido a la ruta de compilación de tu proyecto. Si usas Maven, agrega la dependencia correspondiente; de lo contrario, coloca el JAR en la carpeta `libs` y haz referencia a él durante la compilación.

---

## Paso 1: Configurar el chart builder

El primer paso es crear una instancia de `ChartBuilder` (o equivalente) que generará los objetos de gráfico. Este objeto actúa como una fábrica y contiene la hoja de cálculo o el lienzo donde se colocará el gráfico.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Por qué esto es importante:**  
El builder vincula el gráfico a una hoja de cálculo específica, asegurando que todos los objetos de gráfico posteriores compartan la misma superficie de dibujo. Omitir este paso dejaría sin una ubicación objetivo para los elementos visuales.

---

## Paso 2: **Create doughnut chart**

Ahora generamos un doughnut chart con un tamaño definido. El tamaño del agujero determina cuánto del centro del gráfico está vacío, convirtiendo un pastel regular en un doughnut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explicación:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` crea el objeto de gráfico y reserva espacio en la hoja de cálculo.  
* `setHoleSize(30)` convierte el pastel en un doughnut con un 30 % de centro vacío.  
* `add("{10, 20, 30, 40}", true)` suministra cuatro puntos de datos; el indicador `true` indica a la biblioteca que trate los valores como una sola serie.

**Caso límite:** Si el tipo de gráfico seleccionado no admite un agujero (p. ej., un gráfico de barras), llamar a `getDoughnutChart()` lanza una excepción. Siempre verifica el tipo de gráfico antes de ajustar el tamaño del agujero.

---

## Paso 3: **Insert pie chart**

Después de que el doughnut esté listo, demostramos cómo **insert pie chart** usando el mismo builder. Este paso destaca la similitud entre los dos tipos de gráfico y muestra cómo enfatizar una porción.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explicación:**  

* `ChartType.PIE` indica al builder que cree un clásico pie chart.  
* `setExplode(10)` desplaza la primera porción un 10 % del radio, una técnica común para resaltar un punto de datos clave.  

**Consejo:** El método `setExplode` funciona solo en la primera serie de un pie chart. Si tienes varias series, debes apuntar al índice correcto.

---

## Paso 4: Guardar el workbook

Finalmente, escribe el workbook a un archivo para que puedas ver los gráficos en Excel o cualquier visor compatible.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Por qué guardar ahora:** Persistir el workbook finaliza todas las operaciones de dibujo. Intentar visualizar el archivo antes de guardarlo resulta en un documento vacío o incompleto.

**Resultado:** Al abrir *DoughnutAndPieChart.xlsx* se muestra un doughnut chart con un 30 % de agujero a la izquierda y un pie chart con la primera porción explotada a la derecha.

---

## Paso 5: Variaciones comunes y solución de problemas

| Situación | Ajuste |
|-----------|------------|
| **Dimensiones de gráfico diferentes** | Cambia los argumentos de ancho y alto en `insertChart`. |
| **Múltiples series de datos** | Llama a `add` varias veces o pasa una cadena de matriz 2‑D. |
| **Tamaño de agujero dinámico** | Calcula el tamaño del agujero basado en el rango de datos y luego llama a `setHoleSize`. |
| **Explotar varias porciones** | Recorre `chart.getSeries().get(i).setExplode(percent)` para cada porción que desees desplazar. |
| **Biblioteca que no soporta doughnut** | Usa un pie chart y dibuja manualmente un círculo blanco superpuesto, aunque es menos preciso. |

**Consejo profesional:** Siempre llama a `builder.flush()` (si está disponible) después de insertar gráficos cuando trabajes con workbooks grandes. Esto libera buffers internos y previene fugas de memoria.

---

![Código Java que crea un doughnut chart e inserta un pie chart](https://example.com/images/doughnut-pie-java.png "crear doughnut chart ejemplo en Java")

*La imagen ilustra el diseño final del workbook con ambos gráficos lado a lado.*

---

## Conclusión

Ahora sabes cómo **create doughnut chart** y **insert pie chart** en Java usando una API builder fluida. El ejemplo completo cubre la inicialización, configuración de tamaño, ajuste del agujero, explosión de porciones y salida a archivo. Desde aquí puedes explorar personalizaciones adicionales como colores, leyendas y etiquetas de datos para adaptarlas a tus requisitos de informes.

**Próximos pasos**

* Experimenta con características de **chart customization Java** como rellenos degradados y etiquetas de datos.  
* Integra la generación de gráficos en un servicio web que devuelva el workbook bajo demanda.  
* Compara el enfoque builder con otras bibliotecas (p. ej., JFreeChart) para elegir la que mejor se adapte a tu proyecto.

¡Feliz creación de gráficos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un doughnut chart en un documento Word con Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Guardar documento Word después de editar doughnut chart en Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Insertar Pie Chart en Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}