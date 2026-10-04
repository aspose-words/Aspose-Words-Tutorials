---
category: general
date: 2026-10-04
description: Editar separador de nota de rodapé em Java usando Aspose.Words – aprenda
  como alterar o separador de nota de rodapé e adicionar uma palavra separadora personalizada
  a documentos Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: pt
lastmod: 2026-10-04
og_description: Edite o separador de notas de rodapé em Java com Aspose.Words. Este
  tutorial mostra como alterar o separador de notas de rodapé e inserir uma palavra
  separadora personalizada.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Editar separador de notas de rodapé em Java – guia completo do Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Como editar o separador de notas de rodapé em Java com Aspose.Words
url: /pt/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como editar o separador de nota de rodapé em Java com Aspose.Words

Se você precisa **editar o separador de nota de rodapé** em um documento Word, este guia mostra exatamente como fazer isso em Java. Seja para **alterar o separador de nota de rodapé** para um traço, uma estrela ou qualquer **palavra separadora personalizada**, as etapas abaixo cobrem tudo o que você precisa.

Você aprenderá como carregar um arquivo `.docx`, recuperar a seção especial do separador, modificar seu conteúdo e salvar o resultado. Nenhum script externo ou edição manual é necessário – tudo é feito programaticamente com a biblioteca Aspose.Words for Java.

## Pré-requisitos

- Java 17 ou posterior instalado.
- Maven ou Gradle para gerenciar dependências (o exemplo usa Maven).
- Uma licença válida do Aspose.Words for Java (ou uma chave de avaliação gratuita).
- Um documento Word que já contém notas de rodapé (o separador existe apenas quando há notas de rodapé).

## Adicionar Aspose.Words ao seu projeto

Se você usa Maven, adicione a seguinte dependência ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Para Gradle, adicione:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Etapa 1: Carregar o documento que contém notas de rodapé

A primeira etapa é abrir o arquivo Word que você deseja modificar. Aspose.Words lê o arquivo em um objeto `Document`, que lhe dá acesso total a todas as partes do documento, incluindo os separadores de notas de rodapé.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Por que isso importa:** Carregar o documento cria uma representação em memória, permitindo que você modifique com segurança qualquer nó sem tocar no arquivo original até que o salve explicitamente.

## Etapa 2: Recuperar a seção do separador de nota de rodapé

O Word armazena o separador de nota de rodapé como um nó especial `Separator`. Aspose.Words fornece o método `getFootnoteSeparator()` para obtê-lo diretamente.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Dica profissional:** O nó separador existe apenas se o documento já contiver ao menos uma nota de rodapé. Se você tentar editar um documento sem notas de rodapé, `getFootnoteSeparator()` retornará `null`, portanto sempre verifique essa condição.

## Etapa 3: Inserir uma palavra separadora personalizada

Agora você pode alterar a aparência do separador. Neste exemplo substituímos a linha padrão por um travessão em (`—`). Você poderia, em vez disso, inserir qualquer **palavra separadora personalizada**, como `"NOTE:"` ou `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### O que o código faz

1. **`clearChildren()`** remove quaisquer execuções existentes, garantindo que o separador contenha apenas o texto que você fornece.
2. **`new Run(document, "—")`** cria um nó de texto com o separador desejado. O objeto `Run` respeita o estilo do documento, portanto o separador herda a formatação do separador de nota de rodapé original.
3. **`appendChild(customRun)`** insere a nova execução no parágrafo do separador.

Você também pode aplicar formatação à execução, por exemplo:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Etapa 4: Salvar o documento modificado

Após editar o separador, grave o documento de volta no disco. Escolha um novo nome de arquivo para manter o arquivo original intacto.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Verificação do resultado:** Abra `ModifiedNotes.docx` no Microsoft Word. O separador de nota de rodapé agora deve exibir o travessão personalizado (ou qualquer palavra que você escolheu) em vez da linha padrão.

## Manipulando múltiplos separadores de notas de rodapé

O Word suporta três tipos especiais de separadores:

| Tipo de separador | Método                     |
|-------------------|----------------------------|
| Separador de nota de rodapé | `getFootnoteSeparator()` |
| Separador de continuação de nota de rodapé | `getFootnoteContinuationSeparator()` |
| Separador de nota de rodapé da primeira página | `getFootnoteSeparatorForFirstPage()` |

Se você precisar editar todos eles, repita a **Etapa 2** e a **Etapa 3** para cada método. Exemplo:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Armadilhas comuns e como evitá‑las

| Problema | Causa | Solução |
|----------|-------|---------|
| Nenhum separador aparece após salvar | O documento não tinha notas de rodapé → nó separador é `null` | Adicione ao menos uma nota de rodapé antes de editar, ou crie uma nota de rodapé fictícia programaticamente. |
| O separador mostra espaços extras | Execuções existentes não foram limpas | Chame `clearChildren()` antes de anexar a nova execução. |
| A formatação parece diferente | A execução herda o estilo do separador original | Defina explicitamente as propriedades de fonte na `Run` se precisar de uma aparência específica. |

## Exemplo completo em funcionamento

Juntando todas as peças, aqui está uma classe Java autônoma que você pode copiar, compilar e executar:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Execute o programa, então abra `ModifiedNotes.docx` para confirmar que o separador foi atualizado.

## Conclusão

Agora você sabe como **editar o separador de nota de rodapé** em um documento Word usando Java e Aspose.Words. O tutorial abordou o carregamento de um documento, a recuperação do nó separador especial, a inserção de uma **palavra separadora personalizada** e a gravação do resultado. Seguindo estas etapas, você também pode **alterar o separador de nota de rodapé** para seções de continuação ou notas de rodapé da primeira página.

Em seguida, você pode explorar:

- Adicionar diferentes separadores para notas de rodapé da primeira página (`getFootnoteSeparatorForFirstPage()`).
- Criar notas de rodapé programaticamente quando não existirem.
- Usar Aspose.Words para estilizar o texto das notas de rodapé (fontes, cores, recuo).

Sinta‑se à vontade para experimentar outros caracteres ou palavras para combinar com a identidade visual do seu documento. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir separador de estilo de documento no Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Obter separador de estilo de parágrafo em documento Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Como carregar documentos Word com Aspose.Words Java: Guia abrangente](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}