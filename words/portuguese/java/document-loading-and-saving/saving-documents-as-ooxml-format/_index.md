---
date: 2025-12-29
description: Aprenda a criptografar arquivos docx com senha usando as opções de salvamento
  do Aspose.Words para Java. Proteja, otimize e personalize seus arquivos OOXML sem
  esforço.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Como criptografar DOCX com senha usando Aspose.Words para Java
url: /pt/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Como Criptografar DOCX com Senha Usando Aspose.Words para Java

Neste guia você descobrirá **como criptografar docx com senha** ao salvar documentos no formato OOXML usando Aspose.Words para Java. Seja protegendo relatórios confidenciais ou garantindo rascunhos de contratos, os passos abaixo mostram exatamente como aplicar proteção por senha e ajustar finamente outras opções de salvamento OOXML.

## Respostas Rápidas
- **Posso criptografar um arquivo DOCX com senha?** Sim, use `OoxmlSaveOptions.setPassword()` antes de salvar.  
- **Qual classe controla as configurações de salvamento OOXML?** `OoxmlSaveOptions` (parte do Aspose.Words).  
- **Preciso de licença para proteção por senha?** Uma licença válida do Aspose.Words é necessária para uso em produção.  
- **Posso combinar criptografia com configurações de conformidade?** Absolutamente – defina tanto `setPassword` quanto `setCompliance` na mesma instância de `OoxmlSaveOptions`.  
- **Quais níveis de compressão estão disponíveis?** `NORMAL`, `SUPER_FAST` e `MAXIMUM` via `CompressionLevel`.

## O que é “encrypt docx with password”?
Criptografar um arquivo DOCX significa que o conteúdo do arquivo é armazenado de forma criptografada e só pode ser aberto após a inserção da senha correta. Isso protege informações sensíveis contra acesso não autorizado, permitindo que as ferramentas padrão do Word abram o arquivo uma vez que a senha seja fornecida.

## Por que usar as opções de salvamento do Aspose.Words para criptografia?
Aspose.Words oferece um conjunto rico de **aspose words save options** que permitem controlar não apenas a criptografia, mas também níveis de conformidade, compressão e tratamento de caracteres legados — tudo a partir de código Java. Isso elimina a necessidade de pós‑processamento manual ou ferramentas de terceiros.

## Pré-requisitos
- Java Development Kit (JDK 8 ou superior)  
- Biblioteca Aspose.Words for Java adicionada ao seu projeto (Maven/Gradle ou JAR)  
- Uma licença válida do Aspose.Words para produção (opcional para avaliação)

## Salvando um Documento com Criptografia por Senha

Você pode criptografar seu documento com uma senha ao salvá‑lo no formato OOXML. Veja como fazer:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

## Definindo Conformidade OOXML

Você pode especificar o nível de conformidade OOXML ao salvar o documento. Por exemplo, pode defini‑lo como ISO 29500:2008 (Strict). Veja como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Atualizando a Propriedade “Last Saved Time”

Você pode optar por atualizar a propriedade "Last Saved Time" do documento ao salvá‑lo. Veja como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Mantendo Caracteres de Controle Legados

Se o seu documento contém caracteres de controle legados, você pode optar por mantê‑los ao salvar. Veja como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Definindo Nível de Compressão

Você pode ajustar o nível de compressão ao salvar o documento. Por exemplo, pode defini‑lo como **SUPER_FAST** para compressão mínima. Veja como:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Estas são algumas das principais opções e configurações que você pode usar ao salvar documentos no formato OOXML usando Aspose.Words para Java. Sinta‑se à vontade para explorar mais opções e personalizar o processo de salvamento de documentos conforme necessário.

## Código‑Fonte Completo para Salvar Documentos no Formato OOXML em Aspose.Words para Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Conclusão

Neste guia abrangente, exploramos como **encrypt docx with password** e ajustar finamente uma variedade de opções de salvamento OOXML usando Aspose.Words para Java. Seja para proteger conteúdo confidencial, atender a rigorosas conformidades ISO, preservar caracteres legados ou controlar a compressão, a biblioteca oferece controle granular através da mesma API `OoxmlSaveOptions`.

## Perguntas Frequentes

**Q: Como remover a proteção por senha de um documento protegido por senha?**  
A: Abra o documento com a senha correta, depois salve‑lo novamente sem chamar `setPassword`. O novo arquivo ficará desprotegido.

**Q: Posso definir propriedades personalizadas ao salvar um documento no formato OOXML?**  
A: Sim. Use `BuiltInDocumentProperties` ou `CustomDocumentProperties` no objeto `Document` antes de chamar `save`.

**Q: Qual é o nível de compressão padrão ao salvar um documento no formato OOXML?**  
A: O padrão é `NORMAL`. Você pode mudar para `SUPER_FAST` para velocidade ou `MAXIMUM` para tamanho de arquivo menor.

**Q: As opções de aspose words save funcionam com versões mais antigas do Word?**  
A: Sim. Ajustando `MsWordVersion` e as configurações de conformidade, você pode direcionar o Word 2007‑2019 e garantir compatibilidade.

**Q: É possível combinar múltiplas opções de salvamento em uma única operação?**  
A: Absolutamente. Crie uma instância de `OoxmlSaveOptions`, defina todas as propriedades desejadas (senha, conformidade, compressão, etc.) e passe‑a para `doc.save()`.

---

**Última Atualização:** 2025-12-29  
**Testado com:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}