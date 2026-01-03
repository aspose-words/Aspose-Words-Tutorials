---
date: 2026-01-03
description: Aprende a ajustar los números de página al insertar una tabla de contenido
  usando Aspose.Words para Java. Personaliza los estilos de la tabla de contenido
  y crea documentos sin esfuerzo.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Ajustar números de página y generar índice con Aspose.Words para Java
url: /es/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajustar números de página y generar tabla de contenido en Aspose.Words for Java

En este tutorial descubrirá cómo **ajustar números de página** y **insertar una tabla de contenido** (TOC) con Aspose.Words for Java. Una tabla de contenido bien estructurada facilita la navegación de documentos extensos, y afinar la alineación de los números de página brinda a sus lectores una experiencia profesional. Recorreremos la creación de un documento, la personalización de los estilos de TOC y el ajuste de los tabuladores para que los números de página se alineen exactamente donde los desee.

## Respuestas rápidas
- **¿Qué significa “ajustar números de página”?** Modificar los tabuladores que alinean los números de página en una TOC.  
- **¿Puedo insertar una tabla de contenido automáticamente?** Sí – use la clase `FieldToc`.  
- **¿Necesito una licencia para ejecutar el código?** Una prueba gratuita funciona para desarrollo; se requiere una licencia para producción.  
- **¿Qué versión de Aspose es compatible?** Los ejemplos funcionan con la última versión de Aspose.Words for Java.  
- **¿Es posible personalizar los estilos de TOC?** Absolutamente – puede cambiar fuentes, negritas y más.

## Qué es una tabla de contenido en Aspose.Words?
Una TOC es un campo que escanea el documento en busca de estilos de encabezado (p. ej., Heading 1, Heading 2) y genera una lista de entradas con números de página. Aspose.Words le permite insertar este campo programáticamente y controlar completamente su apariencia.

## ¿Por qué ajustar los números de página en una TOC?
Ajustar los tabuladores le brinda un control preciso sobre dónde aparecen los números de página, lo cual es esencial para:

- Mantener un diseño limpio y alineado en columnas.  
- Cumplir con las guías de estilo corporativas.  
- Mejorar la legibilidad en documentos impresos y digitales.

## Requisitos previos
- Aspose.Words for Java añadido a su proyecto (Maven/Gradle).  
- Familiaridad básica con la sintaxis de Java.  

## Guía paso a paso

### Paso 1: Crear un nuevo documento
Primero, instancie un objeto `Document` vacío que contendrá su contenido y la TOC.

```java
Document doc = new Document();
```

### Paso 2: Personalizar los estilos de TOC
Puede cambiar la apariencia de cada nivel de TOC. En este ejemplo hacemos que las entradas de primer nivel estén en negrita, lo cual es una solicitud de formato común.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Paso 3: Añadir contenido a su documento
Inserte encabezados (p. ej., `Heading1`, `Heading2`) y párrafos normales. El campo TOC posteriormente detectará estos encabezados automáticamente. *(Código omitido por brevedad – el enfoque está en la generación de la TOC.)*

### Paso 4: Insertar el campo TOC
Coloque la TOC donde la desee, típicamente al inicio del documento.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Paso 5: Guardar el documento
Guarde el documento en disco. Puede elegir cualquier formato compatible como DOCX, PDF o HTML.

```java
doc.save("your_output_path_here");
```

## Personalizar los tabuladores en la TOC (Ajustar números de página)
Si el tabulador predeterminado no alinea los números de página como necesita, puede iterar a través de todos los párrafos de la TOC y modificar sus posiciones de tabulación.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Ahora las entradas de la TOC muestran los números de página exactamente donde los desea, proporcionando a su documento un aspecto pulido.

## Problemas comunes y consejos
- **Encabezados faltantes en la TOC:** Asegúrese de que sus encabezados utilicen estilos incorporados (`Heading1`, `Heading2`, etc.) o asocie estilos personalizados a los niveles de TOC.  
- **Tabulador no aplicado:** Verifique que el párrafo realmente pertenezca a un estilo de TOC (`TOC_1`‑`TOC_9`).  
- **Rendimiento en documentos grandes:** Llame a `doc.updateFields()` después de insertar la TOC para actualizar las entradas en una sola pasada.

## Preguntas frecuentes

**Q: ¿Cómo cambio el formato de las entradas de la TOC?**  
A: Use `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` donde *X* es el nivel (1‑9) y modifique su fuente, color o configuraciones de párrafo.

**Q: ¿Cómo puedo agregar más niveles a mi TOC?**  
A: Ajuste el interruptor `\o "1-3"` de `FieldToc` (por ejemplo) para incluir niveles de encabezado adicionales, luego actualice los estilos `TOC_X` correspondientes.

**Q: ¿Puedo cambiar las posiciones de los tabuladores para entradas específicas de la TOC?**  
A: Sí – itere a través de los párrafos como se muestra en la sección “Personalizar los tabuladores” y modifique cada tabulador individualmente.

**Q: ¿Es posible generar una TOC en salida PDF?**  
A: Absolutamente. Guarde el documento como PDF (`doc.save("output.pdf")`) después de que se genere la TOC; el campo se renderiza automáticamente.

**Q: ¿Necesito llamar a `updateFields()` manualmente?**  
A: Cuando inserta un `FieldToc`, Aspose.Words lo actualiza al guardar, pero llamar a `doc.updateFields()` le brinda resultados inmediatos para depuración.

## Conclusión
Ha aprendido cómo **ajustar números de página**, **insertar una tabla de contenido** y **personalizar los estilos de TOC** usando Aspose.Words for Java. Estas técnicas le permiten crear documentos limpios, navegables y con formato profesional que cumplen con cualquier estándar de publicación.

---  

**Última actualización:** 2026-01-03  
**Probado con:** Aspose.Words for Java (latest release)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}