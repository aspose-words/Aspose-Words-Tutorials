---
category: general
date: 2026-04-28
description: Crie um documento PDF UA usando Aspose.Words para Java. Aprenda a carregar
  docx com recuperação, exportar equações para LaTeX, salvar markdown a partir do
  Word e recuperar fontes ausentes.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: pt
og_description: Crie documento PDF UA com Aspose.Words para Java. Guia passo a passo
  que cobre carregamento de recuperação, exportação para LaTeX, salvamento em Markdown
  e recuperação de fontes ausentes.
og_title: Criar Documento PDF UA – Tutorial Completo de Java
tags:
- Aspose.Words
- Java
- PDF/UA
title: Criar documento PDF UA com Aspose.Words – Guia completo em Java
url: /pt/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento PDF UA – Tutorial Completo em Java

Precisa **criar um documento PDF UA** a partir de um arquivo Word enquanto lida com conteúdo corrompido? Neste tutorial, vamos guiá‑lo através do carregamento de um DOCX com recuperação, exportação de equações para LaTeX, salvamento de Markdown a partir do Word e recuperação de fontes ausentes — tudo com Aspose.Words para Java.  

Se você já ficou encarando um .docx quebrado e se perguntou por que seu PDF não é acessível, está no lugar certo. Ao final, você terá um arquivo PDF/UA 1 totalmente compatível, uma versão em Markdown que contém equações LaTeX e uma lista clara de quaisquer substituições de fontes que ocorreram durante o carregamento.

## O que você precisará

- **Aspose.Words for Java** (versão mais recente em 2026) – adicione a dependência Maven/Gradle ou o JAR ao seu classpath.  
- Java 17 ou superior (a API usa streams, portanto um JDK recente é recomendado).  
- Um exemplo `input.docx` que pode conter seções corrompidas, equações Office Math e formas flutuantes.  

Nenhuma biblioteca extra é necessária; tudo está dentro do Aspose.Words.

---

## Etapa 1 – Carregar DOCX no modo de Recuperação  

Quando um documento está parcialmente danificado, o carregador padrão lança uma exceção. Ao habilitar o modo de recuperação, você diz ao Aspose.Words para continuar e exibir avisos em vez disso.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Por que isso importa:* O modo de recuperação impede que todo o seu pipeline quebre por causa de um único parágrafo defeituoso. Ele também preenche `doc.getWarnings()` para que você possa, mais tarde, **recuperar fontes ausentes** e outros problemas.

---

## Etapa 2 – Exportar Equações para LaTeX dentro de um Arquivo Markdown  

A maioria dos desenvolvedores adora Markdown para documentação, mas as equações nativas do Word são difíceis de copiar. Aspose.Words pode traduzi‑las diretamente para LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Dica profissional:* O callback garante que cada imagem extraída seja salva em `imgs/`. Isso reproduz como o GitHub renderiza Markdown – limpo e portátil.

---

## Etapa 3 – Criar Documento PDF / UA com Marcação Adequada  

A conformidade PDF/UA (Universal Accessibility) é obrigatória para muitos projetos do setor público. As opções a seguir fazem o Aspose.Words marcar formas flutuantes corretamente e definir a flag de conformidade PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*O que você verá:* Ao abrir `output.pdf` no Adobe Acrobat Pro, aparecerá “PDF/UA‑1 compliant” nas propriedades do documento. Todas as formas flutuantes (caixas de texto, imagens) terão tags apropriadas para leitores de tela.

---

## Etapa 4 – Ajustar a Sombra de uma Forma (Estilização Opcional)  

Embora não seja exigido para acessibilidade, ajustar aspectos visuais pode ser útil para relatórios internos.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Por que fazer isso?* Se o PDF também for uma peça de marketing, uma sombra sutil deixa o layout mais polido sem quebrar a conformidade.

---

## Etapa 5 – Recuperar Fontes Ausentes e Outros Avisos  

Durante o carregamento em modo de recuperação, Aspose.Words registra quaisquer substituições de fontes. Listá‑las ajuda a decidir se você deve incorporar a fonte correta ou aceitar a alternativa.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Saída típica* (seu console mostrará algo como):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Se você vir fontes críticas faltando, considere instalá‑las no servidor ou incorporá‑las via `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Exemplo Completo Funcional  

Abaixo está a classe Java completa, pronta para ser executada. Cole no seu IDE, ajuste os caminhos e pressione **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Resultados esperados**

| Saída | Descrição |
|--------|-------------|
| `output.md` | Arquivo Markdown onde cada equação Office Math aparece como LaTeX (`$…$`). Imagens são armazenadas em `imgs/`. |
| `output.pdf` | Documento compatível com PDF/UA‑1; abra no Acrobat para ver “PDF/UA‑1” em Arquivo → Propriedades → Padrões. |
| Console | Lista de quaisquer fontes ausentes, por exemplo, “Missing: Calibri → substituted: Arial”. |

---

## Perguntas Frequentes (FAQ)

**P: Isso funciona com versões mais antigas do Aspose.Words?**  
R: Os enums `RecoveryMode`, `OfficeMathExportMode.LATEX` e `PdfCompliance.PDF_UA_1` foram introduzidos na 22.8. Se você estiver usando uma versão anterior, atualize – os recursos de acessibilidade não foram retro‑portados.

**P: E se eu precisar incorporar as fontes originais em vez de usar substituição?**  
R: Defina `pdfOptions.setEmbedFullFonts(true)` e garanta que os arquivos de fonte estejam acessíveis no caminho de fontes da JVM.

**P: Posso exportar para outros formatos de marcação (por exemplo, HTML) mantendo as equações LaTeX?**  
R: Sim. Use `HtmlSaveOptions` e configure `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – o mesmo enum funciona em diferentes formatos.

**P: Meu DOCX contém muitas formas flutuantes; todas serão marcadas?**  
R: Com `setExportFloatingShapesAsInlineTag(true)`, o Aspose.Words envolve cada forma flutuante em uma tag `<Figure>` para PDF/UA, atendendo à maioria das verificações de leitores de tela.

---

## Conclusão  

Acabamos de mostrar como **criar um documento PDF UA** a partir de uma fonte Word, ao mesmo tempo em que **carregamos o docx com recuperação**, **exportamos equações para LaTeX**, **salvamos markdown do Word** e **recuperamos fontes ausentes**. O código é totalmente autocontido, roda em qualquer ambiente Java 17+ e produz ativos prontos tanto para auditorias de acessibilidade quanto para desenvolvedores.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}