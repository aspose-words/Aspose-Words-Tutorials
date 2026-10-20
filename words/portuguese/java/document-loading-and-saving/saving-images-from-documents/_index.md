---
date: 2025-12-27
description: Aprenda como salvar a página como JPEG e extrair imagens de documentos
  Word usando Aspose.Words for Java. Inclui dicas para definir o brilho da imagem,
  a resolução e criar TIFF multipágina.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Como salvar página como JPEG e extrair imagens de documentos com Aspose.Words
  para Java
url: /pt/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Salvar página como JPEG e Extrair Imagens de Documentos no Aspose.Words para Java

Neste tutorial você descobrirá como **save page as jpeg** de um documento Word e como **extract images from Word** usando Aspose.Words para Java. Vamos percorrer cenários reais, como definir o brilho da imagem, ajustar a resolução da imagem em Java e criar um TIFF multipágina. Cada etapa inclui trechos de código prontos para execução, para que você possa copiar, colar e ver os resultados instantaneamente.

## Quick Answers
- **Posso salvar uma única página como JPEG?** Sim – use `ImageSaveOptions` com `setPageSet(new PageSet(pageIndex))`.
- **Como altero o brilho da imagem?** Chame `options.setImageBrightness(floatValue)` (faixa de 0‑1).
- **E se eu precisar de um TIFF multipágina?** Defina um `PageSet` que cubra as páginas desejadas e escolha um método de compressão TIFF.
- **Como posso controlar a resolução da imagem?** Use `setResolution(floatDpi)` ou `setHorizontalResolution(floatDpi)`.
- **Preciso de uma licença para produção?** Uma licença válida do Aspose.Words é necessária para uso que não seja de avaliação.

## O que é “save page as jpeg”?
Salvar uma página como JPEG significa converter uma única página de um documento Word em um arquivo de imagem raster (JPEG). Isso é útil para geração de pré‑visualizações, criação de miniaturas ou incorporação de páginas de documentos em páginas web onde a renderização de PDF não é prática.

## Por que extrair imagens de documentos Word?
Muitos fluxos de trabalho empresariais exigem a extração dos gráficos originais (logotipos, diagramas, fotos) de um arquivo DOCX para reutilização, arquivamento ou análise. Aspose.Words facilita a extração de cada imagem em seu formato nativo sem perda de qualidade.

## Pré‑requisitos
- Java Development Kit (JDK 8 ou superior) instalado.
- Biblioteca Aspose.Words for Java adicionada ao seu projeto. Baixe-a a partir de [here](https://releases.aspose.com/words/java/).
- Um documento Word de exemplo (por exemplo, `Rendering.docx`) colocado em um diretório conhecido.

## Etapa 1: Salvar Imagens como TIFF com Controle de Limiar (Criar TIFF Multipágina)
Para gerar um TIFF em escala de cinza e alto contraste, você pode controlar o limiar de binarização. Isso é útil quando você precisa de uma versão imprimível em preto‑e‑branco do seu documento.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Etapa 2: Salvar uma Página Específica como TIFF Multipágina
Se você precisar de um TIFF que contenha apenas um subconjunto de páginas (por exemplo, páginas 1‑2), configure um `PageSet`. Isso demonstra **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Etapa 3: Salvar Imagens como PNG Indexado de 1 BPP
Quando você precisar de PNGs preto‑e‑branco ultra‑leve (1 bit por pixel), defina o formato de pixel adequadamente. Isso é útil para incorporar gráficos simples em cenários de baixa largura de banda.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Etapa 4: Salvar uma Página como JPEG com Personalização (Definir Brilho e Resolução da Imagem)
Aqui nós **save page as jpeg** enquanto ajustamos brilho, contraste e resolução — perfeito para criar miniaturas ou pré‑visualizações prontas para a web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Etapa 5: Usando um Callback de Salvamento de Página (Personalização Avançada)
Um callback permite renomear cada arquivo de saída dinamicamente, o que é útil ao exportar muitas páginas de uma só vez.

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

## Código‑Fonte Completo para Todos os Cenários
Abaixo está uma única classe que contém todos os métodos demonstrados acima. Você pode executar cada teste individualmente.

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

## Problemas Comuns e Soluções
- **“Unable to locate the document file”** – Verifique se o caminho do arquivo usa o separador correto (`/` ou `\\`) para o seu SO.
- **Images appear blank** – Certifique-se de definir um `ImageColorMode` apropriado (por exemplo, `GRAYSCALE` para TIFF).
- **Out‑of‑memory errors on large documents** – Processar páginas em lotes ajustando o intervalo do `PageSet`.
- **JPEG quality looks poor** – Aumente a resolução com `setHorizontalResolution` ou `setResolution`.

## Perguntas Frequentes

**Q: Como altero o formato da imagem ao salvar com Aspose.Words para Java?**  
A: Defina o formato desejado em `ImageSaveOptions`. Para PNG, você pode simplesmente instanciar `ImageSaveOptions` e atribuir `SaveFormat.PNG` se necessário.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Posso personalizar as configurações de compressão para imagens TIFF?**  
A: Sim. Use `setTiffCompression` para escolher um algoritmo de compressão como `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Como posso salvar uma página específica de um documento como uma imagem separada?**  
A: Use o método `setPageSet` com um índice de página único.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Como aplico configurações personalizadas a imagens JPEG ao salvar?**  
A: Ajuste propriedades como brilho, contraste e resolução via `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Como posso usar um callback para personalizar a gravação de imagens?**  
A: Implemente `IPageSavingCallback` e atribua-o com `setPageSavingCallback`.

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

## Conclusão
Agora você tem um conjunto completo de ferramentas para **saving page as jpeg**, extrair imagens, controlar o brilho da imagem, definir a resolução da imagem em Java e criar arquivos TIFF multipágina com Aspose.Words para Java. Experimente diferentes configurações de `ImageSaveOptions` para atender às necessidades do seu projeto e explore a API mais ampla do Aspose.Words para ainda mais recursos de manipulação de documentos.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}