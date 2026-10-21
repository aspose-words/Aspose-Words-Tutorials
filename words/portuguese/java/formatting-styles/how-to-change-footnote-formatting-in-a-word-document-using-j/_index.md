---
category: general
date: 2026-09-11
description: Aprenda como alterar a formatação de notas de rodapé em Java com Aspose.Words.
  Este guia explica como editar notas de rodapé, atualizar o estilo das notas de rodapé
  e modificar o separador de notas de rodapé.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: pt
lastmod: 2026-09-11
og_description: Altere a formatação de notas de rodapé em Java com Aspose.Words. Siga
  este guia completo para editar notas de rodapé, atualizar o estilo das notas de
  rodapé e modificar o separador de notas de rodapé.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Alterar a formatação de notas de rodapé em Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Como alterar a formatação de notas de rodapé em um documento Word usando Java
url: /pt/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como alterar a formatação de notas de rodapé em um documento Word usando Java

Se você precisa **alterar a formatação de notas de rodapé** em um documento Word, este tutorial orienta você passo a passo usando Aspose.Words for Java. Seja construindo um pipeline de publicação ou apenas precisando **como editar a aparência da nota de rodapé** programaticamente, a solução abaixo cobre tudo, desde o carregamento do arquivo até a gravação da versão atualizada.

Você aprenderá como **atualizar o estilo da nota de rodapé**, tornar o separador de notas de rodapé em negrito e até **modificar as propriedades do separador de notas de rodapé**, como tamanho da fonte ou cor. O guia assume que você tem conhecimentos básicos de Java e uma licença válida do Aspose.Words for Java.

## Pré-requisitos

* Java 17 ou superior instalado.
* Aspose.Words for Java (versão 23.12 ou posterior) adicionado ao classpath do seu projeto.
* Um documento Word (`input.docx`) que contém ao menos uma nota de rodapé.
* Uma IDE ou ferramenta de build (Maven/Gradle) para compilar e executar o código.

Se você não tem certeza de como adicionar o Aspose.Words a um projeto Maven, inclua a seguinte dependência no seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Alterar a formatação de notas de rodapé com Aspose.Words for Java

O núcleo da solução é um pequeno programa Java que carrega um documento, acessa o parágrafo do separador de notas de rodapé, altera sua formatação e salva o resultado. O código é totalmente autocontido, de modo que você pode copiá‑lo para uma nova classe e executá‑lo imediatamente.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Por que cada passo importa

* **Carregando o documento** (`new Document`) cria uma representação em memória que o Aspose.Words pode manipular.  
* **Recuperando o separador de notas de rodapé** (`getFootnoteSeparator`) fornece acesso direto ao parágrafo que separa as notas de rodapé do texto principal. Este é o elemento que você precisa direcionar quando deseja **alterar a formatação de notas de rodapé**.  
* **Formatando a execução** (`setBold`, `setItalic`, `setSize`, `setColor`) demonstra como **modificar as propriedades do separador de notas de rodapé**. Você pode adicionar quaisquer atributos de fonte adicionais aqui, como sublinhado ou realce, para controlar totalmente a aparência.  
* **Salvando o documento** grava as alterações de volta ao disco, produzindo um novo arquivo (`output.docx`) que reflete o estilo de nota de rodapé atualizado.

> **Dica profissional:** Se o seu documento de origem usa um separador de notas de rodapé personalizado que contém múltiplas execuções (por exemplo, uma combinação de símbolos), percorra `footnoteSeparator.getRuns()` e aplique as mesmas configurações de `Font` a cada execução para um estilo consistente.

## Como editar o separador de notas de rodapé programaticamente

Às vezes você pode precisar editar não apenas o separador, mas também o texto da nota de rodapé. A mesma API pode ser usada para acessar cada nota de rodapé, ajustar a formatação do parágrafo ou alterar o estilo de numeração.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

O trecho acima mostra **como editar o corpo da nota de rodapé** depois de já ter **alterado a formatação da nota de rodapé** para o separador. Ao iterar sobre `doc.getFootnotes()`, você garante que cada nota de rodapé herde o mesmo estilo, o que é essencial para um documento com aparência profissional.

## Atualizar o estilo da nota de rodapé para uma aparência consistente do documento

Se você prefere trabalhar com estilos em vez de execuções individuais, o Aspose.Words permite criar ou modificar um objeto `Style` e então aplicá‑lo às notas de rodapé e ao separador. Essa abordagem é útil quando você precisa **atualizar o estilo da nota de rodapé** em vários documentos.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Usar um estilo dedicado facilita a manutenção futura — altere o estilo uma vez, e todas as notas de rodapé e separadores são atualizados automaticamente. Essa técnica é a forma recomendada de **atualizar o estilo da nota de rodapé** em fluxos de trabalho de publicação em grande escala.

## Modificar o separador de notas de rodapé para combinar com sua identidade visual

Diretrizes de marca às vezes determinam que o separador de notas de rodapé use um caractere específico (por exemplo, um asterisco) ou uma linha personalizada. O Aspose.Words permite substituir completamente o conteúdo padrão do separador.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

O código acima **modifica o separador de notas de rodapé** ao limpar quaisquer execuções existentes e inserir uma nova execução com o texto e formatação desejados. Você também pode usar caracteres Unicode como `\u2022` (marcador) ou `\u2014` (travessão) para alcançar o efeito visual exato exigido pela sua marca.

## Resultado esperado

Após executar o programa:

* O separador de notas de rodapé em `output.docx` aparece **negrito**, **itálico**, 10 pt, e cinza (ou qualquer cor que você definiu).  
* Todos os parágrafos de notas de rodapé adotam o estilo que você definiu, garantindo uma aparência uniforme em todo o documento.  
* Se você substituiu o texto do separador, a nova linha personalizada fica visível exatamente onde a linha original estava.

Abra o arquivo resultante no Microsoft Word ou no LibreOffice Writer para verificar as alterações. Você deverá ver o separador atualizado logo acima da primeira nota de rodapé, e o texto da nota de rodapé deve refletir quaisquer modificações de estilo que você aplicou.

## Armadilhas comuns e como evitá‑las

| Problema | Por que acontece | Solução |
|----------|------------------|---------|
| `footnoteSeparator.getRuns().getCount() == 0` lança uma exceção | Alguns documentos têm um parágrafo de separador vazio. | Adicione uma verificação defensiva e crie uma execução se nenhuma existir (veja o exemplo de código). |
| Alterações de fonte não são visíveis | O documento usa um tema que sobrescreve a formatação direta. | Defina `font.setThemeFont(null)` ou aplique um estilo personalizado em vez de formatação direta. |
| Arquivo salvo não reflete as alterações | O arquivo original ainda está aberto no Word, bloqueando o caminho de saída. | Feche todas as instâncias do arquivo antes de executar o programa, ou |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Processamento de Texto com Nota de Rodapé e Nota de Fim](/words/english/net/working-with-footnote-and-endnote/)
- [Definir Posição da Nota de Rodapé e da Nota de Fim](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Como Exibir Informações da Versão do Aspose.Words em Java: Um Guia Abrangente](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}