---
title: Impresión de documentos en Aspose.Words para Java
linktitle: Impresión de documentos
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a imprimir documentos con Aspose.Words para Java. Guía paso a paso para imprimir sin problemas en sus aplicaciones Java.
weight: 10
url: /es/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Impresión de documentos en Aspose.Words para Java


Si desea imprimir documentos con Aspose.Words para Java, está en el lugar correcto. En esta guía paso a paso, le explicaremos el proceso de impresión de documentos con Aspose.Words para Java utilizando el código fuente proporcionado.

## Introducción

Imprimir documentos es una tarea habitual en muchas aplicaciones. Aspose.Words para Java ofrece una potente API para trabajar con documentos de Word, incluida la capacidad de imprimirlos. En este tutorial, le guiaremos paso a paso en el proceso de impresión de un documento de Word.

## Configuración de su entorno

Antes de sumergirnos en el código, asegúrese de tener los siguientes requisitos previos:

- Kit de desarrollo de Java (JDK) instalado
- Biblioteca Aspose.Words para Java descargada y agregada a su proyecto

## Cargando el documento

 Para comenzar, deberá cargar el documento de Word que desea imprimir. Reemplazar`"Your Document Directory"` con la ruta a su documento y`"Your Output Directory"` con el directorio de salida deseado.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Creación de un trabajo de impresión

A continuación, crearemos un trabajo de impresión para imprimir el documento cargado. El fragmento de código que aparece a continuación inicializa un trabajo de impresión y establece la configuración de impresora deseada.

```java
// Crear un trabajo de impresión para imprimir nuestro documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializar un conjunto de atributos con el número de páginas del documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Pase la configuración de la impresora junto con los demás parámetros al documento de impresión.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Impresión del documento

Ahora que hemos configurado nuestro trabajo de impresión, es momento de imprimir el documento. El siguiente fragmento de código asocia el documento con el trabajo de impresión e inicia el proceso de impresión.

```java
// Pase el documento a imprimir mediante el trabajo de impresión.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Código fuente completo
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Crear un trabajo de impresión para imprimir nuestro documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializar un conjunto de atributos con el número de páginas del documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Pase la configuración de la impresora junto con los demás parámetros al documento de impresión.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Pase el documento a imprimir mediante el trabajo de impresión.
pj.setPrintable(awPrintDoc);
pj.print();
```
Código fuente de MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <resumen>
    /// El constructor de la clase PrintDocument personalizada.
    // / </summary>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //Los índices de inicio y final de la página tal como se definen en el conjunto de atributos.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Calcular el índice de la página que se representará a continuación.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Si el índice de la página es mayor que el rango total de páginas, entonces no hay nada
        // Más para renderizar.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Calcula el tamaño de cada marcador de miniatura en puntos.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Calcula el número de la primera página que se imprimirá en esta hoja de papel.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Seleccione el número de la última página que se imprimirá en esta hoja de papel.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Recorrer las páginas seleccionadas desde la página actual almacenada hasta la calculada
        // última página.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Calcular los índices de columnas y filas.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Define la ubicación de la miniatura en coordenadas mundiales (puntos en este caso).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Calcular las posiciones iniciales izquierda y superior.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Representar la página del documento en el objeto Gráficos usando coordenadas calculadas
                // y el tamaño del marcador de posición de miniatura.
                // El valor de retorno útil es la escala en la que se representó la página.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Dibuje los bordes de la página (la miniatura de la página podría ser más pequeña que la miniatura
                // tamaño del marcador de posición).
                if (mPrintPageBorders) {
                    // Obtenga el tamaño real del 100% de la página en puntos.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Dibuje el borde alrededor de la página escalada utilizando el factor de escala conocido.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Dibuje el borde alrededor del marcador de posición de la miniatura.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Si se produce algún error durante la renderización, no haga nada.
                // Esto dibujará una página en blanco si hay algún error durante la representación.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Define el número de columnas y filas en la hoja para la
        // Papel con orientación horizontal.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Intercambie el ancho y la altura si el papel está en orientación vertical.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Conclusión

¡Felicitaciones! Ha impreso correctamente un documento de Word con Aspose.Words para Java. Esta guía paso a paso debería ayudarlo a integrar la impresión de documentos en sus aplicaciones Java sin problemas.

## Preguntas frecuentes

### P1: ¿Puedo imprimir páginas específicas de un documento usando Aspose.Words para Java?

 Sí, puedes especificar el rango de páginas al imprimir un documento. En el ejemplo de código, usamos`attributes.add(new PageRanges(1, doc.getPageCount()))`Para imprimir todas las páginas, puede ajustar el rango de páginas según sea necesario.

### P2: ¿Aspose.Words para Java es adecuado para la impresión por lotes?

¡Por supuesto! Aspose.Words para Java es ideal para tareas de impresión por lotes. Puede recorrer una lista de documentos e imprimirlos uno por uno utilizando un código similar.

### P3: ¿Cómo puedo gestionar errores o excepciones de impresión?

Debes gestionar cualquier excepción potencial que pueda ocurrir durante el proceso de impresión. Consulta la documentación de Aspose.Words para Java para obtener información sobre cómo gestionar excepciones.

### P4: ¿Puedo personalizar aún más la configuración de impresión?

Sí, puede personalizar la configuración de impresión para satisfacer sus requisitos específicos. Explore la documentación de Aspose.Words para Java para obtener más información sobre las opciones de impresión disponibles.

### Q5: ¿Dónde puedo obtener más ayuda y soporte para Aspose.Words para Java?

 Para obtener ayuda y asistencia adicional, puede visitar el sitio[Foro Aspose.Words para Java](https://forum.aspose.com/).

---

Ahora que aprendió a imprimir documentos con Aspose.Words para Java, puede comenzar a implementar esta función en sus aplicaciones Java. ¡Que disfrute programando!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
