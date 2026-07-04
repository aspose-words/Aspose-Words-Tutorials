---
category: general
date: 2026-05-30
description: Aprenda a criar documentos compatíveis com PDF/UA-2 usando Aspose.Words
  para Java. Exporte Word para PDF acessível com código passo a passo.
draft: false
keywords:
- create pdf/ua‑2 compliant document
- export word to accessible pdf
language: pt
og_description: Crie documento compatível com PDF/UA-2 usando Aspose.Words para Java.
  Este guia mostra exatamente como exportar Word para PDF acessível.
og_title: Criar Documento Compatível com PDF/UA-2 – Tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to create PDF/UA-2 compliant document using Aspose.Words
    for Java. Export Word to accessible PDF with step‑by‑step code.
  headline: Create PDF/UA-2 Compliant Document – Complete Java Guide
  type: TechArticle
- description: Learn how to create PDF/UA-2 compliant document using Aspose.Words
    for Java. Export Word to accessible PDF with step‑by‑step code.
  name: Create PDF/UA-2 Compliant Document – Complete Java Guide
  steps:
  - name: Prerequisites
    text: '- Java 17 (or any recent JDK) installed on your machine. - Maven or Gradle
      to manage dependencies (we’ll show the Maven snippet). - A Word document (`.docx`)
      you want to make accessible. - An active Aspose.Words for Java license (the
      free trial works for testing).'
  - name: Expected Output
    text: 'When you run the program, the console prints:'
  - name: 1. Missing Fonts
    text: 'If the source Word uses a font that isn’t installed on the server, Aspose.Words
      will substitute it, which can break accessibility. To pre‑empt this:'
  - name: 2. Custom Tags or Alt Text
    text: Images without `alt` text will be marked as decorative, which is fine for
      purely decorative graphics but not for informative ones. Ensure your Word document
      includes meaningful alt text before conversion.
  - name: 3. Large Documents
    text: For multi‑hundred‑page reports, you might hit memory limits. Use `Document.save(OutputStream,
      SaveOptions)` with a streaming approach, or split the document into sections
      before conversion.
  - name: 4. Document Permissions
    text: 'If you need to lock down editing after conversion, add:'
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF/UA-2
- Accessibility
title: Criar Documento Compatível com PDF/UA-2 – Guia Completo de Java
url: /pt/java/document-conversion-and-export/create-pdf-ua-2-compliant-document-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Compatível com PDF/UA-2 – Guia Completo em Java

Já precisou **criar um documento compatível com PDF/UA-2** a partir de um arquivo Word, mas não tinha certeza de qual chamada de API faria o trabalho pesado? Você não está sozinho. Normas de acessibilidade como PDF/UA‑2 podem parecer um labirinto, especialmente quando você está lidando com conversão de documentos em um projeto Java.

A verdade é que o Aspose.Words for Java torna todo o processo quase indolor. Neste tutorial, vamos percorrer tudo o que você precisa para **exportar Word para PDF acessível**, desde o carregamento do `.docx` de origem até o ajuste das opções de salvamento para total conformidade com PDF/UA‑2. Ao final, você terá um trecho pronto para uso que pode ser inserido em qualquer projeto Maven ou Gradle.

## O que você aprenderá

- Por que o PDF/UA‑2 é importante para acessibilidade e conformidade legal.  
- Quais classes do Aspose.Words estão envolvidas no pipeline de conversão.  
- Como configurar `PdfSaveOptions` para saída PDF/UA‑2.  
- Armadilhas comuns (fonte ausente, tags personalizadas) e como evitá‑las.  
- Um programa Java completo e executável que você pode adaptar imediatamente.

### Pré‑requisitos

- Java 17 (ou qualquer JDK recente) instalado na sua máquina.  
- Maven ou Gradle para gerenciar dependências (mostraremos o trecho Maven).  
- Um documento Word (`.docx`) que você deseja tornar acessível.  
- Uma licença ativa do Aspose.Words for Java (a avaliação gratuita funciona para testes).

> **Dica profissional:** Se você estiver em um servidor CI, defina a licença programaticamente para evitar avisos em tempo de execução.

## Etapa 1: Adicionar a dependência do Aspose.Words

Primeiro, informe à sua ferramenta de build para buscar a biblioteca Aspose.Words. Para Maven, cole isso no seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Se preferir Gradle, o equivalente é:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Por que isso importa:** A biblioteca inclui o renderizador PDF e o motor de acessibilidade, portanto você não precisa de jars adicionais.

## Etapa 2: Carregar o Documento Word de Origem

Agora que a biblioteca está no classpath, você pode ler qualquer `.docx`. A classe `Document` é o ponto de entrada; ela analisa o arquivo Word em um modelo de objeto em memória.

```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your Word file
        String sourcePath = "C:/Docs/ReportWithHR.docx";
        Document doc = new Document(sourcePath);
        // Continue with PDF/UA‑2 settings...
    }
}
```

> **O que está acontecendo:** Aspose.Words lê o pacote Word Open XML, resolve estilos, imagens e até partes XML personalizadas. Não é necessário lidar manualmente com fontes ou layout.

## Etapa 3: Configurar as Opções de Salvamento PDF para PDF/UA‑2

A mágica está em `PdfSaveOptions`. Ao definir o nível de conformidade para `PdfCompliance.PDF_UA_2`, o exportador injeta as tags, elementos de estrutura e metadados necessários que as tecnologias assistivas utilizam.

```java
// Step 3: Set PDF save options to enable PDF/UA‑2 compliance
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCompliance(PdfCompliance.PDF_UA_2);

// Optional: embed all fonts to avoid substitution issues
saveOptions.setEmbedFullFonts(true);

// Optional: add a custom PDF/UA tag for the document title
saveOptions.setDocumentTitle("Annual HR Report – Accessible Version");
```

> **Por que você deve incorporar fontes:** Fontes ausentes podem quebrar a ordem lógica de leitura, fazendo com que leitores de tela falhem. `setEmbedFullFonts(true)` garante uma cópia visual e estrutural fiel.

## Etapa 4: Salvar o Documento como PDF Acessível

Por fim, chame `doc.save()` passando o caminho de saída e as opções configuradas. A biblioteca grava um PDF que passa nas ferramentas de validação PDF/UA‑2 (por exemplo, PDFTron ou veraPDF).

```java
// Step 4: Save the document as a PDF/UA‑2 compliant file
String outputPath = "C:/Docs/Report_UA.pdf";
doc.save(outputPath, saveOptions);

System.out.println("Successfully created PDF/UA-2 compliant document at: " + outputPath);
```

É isso—quatro passos concisos para **exportar Word para PDF acessível**. Execute o programa, abra o PDF resultante no Adobe Acrobat e verifique *Arquivo → Propriedades → Descrição → PDF/A e PDF/UA*; você deverá ver “PDF/UA‑2” listado na conformidade.

## Exemplo Completo em Funcionamento

Abaixo está a classe Java completa e autônoma. Copie, cole e execute; ela produzirá um documento PDF/UA‑2 a partir do arquivo `ReportWithHR.docx` localizado em `C:/Docs`.

```java
import com.aspose.words.*;

public class PdfUaDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        String sourcePath = "C:/Docs/ReportWithHR.docx";
        Document doc = new Document(sourcePath);

        // 2️⃣ Configure PDF/UA‑2 compliance
        PdfSaveOptions saveOptions = new PdfSaveOptions();
        saveOptions.setCompliance(PdfCompliance.PDF_UA_2);
        saveOptions.setEmbedFullFonts(true);
        saveOptions.setDocumentTitle("Annual HR Report – Accessible Version");

        // 3️⃣ Save as an accessible PDF
        String outputPath = "C:/Docs/Report_UA.pdf";
        doc.save(outputPath, saveOptions);

        System.out.println("✅ PDF/UA‑2 file created: " + outputPath);
    }
}
```

### Saída Esperada

Ao executar o programa, o console exibe:

```
✅ PDF/UA-2 file created: C:/Docs/Report_UA.pdf
```

Abra `Report_UA.pdf` em qualquer visualizador de PDF e você notará:

- Todo o texto é selecionável e pesquisável.  
- A hierarquia do documento (títulos, tabelas, listas) está codificada como tags de estrutura.  
- O arquivo passa na validação PDF/UA‑2 (você pode verificar com ferramentas gratuitas como veraPDF).

## Tratando Casos de Borda Comuns

### 1. Fontes Ausentes

Se o Word de origem usar uma fonte que não está instalada no servidor, o Aspose.Words a substituirá, o que pode comprometer a acessibilidade. Para prevenir isso:

```java
saveOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL);
```

### 2. Tags Personalizadas ou Texto Alternativo

Imagens sem texto `alt` serão marcadas como decorativas, o que é aceitável para gráficos puramente decorativos, mas não para imagens informativas. Garanta que seu documento Word inclua texto alternativo significativo antes da conversão.

### 3. Documentos Grandes

Para relatórios com centenas de páginas, você pode atingir limites de memória. Use `Document.save(OutputStream, SaveOptions)` com uma abordagem de streaming, ou divida o documento em seções antes da conversão.

### 4. Permissões do Documento

Se precisar bloquear a edição após a conversão, adicione:

```java
saveOptions.setEncryptDocument(true);
saveOptions.setOwnerPassword("ownerSecret");
saveOptions.setUserPassword("userSecret");
```

## Verificando a Conformidade PDF/UA‑2

Depois de gerar o PDF, é recomendável executar um validador:

1. Baixe o **veraPDF** (validador open‑source).  
2. Execute: `verapdf --format text Report_UA.pdf`.  
3. Procure por “PDF/UA‑2” na seção de conformidade e assegure que não haja erros.

Se encontrar erros, o validador apontará tags ausentes ou fontes não incorporadas—basta ajustar o `PdfSaveOptions` conforme necessário.

## Próximos Passos e Tópicos Relacionados

- **Adicionar tags PDF/UA‑2 manualmente**: Explore `PdfStructureElement` para controle granular.  
- **Conversão em lote**: Percorra um diretório de arquivos `.docx` e gere um zip de PDFs acessíveis.  
- **Combinar com OCR**: Se houver imagens escaneadas dentro do documento Word, use Aspose.OCR para adicionar texto pesquisável antes da conversão.  
- **Integrar com Spring Boot**: Exponha um endpoint que aceita upload de arquivo Word e devolve um stream PDF/UA‑2.

Todos esses recursos se baseiam no padrão central que acabamos de cobrir: carregar → configurar → salvar.

---

*Pronto para tornar cada PDF que você entrega acessível? Pegue o código, execute e permita que seus usuários com deficiência desfrutem do mesmo conteúdo que você. Se encontrar algum problema, deixe um comentário—bom código!*

## O que Você Deve Aprender a Seguir?

- [Create Accessible PDF from Word – Convert to PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}