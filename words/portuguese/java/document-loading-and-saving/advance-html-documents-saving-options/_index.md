---
"description": "Neste tutorial, abordamos várias opções avançadas para salvar documentos HTML com o Aspose.Words para Java. Essas opções permitem que você crie HTML de alta qualidade."
"linktitle": "Salvando documentos HTML com"
"second_title": "API de processamento de documentos Java Aspose.Words"
"title": "Opções avançadas para salvar documentos HTML com Aspose.Words Java"
"url": "/pt/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Opções avançadas para salvar documentos HTML com Aspose.Words Java


Neste tutorial, exploraremos as opções avançadas de salvamento de documentos HTML fornecidas pelo Aspose.Words para Java. O Aspose.Words é uma API Java poderosa para trabalhar com documentos do Word e oferece uma ampla gama de recursos para manipulação e conversão de documentos.

## 1. Introdução
O Aspose.Words para Java permite que você trabalhe com documentos do Word programaticamente. Neste tutorial, vamos nos concentrar nas opções avançadas de salvamento de documentos HTML, que permitem controlar como os documentos do Word são convertidos para HTML.

## 2. Exportar informações de ida e volta
O `exportRoundtripInformation` Este método permite exportar documentos do Word para HTML, preservando as informações de ida e volta. Essas informações podem ser úteis quando você deseja converter HTML de volta para o formato Word sem perder nenhum detalhe específico do documento.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Exportar fontes como Base64
Com o `exportFontsAsBase64` Com este método, você pode exportar as fontes usadas no documento como dados codificados em Base64 no HTML. Isso garante que a representação HTML mantenha os mesmos estilos de fonte do documento original do Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Exportar Recursos
O `exportResources` O método permite especificar o tipo de folha de estilo CSS e exportar recursos de fonte. Você também pode definir uma pasta de recursos e um alias para recursos no HTML.

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/recursos");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. Converta metarquivos para EMF ou WMF
O `convertMetafilesToEmfOrWmf` O método permite que você converta metarquivos no documento para o formato EMF ou WMF, garantindo compatibilidade e renderização suave em HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Ponto vermelho\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Converter metarquivos para SVG
Use o `convertMetafilesToSvg` Método para converter metarquivos para o formato SVG. Este formato é ideal para exibir gráficos vetoriais em documentos HTML.

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

## 7. Adicionar prefixo de nome de classe CSS
Com o `addCssClassNamePrefix` Com o método, você pode adicionar um prefixo aos nomes de classes CSS no HTML exportado. Isso ajuda a evitar conflitos com estilos existentes.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Exportar URLs CID para recursos MHTML
O `exportCidUrlsForMhtmlResources` O método é usado ao salvar documentos no formato MHTML. Ele permite exportar URLs de Content-ID para recursos.

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

## 9. Resolver nomes de fontes
O `resolveFontNames` O método ajuda a resolver nomes de fontes ao salvar documentos no formato HTML, garantindo uma renderização consistente em diferentes plataformas.

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

## 10. Exportar campo de formulário de entrada de texto como texto
O `exportTextInputFormFieldAsText` O método exporta campos de formulário como texto simples no HTML, tornando-os facilmente legíveis e editáveis.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// pasta especificada precisa existir e deve estar vazia.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Defina uma opção para exportar campos de formulário como texto simples, não como elementos de entrada HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Conclusão
Neste tutorial, exploramos as opções avançadas de salvamento de documentos HTML fornecidas pelo Aspose.Words para Java. Essas opções oferecem um controle preciso sobre o processo de conversão, permitindo criar documentos HTML muito semelhantes aos documentos originais do Word.

## Perguntas frequentes
Aqui estão algumas perguntas frequentes sobre como trabalhar com o Aspose.Words para opções de salvamento de documentos Java e HTML:

### P1: Como posso converter HTML de volta para o formato Word usando o Aspose.Words para Java?
Para converter HTML de volta para o formato Word, você pode usar a API Aspose.Words `load` método para carregar o documento HTML e salvá-lo no formato Word.

### P2: Posso personalizar os estilos CSS ao exportar para HTML?
Sim, você pode personalizar os estilos CSS modificando as folhas de estilo usadas no HTML ou usando o `addCssClassNamePrefix` método para adicionar um prefixo aos nomes de classes CSS.

### Q3: Existe uma maneira de otimizar a saída HTML para exibição na web?
Sim, você pode otimizar a saída HTML para exibição na web configurando opções como exportar fontes como Base64 e converter metarquivos para SVG.

### P4: Há alguma limitação ao converter documentos complexos do Word para HTML?
Embora o Aspose.Words para Java forneça recursos de conversão poderosos, documentos complexos do Word com layouts intrincados podem exigir pós-processamento adicional para obter a saída HTML desejada.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}