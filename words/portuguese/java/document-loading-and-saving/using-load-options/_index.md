---
title: Usando opções de carregamento em Aspose.Words para Java
linktitle: Usando opções de carga
second_title: API de processamento de documentos Java Aspose.Words
description: Dominando as opções de carregamento no Aspose.Words para Java. Personalize o carregamento de documentos, manipule a criptografia, converta formas, defina versões do Word e muito mais para processamento eficiente de documentos Java.
weight: 11
url: /pt/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usando opções de carregamento em Aspose.Words para Java


## Introdução ao trabalho com opções de carga no Aspose.Words para Java

Neste tutorial, exploraremos como trabalhar com Load Options no Aspose.Words para Java. Load Options permite que você personalize como os documentos são carregados e processados. Abordaremos vários cenários, incluindo atualização de campos sujos, carregamento de documentos criptografados, conversão de formas para o Office Math, configuração da versão do MS Word, especificação de uma pasta temporária, tratamento de avisos e conversão de metarquivos para PNG. Vamos mergulhar passo a passo.

## Atualizar Campos Sujos

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Este trecho de código demonstra como atualizar campos sujos em um documento. O`setUpdateDirtyFields(true)` O método é usado para garantir que campos sujos sejam atualizados durante o carregamento do documento.

## Carregar documento criptografado

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Aqui, carregamos um documento criptografado usando uma senha. O`LoadOptions` O construtor aceita a senha do documento e você também pode especificar uma nova senha ao salvar o documento usando`OdtSaveOptions`.

## Converter Forma em Matemática de Escritório

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Este código demonstra como converter formas em objetos do Office Math durante o carregamento do documento. O`setConvertShapeToOfficeMath(true)`método permite essa conversão.

## Definir versão do MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Você pode especificar a versão do MS Word para carregamento do documento. Neste exemplo, definimos a versão para Microsoft Word 2010 usando`setMswVersion`.

## Usar pasta temporária

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Ao definir a pasta temporária usando`setTempFolder`, você pode controlar onde os arquivos temporários são armazenados durante o processamento do documento.

## Aviso de retorno de chamada

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Lide com os avisos conforme eles surgem durante o carregamento do documento.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Este código demonstra como configurar um callback de aviso para manipular avisos durante o carregamento de documentos. Você pode personalizar o comportamento do seu aplicativo quando os avisos ocorrerem.

## Converter Metafiles para PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Para converter metarquivos (por exemplo, WMF) em imagens PNG durante o carregamento do documento, você pode usar o`setConvertMetafilesToPng(true)` método.

## Código-fonte completo para trabalhar com opções de carga em Aspose.Words para Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Crie um novo objeto LoadOptions, que carregará documentos de acordo com a especificação do MS Word 2019 por padrão
	// e altere a versão de carregamento para o Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//Imprime avisos e seus detalhes conforme eles surgem durante o carregamento do documento.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Conclusão

Neste tutorial, nos aprofundamos em vários aspectos do trabalho com Load Options no Aspose.Words para Java. Load Options desempenha um papel crucial na personalização de como os documentos são carregados e processados, permitindo que você adapte seu processamento de documentos às suas necessidades específicas. Vamos recapitular os pontos-chave abordados neste guia:

## Perguntas frequentes

### Como posso lidar com avisos durante o carregamento de documentos?

 Você pode configurar um retorno de chamada de aviso conforme mostrado na`warningCallback()` método acima. Personalize o`DocumentLoadingWarningCallback` classe para manipular avisos de acordo com os requisitos do seu aplicativo.

### Posso converter formas em objetos do Office Math ao carregar um documento?

 Sim, você pode converter formas em objetos do Office Math usando`loadOptions.setConvertShapeToOfficeMath(true)`.

### Como especifico a versão do MS Word para carregamento de documentos?

 Usar`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` para especificar a versão do MS Word para carregamento do documento.

###  Qual é o propósito do`setTempFolder` method in Load Options?

 O`setTempFolder` método permite que você especifique a pasta onde os arquivos temporários são armazenados durante o processamento do documento.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
