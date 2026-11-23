---
category: general
date: 2026-11-22
description: Aprenda como carregar markdown com formatação em Java. Este guia mostra
  como ler markdown com formatação usando LoadOptions e Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: pt
lastmod: 2026-11-22
og_description: Como carregar markdown com formatação em Java. Siga este tutorial
  completo para ler markdown com formatação, preservar estilos de sublinhado e trabalhar
  com objetos Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Como carregar markdown com formatação em Java – guia passo a passo
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Como carregar markdown com formatação em Java
url: /pt/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como carregar markdown com formatação em Java

Se você precisa **carregar markdown** mantendo seus estilos visuais, este tutorial oferece uma solução pronta‑para‑usar. Você verá exatamente como **ler markdown com formatação** como texto sublinhado, de modo que o documento renderizado corresponda ao código‑fonte original.

O guia cobre cada passo, desde a configuração do carregador até a verificação de que a formatação sobreviveu à importação. Nenhuma ferramenta externa é necessária além da biblioteca padrão GroupDocs.Viewer (ou qualquer API compatível que forneça `LoadOptions` e `Document`). Ao final, você poderá integrar o carregamento de markdown em qualquer backend Java, serviço web ou aplicativo desktop.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou superior instalado.  
* Maven ou Gradle para gerenciamento de dependências.  
* Acesso ao JAR do GroupDocs.Viewer (ou equivalente) que contém `LoadOptions` e `Document`.  
* Um arquivo markdown de exemplo (`sample.md`) que inclua marcação de sublinhado (por exemplo, `<u>texto sublinhado</u>` ou `_texto sublinhado_` dependendo do parser).

## Etapa 1: Adicionar a dependência necessária

Se você usa Maven, adicione o seguinte ao seu `pom.xml`. Ajuste a versão para a última release estável.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Usuários Gradle podem adicionar:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Incluir a biblioteca disponibiliza as classes `LoadOptions` e `Document` em tempo de compilação.

## Etapa 2: Configurar LoadOptions para importar formatação de sublinhado

O objeto `LoadOptions` indica ao parser quais recursos do markdown devem ser preservados. Habilitar a formatação de sublinhado garante que o estilo visual apareça no `Document` resultante.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Por que isso importa:**  
Sem `setImportUnderlineFormatting(true)`, o parser remove as tags de sublinhado, deixando texto simples. Ativar a flag mantém o estilo intacto, o que é essencial quando o consumidor downstream (por exemplo, um gerador de PDF) depende de pistas visuais.

## Etapa 3: Carregar o documento markdown usando as opções configuradas

Agora você pode ler o arquivo markdown. O construtor `Document` aceita o caminho do arquivo e o `LoadOptions` que você acabou de preparar.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Por que isso importa:**  
Passar o `LoadOptions` ao construtor `Document` garante que o parser respeite a flag de sublinhado durante todo o processo de importação. O objeto `Document` resultante pode ser renderizado, convertido ou inspecionado com formatação completa.

## Etapa 4: Verificar se a formatação de sublinhado sobreviveu

Uma maneira rápida de confirmar que o sublinhado está presente é renderizar o documento para HTML e imprimir a saída. O HTML conterá tags `<u>` se a importação tiver sido bem‑sucedida.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Executar o programa completo deve exibir um trecho HTML que inclui `<u>texto sublinhado</u>`. Se a tag estiver ausente, verifique novamente se `setImportUnderlineFormatting(true)` foi chamado antes de carregar o arquivo.

## Exemplo completo executável

Juntando tudo, aqui está uma classe Java autônoma que você pode compilar e executar:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Saída esperada (truncada para brevidade):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Se a tag `<u>` aparecer, o markdown foi carregado com a formatação intacta.

## Variações comuns e casos de borda

| Situação                                 | O que mudar                                                   |
|------------------------------------------|--------------------------------------------------------------|
| **Extensões markdown diferentes**       | Use `loadOptions.setImportBoldFormatting(true)` para **negrito**. |
| **Arquivos grandes (> 10 MB)**           | Transmita o arquivo com `FileInputStream` e passe o stream ao `Document`. |
| **Necessidade de saída PDF**             | Após o carregamento, use `PdfViewOptions` com `Viewer` para gerar um PDF que mantenha estilos de sublinhado. |
| **Execução em um contêiner servlet**     | Armazene o `Document` no escopo da requisição e renderize para HTML sob demanda. |

**Dica profissional:** Sempre crie uma nova instância de `LoadOptions` para cada operação de carregamento. Reutilizar o mesmo objeto entre threads pode causar vazamento de estado inesperado.

## Conclusão

Agora você sabe **como carregar markdown com formatação em Java** e como **ler markdown com formatação** usando `LoadOptions`. O exemplo completo demonstra configuração, carregamento e verificação, permitindo que você incorpore esse padrão em qualquer projeto Java que processe arquivos markdown.  

Em seguida, explore tópicos relacionados como **ler markdown com imagens**, **converter markdown para PDF** ou **personalizar outras importações de estilo** (negrito, itálico, tachado). Cada uma dessas extensões segue o mesmo padrão: ajuste as flags de `LoadOptions`, carregue o `Document` e renderize no formato desejado.

Bom código!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to load markdown document in Java with custom import options](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [How to read and load a Markdown file in Java with Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [How to Load Markdown in Java – Complete Guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}