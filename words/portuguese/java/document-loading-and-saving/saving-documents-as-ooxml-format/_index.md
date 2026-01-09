---
date: 2026-01-09
description: Aprenda como criptografar docx com senha e alterar o nível de compressão
  ao salvar documentos no formato OOXML usando Aspose.Words para Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Criptografar docx com senha – salvar OOXML com Aspose.Words Java
url: /pt/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Criptografar docx com senha – salvar OOXML com Aspose.Words Java

## Introdução ao Salvamento de Documentos no Formato OOXML no Aspose.Words para Java

Neste guia, você aprenderá como **criptografar docx com senha** e salvar documentos no formato OOXML usando Aspose.Words para Java. OOXML (Office Open XML) é o formato de arquivo moderno usado pelo Microsoft Word e por muitas outras aplicações de escritório. Vamos percorrer as opções mais comuns — proteção por senha, níveis de conformidade, atualização de propriedades, tratamento de caracteres de controle legados e **como alterar o nível de compressão** — para que você possa adaptar a saída exatamente às suas necessidades.

## Respostas Rápidas
- **Como posso proteger um arquivo Word?** Use `OoxmlSaveOptions.setPassword("yourPassword")` antes de salvar.  
- **Qual nível de conformidade OOXML devo escolher?** ISO 29500 2008 Strict para máxima compatibilidade com versões modernas do Office.  
- **Posso manter caracteres de controle legados?** Sim, habilite `setKeepLegacyControlChars(true)`.  
- **Como altero o nível de compressão?** Defina `setCompressionLevel(CompressionLevel.SUPER_FAST)` ou `MAXIMUM` conforme necessário.  
- **Essas opções afetam o tamanho do arquivo?** O nível de compressão e o tratamento de caracteres legados podem mudar perceptivelmente o tamanho final do .docx.

## O que significa “encrypt docx with password”?
Criptografar um arquivo DOCX significa que o documento é salvo com criptografia AES‑256, exigindo uma senha para abri‑lo no Word ou em qualquer visualizador compatível. Isso é essencial para proteger informações confidenciais quando os arquivos são compartilhados por e‑mail, armazenamento em nuvem ou portais internos.

## Por que usar opções de salvamento OOXML?
- **Segurança:** A proteção por senha impede acesso não autorizado.  
- **Compatibilidade:** Configurações de conformidade garantem que o arquivo funcione em diferentes versões do Word.  
- **Desempenho:** Ajustar a compressão pode acelerar a gravação ou reduzir o tamanho do arquivo.  
- **Preservação:** Manter caracteres de controle legados preserva a fidelidade ao converter documentos mais antigos.

## Pré‑requisitos
- Biblioteca Aspose.Words para Java adicionada ao seu projeto (Maven/Gradle ou JAR manual).  
- Java 8 ou superior.  
- Um documento fonte (`.docx` ou `.doc`) que você deseja processar.

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

> **Dica profissional:** Escolha uma senha forte e armazene‑a com segurança; a senha não pode ser recuperada a partir do arquivo criptografado.

## Definindo a Conformidade OOXML

É possível especificar o nível de conformidade OOXML ao salvar o documento. Por exemplo, você pode defini‑lo como ISO 29500:2008 (Strict). Veja como:

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

Você pode optar por atualizar a propriedade “Last Saved Time” do documento ao salvá‑lo. Veja como:

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

Se o seu documento contém caracteres de controle legados, você pode escolher mantê‑los ao salvar. Veja como:

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

## Como Alterar o Nível de Compressão ao Salvar OOXML

É possível ajustar o nível de compressão ao salvar o documento. Por exemplo, você pode defini‑lo como `SUPER_FAST` para compressão mínima ou `MAXIMUM` para o menor tamanho de arquivo. Veja como:

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

Estas são algumas das principais opções e configurações que você pode usar ao salvar documentos no formato OOXML usando Aspose.Words para Java. Sinta‑se à vontade para explorar mais opções e personalizar seu processo de salvamento de documentos conforme necessário.

## Código‑Fonte Completo para Salvar Documentos no Formato OOXML no Aspose.Words para Java

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

Neste guia abrangente, exploramos como **criptografar docx com senha** e salvar documentos no formato OOXML usando Aspose.Words para Java. Seja para proteger seus arquivos, garantir conformidade OOXML estrita, atualizar propriedades do documento, preservar caracteres de controle legados ou **alterar o nível de compressão**, o Aspose.Words oferece um conjunto versátil de ferramentas para atender às suas necessidades.

## Perguntas Frequentes

**P: Como removo a proteção por senha de um documento protegido?**  
R: Abra o documento com a senha correta e, em seguida, salve‑o sem especificar uma senha em `OoxmlSaveOptions`. Isso cria uma cópia sem proteção.

**P: Posso definir propriedades personalizadas ao salvar um documento no formato OOXML?**  
R: Sim. Use `BuiltInDocumentProperties` e `CustomDocumentProperties` no objeto `Document` antes de chamar `save()`.

**P: Qual é o nível de compressão padrão ao salvar um documento no formato OOXML?**  
R: O padrão é `CompressionLevel.NORMAL`. Você pode mudar para `SUPER_FAST` para velocidade ou `MAXIMUM` para o menor tamanho de arquivo.

**P: Habilitar `keepLegacyControlChars` afeta a compatibilidade com versões modernas do Word?**  
R: O Word moderno pode abrir arquivos com caracteres de controle legados, mas alguns recursos antigos podem ser renderizados de forma diferente. Use essa opção somente quando precisar preservar o conteúdo original exatamente.

**P: É possível combinar várias opções de salvamento (ex.: senha + compressão) em uma única chamada?**  
R: Absolutamente. Configure todas as propriedades desejadas em uma única instância de `OoxmlSaveOptions` antes de passá‑la para `doc.save()`.

---

**Última atualização:** 2026-01-09  
**Testado com:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}