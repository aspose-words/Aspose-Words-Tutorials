---
category: general
date: 2026-10-10
description: Aprende cómo rotar un gráfico en un archivo de Word y modificar el gráfico
  en Word para cambiar el tamaño del gráfico de rosquilla con un ejemplo completo
  en Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: es
lastmod: 2026-10-10
og_description: Cómo rotar un gráfico en un archivo de Word y modificar el gráfico
  en Word para cambiar el tamaño del gráfico de rosquilla usando Aspose.Words para
  Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Cómo rotar un gráfico en un documento de Word – guía paso a paso de Java
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cómo rotar un gráfico en un documento de Word usando Aspose.Words
url: /es/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo rotar un gráfico en un documento Word usando Aspose.Words

Si necesitas **cómo rotar un gráfico** dentro de un archivo Microsoft Word, esta guía te muestra los pasos exactos. También aprenderás cómo **modificar gráfico en Word** para **cambiar el tamaño del gráfico de dona** sin salir de tu código Java.

La automatización de Word a menudo se siente como una serie de llamadas API desconectadas, pero con Aspose.Words puedes tratar un gráfico como cualquier otro nodo del documento. Al final de este tutorial tendrás un programa ejecutable que carga un `.docx` existente, rota un gráfico de dona 45°, reduce el agujero al 50 % del radio y guarda el resultado como un nuevo archivo.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.
* Maven (o Gradle) para gestionar dependencias.
* Un documento Word de entrada (`input.docx`) que ya contenga un gráfico de dona.
* Una licencia válida de Aspose.Words for Java (o usar el modo de evaluación).

## Paso 1: Configurar el proyecto Maven

Crea un nuevo proyecto Maven o agrega la siguiente dependencia a tu `pom.xml` existente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Ejecutar `mvn clean install` descargará la biblioteca y pondrá las clases a disposición en tu classpath.

## Paso 2: Cargar el documento Word que contiene un gráfico

La primera operación es abrir el documento existente. La clase `Document` representa todo el archivo.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Cargar el archivo **no** lo modifica; simplemente crea una representación en memoria que puedes consultar y editar.

## Paso 3: Crear un DocumentBuilder para la navegación

`DocumentBuilder` te brinda una API tipo cursor para recorrer el árbol del documento. Lo usaremos para localizar la primera forma de gráfico.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

El builder comienza al inicio del documento, pero puedes moverlo a cualquier nodo más adelante si lo necesitas.

## Paso 4: Recuperar la primera forma de gráfico

Los gráficos se almacenan como nodos `Shape`. Filtrando los nodos hijos de tipo `NodeType.SHAPE` podemos extraer el objeto gráfico.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Si el documento contiene varios gráficos, puedes iterar sobre `getChildNodes` y comprobar cada `Shape` con `hasChart()` antes de hacer el casting.

## Paso 5: Rotar el gráfico (cómo rotar gráfico)

Un gráfico de dona es esencialmente un gráfico de pastel con un agujero. Rotarlo cambia el ángulo de inicio de la primera porción.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

El método `setStartAngle` espera un `double` que representa grados. Los valores positivos rotan en sentido horario, mientras que los negativos lo hacen en sentido antihorario.

## Paso 6: Cambiar el tamaño del agujero de la dona (cambiar el tamaño del gráfico de dona)

El tamaño del agujero se expresa como una fracción del radio del gráfico. Un valor de `0.5` significa que el agujero ocupa el 50 % del radio total.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Consejo:** El rango válido es `0.0` (sin agujero, es decir, un pastel normal) hasta `0.9` (anillo muy delgado). Valores fuera de este rango lanzarán una `IllegalArgumentException`.

## Paso 7: Guardar el documento modificado

Finalmente, escribe los cambios de vuelta al disco.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Al abrir `DoughnutFormatted.docx` en Microsoft Word, verás el gráfico de dona rotado 45° y el agujero reducido a la mitad de su tamaño original.

## Ejemplo completo y ejecutable

Uniendo todas las piezas, aquí tienes el programa completo que puedes copiar y pegar en tu IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Salida esperada

Ejecutar el programa imprime:

```
Chart rotated and doughnut size changed successfully.
```

Abrir `DoughnutFormatted.docx` muestra un gráfico de dona cuya primera porción comienza en la posición 45° y cuyo radio interno ocupa la mitad del radio externo.

## Variaciones comunes y casos límite

| Situación | Qué ajustar | Por qué es importante |
|-----------|-------------|-----------------------|
| **Múltiples gráficos** | Recorrer `getChildNodes(NodeType.SHAPE, true)` y comprobar `shape.hasChart()` para cada uno | Garantiza que modifiques el gráfico deseado y no solo el primero |
| **Gráfico de barras o líneas** | `setStartAngle` no se aplica; usa `chart.getSeries().get(0).setFillFormat(...)` para otros ajustes visuales | No todos los tipos de gráfico admiten rotación; solo los de dona/pastel tienen ángulo de inicio |
| **Gráfico sin agujero de dona** | Omitir `setDoughnutHoleSize` o convertir primero el tipo de gráfico a dona mediante `chart.setChartType(ChartType.DONUT)` | Cambiar el tamaño del agujero en un gráfico que no es dona lanza una excepción |
| **Documentos grandes** | Usar `DocumentBuilder.moveToDocumentStart()` y `builder.moveToNode(chartShape)` para una navegación dirigida | Mejora el rendimiento al evitar recorrer nodos no relacionados |

## Consejos profesionales para una manipulación fiable de gráficos

* **Cachear la referencia al gráfico** – Si planeas modificar varias propiedades, mantén una variable local `Chart` en lugar de llamar repetidamente a `chartShape.getChart()`.
* **Validar los valores de entrada** – Antes de llamar a `setStartAngle` o `setDoughnutHoleSize`, verifica que estén dentro del rango permitido para evitar errores en tiempo de ejecución.
* **Usar una licencia** – El modo de evaluación inserta una marca de agua en la primera página. Aplicar una licencia (`License license = new License(); license.setLicense("Aspose.Words.lic");`) la elimina.

## Próximos pasos

Ahora que sabes **cómo rotar un gráfico** y **cambiar el tamaño del gráfico de dona**, puedes explorar otros escenarios de **modificar gráfico en Word**:

* Cambiar los colores de las porciones con `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Añadir etiquetas de datos llamando a `chart.getSeries().get(0).setHasDataLabel(true)`.
* Exportar el gráfico como imagen usando `chart.toImage(300, 300, ImageType.PNG)`.

Cada una de estas extensiones sigue el mismo patrón: obtener el objeto `Chart`, llamar al setter correspondiente y guardar el documento.

---

**Acabas de dominar la rotación y el cambio de tamaño de gráficos de dona en Word usando Java.** Siéntete libre de adaptar el código a otros tipos de gráficos, integrarlo en una canalización más grande de generación de documentos o combinarlo con Aspose.Slides para la automatización de PowerPoint. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear un gráfico de columnas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ocultar eje del gráfico en un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insertar gráfico de burbujas en documento Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}