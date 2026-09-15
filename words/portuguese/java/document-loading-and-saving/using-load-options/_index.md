---
date: 2025-12-27
description: Aprenda a definir LoadOptions no Aspose.Words para Java, incluindo como
  especificar a pasta temporária, definir a versão do Word, converter metafiles em
  PNG e converter formas em matemática para um processamento flexível de documentos.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Como definir LoadOptions no Aspose.Words para Java
url: /pt/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Definir LoadOptions no Aspose.Words para Java

Neste tutorial vamos percorrer **como definir LoadOptions** para uma variedade de cenários reais ao trabalhar com Aspose.Words para Java. LoadOptions dão controle granular sobre a forma como um documento é aberto — seja para atualizar campos sujos, trabalhar com arquivos criptografados, converter formas para Office Math ou indicar à biblioteca onde armazenar dados temporários. Ao final, você poderá personalizar o comportamento de carregamento para atender exatamente aos requisitos da sua aplicação.

## Respostas Rápidas
- **O que é LoadOptions?** Um objeto de configuração que influencia como o Aspose.Words carrega um documento.  
- **Posso atualizar campos ao carregar?** Sim — defina `setUpdateDirtyFields(true)`.  
- **Como abrir um arquivo protegido por senha?** Passe a senha ao construtor do `LoadOptions`.  
- **É possível mudar a pasta temporária?** Use `setTempFolder("caminho")`.  
- **Qual método converte formas para Office Math?** `setConvertShapeToOfficeMath(true)`.

## Por Que Usar LoadOptions?
LoadOptions permitem evitar etapas de processamento pós‑carregamento, reduzir o uso de memória e garantir que o documento seja interpretado exatamente como você precisa. Por exemplo, converter metafiles para PNG durante o carregamento impede problemas de rasterização posteriores, e especificar a versão do MS Word ajuda a manter a fidelidade do layout ao lidar com arquivos legados.

## Pré‑requisitos
- Java 17 ou superior  
- Aspose.Words para Java (versão mais recente)  
- Uma licença válida da Aspose para uso em produção  

## Guia Passo a Passo

### Atualizar Campos Sujos

Quando um documento contém campos que foram editados mas não atualizados, você pode instruir o Aspose.Words a atualizá‑los automaticamente durante o carregamento.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*A chamada `setUpdateDirtyFields(true)` garante que quaisquer campos sujos sejam recalculados assim que o documento for aberto.*

### Carregar Documento Criptografado

Se o seu arquivo de origem estiver protegido por senha, forneça a senha ao criar a instância de `LoadOptions`. Você também pode definir uma nova senha ao salvar em um formato diferente.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Converter Forma para Office Math

Alguns documentos legados armazenam equações como formas de desenho. Habilitar esta opção converte essas formas em objetos nativos de Office Math, que são mais fáceis de editar posteriormente.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Definir Versão do MS Word

Especificar a versão alvo do Word ajuda a biblioteca a escolher as regras de renderização corretas, especialmente ao lidar com formatos de arquivo mais antigos.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Usar Pasta Temporária

Documentos grandes podem gerar arquivos temporários (por exemplo, ao extrair imagens). Você pode direcionar esses arquivos para uma pasta de sua escolha, o que é útil em ambientes sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback de Avisos

Durante o carregamento, o Aspose.Words pode gerar avisos (por exemplo, recursos não suportados). Implementar um callback permite registrar ou reagir a esses eventos.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Converter Metafiles para PNG

Metafiles como WMF podem ser rasterizadas para PNG durante o carregamento, garantindo renderização consistente em diferentes plataformas.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Código‑Fonte Completo para Trabalhar com Load Options no Aspose.Words para Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## Casos de Uso Comuns & Dicas

- **Pipelines de conversão em lote** – Combine `setTempFolder` com um job agendado para processar centenas de arquivos sem encher o diretório temporário do sistema.  
- **Migração de documentos legados** – Use `setMswVersion` junto com `setConvertShapeToOfficeMath` para levar documentos de engenharia antigos para um formato moderno, preservando as equações.  
- **Manipulação segura de documentos** – Combine `loadEncryptedDocument` com `OdtSaveOptions` para re‑criptografar arquivos com uma nova senha em um formato diferente.  

## Perguntas Frequentes

**P: Como posso tratar avisos durante o carregamento do documento?**  
R: Implemente um `IWarningCallback` personalizado (conforme mostrado no exemplo *Callback de Avisos*) e registre‑o via `loadOptions.setWarningCallback(...)`. Isso permite registrar, ignorar ou abortar com base na gravidade do aviso.

**P: Posso converter formas para objetos Office Math ao carregar um documento?**  
R: Sim — chame `loadOptions.setConvertShapeToOfficeMath(true)` antes de construir o `Document`. A biblioteca substituirá automaticamente as formas compatíveis por objetos nativos de Office Math.

**P: Como especificar a versão do MS Word para o carregamento do documento?**  
R: Use `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (ou qualquer outro valor do enum) para indicar ao Aspose.Words quais regras de renderização do Word aplicar.

**P: Qual é a finalidade do método `setTempFolder` em LoadOptions?**  
R: Ele direciona todos os arquivos temporários gerados durante o carregamento (como imagens extraídas) para uma pasta que você controla, essencial em ambientes com diretórios temporários restritos.

**P: É possível converter metafiles como WMF para PNG durante o carregamento?**  
R: Absolutamente — habilite com `loadOptions.setConvertMetafilesToPng(true)`. Isso garante que imagens rasterizadas sejam armazenadas como PNG, melhorando a compatibilidade com visualizadores modernos.

## Conclusão

Cobremos as técnicas essenciais para **como definir LoadOptions** no Aspose.Words para Java, desde atualizar campos sujos até lidar com arquivos criptografados, converter formas, especificar a versão do Word, direcionar armazenamento temporário e muito mais. Ao aproveitar essas opções, você pode construir pipelines de processamento de documentos robustos e de alto desempenho que se adaptam a uma ampla variedade de cenários de entrada.

---

**Última atualização:** 2025-12-27  
**Testado com:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}