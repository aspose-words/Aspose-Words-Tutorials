---
date: '2026-02-06'
description: Aprenda como carregar HTML VML com Aspose.Words para Java, criptografar
  arquivos HTML Java, definir a URI base do HTML e configurar opções de controle HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Carregar HTML VML usando Aspose.Words para Java – Guia Completo
url: /pt/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Recursos Abrangentes de HTML com Aspose.Words para Java: Um Guia para Desenvolvedores

## Introdução

Navegar pelo complexo mundo do processamento de documentos pode ser assustador, especialmente ao lidar com vários recursos de HTML. Seja lidando com suporte a Vector Markup Language (VML), documentos criptografados ou comportamentos específicos de importação de HTML, **Aspose.Words for Java** oferece uma solução robusta. Neste guia, você aprenderá **how to load html vml** de forma eficiente e segura, além de abordar tarefas relacionadas como **encrypt html java**, **set html base uri** e opções de **configure html control**.

**O que você aprenderá:**
- Como carregar documentos HTML com suporte a VML.
- Técnicas para lidar com HTML de página fixa e avisos.
- Métodos para criptografar e carregar documentos HTML protegidos por senha.
- Utilizando URIs base nas Opções de Carregamento de HTML.
- Importando elementos de entrada HTML como tags de documento estruturado ou campos de formulário.
- Ignorando elementos `<noscript>` durante o carregamento de HTML.
- Configurando modos de importação de blocos para controlar a preservação da estrutura HTML.
- Suportando regras `@font-face` para fontes personalizadas.

## Respostas Rápidas
- **Qual é a forma principal de habilitar VML ao carregar HTML?** Defina `loadOptions.setSupportVml(true)`.
- **Posso carregar arquivos HTML protegidos por senha?** Sim, passe a senha para `HtmlLoadOptions`.
- **Como resolvo caminhos relativos de imagens?** Use `loadOptions.setBaseUri("your/base/uri")`.
- **É possível importar `<select>` como um campo de formulário?** Defina `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Qual classe captura avisos durante o carregamento?** Implemente `IWarningCallback` e atribua-a a `loadOptions.setWarningCallback(...)`.

## Pré-requisitos

Antes de começarmos a implementar vários recursos de HTML com Aspose.Words para Java, certifique-se de que seu ambiente está configurado corretamente:

- **Bibliotecas Necessárias:** Você precisa da biblioteca Aspose.Words versão 25.3 ou posterior.
- **Ambiente de Desenvolvimento:** Este guia assume que você está usando Maven ou Gradle para gerenciamento de dependências.
- **Base de Conhecimento:** Um entendimento básico de Java e familiaridade com documentos HTML será benéfico.

## Configurando Aspose.Words

Para começar a trabalhar com Aspose.Words, primeiro você precisa incluí-lo em seu projeto. Abaixo estão os passos para configurar a biblioteca usando Maven e Gradle:

### Maven

Adicione a seguinte dependência ao seu arquivo `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Inclua isto no seu arquivo `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Aquisição de Licença

Aspose.Words requer uma licença para funcionalidade completa. Você pode obter um teste gratuito, solicitar uma licença temporária ou comprar uma permanente. Visite a [página de compra](https://purchase.aspose.com/buy) para mais detalhes.

Para inicializar o Aspose.Words em seu projeto Java, certifique-se de que a licença está configurada corretamente:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Guia de Implementação

Dividiremos a implementação em seções com base nos recursos que desejamos implementar.

### Como carregar html vml com Aspose.Words

**Visão geral:** Carregar um documento HTML com suporte a VML permite renderização versátil de gráficos vetoriais, como diagramas e formas. Esta é a etapa central para a palavra‑chave principal **load html vml**.

#### Step‑by‑step

1. **Configurar Opções de Carregamento**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Carregar o Documento**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Verificar Tipo de Imagem**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Carregar HTML Fixo e Tratar Avisos

**Visão geral:** Carregar documentos HTML de página fixa pode gerar avisos que precisam ser gerenciados para um processamento preciso.

#### Step‑by‑step

1. **Definir Callback de Aviso**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Configurar Opções de Carregamento**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Carregar Documento e Verificar Avisos**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Criptografar Documentos HTML

**Visão geral:** Criptografar um documento HTML com uma senha garante acesso seguro, o que é essencial para informações sensíveis — isso aborda o cenário **encrypt html java**.

#### Step‑by‑step

1. **Preparar Opções de Assinatura Digital**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Assinar e Criptografar o Documento**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Carregar Documento Criptografado**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### URI Base para Opções de Carregamento de HTML

**Visão geral:** Especificar um **set html base uri** ajuda a resolver URIs relativos, especialmente ao lidar com imagens ou outros recursos vinculados.

#### Step‑by‑step

1. **Configurar Opções de Carregamento com URI Base**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Carregar Documento e Verificar Imagem**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Importar `<select>` HTML como Tag de Documento Estruturado

**Visão geral:** Para **configure html control**, você pode importar elementos `<select>` como Tags de Documento Estruturado, proporcionando controle mais refinado sobre campos de formulário dentro de documentos Word.

#### Step‑by‑step

1. **Definir Tipo de Controle Preferido**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Carregar Documento e Verificar Estrutura**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Problemas Comuns e Soluções

| Problema | Motivo | Correção |
|----------|--------|----------|
| Gráficos VML não aparecem | `supportVml` flag left as default (`false`) | Certifique-se de chamar `loadOptions.setSupportVml(true)` antes de carregar. |
| Imagens ausentes após o carregamento | Caminhos relativos não podem ser resolvidos | Use **set html base uri** (`loadOptions.setBaseUri(...)`) para apontar para a pasta correta. |
| HTML protegido por senha gera exceção | Senha não fornecida | Passe a senha para `new HtmlLoadOptions("yourPassword")`. |
| Controles de formulário aparecem como texto simples | `HtmlControlType` errado | Defina `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` ou `FormField` conforme necessário. |
| Avisos inesperados | Elementos HTML não tratados | Implemente `IWarningCallback` para capturar e revisar avisos. |

## Perguntas Frequentes

**Q: Posso carregar arquivos HTML que contenham tanto VML quanto gráficos SVG modernos?**  
A: Sim. Habilite VML com `setSupportVml(true)`; SVG é tratado automaticamente pelo Aspose.Words.

**Q: Como criptografo um documento HTML sem usar um certificado digital?**  
A: Use o construtor `HtmlLoadOptions` que aceita uma senha e salve o documento com `Document.save(..., SaveFormat.HTML)` após definir a senha.

**Q: O que acontece se a URI base apontar para uma pasta inexistente?**  
A: Aspose.Words lançará um `FileNotFoundException` para recursos ausentes. Verifique o caminho antes de carregar.

**Q: É possível alterar o tipo de controle padrão para todos os elementos de formulário HTML?**  
A: Sim. Use `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` para aplicá-lo globalmente.

**Q: Callbacks de aviso são thread‑safe?**  
A: A implementação do callback deve ser thread‑safe se você planeja carregar documentos simultaneamente. Use coleções sincronizadas ou armazenamento thread‑local.

---

**Última atualização:** 2026-02-06  
**Testado com:** Aspose.Words for Java 25.3  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}