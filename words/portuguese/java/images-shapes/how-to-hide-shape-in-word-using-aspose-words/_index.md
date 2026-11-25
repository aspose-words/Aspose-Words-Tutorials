---
category: general
date: 2026-11-25
description: Oculte a forma no Word com Aspise.Words e aprenda a criar documentos
  Word com Aspose enquanto insere uma forma retangular no Word em apenas algumas linhas
  de código.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: pt
lastmod: 2026-11-25
og_description: Ocultar forma no Word usando Aspose.Words. Este tutorial mostra como
  criar um documento Word com Aspose, inserir uma forma retangular no Word e ocultá‑la
  programaticamente.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Ocultar forma no Word com Aspose.Words – guia rápido passo a passo
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Como ocultar forma no Word usando Aspose.Words
url: /pt/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como ocultar forma no Word usando Aspose.Words

Se você precisar **ocultar forma no Word** ao gerar documentos programaticamente, o Aspose.Words torna isso simples. Neste guia você verá exatamente como criar um documento Word aspose, inserir forma retangular word, e então ocultar essa forma para que não apareça no layout. O exemplo completo e executável é fornecido para que você possa copiar‑colar no seu IDE e ver o resultado imediatamente.

Você concluirá este tutorial com um arquivo Word que contém um retângulo oculto — útil para marcadores de posição, conteúdo condicional ou metadados que devem permanecer invisíveis ao leitor. Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words for Java (ou .NET).

## O que você aprenderá

* Como **criar um documento Word aspose** do zero.  
* Como **inserir forma retangular word** usando o `DocumentBuilder`.  
* Como definir a propriedade `hidden` da forma para que não seja renderizada no layout final.  
* Como verificar se a forma está oculta e como torná‑la visível novamente, se necessário.  

### Pré‑requisitos

* Java 17+ (ou .NET 6+ se preferir C# — as chamadas da API são análogas).  
* Aspose.Words for Java 24.x (a versão mais recente no momento da escrita).  
* Uma IDE como IntelliJ IDEA, Eclipse ou VS Code.  

> **Dica profissional:** Use a licença temporária gratuita da Aspose se ainda não possuir uma licença comercial. A biblioteca funciona sem licença para avaliação, mas uma licença remove as marcas d'água de avaliação.

## Ocultar forma no Word com Aspose.Words

Os passos principais são:

1. **Criar um novo `Document`.**  
2. **Inserir uma forma retangular** usando `DocumentBuilder`.  
3. **Marcar a forma como oculta** para que não apareça quando o arquivo for aberto.  

### Etapa 1: Criar um documento Word aspose

Primeiro, instancie um `Document` em branco e um `DocumentBuilder`. O builder fornece uma API fluente para adicionar conteúdo, incluindo formas.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Por que isso importa:**  
Criar um `Document` novo fornece uma tela limpa. O `DocumentBuilder` é a forma recomendada de modificar o documento porque ele rastreia automaticamente o ponto de inserção atual e gerencia seções/páginas para você.

### Etapa 2: Inserir forma retangular word

Agora adicionamos uma forma retangular. O método `insertShape` requer o tipo de forma e suas dimensões em pontos (1 ponto = 1/72 polegada).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Por que isso importa:**  
`insertShape` cria um objeto de desenho que vive na parte *drawing* do documento. Ao especificar o tamanho, você controla quanto espaço a forma ocuparia se estivesse visível. A estilização opcional ajuda a verificar a forma antes de ocultá‑la.

### Etapa 3: Ocultar a forma para que não apareça no layout

Aspose.Words reproduz o atributo *Hidden* do Microsoft Word. Definir como `true` indica ao Word que omita a forma na renderização, mantendo o objeto na estrutura do documento.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Por que isso importa:**  
Uma forma oculta ainda pode ser acessada programaticamente (por exemplo, para processamento condicional) e pode ser tornada visível posteriormente alterando a propriedade. Isso é ideal para cenários como **marcadores de posição condicionais** que devem aparecer apenas para determinados públicos.

### Etapa 4: Salvar e verificar o resultado

Finalmente, grave o documento no disco. Abra o arquivo no Microsoft Word para confirmar que o retângulo não está visível. Você também pode inspecionar o XML subjacente para ver a flag oculta.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Saída esperada:**  
Executar o programa imprime:

```
Document saved to HideShapeResult.docx
```

Ao abrir *HideShapeResult.docx* no Word, a página aparece vazia (ou contém qualquer outro conteúdo que você adicionou antes da forma). O retângulo está presente no XML do arquivo (atributo `<w:hidden>`) mas não é renderizado.

### Etapa 5: (Opcional) Tornar a forma visível novamente mais tarde

Se precisar tornar a forma visível novamente, carregue o documento, localize a forma e defina `hidden` como `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Por que isso importa:**  
Ser capaz de alternar a flag oculta dá controle total sobre a geração dinâmica de documentos — por exemplo, você pode gerar um documento mestre com todos os elementos opcionais ocultos e, então, tornar visíveis seletivamente com base nas preferências do usuário.

## Exemplo completo e executável (criar documento Word aspose, inserir forma retangular word, ocultar forma)

Abaixo está o programa completo que você pode compilar e executar diretamente.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Executando o código**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Substitua `aspose-words-24.10.jar` pela versão real que você baixou.

### O que os arquivos de saída contêm

* **HideShapeResult.docx** – o retângulo está oculto; a página parece vazia.  
* **UnhiddenShape.docx** – o mesmo retângulo está visível, mostrando uma caixa vermelha com contorno preto.

## Perguntas comuns e tratamento de casos extremos

| Question | Answer |
|----------|--------|
| *A forma oculta afetará a paginação?* | Não. Objetos ocultos são ignorados pelo mecanismo de layout, portanto não empurram o texto para uma nova página. |
| *Posso ocultar outros objetos do Word (por exemplo, imagens, tabelas)?* | Sim. A maioria das subclasses de `Node` (incluindo `Shape`, `Paragraph`, `Run`) expõe um método `setHidden(boolean)`. |
| *E se o documento já contiver formas?* | Use `doc.getChildNodes(NodeType.SHAPE, true)` para iterar e ocultar apenas as formas que você deseja. |
| *Ocultar uma forma aumenta o tamanho do arquivo?* | Um pouco, porque o XML da forma permanece. O impacto é insignificante para documentos típicos. |
| *A flag oculta será mantida quando o documento for salvo como PDF?* | Ao converter para PDF, as formas ocultas são omitidas por padrão. Você pode controlar isso com `PdfSaveOptions` se necessário. |

## Melhores práticas ao trabalhar com objetos ocultos

* **Nomeie suas formas** usando `setName("MyPlaceholder")`. Isso facilita localizá‑las posteriormente.  
* **Agrupe objetos ocultos relacionados** dentro de um `GroupShape` se precisar alternar a visibilidade de vários elementos de uma vez.  
* **Documente o propósito** dos elementos ocultos em comentários ou em um arquivo de especificação separado — futuros mantenedores apreciarão o contexto.  
* **Evite usar excessivamente objetos ocultos**; eles aumentam a complexidade do documento e podem confundir os usuários finais que inspecionam o XML manualmente.  

## Conclusão

Agora você sabe como **ocultar forma no Word** usando Aspose.Words, como **criar documento Word aspose** e como **inserir forma retangular word** antes de ocultá‑la. O exemplo demonstra todo o ciclo de vida: criação, inserção, ocultação, salvamento e, opcionalmente, tornar visível. Aplique essas técnicas para construir relatórios dinâmicos, modelos condicionais ou qualquer fluxo de trabalho automatizado no Word onde marcadores de posição invisíveis são necessários.

### Próximos passos

* Explore **conteúdo condicional** combinando formas ocultas com campos de mesclagem de correspondência.  
* Aprenda como **ocultar execuções de texto** (`Run.setHidden(true)`) para controle mais granular.  
* Consulte a documentação do Aspose.Words sobre **proteção de documentos** para impedir que usuários revelem acidentalmente formas ocultas.

Feliz codificação, e deixe seus arquivos Word gerados limpos enquanto ainda carregam os dados ocultos de que você precisa!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Criar um documento Word programaticamente, adicionar e ocultar uma forma em Java usando Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Como ocultar forma em um documento Word usando Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Criar um documento Word .docx em branco e adicionar uma forma retangular oculta com Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}