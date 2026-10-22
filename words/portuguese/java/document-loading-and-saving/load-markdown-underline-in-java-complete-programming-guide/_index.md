---
category: general
date: 2026-08-04
description: Carregue sublinhado em markdown no Java e preserve a formatação markdown
  ao carregar o markdown no documento. Siga este tutorial passo a passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: pt
lastmod: 2026-08-04
og_description: Carregue sublinhado de markdown em Java e preserve a formatação markdown.
  Aprenda como carregar markdown em um documento com suporte total a sublinhado.
og_image_alt: Diagram showing load markdown underline process
og_title: Carregar sublinhado de markdown no Java – guia passo a passo
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Carregar sublinhado markdown em Java – guia completo de programação
url: /pt/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Carregar sublinhado markdown em Java – guia completo de programação

Se você precisa **carregar sublinhado markdown** ao converter um arquivo Markdown para um objeto `Document`, este guia mostra exatamente como fazer isso. Você também aprenderá como **carregar markdown em documento** sem perder nenhum estilo de sublinhado, garantindo que a formatação original do Markdown seja totalmente preservada.

O tutorial cobre tudo o que você precisa saber: bibliotecas necessárias, cada passo de configuração e como verificar se a formatação de sublinhado sobreviveu à importação. Ao final, você terá um trecho de código reutilizável que pode inserir em qualquer projeto Java.

## Pré-requisitos

- Java 17 ou posterior instalado (o exemplo usa o sistema de módulos moderno)
- A versão mais recente do **GroupDocs.Viewer** (ou uma biblioteca compatível que fornece `LoadOptions` e `Document`)
- Um arquivo Markdown (`sample.md`) que contém texto sublinhado, por exemplo, `<u>underlined</u>` ou a sintaxe ao estilo GitHub `__underlined__`
- Uma IDE como IntelliJ IDEA ou VS Code, embora qualquer editor de texto funcione

Esses requisitos garantem que o código seja executado sem configuração adicional.

## Carregar sublinhado markdown – guia passo a passo

O processo consiste em três ações principais: criar uma instância de `LoadOptions`, habilitar a detecção de sublinhado e, finalmente, carregar o arquivo Markdown com essas opções. Cada passo é explicado abaixo.

### Etapa 1: Criar `LoadOptions` para o documento

`LoadOptions` permite personalizar como a biblioteca analisa o arquivo fonte. Criar uma nova instância fornece uma base limpa para configurações posteriores.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

O objeto `LoadOptions` é o ponto de entrada para todas as personalizações relacionadas à importação. Você o usará na próxima etapa para ativar a detecção de sublinhado.

### Etapa 2: Habilitar a detecção de formatação de sublinhado ao carregar

Por padrão, o visualizador pode ignorar tags de sublinhado porque são menos comuns no Markdown. Habilitar essa flag indica ao analisador que mantenha os trechos sublinhados intactos.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Definir `setImportUnderlineFormatting(true)` garante que qualquer tag HTML `<u>` ou sintaxe de sublinhado ao estilo GitHub seja traduzida para o modelo `Document` como um estilo de sublinhado. Essa é a ação chave que faz o **carregar sublinhado markdown** funcionar como esperado.

### Etapa 3: Carregar o arquivo Markdown usando as opções configuradas

Agora você pode carregar o arquivo. Passe o objeto `loadOptions` para o construtor `Document` para que o analisador respeite a flag de sublinhado.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Quando o construtor termina, `markdownDoc` contém uma representação completa em memória da fonte Markdown, completa com trechos sublinhados.

### Etapa 4: Verificar se a formatação de sublinhado foi preservada

Uma verificação rápida ajuda a confirmar que **preservar formatação markdown** funcionou. O trecho a seguir imprime o texto de cada parágrafo e marca fragmentos sublinhados com um til (`~`) para visibilidade.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Saída esperada** (supondo que `sample.md` contenha `This is __underlined__ text`):

```
This is ~underlined~ text
```

Os tildes indicam que o estilo de sublinhado sobreviveu à importação, confirmando que a operação **carregar markdown em documento** preservou a formatação original.

## Armadilhas comuns e como evitá‑las

| Sintoma | Causa | Correção |
|---|---|---|
| Sublinhado desaparece após o carregamento | `setImportUnderlineFormatting` deixado em seu padrão `false` | Certifique‑se de chamar `loadOptions.setImportUnderlineFormatting(true)` antes de criar o `Document`. |
| Apenas parte do texto está sublinhada | Sintaxe Markdown misturada (por exemplo, HTML `<u>` misturado com `__underline__`) | A biblioteca suporta ambos; verifique se o arquivo fonte usa um marcador de sublinhado consistente. |
| Falha ao carregar o documento | Caminho de arquivo incorreto ou dependências de biblioteca ausentes | Use um caminho absoluto ou coloque `sample.md` relativo ao diretório de trabalho; inclua os JARs do viewer no classpath. |

**Dica profissional:** Se você também precisar manter estilos negrito ou itálico, habilite‑os com `setImportBoldFormatting(true)` e `setImportItalicFormatting(true)` respectivamente. Combinar essas flags fornece uma importação totalmente fiel da maioria dos estilos Markdown comuns.

## Exemplo completo executável

Abaixo está um programa Java autônomo que reúne tudo. Copie o código para um arquivo chamado `LoadMarkdownUnderlineDemo.java`, ajuste o caminho do arquivo e execute‑o com `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Executar o programa imprime o conteúdo do documento com marcadores de sublinhado, provando que o recurso **carregar sublinhado markdown** funciona e que você pode **preservar formatação markdown** ao longo do pipeline de importação.

## Conclusão

Agora você sabe como **carregar sublinhado markdown** em Java, como **carregar markdown em documento** mantendo a estilização original, e como verificar se a formatação de sublinhado está intacta. Essa abordagem funciona com as versões mais recentes do GroupDocs.Viewer e pode ser estendida para suportar recursos adicionais do Markdown, como negrito, itálico e tabelas.

Em seguida, explore tópicos relacionados como **preservar formatação markdown para tabelas**, **renderizar Markdown para PDF**, ou **estilização personalizada de elementos Markdown importados**. Ajuste as flags de `LoadOptions` para corresponder aos requisitos exatos de formatação da sua aplicação, e você terá controle detalhado sobre cada etapa de importação. Feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Domine as Opções de Carregamento de Markdown com Aspose.Words para Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Domine as Opções de Carregamento de Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}