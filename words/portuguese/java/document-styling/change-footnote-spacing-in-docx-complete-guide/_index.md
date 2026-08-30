---
category: general
date: 2026-07-20
description: Altere o espaçamento das notas de rodapé em arquivos DOCX facilmente.
  Aprenda como definir o espaçamento, ajustar o separador de notas de rodapé e definir
  o espaçamento entre linhas dos parágrafos com Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: pt
lastmod: 2026-07-20
og_description: Altere o espaçamento de notas de rodapé em arquivos DOCX rapidamente.
  Este guia mostra como definir o espaçamento, ajustar o separador de notas de rodapé
  e personalizar o espaçamento entre linhas de parágrafos em Java.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Alterar espaçamento de notas de rodapé no DOCX – Guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Alterar espaçamento de notas de rodapé em DOCX – Guia completo
url: /pt/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar espaçamento de notas de rodapé em DOCX – Guia Completo

Já precisou **alterar o espaçamento de notas de rodapé** em um documento Word, mas não sabia por onde começar? Você não está sozinho. Seja refinando uma tese ou ajustando um contrato, acertar o separador de notas de rodapé pode fazer uma grande diferença.  

Neste tutorial, vamos percorrer **como definir espaçamento**, ajustar o separador de notas de rodapé e **definir o espaçamento entre linhas de parágrafos** usando bibliotecas baseadas em Java. Ao final, você terá um exemplo pronto‑para‑executar que pode inserir em qualquer projeto.

## O que você precisará

- Java 17 ou mais recente (o código usa os recursos modernos da linguagem)
- Maven ou Gradle para gerenciamento de dependências
- Um arquivo DOCX com pelo menos uma nota de rodapé (ou você pode criar um manualmente)
- A biblioteca **Aspose.Words for Java** (ou qualquer API compatível; usaremos Aspose no exemplo)

É isso—sem frameworks pesados, apenas Java puro e uma única biblioteca.

![Exemplo de alteração de espaçamento de notas de rodapé em DOCX](/images/footnote-spacing.png){alt="Exemplo de alteração de espaçamento de notas de rodapé em DOCX"}

## Etapa 1: Carregar o documento DOCX (Alterar espaçamento de notas de rodapé)

A primeira coisa que você precisa fazer é abrir o arquivo Word. Isso fornece um objeto `Document` que você pode manipular.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Por que isso importa*: Carregar o documento é o ponto de entrada para **alterar o espaçamento de notas de rodapé**. Sem uma instância `Document` você não pode acessar o separador de notas de rodapé ou quaisquer formatos de parágrafo.

## Etapa 2: Recuperar e ajustar o separador de notas de rodapé (Ajustar separador de notas de rodapé)

Um separador de notas de rodapé é um parágrafo oculto que fica entre o texto principal e a lista de notas de rodapé. Para alterar seu espaçamento entre linhas, você precisa obter esse parágrafo e ajustar seu formato.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Como isso resolve o problema

- **Recuperar o separador de notas de rodapé** – esta é a parte que você realmente deseja modificar, atendendo ao requisito de *ajustar separador de notas de rodapé*.
- **Definir o espaçamento entre linhas** – `setLineSpacing(12.0)` responde diretamente a *como definir espaçamento* para esse parágrafo oculto.
- **Tratamento de casos extremos** – se o documento, de alguma forma, não possuir um separador, criamos um na hora, evitando um `NullPointerException`.

## Etapa 3: Verificar a alteração e salvar (Definir espaçamento entre linhas de parágrafo)

Depois de alterar o separador, você vai querer garantir que a mudança foi persistida. Abrir o arquivo salvo no Word mostrará o novo espaçamento, mas você também pode verificar programaticamente.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Adicione uma chamada a `verifySpacing(doc);` logo antes de `doc.save(...)` em `main`. Quando você executar o programa, deverá ver:

```
Current footnote separator line spacing: 12.0
```

Isso confirma que a operação **alterar espaçamento de linhas docx** foi bem-sucedida.

## Armadilhas comuns e dicas profissionais

- **Armadilha**: Usar `setLineSpacing` com um valor que parece “12”, mas é interpretado como “12 pts” versus “12 linhas”. Aspose espera pontos, então 12 significa 12 pt. Para espaçamento duplo use `24.0`.
- **Dica profissional**: Se precisar de uma aparência consistente em todos os tipos de notas de rodapé (separador, separador de continuação, etc.), repita os mesmos passos para `doc.getFootnoteContinuationSeparator()` e `doc.getFootnoteContinuationNotice()`.
- **Armadilha**: Esquecer de chamar `save()` após as modificações. O documento na memória é alterado, mas o arquivo no disco permanece o mesmo.
- **Dica profissional**: Combine alterações de espaçamento com atualizações de estilo (`ParagraphStyle`) para uma seção de notas de rodapé totalmente polida.

## Exemplo completo em funcionamento (Todas as etapas em um único arquivo)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Copie o código acima para uma nova classe Java, adicione a dependência Maven do Aspose.Words e execute. Seu `output.docx` agora terá o espaçamento de linha do separador de notas de rodapé definido para **12 pt**, efetivamente **alterando o espaçamento de notas de rodapé**.

### Dependência Maven

Adicione este trecho ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Se preferir Gradle, o equivalente é:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Conclusão

Você acabou de aprender como **alterar o espaçamento de notas de rodapé** em um arquivo DOCX usando Java. Ao carregar o documento, recuperar o **separador de notas de rodapé** e aplicar **definir espaçamento entre linhas de parágrafo**, você obtém controle preciso sobre a aparência das notas de rodapé.  

A partir daqui, você pode explorar ajustes relacionados, como modificar o estilo do texto da nota de rodapé, adicionar separadores personalizados ou até automatizar atualizações em massa em vários documentos.  

Tem mais perguntas sobre **ajustar separador de notas de rodapé** ou outras tarefas de automação do Word? Deixe um comentário e feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Alterar espaçamento e recuos de parágrafo asiático em documento Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Alterar espaçamento e recuos de parágrafo asiático](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Alterar espaçamento e recuos de parágrafo asiático](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}