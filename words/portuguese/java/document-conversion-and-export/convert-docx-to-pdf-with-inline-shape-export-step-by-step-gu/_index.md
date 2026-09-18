---
category: general
date: 2026-02-18
description: Aprenda a converter DOCX para PDF e salvar Word como PDF preservando
  formas flutuantes. Este guia mostra como exportar as formas corretamente.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: pt
og_description: Converta DOCX para PDF e aprenda como exportar formas. Siga este tutorial
  completo para salvar o Word como PDF com marcação adequada.
og_title: Converter DOCX para PDF – Guia de Exportação de Formas Inline
tags:
- Aspose.Words
- Java
- PDF conversion
title: Converter DOCX para PDF com Exportação de Formas Inline – Guia Passo a Passo
url: /pt/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Converter DOCX para PDF – Guia de Exportação de Formas Inline

Já precisou **converter DOCX para PDF** mas ficou preocupado que suas imagens flutuantes ou caixas de texto desaparecessem ou se deslocassem? Você não está sozinho. Em muitos projetos—pense em geradores automáticos de relatórios ou pipelines de processamento em lote—preservar o layout exato de um documento Word é inegociável.  

A boa notícia? Com algumas linhas de código você pode **salvar Word como PDF** e controlar se essas formas flutuantes se tornam tags inline ou permanecem como elementos de nível de bloco. A seguir você verá exatamente **como exportar formas** da maneira que deseja, além de algumas dicas que evitam armadilhas comuns.

---

## O que você vai aprender

* Carregar um arquivo `.docx` do disco.  
* Configurar `PdfSaveOptions` para que formas flutuantes sejam exportadas como tags inline.  
* Gravar o PDF resultante em uma pasta de sua escolha.  
* Entender por que a flag `setExportFloatingShapesAsInlineTag` é importante e quando você pode alterá‑la.  

Sem serviços externos, sem UI “clique‑para‑baixar” mágica—apenas código Java puro que você pode inserir em qualquer projeto Maven ou Gradle.

---

## Pré‑requisitos

| Requisito | Por que importa |
|-----------|-----------------|
| **Aspose.Words for Java** (v23.12 ou superior) | Fornece as classes `Document` e `PdfSaveOptions` usadas no exemplo. |
| **JDK 8+** | A biblioteca é compilada para Java 8 e versões posteriores; runtimes mais antigos lançarão `UnsupportedClassVersionError`. |
| **Um arquivo DOCX** com ao menos uma forma flutuante (imagem, caixa de texto, WordArt) | Para ver o efeito da opção de exportação de forma, você precisa de um documento que realmente contenha objetos flutuantes. |

Se você já tem esses itens, ótimo—vamos começar.

---

## Etapa 1 – Carregar o documento fonte  

Primeiro criamos uma instância `Document` apontando para o `.docx` que você deseja converter. O construtor lê o arquivo para a memória, analisa o pacote OpenXML e prepara o modelo interno de objetos.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Dica profissional:** Se você estiver processando muitos arquivos em um loop, reutilize um único objeto `Document` somente depois de chamar `doc.close()` (ou deixe o coletor de lixo fazer isso). Isso evita vazamentos de manipuladores de arquivo no Windows.

---

## Etapa 2 – Configurar as opções de salvamento PDF para exportar formas  

O coração do tutorial está aqui. `PdfSaveOptions` permite definir como a conversão se comporta. Definir `setExportFloatingShapesAsInlineTag(true)` força que cada forma flutuante seja tratada como um elemento *inline* na estrutura de tags do PDF. Isso significa que leitores de tela lerão a forma na mesma ordem do texto ao redor, o que costuma ser exigido para conformidade de acessibilidade.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Quando você definiria isso como `false`?**  
Se o seu PDF for destinado apenas à impressão e você quiser que as formas mantenham seu posicionamento original sem afetar a ordem lógica de leitura, pode preferir a marcação em nível de bloco. O padrão é `false`, então habilitamos explicitamente o comportamento inline para este tutorial.

---

## Etapa 3 – Salvar o documento como PDF  

Agora que as opções estão prontas, chame `save` com o nome de arquivo de destino e o objeto de opções. A biblioteca cuida do trabalho pesado: motor de layout, incorporação de fontes e geração de tags.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Após a chamada terminar, você encontrará `shapes.pdf` na pasta especificada. Abra‑o no Adobe Acrobat ou em qualquer visualizador de PDF que mostre tags (geralmente em **File → Properties → Tags**) e verá que a forma flutuante aparece como uma tag inline.

---

## Exemplo completo e executável  

Juntando tudo, aqui está uma classe Java autônoma que você pode compilar e executar. Certifique‑se de que o JAR do Aspose.Words esteja no seu classpath.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado:**  
- O arquivo PDF contém o mesmo conteúdo textual do DOCX original.  
- Qualquer imagem ou caixa de texto flutuante agora está marcada como *inline*, ou seja, aparece na ordem de leitura em vez de blocos separados.  
- Se você abrir o painel **Tags** do PDF, verá um elemento `<Figure>` aninhado dentro de um `<Paragraph>`—exatamente o que `setExportFloatingShapesAsInlineTag(true)` garante.

---

## Perguntas frequentes & Casos de borda  

### 1️⃣ Isso funciona com arquivos DOCX protegidos por senha?  
Sim—basta fornecer a senha antes de carregar:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ E quanto a imagens SVG ou EMF dentro do Word?  
Aspose.Words rasteriza automaticamente gráficos vetoriais ao salvar em PDF. Se precisar que eles permaneçam vetoriais, defina:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Como preservo hyperlinks durante a conversão?  
Links são mantidos por padrão. Contudo, se você desativar tags (`pdfOptions.setSaveFormat(SaveFormat.PDF)` sem opções), pode perder a estrutura lógica. Mantenha o objeto `PdfSaveOptions` para reter tanto tags quanto links.

### 4️⃣ Posso processar em lote uma pasta de arquivos DOCX?  
Absolutamente. Envolva a lógica `DocxToPdfWithShapes` em um loop que itere sobre `Files.list(Paths.get("YOUR_DIRECTORY"))`. Lembre‑se de tratar exceções por arquivo para que um documento problemático não interrompa a execução inteira.

---

## Dicas de campo  

* **Fique atento a fontes ausentes.** Se o DOCX fonte usar uma fonte personalizada que não esteja instalada no servidor, o PDF substituirá por uma fonte fallback, possivelmente quebrando o layout. Use `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` para forçar a incorporação.  
* **Testando acessibilidade.** Após a conversão, execute o **Accessibility Checker** do Acrobat. A marcação inline costuma melhorar a pontuação, mas ainda pode ser necessário adicionar texto alternativo às imagens manualmente.  
* **Dica de desempenho:** Para documentos grandes (100+ páginas), habilite `pdfOptions.setMemoryOptimization(true)` para reduzir o uso de heap.

---

## Confirmação visual  

Abaixo está uma captura de tela rápida do PDF aberto no Adobe Acrobat, mostrando a forma marcada como inline realçada no painel **Tags**.

![Convert DOCX to PDF example output](image.png)

*Texto alternativo: exemplo de saída de conversão de docx para pdf mostrando tags de forma inline.*

---

## Conclusão  

Agora você sabe **como converter DOCX para PDF** controlando a forma como objetos flutuantes são exportados. Ao alternar `setExportFloatingShapesAsInlineTag`, decide se as formas entram na ordem de leitura ou permanecem como blocos independentes—crucial tanto para acessibilidade quanto para fidelidade visual.  

A partir daqui você pode:

* **Salvar Word como PDF** em massa para arquivamento.  
* Experimentar outras `PdfSaveOptions` como `setCompliance(PdfCompliance.PDF_A_1B)` para preservação a longo prazo.  
* Aprofundar em **como exportar formas** explorando a documentação completa do Aspose.Words ou testando a flag `setExportDocumentStructure(true)` para árvores de tags mais ricas.

Teste, ajuste as opções e deixe seus PDFs exatamente como você precisa. Boa codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}