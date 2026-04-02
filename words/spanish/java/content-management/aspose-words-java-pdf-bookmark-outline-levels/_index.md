---
date: '2026-04-02'
description: Aprenda cómo crear marcadores anidados, establecer niveles de esquema
  de marcadores y guardar documentos de Word como PDF con Aspose.Words para Java.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Crear marcadores anidados y establecer niveles de esquema en PDFs usando Aspose.Words
  para Java
url: /es/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear marcadores anidados y establecer niveles de esquema en PDFs usando Aspose.Words para Java

## Introducción
¿Tienes problemas para gestionar los marcadores al convertir documentos de Word a PDFs? **Este tutorial te muestra cómo crear marcadores anidados**, configurar sus niveles de esquema y guardar el resultado como un PDF limpio y navegable usando Aspose.Words para Java. Al final de esta guía tendrás un PDF de aspecto profesional donde los lectores pueden ir directamente a las secciones que necesitan.

**Qué aprenderás**
- Configurar Aspose.Words para Java en tu proyecto  
- **Crear marcadores anidados** en un documento Word  
- **Cómo establecer niveles de esquema de los marcadores** para una jerarquía clara  
- **Guardar los marcadores de Word en PDF** con la estructura correcta  

### Respuestas rápidas
- **¿Cuál es la clase principal para crear documentos?** `DocumentBuilder`  
- **¿Qué método agrega un nivel de esquema a un marcador?** `BookmarksOutlineLevels.add()`  
- **¿Necesito una licencia para exportar PDFs?** Se requiere una licencia para producción; una prueba gratuita funciona para evaluación.  
- **¿Puedo anidar marcadores arbitrariamente profundos?** Sí, pero mantén la jerarquía legible para los usuarios finales.  
- **¿Qué versión de Aspose.Words se requiere?** Versión 25.3 o posterior.

## Qué es “crear marcadores anidados”
Los marcadores anidados son marcadores ubicados dentro de otros marcadores, formando una jerarquía padre‑hijo. En un PDF aparecen como elementos expandibles en el panel de marcadores, permitiendo a los lectores contraer o expandir secciones según sea necesario.

## Por qué establecer niveles de esquema de los marcadores
Los niveles de esquema definen el orden visual de anidamiento en el panel de marcadores del PDF. Los niveles adecuados mejoran la navegación, especialmente en contratos legales extensos, informes técnicos o libros electrónicos donde los usuarios necesitan localizar información rápidamente.

## Requisitos previos
- **Bibliotecas y dependencias**: Aspose.Words para Java (versión 25.3 o posterior).  
- **Entorno**: JDK 8+ y un IDE como IntelliJ IDEA o Eclipse.  
- **Conocimientos**: Java básico, familiaridad con Maven o Gradle.

### Configuración de Aspose.Words
Agrega la biblioteca a tu proyecto con Maven o Gradle.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Obtención de licencia
Aspose.Words es un producto comercial, pero puedes comenzar con una prueba gratuita.

1. **Prueba gratuita** – Descarga desde [Aspose's release page](https://releases.aspose.com/words/java/) para probar todas las capacidades.  
2. **Licencia temporal** – Solicita en [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/) si necesitas una clave a corto plazo.  
3. **Compra** – Compra una licencia permanente a través del [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

Inicializa el archivo de licencia en tu código antes de usar cualquier API de Aspose para desbloquear todas las funciones.

## Guía de implementación

### Cómo crear marcadores anidados en un documento Word
Crearemos un documento sencillo y añadiremos tres marcadores, uno de los cuales contiene otro marcador.

#### Paso 1: Inicializar el documento y el constructor
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Paso 2: Insertar el primer marcador (padre)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Paso 3: Anidar un segundo marcador dentro del primero
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Paso 4: Cerrar el marcador externo
```java
builder.endBookmark("Bookmark 1");
```

#### Paso 5: Añadir un tercer marcador independiente
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Cómo establecer niveles de esquema de los marcadores para la exportación a PDF
Ahora configuraremos la jerarquía de esquema que aparecerá en el PDF final.

#### Paso 1: Preparar `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Paso 2: Asignar niveles de esquema a cada marcador
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Paso 3: Guardar el documento como PDF con los marcadores configurados
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Problemas comunes y soluciones
- **Marcadores faltantes** – Verifica que cada `startBookmark` tenga un `endBookmark` correspondiente.  
- **Jerarquía incorrecta** – Revisa los números de nivel que asignas; un número menor significa un nivel superior (padre).  
- **Licencia no aplicada** – Si los marcadores desaparecen, asegúrate de que el archivo de licencia se cargue antes de cualquier procesamiento del documento.  

## Aplicaciones prácticas
1. **Contratos legales** – Salta rápidamente a cláusulas, subcláusulas y anexos.  
2. **Informes técnicos** – Navega por secciones, tablas y figuras sin desplazarte.  
3. **Material de e‑learning** – Permite a los estudiantes expandir capítulos y contraer ejemplos según sea necesario.

## Consejos de rendimiento
- Elimina secciones o imágenes no utilizadas antes de guardar para mantener el tamaño del PDF pequeño.  
- Para documentos muy grandes, llama a `doc.cleanup()` o procesa el archivo en fragmentos para reducir la presión de memoria.

## Preguntas frecuentes

**P: ¿Cómo instalo Aspose.Words para Java?**  
**R:** Añade la dependencia de Maven o Gradle mostrada arriba, luego coloca tu archivo de licencia en el proyecto e inicialízalo en el código.

**P: ¿Puedo usar marcadores sin establecer niveles de esquema?**  
**R:** Sí, pero sin niveles de esquema el panel de marcadores del PDF mostrará una lista plana, lo que dificulta la navegación.

**P: ¿Existe un límite de cuán profundo pueden anidarse los marcadores?**  
**R:** Técnicamente no, pero mantén la jerarquía razonable (3‑4 niveles) para la legibilidad del usuario.

**P: ¿Cómo maneja Aspose archivos Word muy grandes?**  
**R:** La biblioteca transmite el contenido y ofrece métodos como `Document.optimizeResources()` para mantener bajo el uso de memoria.

**P: ¿Puedo editar los marcadores después de generar el PDF?**  
**R:** Sí, puedes usar Aspose.PDF para Java para modificar los títulos de los marcadores, destinos o la jerarquía después de la creación.

## Recursos
- [Documentación de Aspose.Words](https://reference.aspose.com/words/java/)
- [Descargar últimas versiones](https://releases.aspose.com/words/java/)
- [Comprar una licencia](https://purchase.aspose.com/buy)
- [Prueba gratuita](https://releases.aspose.com/words/java/)
- [Solicitud de licencia temporal](https://purchase.aspose.com/temporary-license/)
- [Foro de soporte de Aspose](https://forum.aspose.com/c/words/10)

---

**Última actualización:** 2026-04-02  
**Probado con:** Aspose.Words 25.3 for Java  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}