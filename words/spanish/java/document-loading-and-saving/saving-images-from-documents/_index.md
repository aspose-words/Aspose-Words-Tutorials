---
date: 2025-12-27
description: Aprenda a guardar una página como JPEG y extraer imágenes de documentos
  Word usando Aspose.Words para Java. Incluye consejos para ajustar el brillo de la
  imagen, la resolución y crear TIFF multipágina.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Cómo guardar una página como JPEG y extraer imágenes de documentos con Aspose.Words
  para Java
url: /es/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Save page as JPEG y Extraer Imágenes de Documentos en Aspose.Words for Java

En este tutorial descubrirá cómo **save page as jpeg** desde un documento Word y cómo **extract images from Word** archivos usando Aspose.Words for Java. Recorreremos escenarios del mundo real como establecer el brillo de la imagen, ajustar la resolución de la imagen en Java y crear un TIFF multipágina. Cada paso incluye fragmentos de código listos para ejecutar, para que pueda copiar, pegar y ver los resultados al instante.

## Respuestas rápidas
- **¿Puedo guardar una sola página como JPEG?** Sí – use `ImageSaveOptions` con `setPageSet(new PageSet(pageIndex))`.
- **¿Cómo cambio el brillo de la imagen?** Llama a `options.setImageBrightness(floatValue)` (rango 0‑1).
- **¿Qué pasa si necesito un TIFF multipágina?** Configura un `PageSet` que cubra las páginas deseadas y elige un método de compresión TIFF.
- **¿Cómo puedo controlar la resolución de la imagen?** Usa `setResolution(floatDpi)` o `setHorizontalResolution(floatDpi)`.
- **¿Necesito una licencia para producción?** Se requiere una licencia válida de Aspose.Words para uso que no sea de prueba.

## Qué es “save page as jpeg”
Guardar una página como JPEG significa convertir una sola página de un documento Word en un archivo de imagen raster (JPEG). Esto es útil para generar vistas previas, crear miniaturas o incrustar páginas de documentos en páginas web donde la renderización de PDF no es práctica.

## Por qué extraer imágenes de documentos Word
Muchos flujos de trabajo empresariales requieren extraer los gráficos originales (logotipos, diagramas, fotos) de un archivo DOCX para reutilizarlos, archivarlos o analizarlos. Aspose.Words facilita la extracción de cada imagen en su formato nativo sin perder calidad.

## Requisitos previos
- Java Development Kit (JDK 8 o posterior) instalado.
- Biblioteca Aspose.Words for Java añadida a su proyecto. Descárguela desde [here](https://releases.aspose.com/words/java/).
- Un documento Word de ejemplo (p. ej., `Rendering.docx`) colocado en un directorio conocido.

## Paso 1: Guardar imágenes como TIFF con control de umbral (Crear TIFF multipágina)
Para generar un TIFF en escala de grises y alto contraste, puede controlar el umbral de binarización. Esto es útil cuando necesita una versión imprimible en blanco y negro de su documento.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Paso 2: Guardar una página específica como TIFF multipágina
Si necesita un TIFF que contenga solo un subconjunto de páginas (p. ej., páginas 1‑2), configure un `PageSet`. Esto demuestra **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Paso 3: Guardar imágenes como PNG indexado de 1 BPP
Cuando necesite PNG en blanco y negro ultra ligeros (1 bit por píxel), establezca el formato de píxel correspondiente. Esto es útil para incrustar gráficos simples en escenarios de bajo ancho de banda.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Paso 4: Guardar una página como JPEG con personalización (Establecer brillo y resolución de la imagen)
Aquí **save page as jpeg** mientras ajustamos el brillo, el contraste y la resolución, perfecto para crear miniaturas o vistas previas listas para la web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Paso 5: Usar una devolución de llamada de guardado de página (Personalización avanzada)
Una devolución de llamada le permite renombrar cada archivo de salida dinámicamente, lo cual es útil al exportar muchas páginas a la vez.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Código fuente completo para todos los escenarios
A continuación hay una única clase que contiene cada método demostrado arriba. Puede ejecutar cada prueba individualmente.

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Problemas comunes y soluciones
- **“Unable to locate the document file”** – Verifique que la ruta del archivo use el separador correcto (`/` o `\\`) para su SO.
- **Images appear blank** – Asegúrese de establecer un `ImageColorMode` apropiado (p. ej., `GRAYSCALE` para TIFF).
- **Out‑of‑memory errors on large documents** – Procese las páginas en lotes ajustando el rango del `PageSet`.
- **JPEG quality looks poor** – Aumente la resolución con `setHorizontalResolution` o `setResolution`.

## Preguntas frecuentes

**Q: How do I change the image format when saving with Aspose.Words for Java?**  
A: Establezca el formato deseado en `ImageSaveOptions`. Para PNG, simplemente puede instanciar `ImageSaveOptions` y asignar `SaveFormat.PNG` si es necesario.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Can I customize the compression settings for TIFF images?**  
A: Sí. Use `setTiffCompression` para elegir un algoritmo de compresión como `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: How can I save a specific page from a document as a separate image?**  
A: Use el método `setPageSet` con un índice de página único.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: How do I apply custom settings to JPEG images when saving?**  
A: Ajuste propiedades como brillo, contraste y resolución mediante `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: How can I use a callback for customizing image saving?**  
A: Implemente `IPageSavingCallback` y asígnelo con `setPageSavingCallback`.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Conclusión
Ahora dispone de una caja de herramientas completa para **saving page as jpeg**, extraer imágenes, controlar el brillo de la imagen, establecer la resolución de la imagen en Java y crear archivos TIFF multipágina con Aspose.Words for Java. Experimente con diferentes configuraciones de `ImageSaveOptions` para adaptarlas a las necesidades de su proyecto y explore la API más amplia de Aspose.Words para obtener aún más capacidades de manipulación de documentos.

---

**Última actualización:** 2025-12-27  
**Probado con:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}