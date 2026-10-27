---
category: general
date: 2026-08-07
description: Como editar nota de rodapé em Java com Aspose.Words – adicionar traço
  personalizado, alterar a linha da nota de rodapé e definir o alinhamento do parágrafo
  para documentos refinados.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: pt
lastmod: 2026-08-07
og_description: Como editar notas de rodapé em Java com Aspose.Words. Aprenda a adicionar
  um traço personalizado, alterar a linha da nota de rodapé e definir o alinhamento
  do parágrafo em apenas alguns passos.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Como editar nota de rodapé no Java – adicionar traço, mudar linha, definir
  alinhamento
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Como editar nota de rodapé em Java com Aspose.Words
url: /pt/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como editar nota de rodapé em Java com Aspose.Words

Se você precisa **como editar nota de rodapé** em um documento Word usando Java, este guia mostra o fluxo de trabalho completo. Você aprenderá a adicionar um traço personalizado, alterar a linha da nota de rodapé e definir o alinhamento do parágrafo para que o separador de nota de rodapé tenha uma aparência profissional.

Editar notas de rodapé é uma necessidade comum ao preparar contratos legais, trabalhos acadêmicos ou brochuras de marketing. As etapas abaixo cobrem tudo o que você precisa — desde o carregamento do documento até a gravação do arquivo final — sem exigir ferramentas adicionais.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou mais recente instalado.
* Aspose.Words for Java (última versão) adicionado ao classpath do seu projeto.
* Um arquivo DOCX (`input.docx`) que contenha ao menos uma nota de rodapé.

Esses itens garantem que o código seja executado sem erros em tempo de execução.

## Como editar o separador e a linha da nota de rodapé

O separador de nota de rodapé é o parágrafo que aparece entre o texto principal e a lista de notas de rodapé. Alterar sua aparência melhora a legibilidade e corresponde à identidade visual da empresa.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Por que cada linha importa

1. **Carregando o documento** – `new Document(...)` lê o arquivo DOCX na memória, dando acesso a todos os seus nós.  
2. **Obtendo o separador** – `getFootnoteSeparator()` devolve o parágrafo especial que o Aspose.Words trata como a linha da nota de rodapé. Este objeto é o único local onde você pode modificar o separador com segurança.  
3. **Definindo alinhamento de parágrafo** – `setAlignment(ParagraphAlignment.CENTER)` altera o alinhamento da linha. A palavra‑chave *set paragraph alignment* é aplicada diretamente ao separador, garantindo um traço centralizado.  
4. **Adicionando um traço personalizado** – Ao limpar as execuções existentes e adicionar um novo `Run` com o caractere em‑dash (`—`), você obtém o efeito *add custom dash* enquanto também *change footnote line* para o estilo desejado.  
5. **Gravando o documento** – `doc.save(...)` escreve as alterações de volta ao disco, produzindo um arquivo de saída que reflete todas as modificações.

## Adicionar traço personalizado ao separador da nota de rodapé

O código no **Passo 4** demonstra a técnica *add custom dash*. Você pode substituir o em‑dash por qualquer string, como `"***"` ou `"---"`, para combinar com a linguagem visual do seu documento.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Usar um traço personalizado é especialmente útil quando a linha fina padrão não atende às diretrizes de branding.

## Alterar o estilo da linha da nota de rodapé

Se você prefere uma linha sólida em vez de um traço, pode inserir um caractere Unicode de desenho de caixa ou um sublinhado repetido.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

A etapa *change footnote line* funciona da mesma forma, independentemente do caractere escolhido, pois o parágrafo separador simplesmente renderiza o texto que contém.

## Definir alinhamento de parágrafo para o separador da nota de rodapé

A operação *set paragraph alignment* não se limita ao alinhamento central. Você pode alinhar à esquerda, à direita ou justificar de acordo com as necessidades do layout.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Alinhar o separador à direita pode ser útil para documentos que utilizam notas de rodapé alinhadas à direita, como publicações bilíngues.

## Exemplo completo e executável

Abaixo está o programa completo que incorpora todos os conceitos — carregamento de documento, edição do separador de nota de rodapé, adição de traço personalizado, alteração do estilo da linha e definição de alinhamento.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Saída esperada:** O arquivo `output.docx` contém um em‑dash centralizado onde antes havia a linha fina original. Todas as notas de rodapé permanecem intactas, e o layout do documento reflete o novo estilo do separador.

## Armadilhas comuns e como evitá‑las

| Problema | Motivo | Solução |
|----------|--------|---------|
| Separador não encontrado | O documento não tem notas de rodapé ou usa um estilo de nota de rodapé personalizado | Certifique‑se de que o DOCX de origem contenha ao menos uma nota de rodapé antes de chamar `getFootnoteSeparator()` |
| Traço personalizado não visível | A fonte não suporta o caractere escolhido | Use um caractere Unicode suportado pela fonte padrão do documento ou incorpore uma fonte compatível |
| Alinhamento parece não ter mudado | O formato do parágrafo é sobrescrito posteriormente no código | Aplique o alinhamento **depois** de quaisquer outras chamadas de formatação que possam redefini‑lo |

Abordar esses pontos evita erros em tempo de execução e garante que o processo *como editar nota de rodapé* funcione de forma confiável.

## Próximos passos

Agora que você sabe **como editar nota de rodapé** elementos, pode explorar tarefas relacionadas:

* **Adicionar estilo de referência de nota de rodapé personalizado** – modifique nós `FootnoteReference` para mudar a numeração ou símbolos.  
* **Inserir programaticamente novas notas de rodapé** – use `DocumentBuilder.insertFootnote()` para conteúdo dinâmico.  
* **Aplicar formatação condicional** – altere a aparência da nota de rodapé com base no estilo do parágrafo ou no comprimento do conteúdo.

Cada uma dessas extensões se baseia na mesma superfície de API que você usou para *add custom dash*, *change footnote line* e *set paragraph alignment*.

---

*Feliz codificação! Se o tutorial ajudou você a dominar a edição de notas de rodapé, considere compartilhá‑lo com sua equipe ou contribuir com um pull request para melhorar ainda mais o exemplo.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Definir posição de nota de rodapé e nota de fim](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}