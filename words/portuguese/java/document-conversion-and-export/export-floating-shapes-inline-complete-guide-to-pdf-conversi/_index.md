---
category: general
date: 2026-07-03
description: Exportar formas flutuantes em linha ao converter Word para PDF em linha.
  Aprenda como definir opções de PDF e salvar Word como PDF usando Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: pt
og_description: Exporte formas flutuantes em linha ao converter um documento Word
  para PDF. Este tutorial mostra como definir as opções de PDF e as opções de salvar
  Word como PDF.
og_title: Exportar Formas Flutuantes Inline – Guia de Conversão de PDF em Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Exportar Formas Flutuantes em Linha – Guia Completo de Conversão para PDF
url: /pt/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar Formas Flutuantes Inline – Guia Completo para Conversão em PDF

Já precisou **exportar formas flutuantes inline** ao converter um documento Word para PDF? Você não está sozinho—muitos desenvolvedores encontram esse problema quando diagramas ou ícones misteriosamente mudam para camadas separadas. A boa notícia é que uma única opção de PDF pode manter essas formas dentro de tags `<span>`, preservando o layout exatamente como você vê no Word.

Neste tutorial vamos percorrer **como definir opções de PDF** em Java, mostrar o código exato para **salvar Word como opções de PDF**, e explicar por que você pode querer **converter Word para PDF inline** em vez da exportação padrão em nível de bloco. Ao final, você terá um snippet pronto‑para‑executar que pode ser inserido em qualquer projeto Maven ou Gradle.

## O que Você Vai Aprender

- A diferença entre exportação inline `<span>` e bloco `<div>` para formas flutuantes.  
- Como configurar `PdfSaveOptions` para forçar a renderização inline.  
- Código passo‑a‑passo que carrega um `.docx`, aplica a opção e grava um PDF.  
- Armadilhas comuns (fonts ausentes, formas não suportadas) e como evitá‑las.  
- Dicas para testar a saída e estender a abordagem a outros elementos do documento.

**Pré‑requisitos** – você precisará do Java 8 ou superior, da biblioteca Aspose.Words for Java (ou qualquer API que espelhe sua classe `PdfSaveOptions`), e de um arquivo Word de exemplo com formas flutuantes (o tutorial usa `FloatingShapes.docx`). Nenhuma outra ferramenta externa é necessária.

---

## Etapa 1: Carregar o Documento Word de Origem

A primeira coisa a fazer é abrir o `.docx` que você deseja transformar. Isso é simples, mas certifique‑se de que o caminho seja absoluto ou resolvido corretamente a partir do seu classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Por que isso importa:*  
Se o documento não for carregado corretamente, a conversão subsequente para PDF lançará um `FileNotFoundException`. Usar `Document` garante que o modelo interno de objetos esteja totalmente populado, incluindo quaisquer formas flutuantes que estejam na página.

---

## Etapa 2: Criar Opções de Salvamento PDF e Definir Formas Flutuantes como Inline

É aqui que a mágica acontece. Por padrão, Aspose.Words exporta formas flutuantes como elementos `<div>` de nível de bloco, o que pode quebrar o fluxo em PDFs baseados em HTML. Definir `setExportFloatingShapesAsInlineTag(true)` instrui o motor a envolver cada forma em um `<span>` inline.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Por que isso importa:*  
- **Fidelidade de layout** – Tags inline mantêm a forma alinhada ao texto ao redor, evitando lacunas indesejadas.  
- **Indexabilidade** – Elementos inline têm mais chances de serem indexados corretamente por leitores de PDF.  
- **Controle de estilo** – Você pode direcionar o `<span>` com CSS se, mais tarde, converter o PDF de volta para HTML.

> **Dica de especialista:** Se precisar do comportamento antigo de bloco para um documento específico, basta passar `false` ou omitir a chamada completamente.

---

## Etapa 3: Salvar o Documento como PDF Usando as Opções Configuradas

Agora você combina o `Document` carregado com o `PdfSaveOptions` e grava o arquivo. Essa única linha faz o trabalho pesado.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Por que isso importa:*  
O método `save` respeita cada flag que você definiu em `pdfOptions`. Esquecer de passar as opções reverterá para a exportação padrão em bloco, anulando o objetivo de **exportar formas flutuantes inline**.

---

## Exemplo Completo Funcional

Juntando tudo, aqui está um programa compacto que você pode compilar e executar agora mesmo. Substitua `YOUR_DIRECTORY` por um caminho real na sua máquina.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Saída esperada** – Após executar o programa, abra `FloatingShapes.pdf`. Você deverá ver as formas alinhadas ao texto, sem espaço em branco extra, e a representação HTML (se inspecionar a estrutura interna do PDF) conterá tags `<span>` ao redor de cada forma.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Texto alternativo da imagem:* **export floating shapes inline** captura de tela do PDF com formas inline.

---

## Perguntas Frequentes & Casos Limite

### 1. “E se meu documento contiver SmartArt complexo?”

SmartArt é tratado como um objeto de desenho. A flag inline funciona para a maioria das formas vetoriais, mas SmartArt muito intricado ainda pode ser renderizado como imagem. Nesses casos, considere achatar o SmartArt no Word antes da conversão, ou use `pdfOptions.setExportSmartArtAsImage(true)` para forçar a exportação como imagem.

### 2. “Posso combinar exportações inline e em bloco no mesmo documento?”

Infelizmente a API aplica a configuração globalmente. Se precisar de comportamento misto, divida o documento em seções, exporte cada seção separadamente com opções diferentes e, depois, mescle os PDFs usando `PdfMerger`.

### 3. “Isso afeta a incorporação de fontes?”

Não. A incorporação de fontes é controlada por `pdfOptions.setEmbedFullFonts(true)` (padrão). Você pode habilitar ou desabilitar isso sem tocar na flag de forma inline.

### 4. “Como verifico se as formas realmente são `<span>`?”

Abra o PDF resultante em uma ferramenta como **PDF.js** ou **Adobe Acrobat** → **Editar PDF** → **Inspetor de Objetos**. Você verá a forma envolvida por um elemento `<span>` no XML subjacente. Se aparecer `<div>`, a opção não foi aplicada.

---

## Estendendo a Abordagem – Opções Relacionadas

Aproveitando o momento, você pode explorar outros ajustes de conversão para PDF:

| Opção | O que faz | Caso de uso típico |
|--------|--------------|------------------|
| `setCompressImages(true)` | Reduz o tamanho das imagens | Downloads mais rápidos |
| `setUseHighQualityRendering(true)` | Melhora a renderização vetorial | PDFs prontos para impressão |
| `setExportDocumentStructure(true)` | Adiciona tags estruturais para acessibilidade | Conformidade WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Define explicitamente o formato (raramente necessário) | Pipelines multiformato |

Essas configurações combinam bem com cenários de **convert word to pdf inline** onde você precisa tanto de fidelidade de layout quanto de desempenho.

---

## Testando Sua Conversão

1. **Verificação visual** – Abra o PDF em dois visualizadores (Chrome e Adobe Reader) para garantir que as formas estejam alinhadas.  
2. **Diferença automatizada** – Use uma biblioteca como `pdfbox` para extrair o XML e afirmar a presença de tags `<span>`.  
3. **Benchmark de desempenho** – Meça o tempo gasto com e sem `setCompressImages` para observar o trade‑off.

Um exemplo rápido de JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Conclusão

Agora você tem uma solução sólida, de ponta a ponta, para **exportar formas flutuantes inline** ao **converter Word para PDF inline**. Configurando `PdfSaveOptions` você controla a tag HTML usada para cada forma, mantendo seus PDFs organizados e pesquisáveis. Lembre‑se de testar a saída, ajustar opções relacionadas como compressão de imagens e tratar casos limites como SmartArt complexo.

Pronto para o próximo passo? Experimente aplicar a mesma técnica para **exportar tabelas flutuantes inline** ou experimente PDFs estilizados com CSS usando `HtmlSaveOptions` da Aspose. O mesmo padrão—carregar, configurar, salvar—vale para quase todo cenário de documento‑para‑PDF.

Tem mais dúvidas sobre **como definir opções de pdf** ou precisa de ajuda com **salvar word como opções de pdf** para outra biblioteca? Deixe um comentário, e feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais abaixo abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}