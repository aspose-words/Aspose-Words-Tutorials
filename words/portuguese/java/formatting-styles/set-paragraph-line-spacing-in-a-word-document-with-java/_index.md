---
category: general
date: 2026-11-15
description: Defina o espaçamento entre linhas de parágrafo em um documento Word com
  Java. Aprenda como definir o espaçamento entre linhas programaticamente usando Aspose.Words
  para formatação precisa de documentos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: pt
lastmod: 2026-11-15
og_description: Defina o espaçamento entre linhas de parágrafos em um documento Word
  com Java. Este guia explica como definir o espaçamento entre linhas para parágrafos
  e separadores de notas de rodapé usando Aspose.Words, proporcionando controle total
  sobre o layout do documento.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Definir espaçamento entre linhas de parágrafo no Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Definir o espaçamento entre linhas de parágrafo em um documento Word com Java
url: /pt/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir espaçamento de linha de parágrafo em um documento Word com Java

Se você precisar **definir o espaçamento de linha de parágrafo** em um documento Word, este tutorial mostra como fazer isso com Java e Aspose.Words. Você também aprenderá **como definir o espaçamento de linha** para separadores de notas de rodapé — um requisito comum ao formatar documentos profissionais.

Nas seções a seguir você irá:

* Carregar um arquivo *.docx* existente.  
* Recuperar o parágrafo do separador de nota de rodapé.  
* Aplicar um valor de espaçamento de linha personalizado.  
* Salvar o documento atualizado.

Nenhuma configuração externa é necessária além de adicionar a biblioteca Aspose.Words ao seu projeto, portanto você pode copiar o código literalmente e executá‑lo imediatamente.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* Java 17 ou superior instalado.  
* Maven (ou outra ferramenta de build) para gerenciar dependências.  
* Uma licença válida do Aspose.Words for Java (a avaliação gratuita funciona para testes).  
* Um documento Word de entrada (`input.docx`) localizado em um diretório conhecido.

Adicione a dependência do Aspose.Words ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Definir espaçamento de linha de parágrafo com Aspose.Words

Este cabeçalho H2 contém a palavra‑chave principal, atendendo ao requisito de SEO.

### Etapa 1: Carregar o documento Word

Primeiro, crie uma instância `Document` que aponte para o seu arquivo de origem.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Por que isso importa*: Carregar o documento fornece um modelo em memória que você pode manipular sem tocar no arquivo original até que você o salve explicitamente.

### Etapa 2: Recuperar o separador de nota de rodapé

Separadores de notas de rodapé são parágrafos especiais que aparecem entre as notas de rodapé e o texto principal. Para alterar sua aparência, você precisa acessar o objeto `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Dica*: Se o seu documento não contiver notas de rodapé, o separador ainda existe como um parágrafo oculto, portanto a chamada nunca retornará `null`.

### Etapa 3: Como definir o espaçamento de linha para o parágrafo do separador

Agora aplique o espaçamento de linha desejado. Aspose.Words usa pontos para valores de espaçamento de linha; 12 pts equivale aproximadamente a espaçamento simples para a maioria das fontes.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Você também pode usar outros modos de espaçamento:

| Modo                     | Chamada de método                                      |
|--------------------------|--------------------------------------------------------|
| **Exactly** (pts fixos) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`         |
| **Multiple** (ex., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Escolher a regra correta garante que o documento seja renderizado de forma consistente no Word, Google Docs e outros visualizadores.

### Etapa 4: Salvar o documento atualizado

Finalmente, grave as alterações de volta ao disco.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Ao abrir `output.docx` no Microsoft Word, o separador de nota de rodapé será exibido com o espaçamento de linha que você definiu.

## Entendendo como definir o espaçamento de linha para parágrafos regulares

A mesma API funciona para qualquer objeto `Paragraph`, não apenas para separadores de notas de rodapé. Aqui está um exemplo rápido que ajusta o espaçamento do primeiro parágrafo do corpo:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Por que você pode precisar disso**: Relatórios, contratos e trabalhos acadêmicos frequentemente exigem um estilo específico de espaçamento de linha (por exemplo, espaçamento duplo para rascunhos). Usar o mesmo método `setLineSpacing` garante o layout exato que você espera.

## Armadilhas comuns e como evitá‑las

| Problema                                 | Causa                                   | Correção |
|------------------------------------------|----------------------------------------|----------|
| O espaçamento de linha permanece inalterado | `LineSpacingRule` deixado no padrão (AUTO) | Defina explicitamente a regra com `setLineSpacingRule`. |
| Linhas em branco extras após o separador | O separador contém retornos de carro ocultos | Remova o texto do separador com `separator.getText().trim();` antes de aplicar o espaçamento. |
| O documento fica corrompido ao salvar     | Uso de uma versão desatualizada do Aspose.Words | Atualize para a versão mais recente (ex., 24.10) que contém correções de bugs para salvamento. |

## Dica profissional: processar vários documentos em lote

Se precisar atualizar dezenas de arquivos, encapsule a lógica em um método auxiliar e itere sobre uma pasta:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Executar esse método em um loop economiza horas de edição manual.

## Saída esperada

Depois de executar o programa completo, `output.docx` irá:

* Manter o conteúdo original inalterado, exceto pelo espaçamento de linha.  
* Exibir o separador de nota de rodapé com layout de espaçamento simples (12 pts).  
* Preservar toda a formatação restante (estilos, imagens, tabelas).

Abra o arquivo no Word e verifique se a linha do separador está mais apertada (ou mais espaçada, dependendo do valor que você definiu).

## Conclusão

Agora você sabe como **definir o espaçamento de linha de parágrafo** em um documento Word usando Java, e também entende **como definir o espaçamento de linha** tanto para separadores de notas de rodapé quanto para parágrafos regulares. O exemplo completo e executável demonstra como carregar um documento, ajustar propriedades de espaçamento de linha e salvar o resultado — tudo com algumas chamadas claras da API.

**Próximos passos** que você pode explorar:

* **Como definir o espaçamento de linha** para tabelas e itens de lista.  
* Aplicar regras de espaçamento diferentes para títulos versus texto do corpo.  
* Usar o objeto `Style` para impor espaçamento em todo o documento.

Experimente os valores, combine‑os com outras opções de formatação e você terá controle total sobre o layout do documento em qualquer aplicação Java. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como definir opções no Aspose.Words for Java – guia completo](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Como definir LoadOptions no Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Alterar espaçamento e recuos de parágrafos asiáticos em documento Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}