---
date: '2026-04-27'
description: Aprende a crear marcadores y guardar PDF con marcadores usando Aspose.Words
  para Java. Mejora la legibilidad y la navegación con esta guía completa.
keywords:
- how to set bookmarks
- save pdf with bookmarks
- create nested bookmarks
- generate pdf with bookmarks
- convert word pdf bookmarks
title: Cómo establecer marcadores en PDFs con Aspose.Words Java
url: /es/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo establecer marcadores en PDFs con Aspose.Words Java

## Introducción
Si tienes dificultades para gestionar **cómo establecer marcadores** al convertir documentos Word a PDFs, estás en el lugar correcto. En este tutorial recorreremos todo el proceso usando Aspose.Words para Java, desde crear marcadores anidados hasta configurar sus niveles de esquema, de modo que el PDF final sea limpio, profesional y fácil de navegar.

**Lo que aprenderás**
- Configura Aspose.Words para Java en tu proyecto  
- **Crear marcadores anidados** dentro de un documento Word  
- **Configurar niveles de esquema de marcadores** para un esquema PDF estructurado  
- **Guardar PDF con marcadores** que reflejen la jerarquía que definiste  

### Respuestas rápidas
- **¿Cuál es la clase principal para crear documentos?** `DocumentBuilder`  
- **¿Qué opción controla la jerarquía de marcadores?** `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`  
- **¿Puedo usar Maven o Gradle?** Sí, ambos son compatibles (ver fragmentos de código)  
- **¿Necesito una licencia?** Una prueba funciona para evaluación; se requiere una licencia permanente para producción  
- **¿El PDF conservará los marcadores anidados?** Absolutamente, cuando los niveles de esquema se establecen correctamente  

## ¿Qué es “cómo establecer marcadores” en un PDF?
Establecer marcadores significa definir entradas clicables en el panel de navegación de un PDF que saltan a secciones específicas del documento. Cuando los marcadores están anidados y se les asignan niveles de esquema, aparecen como un árbol colapsable, lo que facilita mucho la exploración de documentos extensos.

## ¿Por qué usar Aspose.Words para niveles de esquema de marcadores?
Aspose.Words te brinda control total programático sobre la conversión de Word a PDF, incluida la capacidad de **generar PDF con marcadores** que reflejen la estructura de tu documento. Esto elimina la necesidad de procesamiento manual posterior y garantiza una experiencia de usuario consistente en todos los PDFs generados.

## Requisitos previos
- **Bibliotecas y dependencias**: Aspose.Words para Java (versión 25.3 o posterior).  
- **Entorno**: JDK 8 o más reciente, IDE como IntelliJ IDEA o Eclipse.  
- **Conocimientos**: Java básico, familiaridad con Maven o Gradle.

## Configuración de Aspose.Words
Agrega la biblioteca requerida a tu sistema de compilación.

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

1. **Prueba gratuita**: Descarga desde [Página de lanzamientos de Aspose](https://releases.aspose.com/words/java/) para probar todas las capacidades.  
2. **Licencia temporal**: Solicita una licencia temporal en [Página de licencia temporal de Aspose](https://purchase.aspose.com/temporary-license/) si es necesario.  
3. **Compra**: Para uso continuo, adquiere una licencia en [Portal de compras de Aspose](https://purchase.aspose.com/buy).

Inicializa el archivo de licencia en tu código para desbloquear todas las funciones.

## Guía de implementación
A continuación se muestra una guía paso a paso que cubre **crear marcadores anidados**, establecer sus niveles de esquema y, finalmente, **guardar PDF con marcadores**.

### Creación de marcadores anidados
**Visión general**: Construye un documento Word e incrusta marcadores que reflejen una jerarquía.

#### Paso 1: Inicializar documento y builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Esto crea un documento nuevo listo para la inserción de contenido.

#### Paso 2: Insertar marcadores anidados
Comienza con un marcador principal, luego anida un segundo dentro de él.

```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

```java
builder.endBookmark("Bookmark 1");
```

#### Paso 3: Añadir marcadores adicionales
Puedes seguir añadiendo marcadores independientes según sea necesario.

```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Configuración de niveles de esquema de marcadores
**Visión general**: Asigna niveles de esquema para que el panel de marcadores del PDF refleje la jerarquía prevista.

#### Paso 1: Configurar PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Estas opciones se usarán al guardar el documento como PDF.

#### Paso 2: Añadir niveles de esquema
Mapea cada nombre de marcador a un nivel de esquema (1 = nivel superior, 2 = hijo, etc.).

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Paso 3: Guardar el documento
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
El PDF resultante ahora contiene un árbol de marcadores estructurado.

## Problemas comunes y soluciones
- **Marcadores faltantes** – Verifica que cada `startBookmark` tenga un `endBookmark` correspondiente.  
- **Jerarquía incorrecta** – Revisa los números de nivel de esquema; un hijo debe tener un número mayor que su padre.  
- **Documentos grandes** – Llama a `doc.removeUnusedResources()` antes de guardar para reducir el tamaño del archivo.

## Aplicaciones prácticas
1. **Contratos legales** – Salta rápidamente a cláusulas y subcláusulas.  
2. **Informes anuales** – Navega por secciones, tablas y gráficos con facilidad.  
3. **Material de e‑learning** – Proporciona una tabla de contenidos clicable para los estudiantes.

## Consideraciones de rendimiento
- Elimina nodos innecesarios antes de la conversión para mantener el PDF ligero.  
- Para archivos muy grandes, considera transmitir el documento para evitar un alto consumo de memoria.

## Conclusión
Ahora sabes **cómo establecer marcadores**, configurar sus niveles de esquema y **guardar PDF con marcadores** usando Aspose.Words para Java. Esta técnica mejora drásticamente la navegación en PDFs y brinda a tus documentos un acabado profesional.

**Próximos pasos**: Intenta agregar íconos personalizados a los marcadores o integrar este flujo de trabajo en un servicio de procesamiento por lotes.

## Preguntas frecuentes

**Q: ¿Cómo instalo Aspose.Words para Java?**  
A: Agrega la dependencia Maven o Gradle mostrada arriba, luego coloca tu archivo de licencia en la carpeta resources del proyecto.

**Q: ¿Puedo crear marcadores sin niveles de esquema?**  
A: Sí, pero sin niveles de esquema el panel de navegación del PDF listará todos los marcadores al mismo nivel, lo que dificulta la navegación en documentos extensos.

**Q: ¿Existe un límite en la profundidad de los marcadores anidados?**  
A: Técnicamente no, pero mantén la jerarquía legible para los usuarios finales—generalmente 3‑4 niveles son suficientes.

**Q: ¿Cómo maneja Aspose archivos Word muy grandes?**  
A: Transmite el contenido y ofrece métodos como `Document.optimizeResources()` para mantener bajo el uso de memoria.

**Q: ¿Puedo editar los marcadores después de generar el PDF?**  
A: Sí, puedes usar Aspose.PDF para Java para modificar los títulos, destinos o la jerarquía de los marcadores después de la conversión.

---

**Última actualización:** 2026-04-27  
**Probado con:** Aspose.Words 25.3 para Java  
**Autor:** Aspose  

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