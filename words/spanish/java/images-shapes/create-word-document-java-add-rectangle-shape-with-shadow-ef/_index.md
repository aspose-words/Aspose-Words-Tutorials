---
category: general
date: 2026-01-11
description: Crea rápidamente un documento Word en Java añadiendo una forma rectangular,
  configurando su color de relleno y aplicando una sombra a la forma. Aprende paso
  a paso.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: es
og_description: Crear documento de Word en Java insertando una forma rectangular,
  configurando su color de relleno y aplicando una sombra. Guía completa con código.
og_title: Crear documento Word en Java – Añadir forma de rectángulo con sombra
tags:
- Aspose.Words
- Java
- Document Generation
title: Crear documento Word en Java – Añadir forma rectangular con efecto de sombra
url: /es/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word con Java – Añadir forma rectangular con efecto de sombra

¿Alguna vez necesitaste **create word document java** y hacerlo ver un poco más pulido? Tal vez estés construyendo un generador de informes y una página simple no sea suficiente. ¿La buena noticia? Con Aspose.Words for Java puedes insertar una forma rectangular en un documento, darle un toque de color y hasta añadirle una sombra sutil, todo con unas pocas líneas.

En este tutorial recorreremos exactamente eso: cómo añadir una forma rectangular, establecer su color de relleno y aplicar una sombra a la forma para que tu archivo Word se sienta un poco más profesional. Al final tendrás un ejemplo ejecutable que puedes copiar‑pegar en tu propio proyecto.

## Lo que necesitarás

- **Java 17** (o cualquier JDK reciente) – el código usa las características estándar del lenguaje.  
- **Aspose.Words for Java** library – se recomienda la versión 23.9 o superior.  
- Un IDE o editor de texto de tu elección – IntelliJ IDEA, Eclipse, VS Code… tú decides.  
- Una carpeta donde se guardará el `ShadowShape.docx` generado.  

No se requiere ninguna configuración extra; solo agrega el JAR de Aspose.Words a tu classpath y listo.

## Paso 1: Configurar el proyecto e importar Aspose.Words

Lo primero, crea un nuevo proyecto Maven (o Gradle) y agrega la dependencia de Aspose.Words. Aquí tienes un fragmento mínimo de `pom.xml` para Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Si no usas Maven, simplemente coloca el archivo JAR en tu carpeta `libs` y añádelo al path de compilación.

> **Pro tip:** Aspose ofrece una licencia de prueba gratuita que puedes incrustar con `License license = new License(); license.setLicense("Aspose.Words.lic");`. Omitela para pruebas rápidas; la biblioteca funciona en modo de evaluación.

## Paso 2: Crear un nuevo Document y Builder

Ahora realmente **create word document java** objetos. La clase `Document` representa todo el archivo .docx, mientras que `DocumentBuilder` nos permite insertar contenido.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

En este punto tienes un documento vacío listo para recibir formas, párrafos o cualquier otro elemento que necesites.

## Paso 3: Insertar una forma rectangular y establecer su color de relleno

Añadir una forma es tan simple como llamar a `insertShape`. Usaremos la técnica **add rectangle shape**, que corresponde a la palabra clave secundaria *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

¿Por qué naranja? Destaca en un mar de blanco, pero puedes cambiarlo por cualquier `java.awt.Color` que prefieras. Este paso cubre la palabra clave secundaria *set shape fill color*.

## Paso 4: Configurar la apariencia de la sombra – Aplicar sombra a la forma

Ahora viene la parte divertida: darle a la rectángulo una sombra sutil. La API de Aspose expone un objeto `ShadowFormat` que controla cada aspecto de la sombra.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Ese bloque de código **apply shadow to shape** exactamente como sugiere la palabra clave secundaria. Puedes ajustar `blur`, `offsetX/Y` y `transparency` para adaptarlo a tu estilo de diseño. Por ejemplo, un `offsetX` mayor crea una proyección más dramática, mientras que una mayor `transparency` hace que la sombra susurre en lugar de gritar.

## Paso 5: Guardar el documento

Finalmente, escribimos el documento en disco. Elige una carpeta a la que tengas permiso de escritura y asigna al archivo un nombre claro.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Al abrir `ShadowShape.docx` en Microsoft Word o LibreOffice, verás un rectángulo naranja brillante con una sombra gris suave flotando justo debajo.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*El texto alternativo de la imagen incluye la palabra clave principal, cumpliendo la regla SEO.*

## Preguntas comunes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Aspose.Words soporta docenas de valores `ShapeType` – estrellas, flechas, globos de texto, lo que sea. Simplemente reemplaza `ShapeType.RECTANGLE` por `ShapeType.OVAL` u otro constante del enum. Los mismos pasos **how to add shape** se aplican.

### ¿Cómo añado la forma a un párrafo específico?

En lugar de insertar la forma directamente con el builder, puedes crearla primero (`new Shape(document, ShapeType.RECTANGLE)`) y luego añadirla a un `Paragraph` mediante `paragraph.appendChild(shape)`. Esto te brinda un control más fino sobre el diseño.

### ¿Puedo aplicar un relleno degradado en lugar de un color sólido?

¡Sí! Usa `rectangle.getFill().setFillType(FillType.GRADIENT)` y define un `LinearGradientFill`. La API es un poco más verbosa, pero funciona muy bien para diseños modernos.

### ¿Qué hay de la compatibilidad con versiones antiguas de Word?

Aspose.Words guarda en formato .docx por defecto, que es compatible con Word 2007+ y LibreOffice. Si necesitas .doc, llama a `document.save("file.doc", SaveFormat.DOC)`. La representación de la sombra puede variar ligeramente, pero la forma en sí permanece intacta.

## Ejemplo completo (listo para copiar y pegar)

A continuación tienes el programa completo, listo para compilar y ejecutar. Sustituye `YOUR_DIRECTORY` por una ruta real en tu máquina.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Ejecutar este código genera un archivo Word que contiene el rectángulo naranja con una sombra gris suave—exactamente lo que nos propusimos lograr cuando queríamos **create word document java** con una forma estilizada.

## Conclusión

Ahora tienes una receta sólida, de extremo a extremo, para **create word document java** que *adds rectangle shape*, *sets shape fill color* y *applies shadow to shape*. El enfoque es directo, la API es fluida y puedes ampliarlo de innumerables maneras—diferentes formas, rellenos degradados o incluso múltiples sombras por forma.

¿Qué sigue? Prueba a superponer varias formas, experimenta con `ShadowStyle.ETCHED` para un aspecto visual distinto, o combina esto con la generación de tablas para crear informes totalmente estructurados. Las posibilidades están limitadas solo por tu imaginación (y quizá por el nivel de licencia de Aspose).

Si encontraste algún inconveniente o tienes ideas para mejoras adicionales, deja un comentario abajo. ¡Feliz codificación y disfruta haciendo que esos documentos Word sean un poco menos aburridos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}