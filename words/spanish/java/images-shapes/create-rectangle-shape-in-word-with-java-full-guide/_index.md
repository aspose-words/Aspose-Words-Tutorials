---
category: general
date: 2026-02-10
description: Crear una forma rectangular en un documento Word usando Aspose.Words
  para Java. Aprende cómo establecer el color de la sombra, cómo agregar sombra y
  cómo crear un documento Word programáticamente.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: es
og_description: Crea una forma rectangular en un documento de Word usando Aspose.Words
  para Java. Sigue este tutorial paso a paso para establecer el color de la sombra,
  agregar sombra y crear el documento de Word.
og_title: Crear forma de rectángulo en Word con Java – Guía completa
tags:
- Aspose.Words
- Java
- Document Automation
title: Crear forma de rectángulo en Word con Java – Guía completa
url: /es/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear forma rectangular en Word con Java – Guía completa

¿Alguna vez necesitaste **crear forma rectangular** en un documento de Word pero no sabías por dónde empezar? No estás solo: muchos desarrolladores se topan con ese obstáculo la primera vez que intentan dibujar gráficos programáticamente en Word. ¿La buena noticia? Con Aspose.Words para Java puedes colocar un rectángulo en una página, añadirle una sombra agradable y guardar el archivo en segundos. En este tutorial recorreremos paso a paso **cómo añadir sombra**, **establecer el color de la sombra** y **crear un documento Word** desde cero.  

Cubriremos todo lo que necesitas: las bibliotecas requeridas, cada línea de código, por qué ciertos ajustes son importantes y algunos trucos que quizás no encuentres en la documentación oficial. Al final tendrás un ejemplo listo para ejecutar que crea una forma rectangular con una sombra gris suave, guardado como *Shadow.docx*.

## Requisitos previos – Lo que necesitas antes de comenzar

Antes de sumergirnos en el código, asegúrate de contar con lo siguiente:

| Requisito | Motivo |
|-----------|--------|
| Java Development Kit (JDK) 8 o superior | Aspose.Words funciona con cualquier JDK moderno. |
| Maven o Gradle (opcional) | Simplifica la incorporación de la dependencia Aspose.Words. |
| Licencia de Aspose.Words para Java (o una prueba gratuita) | La biblioteca es comercial; una prueba sirve para pruebas. |
| Un IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Te ayuda a ejecutar y depurar el ejemplo rápidamente. |

Si ya tienes un proyecto Java, solo agrega la coordenada Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

No necesitas una configuración sofisticada más allá de eso; un simple método `public static void main` será suficiente.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Texto alternativo de la imagen: ejemplo de creación de forma rectangular que muestra un rectángulo cian con una sombra gris.*

## Paso 1 – Crear un nuevo documento Word

Lo primero que debemos hacer es iniciar un documento en blanco. Piensa en ello como abrir un archivo Word nuevo en el que luego pintarás.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

¿Por qué comenzar con un `Document` vacío? Porque Aspose.Words trata a la clase `Document` como el lienzo para todas las operaciones posteriores: añadir párrafos, tablas o formas. Si omites este paso obtendrás un `NullPointerException` en el momento en que intentes insertar cualquier elemento.

## Paso 2 – Configurar un DocumentBuilder

Un `DocumentBuilder` es tu lápiz amigable que escribe dentro del `Document`. Es la forma recomendada de agregar contenido porque gestiona automáticamente la posición del cursor.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Quizás te preguntes: “¿Por qué no manipular el documento directamente?” La respuesta: el builder abstrae los detalles de bajo nivel, como el manejo de secciones, lo que hace que el código sea más limpio y menos propenso a errores.

## Paso 3 – Insertar la forma rectangular

Ahora llega la parte divertida—**cómo crear una forma**. Insertaremos un rectángulo de 100 × 50 puntos y le daremos un relleno cian para que sea visible.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Algunas notas:

* `ShapeType.RECTANGLE` indica a Aspose que queremos un rectángulo; puedes cambiarlo por `OVAL`, `LINE`, etc.
* Las dimensiones se expresan en puntos (1 pt ≈ 1/72 in). Ajústalas según tu diseño.
* Sin un color de relleno la forma sería invisible sobre una página blanca—de ahí el cian.

## Paso 4 – Añadir una sombra y **establecer el color de la sombra**

Aquí respondemos a la parte **cómo añadir sombra** del rompecabezas. El objeto `ShadowFormat` controla cada aspecto visual de la sombra, desde el color hasta el radio de difuminado.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

¿Por qué estos valores en particular?

* **Visibilidad** – Sin `setVisible(true)` el resto de los ajustes se ignoran.
* **Color** – El gris es una opción neutra que funciona tanto en fondos claros como oscuros. Si lo deseas, reemplaza `java.awt.Color.GRAY` por cualquier `java.awt.Color` que prefieras.
* **Radio de difuminado** – Un valor de `5.0` produce una sombra suave; valores mayores hacen que la sombra se vea más difusa.
* **OffsetX/Y** – Los desplazamientos mueven la sombra a la derecha y hacia abajo, imitando una fuente de luz desde la esquina superior izquierda.
* **Transparencia** – Una sombra semitransparente se integra mejor con la página, sobre todo al imprimir.

Si prefieres un aspecto más nítido, reduce el radio de difuminado a `0` y aumenta el desplazamiento. La experimentación está recomendada: las sombras son altamente visuales y la configuración adecuada depende del diseño de tu documento.

## Paso 5 – Guardar el documento

Finalmente, persistimos todo en un archivo `.docx`. Puedes elegir cualquier ruta que desees; solo asegúrate de que el directorio exista.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Al abrir *Shadow.docx* en Microsoft Word, verás un rectángulo cian con una sutil sombra gris desplazada 4 pts a la derecha y hacia abajo. Ese es el flujo completo para **crear un documento Word**.

### Resultado esperado

| Elemento | Apariencia |
|----------|------------|
| Rectángulo | Relleno cian, tamaño 100 × 50 pt |
| Sombra | Gris, 30 % transparente, difuminado 5 pt, desplazamiento (4, 4) |
| Archivo | `Shadow.docx` almacenado en la ruta que proporcionaste |

Si la forma no aparece, verifica que el color de relleno no sea el mismo que el fondo de la página y que la sombra esté configurada como visible.

## Consejos profesionales y errores comunes

* **Consejo pro:** Usa `rectangle.setStrokeColor(java.awt.Color.BLACK);` si deseas un contorno alrededor de la forma. Hace que el rectángulo destaque más en una página impresa.
* **Cuidado con:** Guardar en una carpeta de solo lectura lanzará una `IOException`. Elige una ubicación con permisos de escritura o ajusta los permisos del archivo.
* **Caso límite:** Si necesitas un relleno transparente (sin color), llama a `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. La forma seguirá proyectando sombra, lo que puede ser útil para gráficos tipo marca de agua.
* **Nota de rendimiento:** Añadir cientos de formas dentro de un bucle puede incrementar el uso de memoria. Llama a `document.save` solo una vez después de agregar todas las formas.

## Ejemplo completo y funcional

A continuación tienes el programa completo que puedes copiar y pegar en una clase Java llamada `ShadowDemo`. Compila y ejecuta tal cual (siempre que tengas el JAR de Aspose.Words en el classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Ejecuta el programa, abre el *Shadow.docx* resultante y verás el rectángulo con su sombra exactamente como se describió.

## ¿Qué pasa si necesitas más formas?

Quizás te preguntes: “¿Puedo **crear forma rectangular** varias veces o usar otras formas?” Absolutamente. Simplemente itera sobre el código de inserción y ajusta las coordenadas usando `builder.moveTo` o `builder.insertParagraph`. Las mismas configuraciones de sombra pueden reutilizarse extrayéndolas a un método auxiliar:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Llama a `applyStandardShadow(rectangle);` después de cada inserción de forma para mantener tu código DRY (Don’t Repeat Yourself).

## Próximos pasos – Más allá de lo básico

Ahora que sabes **cómo añadir sombra**, considera explorar estos temas relacionados:

* **Cómo establecer el color de la sombra** para fragmentos de texto – brinda a los títulos un sutil relieve.
* **Crear documento Word** con tablas e imágenes – combina formas con otro contenido.
* **Cómo crear animaciones de forma** usando las funciones integradas de Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}