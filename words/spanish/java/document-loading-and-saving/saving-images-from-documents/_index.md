---
"description": "Aprende a guardar imágenes de documentos con Aspose.Words para Java con nuestra completa guía paso a paso. Personaliza formatos, compresión y más."
"linktitle": "Guardar imágenes de documentos"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Guardar imágenes de documentos en Aspose.Words para Java"
"url": "/es/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Guardar imágenes de documentos en Aspose.Words para Java


## Introducción al guardado de imágenes desde documentos en Aspose.Words para Java

En este tutorial, exploraremos cómo guardar imágenes de documentos con Aspose.Words para Java. Abordaremos diversos escenarios y opciones de personalización para guardar imágenes. Esta guía proporciona instrucciones paso a paso con ejemplos de código fuente.

## Prerrequisitos

Antes de comenzar, asegúrese de tener la biblioteca Aspose.Words para Java integrada en su proyecto. Puede descargarla desde [aquí](https://releases.aspose.com/words/java/).

## Paso 1: Guardar imágenes como TIFF con control de umbral

Para guardar imágenes en formato TIFF con control de umbral, siga estos pasos:

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

Para guardar una página específica como un TIFF de varias páginas, utilice el siguiente código:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Paso 3: Guardar imágenes como PNG indexado de 1 BPP

Para guardar imágenes como PNG indexado de 1 BPP, siga estos pasos:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Paso 4: Guardar una página como JPEG con personalización

Para guardar una página específica como JPEG con opciones de personalización, use este código:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Paso 5: Uso de la devolución de llamada para guardar la página

Puedes usar una devolución de llamada para personalizar el guardado de la página. Aquí tienes un ejemplo:

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

## Código fuente completo para guardar imágenes de documentos en Aspose.Words para Java

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
	// Establezca "PageSet" en "0" para convertir solo la primera página de un documento.
	options.setPageSet(new PageSet(0));
	// Cambiar el brillo y el contraste de la imagen.
	// Ambos están en una escala de 0 a 1 y están en 0,5 por defecto.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Cambiar la resolución horizontal.
	// El valor predeterminado para estas propiedades es 96.0, para una resolución de 96 ppp.
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

## Conclusión

Ha aprendido a guardar imágenes de documentos con Aspose.Words para Java. Estos ejemplos muestran diversas opciones de personalización para guardar imágenes, como el formato, la compresión y el uso de devoluciones de llamada. Explore más posibilidades con las potentes funciones de Aspose.Words para Java.

## Preguntas frecuentes

### ¿Cómo cambio el formato de imagen al guardar con Aspose.Words para Java?

Puede cambiar el formato de la imagen especificando el formato deseado en el `ImageSaveOptions`Por ejemplo, para guardar como PNG, utilice `SaveFormat.PNG` como se muestra en el código:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### ¿Puedo personalizar la configuración de compresión para las imágenes TIFF?

Sí, puedes personalizar la configuración de compresión de imágenes TIFF. Por ejemplo, para configurar el método de compresión en CCITT_3, usa el siguiente código:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### ¿Cómo puedo guardar una página específica de un documento como una imagen separada?

Para guardar una página específica como imagen, utilice el `setPageSet` método en `ImageSaveOptions`Por ejemplo, para guardar solo la primera página, configure el `PageSet` a `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Guardar la primera página como imagen
```

### ¿Cómo puedo aplicar configuraciones personalizadas a las imágenes JPEG al guardarlas?

Puede aplicar configuraciones personalizadas a las imágenes JPEG usando `ImageSaveOptions`Ajuste propiedades como el brillo, el contraste y la resolución. Por ejemplo, para cambiar el brillo a 0,3 y el contraste a 0,7, use este código:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### ¿Cómo puedo utilizar una devolución de llamada para personalizar el guardado de imágenes?

Para utilizar una devolución de llamada para personalizar el guardado de imágenes, configure el `PageSavengCallback` in `ImageSaveOptions`. Crea una clase que implemente el `IPageSavingCallback` interfaz y anular la `pageSaving` método.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Luego, crea una clase que implemente el `IPageSavingCallback` interfaz y personalizar el nombre del archivo y la ubicación en el `pageSaving` método.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}