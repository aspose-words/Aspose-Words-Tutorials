---
title: Generación de índices
linktitle: Generación de índices
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a crear una tabla de contenido dinámica con Aspose.Words para Java. Domine la generación de tablas de contenido con instrucciones paso a paso y ejemplos de código fuente.
weight: 14
url: /es/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Generación de índices

## Introducción

¿Alguna vez tuvo problemas para crear una tabla de contenido (TOC) dinámica y de aspecto profesional en sus documentos de Word? ¡No busque más! Con Aspose.Words para Java, puede automatizar todo el proceso, ahorrando tiempo y garantizando la precisión. Ya sea que esté creando un informe completo o un artículo académico, este tutorial lo guiará en la generación de una TOC mediante programación con Java. ¿Listo para comenzar? ¡Comencemos!

## Prerrequisitos

Antes de comenzar a codificar, asegúrese de tener lo siguiente:

1.  Kit de desarrollo de Java (JDK): instalado en su sistema. Puede descargarlo desde[Sitio web de Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Biblioteca Aspose.Words para Java: Descargue la última versión desde[página de lanzamiento](https://releases.aspose.com/words/java/).
3. Entorno de desarrollo integrado (IDE): como IntelliJ IDEA, Eclipse o NetBeans.
4.  Licencia Temporal Aspose: Para evitar limitaciones de evaluación, obtenga una[licencia temporal](https://purchase.aspose.com/temporary-license/).

## Importar paquetes

Para utilizar Aspose.Words para Java de forma eficaz, asegúrese de importar las clases necesarias. Estas son las importaciones:

```java
import com.aspose.words.*;
```

Siga estos pasos para generar una tabla de contenidos dinámica en su documento de Word.

## Paso 1: Inicializar el documento y DocumentBuilder

 El primer paso es crear un nuevo documento y utilizar el`DocumentBuilder` clase para manipularlo.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`:Representa el documento de Word.
- `DocumentBuilder`:Una clase auxiliar que permite una fácil manipulación del documento.

## Paso 2: Insertar la tabla de contenidos

Ahora, insertemos la tabla de contenidos al principio del documento.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Inserta un campo de índice. Los parámetros especifican:
  - `\o "1-3"`:Incluye títulos de los niveles 1 al 3.
  - `\h`:Crear hipervínculos a las entradas.
  - `\z`:Suprimir números de página para documentos web.
  - `\u`: Conservar estilos para hipervínculos.
- `insertBreak`:Agrega un salto de página después de la tabla de contenidos.

## Paso 3: Agregar encabezados para completar la tabla de contenidos

Para completar la tabla de contenidos, es necesario agregar párrafos con estilos de título.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` :Establece el estilo de párrafo a un nivel de encabezado específico (por ejemplo,`HEADING_1`, `HEADING_2`).
- `writeln`:Agrega texto al documento con el estilo especificado.

## Paso 4: Agregar encabezados anidados

Para demostrar los niveles de TOC, incluya encabezados anidados.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Agregue encabezados de niveles más profundos para mostrar la jerarquía en la tabla de contenidos.

## Paso 5: Actualizar los campos de la tabla de contenidos

El campo TOC debe actualizarse para mostrar los encabezados más recientes.


```java
doc.updateFields();
```

- `updateFields`:Actualiza todos los campos del documento, garantizando que la tabla de contenido refleje los encabezados agregados.

## Paso 6: Guardar el documento

Por último, guarde el documento en el formato que desee.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` : Exporta el documento a un`.docx` archivo. Puede especificar otros formatos como`.pdf` o`.txt` Si es necesario.

## Conclusión

¡Felicitaciones! Ha creado con éxito una tabla de contenido dinámica en un documento de Word con Aspose.Words para Java. Con solo unas pocas líneas de código, ha automatizado una tarea que de otro modo podría llevar horas. ¿Qué sigue? Pruebe a experimentar con diferentes estilos y formatos de encabezado para adaptar su tabla de contenido a necesidades específicas.

## Preguntas frecuentes

### ¿Puedo personalizar aún más el formato de TOC?
¡Por supuesto! Puedes ajustar los parámetros de la tabla de contenidos, como incluir números de página, alinear el texto o usar estilos de encabezado personalizados.

### ¿Es obligatoria una licencia para Aspose.Words para Java?
 Sí, se requiere una licencia para tener todas las funciones. Puedes empezar con una[licencia temporal](https://purchase.aspose.com/temporary-license/).

### ¿Puedo generar una tabla de contenidos para un documento existente?
 ¡Sí! Cargue el documento en un`Document` objeto y siga los mismos pasos para insertar y actualizar la tabla de contenidos.

### ¿Funciona esto para exportaciones en formato PDF?
 Sí, la tabla de contenidos aparecerá en el PDF si guarda el documento en`.pdf` formato.

### ¿Dónde puedo encontrar más documentación?
 Echa un vistazo a la[Documentación de Aspose.Words para Java](https://reference.aspose.com/words/java/) para más ejemplos y detalles.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
