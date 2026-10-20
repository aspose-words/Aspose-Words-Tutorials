---
category: general
date: 2026-10-20
description: Crie um documento Word em branco, insira uma imagem, oculte a forma e
  salve o arquivo como DOCX. Aprenda como ocultar a imagem no Word com um guia passo
  a passo claro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- how to hide image
- save document as docx
- hide shape in word
language: pt
lastmod: 2026-10-20
og_description: Crie um documento Word em branco, depois oculte uma imagem inserida
  e salve como DOCX com este tutorial completo.
og_image_alt: Screenshot of a blank Word document with a hidden image shape
og_title: Crie um documento Word em branco e oculte uma imagem – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank Word document, insert an image, hide the shape, and
    save the file as DOCX. Learn how to hide image in Word with a clear step‑by‑step
    guide.
  headline: Create a blank Word document and hide an inserted image
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- Java
- Document processing
title: Criar um documento Word em branco e ocultar uma imagem inserida
url: /pt/java/images-shapes/create-a-blank-word-document-and-hide-an-inserted-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar um documento Word em branco e ocultar uma imagem inserida

Se você precisa **criar um documento Word em branco** que mais tarde contém uma imagem que não deseja que apareça no layout, este tutorial mostra exatamente como fazer. Você aprenderá a inserir uma imagem no Word, ocultar a forma e, finalmente, **salvar o documento como docx** para que a imagem oculta permaneça invisível aos leitores.

O guia percorre cada linha de código, explica por que cada chamada é importante e aborda armadilhas comuns, como arquivos de imagem ausentes ou várias formas ocultas. Ao final, você terá um método reutilizável que funciona com Aspose.Words for Java (versão 23.10 ou posterior).

## Pré-requisitos

* Java 17 ou superior instalado.
* Biblioteca Aspose.Words for Java (artefato Maven `com.aspose:aspose-words:23.10`).
* Um arquivo de imagem (por exemplo, `logo.png`) colocado em um diretório conhecido.
* Um entendimento básico da estrutura de projetos Java.

## Etapa 1: Criar um documento Word em branco

A primeira operação é instanciar um objeto `Document` vazio. Esse objeto representa todo o arquivo DOCX e começa sem seções ou conteúdo.

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();          // <-- primary action
        // Continue with the remaining steps
        insertAndHideImage(doc, "YOUR_DIRECTORY/logo.png");
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);
    }
}
```

**Por que isso importa:**  
Um documento em branco fornece uma tela limpa. O Aspose.Words adiciona automaticamente uma seção padrão e um único corpo vazio, permitindo que você comece a adicionar formas sem se preocupar com a configuração da página.

## Etapa 2: Inserir imagem no Word

Para inserir uma imagem, você precisa de um `DocumentBuilder`. O builder atua sobre o nó atual (o corpo do documento) e fornece o método `insertImage`, que retorna um objeto `Shape` representando a imagem.

```java
private static void insertAndHideImage(Document doc, String imagePath) throws Exception {
    // Initialize a DocumentBuilder to work with the document
    DocumentBuilder builder = new DocumentBuilder(doc);

    // Insert the image and capture the Shape object
    Shape imageShape = builder.insertImage(imagePath);   // <-- secondary keyword
    // Proceed to hide the shape
    hideShape(imageShape);
}
```

**Por que isso importa:**  
`insertImage` incorpora a imagem como uma **shape**. A `Shape` retornada permite ajustar propriedades como tamanho, layout e visibilidade. Se o caminho do arquivo estiver incorreto, o Aspose lança uma `IllegalArgumentException`, portanto pode ser desejável envolver a chamada em um bloco try‑catch para código de produção.

## Etapa 3: Ocultar forma no Word

Uma forma pode ser ocultada definindo sua propriedade `Hidden` como `true`. Quando o documento é aberto no Microsoft Word, a forma não participa do layout ou da impressão, mas permanece no arquivo.

```java
private static void hideShape(Shape shape) {
    // Hide the shape so it does not appear in the layout
    shape.setHidden(true);               // <-- how to hide image
}
```

**Por que isso importa:**  
Ocultar a forma é útil para marcas d'água, gráficos de fundo ou imagens de metadados que não devem distrair os leitores. A bandeira de ocultação é armazenada no XML subjacente (`<w:hidden/>`), tornando a imagem invisível sem excluí-la.

### Caso de borda: múltiplas imagens ocultas

Se você precisar de várias imagens invisíveis, repita a sequência inserir‑e‑ocultar para cada imagem. A chamada `setHidden(true)` funciona independentemente em cada instância de `Shape`.

```java
// Example for inserting two hidden logos
builder.insertImage("logo1.png").setHidden(true);
builder.insertImage("logo2.png").setHidden(true);
```

## Etapa 4: Salvar documento como DOCX

Finalmente, persista o `Document` em memória para um arquivo físico. A constante `SaveFormat.DOCX` garante que o arquivo seja salvo no formato moderno Office Open XML.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX); // <-- save document as docx
```

**Por que isso importa:**  
Salvar como DOCX preserva todas as propriedades da forma, incluindo a bandeira de ocultação. Se você salvar em um formato mais antigo (por exemplo, `.doc`), alguns atributos da forma podem ser perdidos.

## Exemplo completo executável

Juntando tudo, aqui está um programa autônomo que você pode compilar e executar:

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();

        // 2️⃣ Insert an image and obtain the Shape object
        DocumentBuilder builder = new DocumentBuilder(doc);
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 3️⃣ Hide the shape so it does not appear in the layout
        imageShape.setHidden(true);

        // 4️⃣ Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);

        System.out.println("Document created and saved successfully.");
    }
}
```

**Resultado esperado:**  
Abrir `HiddenShape.docx` no Microsoft Word exibe uma página completamente em branco. O arquivo de imagem está presente no pacote do documento (você pode verificar abrindo o DOCX como um zip), mas não é renderizado porque a forma está oculta.

## Perguntas comuns e solução de problemas

| Pergunta | Resposta |
|----------|----------|
| *E se o arquivo de imagem estiver ausente?* | Aspose.Words lança `FileNotFoundException`. Envolva `insertImage` em um bloco try‑catch e registre uma mensagem útil. |
| *Posso revelar a imagem posteriormente?* | Sim. Recupere a forma (`doc.getChildNodes(NodeType.SHAPE, true)`) e chame `setHidden(false)`. |
| *Ocultar afeta a conversão para PDF?* | Ao converter para PDF, formas ocultas são omitidas por padrão. Use `PdfSaveOptions.setExportHiddenObjects(true)` se precisar delas. |
| *A bandeira de ocultação é suportada em versões mais antigas do Word?* | Word 2007+ (DOCX) suporta totalmente. O formato legado `.doc` pode remover a bandeira. |

## Dicas profissionais

* **Reuse the builder:** Se você planeja adicionar mais conteúdo após a imagem, mantenha a mesma instância de `DocumentBuilder`; ela mantém a posição do cursor.
* **Set shape size before hiding:** Ajuste `imageShape.setWidth(100); imageShape.setHeight(50);` para controlar as dimensões da imagem oculta, o que pode afetar o tamanho do arquivo.
* **Batch processing:** Para lotes grandes, crie o documento uma única vez, insira todas as imagens ocultas e então salve — isso reduz a sobrecarga de I/O.

## Conclusão

Agora você sabe como **criar um documento Word em branco**, **inserir imagem no Word**, **ocultar forma no Word** e **salvar o documento como docx** usando Aspose.Words for Java. A imagem oculta permanece invisível para os usuários finais enquanto continua parte do arquivo, permitindo cenários como marcas d'água invisíveis ou armazenamento de metadados.

**Próximos passos:**  
* Explore outras propriedades de forma, como rotação, inversão e ajuste de texto.  
* Aprenda a adicionar uma marca d'água visível com `Shape.setWrapType(WrapType.NONE)`.  
* Integre esta rotina em um serviço web que gera relatórios personalizados em tempo real.

Sinta-se à vontade para experimentar múltiplas formas ocultas, diferentes formatos de imagem (PNG, JPEG, SVG) e combinar esta técnica com mesclagem de documentos para pipelines de documentos automatizados e poderosos. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar um Documento Word em Branco com uma Forma Elipse Oculta – Guia Completo em C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)
- [Inserir Imagem Flutuante em Documento Word](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Criar documento Word em branco com Aspose.Words – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}