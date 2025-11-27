---
date: '2025-11-27'
description: Aprenda a crear marcadores, generar PDF con marcadores y convertir Word
  a PDF en Java usando Aspose.Words. Esta guía cubre marcadores anidados y niveles
  de esquema.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: es
title: Cómo crear marcadores y establecer niveles de esquema en PDFs usando Aspose.Words
  Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear marcadores y establecer niveles de esquema en PDFs usando Aspose.Words Java

## Introducción
Si alguna vez has tenido dificultades para **crear marcadores** que se mantengan organizados al convertir un documento Word a PDF, estás en el lugar correcto. En este tutorial recorreremos todo el proceso de generar un PDF con marcadores, anidarlos y asignar niveles de esquema para que el PDF final sea fácil de navegar. Al final podrás **convertir Word a PDF con Java**‑style con una jerarquía de marcadores limpia que funciona en cualquier visor de PDF.

### Lo que aprenderás
- Configura Aspose.Words para Java en tu entorno de desarrollo.  
- **Cómo crear marcadores** programáticamente y anidarlos.  
- Configura los niveles de esquema de los marcadores para generar un PDF con marcadores que reflejen la estructura del documento.  
- Guarda el archivo Word como PDF manteniendo la jerarquía de marcadores.

## Respuestas rápidas
- **¿Cuál es la clase principal para crear documentos?** `DocumentBuilder`.  
- **¿Qué opción controla la jerarquía de marcadores?** `BookmarksOutlineLevelCollection` dentro de `PdfSaveOptions`.  
- **¿Puedo usar Maven o Gradle?** Sí, ambos se muestran a continuación.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia permanente para producción.  
- **¿Es este enfoque adecuado para documentos grandes?** Sí, pero considera técnicas de optimización de memoria (p. ej., eliminar recursos no usados).

### Requisitos previos
Antes de comenzar, asegúrate de tener:

- **Bibliotecas y dependencias** – Aspose.Words for Java (25.3 o posterior).  
- **Entorno** – JDK 8 o superior, y un IDE como IntelliJ IDEA o Eclipse.  
- **Conocimientos básicos** – Fundamentos de programación Java y familiaridad con Maven o Gradle.

## Configuración de Aspose.Words
Para comenzar, incluye las dependencias necesarias en tu proyecto. Así es como puedes añadir Aspose.Words usando Maven o Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Obtención de la licencia
Aspose.Words es una biblioteca comercial, pero puedes comenzar con una prueba gratuita:

1. **Prueba gratuita** – Descarga desde la [página de lanzamientos de Aspose](https://releases.aspose.com/words/java/).  
2. **Licencia temporal** – Solicítala en la [página de licencia temporal](https://purchase.aspose.com/temporary-license/) si necesitas una clave a corto plazo.  
3. **Licencia completa** – Compra a través del [portal de compras de Aspose](https://purchase.aspose.com/buy) para uso en producción.

Después de obtener el archivo de licencia, cárgalo al iniciar la aplicación para desbloquear todas las funciones.

## Cómo crear marcadores en PDFs con Aspose.Words Java
A continuación dividimos la implementación en pasos claros y numerados. Cada paso incluye una breve explicación seguida del bloque de código original (sin cambios).

### Paso 1: Inicializar un Document y un DocumentBuilder
Comenzamos con una nueva instancia de `Document` y un `DocumentBuilder` que nos permite insertar contenido y marcadores.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Paso 2: Insertar el primer marcador (padre)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Paso 3: Anidar un marcador hijo dentro del padre
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Paso 4: Cerrar el marcador padre
```java
builder.endBookmark("Bookmark 1");
```

### Paso 5: Añadir un tercer marcador independiente
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Configuración de los niveles de esquema de los marcadores
Una vez que los marcadores están en su lugar, indicamos a Aspose.Words cómo deben aparecer esos marcadores en el esquema del PDF (el panel de navegación izquierdo).

### Paso 6: Preparar PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Paso 7: Asignar niveles de jerarquía
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Paso 8: Guardar el documento como PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## ¿Por qué usar este enfoque para generar PDF con marcadores?
- **Navegación profesional** – Los lectores pueden saltar directamente a secciones, mejorando la usabilidad en informes extensos o contratos legales.  
- **Control total** – Tú decides la jerarquía, no el visor de PDF.  
- **Multiplataforma** – Funciona igual en Windows, Linux y macOS porque es Java puro.  

## Problemas comunes y soluciones

| Síntoma | Causa probable | Solución |
|---|---|---|
| Marcadores ausentes en el PDF | Un `startBookmark` sin su correspondiente `endBookmark` | Verifica que cada `startBookmark` tenga un `endBookmark` correspondiente. |
| Jerarquía incorrecta | Niveles de esquema asignados fuera de orden | Asegúrate de que los marcadores padres tengan números de nivel más bajos que sus hijos. |
| Licencia no aplicada | Archivo de licencia no cargado antes de crear el documento | Carga la licencia al inicio de tu aplicación (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Aplicaciones prácticas
1. **Documentos legales** – Navega rápidamente entre cláusulas, anexos y apéndices.  
2. **Informes financieros** – Salta entre secciones como Estado de resultados, Balance general y notas.  
3. **Materiales de e‑learning** – Proporciona una tabla de contenidos que refleje el esquema del PDF.  

## Consideraciones de rendimiento
- **Gestión de memoria** – Para archivos Word muy grandes, considera llamar a `doc.cleanup()` antes de guardar.  
- **Optimización de recursos** – Elimina imágenes o estilos no usados para mantener pequeño el tamaño del PDF.  

## Preguntas frecuentes

**P: ¿Cómo instalo Aspose.Words para Java?**  
R: Añade la dependencia Maven o Gradle mostrada anteriormente, luego coloca tu archivo de licencia en el classpath y cárgalo en tiempo de ejecución.

**P: ¿Puedo crear marcadores sin establecer niveles de esquema?**  
R: Sí, pero el visor de PDF los mostrará como una lista plana, lo que puede ser difícil de navegar en documentos complejos.

**P: ¿Hay un límite a la profundidad de anidación de los marcadores?**  
R: Técnicamente no, pero la mayoría de los visores de PDF soportan cómodamente hasta 9 niveles. Mantén la jerarquía lógica para los lectores.

**P: ¿Cómo maneja Aspose archivos Word muy grandes?**  
R: La biblioteca transmite el contenido y ofrece métodos como `Document.optimizeResources()` para reducir la huella de memoria.

**P: ¿Puedo editar los marcadores después de generar el PDF?**  
R: Por supuesto – puedes usar Aspose.PDF para Java para añadir, eliminar o renombrar marcadores en un PDF existente.

## Recursos
- [Documentación de Aspose.Words](https://reference.aspose.com/words/java/)  
- [Descargar últimas versiones](https://releases.aspose.com/words/java/)  
- [Comprar una licencia](https://purchase.aspose.com/buy)  
- [Prueba gratuita](https://releases.aspose.com/words/java/)  
- [Solicitud de licencia temporal](https://purchase.aspose.com/temporary-license/)  
- [Foro de soporte de Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Última actualización:** 2025-11-27  
**Probado con:** Aspose.Words 25.3 for Java  
**Autor:** Aspose