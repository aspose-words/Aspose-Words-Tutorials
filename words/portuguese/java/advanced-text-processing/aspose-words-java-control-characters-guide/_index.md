---
date: '2025-11-12'
description: Aprenda como inserir caracteres de controle, gerenciar retornos de carro
  e adicionar quebras de página ou de coluna em Java usando Aspose.Words para formatação
  precisa de documentos.
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: pt
title: Inserir caracteres de controle em Java com Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

We need to translate the provided content to Portuguese, preserving markdown, code blocks placeholders unchanged, not translating URLs, file paths, variable names, function names. Also keep technical terms in English. Also note rule 6: "For Portuguese, ensure proper RTL formatting if needed" but Portuguese is LTR, so ignore.

We need to translate all textual content, headings, table contents, bullet points, etc. Keep placeholders like ```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
``` unchanged. Also keep the block tags unchanged.

We must not translate the block tags themselves: they are part of the content. So we keep them as is.

We need to translate the tutorial text.

Let's go through line by line.

Start:

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Control Characters in Java with Aspose.Words

Translate heading: "# Inserir Caracteres de Controle em Java com Aspose.Words"

## Introduction

"## Introdução"

Then the paragraph:

"Do you need pixel‑perfect control over line breaks, tabs, or page divisions when generating invoices, reports, or newsletters?" translate: "Você precisa de controle pixel‑perfeito sobre quebras de linha, tabulações ou divisões de página ao gerar faturas, relatórios ou newsletters?" Keep hyphen.

"Control characters are the invisible building blocks that let you shape document layout programmatically." -> "Os caracteres de controle são os blocos invisíveis que permitem modelar o layout do documento programaticamente."

"In this tutorial you’ll learn how to **insert**, **verify**, and **manage** control characters such as carriage returns, non‑breaking spaces, and column breaks using the Aspose.Words for Java API." -> "Neste tutorial, você aprenderá a **inserir**, **verificar** e **gerenciar** caracteres de controle, como retornos de carro, espaços não‑quebráveis e quebras de coluna, usando a API Aspose.Words for Java."

**What you’ll achieve:** -> "**O que você alcançará:**"

List items translate.

1. Insert and validate carriage returns, line feeds, and page breaks. -> "Inserir e validar retornos de carro, feeds de linha e quebras de página."

2. Add spaces, tabs, non‑breaking spaces, and column breaks to create multi‑column layouts. -> "Adicionar espaços, tabulações, espaços não‑quebráveis e quebras de coluna para criar layouts de múltiplas colunas."

3. Apply best‑practice performance tips for large‑scale document automation. -> "Aplicar dicas de desempenho de boas práticas para automação de documentos em grande escala."

## Prerequisites

"## Pré-requisitos"

Paragraph: "Before we start, make sure you have the following ready:" -> "Antes de começarmos, certifique‑se de que você tem o seguinte pronto:"

Table: translate headers and content.

| Requirement | Details |
|-------------|----------|
| **Aspose.Words for Java** | Version 25.3 or newer (the API remains stable across later releases). |
| **JDK** | Java 8 + (Java 11 or 17 recommended). |
| **IDE** | IntelliJ IDEA, Eclipse, or any Java‑compatible editor. |
| **Build tool** | Maven **or** Gradle for dependency management. |
| **License** | A temporary or purchased Aspose.Words license file. |

Translate each cell but keep code formatting.

Requirement -> "Requisito". Details -> "Detalhes".

Rows:

**Aspose.Words for Java** -> same. "Version 25.3 or newer (the API remains stable across later releases)." -> "Versão 25.3 ou mais recente (a API permanece estável nas versões posteriores)."

**JDK** -> same. "Java 8 + (Java 11 or 17 recommended)." -> "Java 8 + (Java 11 ou 17 recomendado)."

**IDE** -> same. "IntelliJ IDEA, Eclipse, or any Java‑compatible editor." -> "IntelliJ IDEA, Eclipse ou qualquer editor compatível com Java."

**Build tool** -> "Ferramenta de compilação". "Maven **or** Gradle for dependency management." -> "Maven **ou** Gradle para gerenciamento de dependências."

**License** -> "Licença". "A temporary or purchased Aspose.Words license file." -> "Um arquivo de licença Aspose.Words temporário ou adquirido."

### Quick Environment Checklist

"### Lista de Verificação Rápida do Ambiente"

1. Maven **or** Gradle installed. -> "1. Maven **ou** Gradle instalado."

2. License file accessible (e.g., `src/main/resources/aspose.words.lic`). -> "2. Arquivo de licença acessível (por exemplo, `src/main/resources/aspose.words.lic`)."

3. Project compiled without errors. -> "3. Projeto compilado sem erros."

## Setting Up Aspose.Words

"## Configurando Aspose.Words"

We’ll first add the library to the project, then load the license. Choose the build system that matches your workflow.

Translate: "Primeiro adicionaremos a biblioteca ao projeto e, em seguida, carregaremos a licença. Escolha o sistema de compilação que corresponde ao seu fluxo de trabalho."

### Maven Dependency

"### Dependência Maven"

Add the following snippet to your `pom.xml` inside `<dependencies>`:

"Adicione o seguinte trecho ao seu `pom.xml` dentro de `<dependencies>`:"

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
``` keep.

### Gradle Dependency

"### Dependência Gradle"

Insert this line into the `dependencies` block of `build.gradle`:

"Insira esta linha no bloco `dependencies` do `build.gradle`:"

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization (Java code)

"### Inicialização da Licença (código Java)"

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Note:** Replace `"path/to/aspose.words.lic"` with the actual path to your license file.

Translate note: "> **Nota:** Substitua `"path/to/aspose.words.lic"` pelo caminho real do seu arquivo de licença."

## Feature 1: Handle Carriage Returns and Page Breaks

"## Recurso 1: Manipular Retornos de Carro e Quebras de Página"

Carriage returns (`ControlChar.CR`) and page breaks (`ControlChar.PAGE_BREAK`) are essential when you need the output text to reflect the visual layout of a document.

Translate: "Retornos de carro (`ControlChar.CR`) e quebras de página (`ControlChar.PAGE_BREAK`) são essenciais quando você precisa que o texto de saída reflita o layout visual de um documento."

### Step‑by‑Step Implementation

"### Implementação Passo a Passo"

1. **Create a new Document and DocumentBuilder.** -> "1. **Criar um novo Document e DocumentBuilder.**"

2. **Write two paragraphs.** -> "2. **Escrever dois parágrafos.**"

3. **Verify that the generated text contains the expected control characters.** -> "3. **Verificar se o texto gerado contém os caracteres de controle esperados.**"

4. **Trim the text and re‑check the result.** -> "4. **Remover espaços extras do texto e verificar novamente o resultado.**"

#### 1. Create a Document

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Paragraphs

```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. Verify Control Characters

```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. Trim and Check Text

```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**Result:** The `doc.getText()` string now contains explicit CR and page‑break symbols, guaranteeing that downstream systems (e.g., plain‑text exporters) preserve the layout.

Translate: "**Resultado:** A string `doc.getText()` agora contém símbolos explícitos de CR e quebra de página, garantindo que sistemas downstream (por exemplo, exportadores de texto simples) preservem o layout."

## Feature 2: Insert Various Control Characters

"## Recurso 2: Inserir Diversos Caracteres de Controle"

Beyond carriage returns, Aspose.Words offers constants for spaces, tabs, line feeds, paragraph breaks, and column breaks. This section shows how to embed each one.

Translate: "Além dos retornos de carro, Aspose.Words oferece constantes para espaços, tabulações, feeds de linha, quebras de parágrafo e quebras de coluna. Esta seção mostra como inserir cada um."

### Step‑by‑Step Implementation

"### Implementação Passo a Passo"

1. **Initialize a fresh DocumentBuilder.** -> "1. **Inicializar um novo DocumentBuilder.**"

2. **Write examples for space, non‑breaking space, and tab characters.** -> "2. **Escrever exemplos para caracteres de espaço, espaço não‑quebrável e tabulação.**"

3. **Add line feeds, paragraph breaks, and section breaks, then validate node counts.** -> "3. **Adicionar feeds de linha, quebras de parágrafo e quebras de seção, então validar contagens de nós.**"

4. **Create a two‑column layout and insert a column break.** -> "4. **Criar um layout de duas colunas e inserir uma quebra de coluna.**"

#### 1. Initialize DocumentBuilder

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Space‑Related Characters

- **Space (`ControlChar.SPACE_CHAR`)** -> "- **Espaço (`ControlChar.SPACE_CHAR`)**"

```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```

- **Non‑Breaking Space (`ControlChar.NON_BREAKING_SPACE`)** -> "- **Espaço Não‑Quebrável (`ControlChar.NON_BREAKING_SPACE`)**"

```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```

- **Tab (`ControlChar.TAB`)** -> "- **Tabulação (`ControlChar.TAB`)**"

```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. Line, Paragraph, and Section Breaks

```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. Column Break in a Multi‑Column Layout

```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**Result:** The document now contains a two‑column page where text flows automatically from the first column to the second after the `COLUMN_BREAK`.

Translate: "**Resultado:** O documento agora contém uma página de duas colunas onde o texto flui automaticamente da primeira coluna para a segunda após o `COLUMN_BREAK`."

## Practical Applications

"## Aplicações Práticas"

Table headings translate.

| Scenario | How Control Characters Help |
|----------|-----------------------------|
| **Invoice Generation** | Use `PAGE_BREAK` to start a new page for each invoice batch. |
| **Financial Report** | Align figures with `TAB` and keep headings together using `NON_BREAKING_SPACE`. |
| **Newsletter Layout** | Create side‑by‑side articles with `COLUMN_BREAK` in a multi‑column section. |
| **CMS Content Export** | Preserve line structure when converting rich text to plain text via `LINE_FEED`. |
| **Automated Templates** | Dynamically insert `PARAGRAPH_BREAK` or `SECTION_BREAK` based on user input. |

Translate:

Scenario -> "Cenário". How Control Characters Help -> "Como os Caracteres de Controle Ajudam".

Rows:

**Invoice Generation** -> "**Geração de Faturas**". "Use `PAGE_BREAK` to start a new page for each invoice batch." -> "Use `PAGE_BREAK` para iniciar uma nova página para cada lote de faturas."

**Financial Report** -> "**Relatório Financeiro**". "Align figures with `TAB` and keep headings together using `NON_BREAKING_SPACE`." -> "Alinhar números com `TAB` e manter cabeçalhos juntos usando `NON_BREAKING_SPACE`."

**Newsletter Layout** -> "**Layout de Newsletter**". "Create side‑by‑side articles with `COLUMN_BREAK` in a multi‑column section." -> "Criar artigos lado a lado com `COLUMN_BREAK` em uma seção de múltiplas colunas."

**CMS Content Export** -> "**Exportação de Conteúdo CMS**". "Preserve line structure when converting rich text to plain text via `LINE_FEED`." -> "Preservar a estrutura de linhas ao converter texto rico para texto simples via `LINE_FEED`."

**Automated Templates** -> "**Modelos Automatizados**". "Dynamically insert `PARAGRAPH_BREAK` or `SECTION_BREAK` based on user input." -> "Inserir dinamicamente `PARAGRAPH_BREAK` ou `SECTION_BREAK` com base na entrada do usuário."

## Performance Considerations

"## Considerações de Desempenho"

* **Batch Inserts:** Group multiple `write` calls into a single operation to reduce internal reflows. -> "* **Inserções em Lote:** Agrupe múltiplas chamadas `write` em uma única operação para reduzir reflows internos.*"

* **Avoid Frequent Node Traversal:** Cache `NodeCollection` results when you need to count paragraphs repeatedly. -> "* **Evite Traversal Frequente de Nós:** Cache os resultados de `NodeCollection` quando precisar contar parágrafos repetidamente.*"

* **Profile Large Docs:** Use Java profilers (e.g., VisualVM) to identify hotspots in text manipulation loops. -> "* **Perfil de Documentos Grandes:** Use perfis Java (por exemplo, VisualVM) para identificar pontos críticos em loops de manipulação de texto.*"

## Conclusion

"## Conclusão"

You now have a concrete, step‑by‑step method for **inserting**, **validating**, and **optimizing** control characters in Java documents using Aspose.Words. These techniques empower you to produce professional‑grade invoices, reports, and multi‑column publications programmatically.

Translate: "Agora você tem um método concreto, passo a passo, para **inserir**, **validar** e **otimizar** caracteres de controle em documentos Java usando Aspose.Words. Essas técnicas permitem que você produza faturas, relatórios e publicações de múltiplas colunas de nível profissional programaticamente."

## Next Steps

"## Próximos Passos"

1. Experiment with additional `ControlChar` constants such as `EM_SPACE` or `EN_SPACE`. -> "1. Experimente constantes