---
category: general
date: 2026-05-04
description: Como definir a resolução para exportação de Markdown a partir do Word.
  Aprenda a resolução de imagens em markdown, como exportar equações e salvar o Word
  como markdown em Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: pt
og_description: Como definir a resolução para exportação em Markdown do Word. Este
  guia mostra a resolução de imagens em markdown, a exportação de equações e como
  salvar o Word como markdown.
og_title: Como definir a resolução ao salvar Word como Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Como definir a resolução ao salvar Word como Markdown
url: /pt/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Definir Resolução ao Salvar Word como Markdown

Já se perguntou **como definir resolução** para imagens que aparecem em um arquivo Markdown gerado a partir de um documento Word? Você não está sozinho. Muitos desenvolvedores se deparam com o problema de que as imagens matemáticas rasterizadas padrão ficam borradas, especialmente em telas de alta‑DPI.  

Neste tutorial vamos percorrer os passos exatos para controlar *resolução de imagens em markdown* enquanto também mostramos **como exportar equações** como LaTeX e, por fim, **como salvar Word como markdown** usando Aspose.Words for Java. Ao final, você terá um arquivo Markdown nítido e pronto para produção, que renderiza equações de forma limpa e imagens com a qualidade que você precisa.

## Pré‑requisitos

- Java 17 (ou qualquer JDK recente)  
- Aspose.Words for Java 23.6 ou mais recente – você pode obtê‑lo no Maven Central  
- Um documento Word (`.docx`) que contenha objetos OfficeMath (equações) e, possivelmente, imagens rasterizadas  
- Familiaridade básica com Maven/Gradle e uma IDE (IntelliJ IDEA, Eclipse, VS Code, etc.)

Nenhuma biblioteca adicional é necessária; todo o resto é tratado pelo Aspose.Words.

---

## Como Definir Resolução para Exportação em Markdown

> **Dica profissional:** A resolução que você escolher influencia diretamente o tamanho do arquivo das imagens geradas. Um valor de **300 dpi** é um bom equilíbrio para a maioria dos visualizadores de Markdown baseados na web.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

A chamada `setImageResolution(int dpi)` é o coração de **como definir resolução**. Ela indica ao Aspose.Words para rasterizar quaisquer imagens de fallback (por exemplo, quando uma equação não pode ser representada em LaTeX puro) com os pontos‑por‑polegada especificados. Se você omitir esta linha, a biblioteca usa seu padrão de 220 dpi, que pode parecer desfocado em telas retina.

### Por que usar LaTeX para equações?

Ao exportar equações como LaTeX (`OfficeMathExportMode.LATEX`), o Markdown resultante contém código LaTeX bruto envolto em `$…$` ou `$$…$$`. A maioria dos renderizadores modernos de Markdown (GitHub, GitLab, MkDocs com MathJax) renderizam isso como gráficos vetoriais nítidos e escaláveis—sem preocupações de resolução. A configuração de resolução importa apenas para **resolução de imagens em markdown** de quaisquer imagens raster de fallback, como gráficos incorporados ou fotos que não são suportados nativamente no Markdown.

---

## Como usar a Resolução de Imagens em Markdown de Forma Eficaz

Se você precisar incorporar imagens regulares (por exemplo, capturas de tela) dentro do seu arquivo Word, elas serão convertidas para PNG pelo Aspose.Words. O mesmo método `setImageResolution` se aplica, garantindo que esses PNGs herdem o DPI que você especificar. Aqui está um checklist rápido:

1. **Escolha um DPI que corresponda à sua plataforma de destino** – 72 dpi para web legada, 150 dpi para telas padrão, 300 dpi para PDFs de qualidade de impressão.  
2. **Teste a saída** – abra o arquivo `.md` gerado no seu visualizador favorito e dê zoom para verificar a nitidez.  
3. **Considere o tamanho do arquivo** – DPI mais alto gera PNGs maiores; se a largura de banda for uma preocupação, experimente 200 dpi e compare.

---

## Como Exportar Equações como LaTeX

A linha `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` indica ao Aspose.Words para traduzir cada objeto OfficeMath em LaTeX. Esta é a abordagem recomendada porque:

- **Escalabilidade** – LaTeX renderiza em qualquer tamanho sem perder qualidade.  
- **Editabilidade** – Você pode ajustar o LaTeX diretamente no arquivo Markdown posteriormente.  
- **Compatibilidade** – A maioria dos geradores de sites estáticos e ferramentas de documentação já suportam renderização de LaTeX.

Se você precisar do antigo fallback baseado em imagem, basta mudar para `OfficeMathExportMode.IMAGE`. Nesse caso, a resolução que você definiu torna‑se ainda mais crítica.

---

## Salvar Word como Markdown – Exemplo Completo de Ponta a Ponta

Abaixo está um trecho completo de projeto Maven executável que demonstra todo o fluxo, desde a declaração de dependências até a execução.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Resultado esperado:** `MathExport.md` conterá blocos LaTeX para cada equação, e quaisquer imagens incorporadas aparecerão como links PNG cujo DPI é 300. Abra o arquivo em um visualizador de Markdown que suporte MathJax (por exemplo, VS Code com a extensão Markdown Preview Enhanced) e você deverá ver equações e imagens perfeitamente nítidas.

---

## Perguntas Comuns e Casos Extremos

### E se eu precisar de um DPI diferente para apenas uma imagem?

Aspose.Words aplica o DPI globalmente via `setImageResolution`. Para lidar com DPI por imagem, você precisaria pós‑processar o Markdown gerado: substituir os arquivos PNG por versões de resolução mais alta e ajustar os links manualmente. Não é o ideal, mas é viável para alguns casos especiais.

### Isso funciona no Linux/macOS?

Com certeza. A biblioteca é pura Java, então o mesmo código roda em qualquer lugar onde o JDK roda. Apenas garanta que os caminhos de arquivo usem barras normais ou `Paths.get(...)` para tratamento independente de plataforma.

### E quanto à saída SVG?

Se preferir imagens vetoriais para gráficos, você pode definir `saveOptions.setExportImagesAsSvg(true);`. SVGs ignoram DPI, então a preocupação com **resolução de imagens em markdown** desaparece. Contudo, nem todos os renderizadores de Markdown lidam bem com SVG, então teste sua plataforma alvo primeiro.

### Posso incorporar o Markdown gerado em um gerador de site estático?

Sim. A saída é um simples `.md` com sintaxe Markdown padrão mais delimitadores LaTeX. A maioria dos geradores (Jekyll, Hugo, MkDocs) aceita isso sem ajustes. Apenas lembre‑se de habilitar MathJax ou KaTeX na configuração do seu site.

---

## Conclusão

Cobremos **como definir resolução** para imagens ao **salvar Word como markdown**, exploramos nuances de **resolução de imagens em markdown**, demonstramos **como exportar equações** como LaTeX e apresentamos a implementação Java completa. Ao ajustar `setImageResolution` e escolher o `OfficeMathExportMode` adequado, você obtém controle preciso tanto sobre a fidelidade visual quanto sobre o tamanho do arquivo.

Pronto para o próximo passo? Experimente combinar esta abordagem com Aspose.PDF para converter a mesma fonte Word diretamente em PDF, ou teste `setExportImagesAsSvg(true)` para gráficos baseados em vetor. As técnicas aprendidas aqui são blocos de construção para qualquer pipeline automatizado de documentação.

Se este guia foi útil, dê uma estrela no GitHub, compartilhe com a equipe ou deixe um comentário abaixo com suas próprias dicas. Feliz codificação!  

![How to set resolution example](resolution.png "Como definir resolução ao salvar Word como Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}