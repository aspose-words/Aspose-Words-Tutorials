---
category: general
date: 2026-05-04
description: Crear un documento de Word en blanco en Java y aprender a establecer
  el color de la sombra, el desenfoque y el desplazamiento de las formas – tutorial
  rápido.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: es
og_description: Crea un documento de Word en blanco en Java y aprende cómo establecer
  el color, el desenfoque y el desplazamiento de la sombra para las formas. Sigue
  este tutorial paso a paso.
og_title: Crear palabra en blanco con sombra en Java – Guía completa
tags:
- Aspose.Words
- Java
- Document Automation
title: Crear una palabra en blanco con sombra en Java – Guía completa
url: /es/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento Word en blanco con sombra en Java – Guía completa

¿Alguna vez necesitaste **create blank word** archivos desde código y hacer que se vean un poco más elegantes? No eres el único. En muchos proyectos de generación de informes o plantillas, lo primero que haces es crear un documento Word vacío y luego añadir una forma con sombra para darle ese aspecto pulido.  

En este tutorial recorreremos exactamente eso: cómo crear un documento Word en blanco usando Aspose.Words for Java, **how to add shadow** a una forma, y los detalles de **set shadow color**, **how to set blur** y **how to set offset**. Al final tendrás un archivo `.docx` listo para usar que muestra un rectángulo con una sombra roja ligeramente difuminada y semi‑transparente.

## Lo que necesitarás

- **Aspose.Words for Java** (cualquier versión reciente; el código funciona con 23.9+)
- JDK 8 o superior
- Un IDE o editor de texto simple más una terminal
- Conocimientos básicos de Java—nada sofisticado, solo la capacidad de ejecutar un método `main`

No se requiere configuración extra de Maven o Gradle para la demo; simplemente coloca el JAR de Aspose en tu classpath y estarás listo para continuar.

---

![ejemplo de documento Word en blanco con sombra](image-placeholder.png){: .center alt="ejemplo de documento Word en blanco con sombra"}

## Crear documento Word en blanco – Inicializando el Documento

El primer paso es crear un archivo Word nuevo y vacío. Piensa en él como un lienzo limpio donde luego podrás dibujar formas, tablas o texto.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Por qué es importante:** `Document` representa todo el paquete `.docx`. Al crearlo con el constructor por defecto, estás efectivamente **create blank word** – no hay contenido, ni secciones, solo la estructura del archivo lista para que la completes.

## Cómo añadir sombra a una forma

Ahora que tenemos un documento limpio, insertemos un rectángulo que alojará nuestra sombra. Aquí es donde comienza la magia visual.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Consejo profesional:** La llamada `insertShape` agrega automáticamente la forma al párrafo actual, por lo que no necesitas gestionar la posición manualmente a menos que quieras una ubicación absoluta.

## Establecer color de sombra – haciendo que la sombra destaque

Una sombra sin color es solo un difuminado gris, lo que puede parecer plano. Al establecer el color de la sombra puedes coincidir con la marca o simplemente hacer que resalte.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Qué está sucediendo:** `ShadowFormat` controla cada aspecto visual de la sombra. Activar `setVisible(true)` enciende el efecto, y `setColor` te permite elegir cualquier `java.awt.Color`. En nuestro ejemplo elegimos rojo para demostrar claramente **set shadow color**.

## Cómo establecer difuminado para un efecto sutil

Una sombra nítida y de bordes duros puede parecer dura. Añadir difuminado suaviza los bordes, proporcionando un aspecto más natural.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Por qué el difuminado importa:** El valor de `setBlur` se mide en puntos. Un valor de `5.0` crea una difusión suave; aumentarlo para una sombra más difusa, disminuirlo para un contorno más nítido.

## Cómo establecer desplazamiento – posicionando la sombra

Los desplazamientos determinan dónde se sitúa la sombra respecto a la forma. Piensa en ellos como desplazamientos en X y Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Explicación del desplazamiento:** Un X positivo mueve la sombra a la derecha, un Y positivo la mueve hacia abajo. Juega con números negativos si deseas que la sombra aparezca en el lado opuesto.

## Ajuste fino de la transparencia

Si deseas que la sombra sea menos dominante, ajusta su transparencia. Este paso no es un requisito de palabra clave, pero completa el control visual.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Guardando el documento – ver el resultado

Finalmente, escribe el documento en disco. Obtendrás un `.docx` que puedes abrir en Word, LibreOffice o cualquier visor que soporte el formato.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Lo que deberías ver:** Abre `ShadowShape.docx`. Una sola página mostrará un rectángulo de 150 × 80 pt con una sombra roja ligeramente difuminada desplazada 8 pt hacia abajo y a la derecha. La sombra es 30 % transparente, por lo que el rectángulo sigue siendo claramente visible.

---

## Preguntas comunes y casos límite

### ¿Qué pasa si necesito una forma diferente?

Reemplaza `ShapeType.RECTANGLE` por cualquier otro valor del enum (`ELLIPSE`, `CLOUD`, `CALLOUT`, etc.). La configuración de la sombra funciona idénticamente en todas las formas.

### ¿Puedo aplicar la misma sombra a múltiples formas sin repetir código?

Absolutamente. Crea un método auxiliar:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Luego llama a `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` para cualquier forma.

### ¿Esto funciona con versiones antiguas de Aspose?

La API `ShadowFormat` ha sido estable desde la versión 19.8, por lo que deberías estar bien con la mayoría de las versiones recientes. Si estás en una compilación muy antigua, revisa el Javadoc de `ShadowFormat` para verificar los nombres de los métodos.

### ¿Cómo exportar a PDF manteniendo la sombra?

Simplemente llama a `document.save("output.pdf");` después de crear la forma. Aspose.Words renderiza las sombras correctamente en PDF, preservando el difuminado y la transparencia.

---

## Recapitulación – crear documento Word en blanco con una sombra personalizada

Comenzamos con **create blank word** usando `new Document()`, luego insertamos un rectángulo, **set shadow color**, aprendimos **how to add shadow**, ajustamos **how to set blur**, y finalmente modificamos **how to set offset** para posicionarlo correctamente. El código completo y ejecutable está en el fragmento anterior, y el archivo resultante muestra el efecto claramente.

---

## ¿Qué sigue?

- **Experimentar con otras propiedades de sombra** como `ShadowFormat.setStyle(ShadowStyle.OUTER)` para diferentes estilos visuales.
- **Combinar múltiples formas** cada una con su propia sombra para crear diagramas complejos.
- **Agregar texto dentro de la forma** usando `builder.insertHtml("<b>Hello</b>")` antes de insertar la forma, luego aplicar la misma lógica de sombra.
- **Explorar otras opciones de formato** como estilo de línea, color de relleno o rellenos degradados—Aspose.Words ofrece una API rica para todo esto.

Siéntete libre de ajustar el radio del difuminado, los desplazamientos o los colores hasta que la sombra se sienta perfecta para el lenguaje de diseño de tu documento. ¡Feliz codificación, y que tus archivos Word generados siempre luzcan un poco más pulidos!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}