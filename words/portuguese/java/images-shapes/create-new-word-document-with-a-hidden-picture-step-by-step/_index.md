---
category: general
date: 2026-09-27
description: Crie um novo documento Word e insira uma forma de imagem que permaneça
  oculta. Aprenda como ocultar a forma e adicionar uma imagem oculta usando Aspose.Words
  para Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: pt
lastmod: 2026-09-27
og_description: Crie um novo documento Word e insira uma forma de imagem que permanece
  oculta. Aprenda como ocultar a forma e adicionar uma imagem oculta usando Aspose.Words
  para Java.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: Criar novo documento Word com uma imagem oculta – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: Criar novo documento do Word com uma imagem oculta – guia passo a passo
url: /pt/java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar novo documento Word com uma imagem oculta – guia passo a passo

Se você precisa **create new Word document** que contém um logotipo, mas não quer que o logotipo afete o layout da página, este guia mostra exatamente como fazer isso. Você aprenderá como **insert image shape**, entender **how to hide shape**, e finalmente **add hidden picture** ao arquivo sem nenhum impacto visual.

O tutorial cobre tudo, desde a configuração do projeto até a etapa final de verificação. Ao final, você terá um programa Java totalmente funcional que cria um arquivo Word, insere uma forma de imagem, a oculta e salva o resultado. Nenhuma ferramenta extra é necessária além da biblioteca Aspose.Words for Java.

## Pré-requisitos

* Java 17 (ou mais recente) instalado.
* Um projeto Maven ou Gradle onde você pode adicionar dependências.
* Aspose.Words for Java 23.9 (ou a versão mais recente) – veja o repositório Maven oficial para as coordenadas corretas.
* Um arquivo de imagem (por exemplo, `logo.png`) colocado em uma pasta que você pode referenciar a partir do seu código.

> **Dica profissional:** Mantenha a imagem no mesmo diretório do seu arquivo fonte durante o desenvolvimento; isso simplifica o manuseio de caminhos.

## Etapa 1: Configurar o projeto e importar Aspose.Words

Adicione a dependência Aspose.Words ao seu `pom.xml` (Maven) ou `build.gradle` (Gradle). Abaixo está o trecho Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Agora crie uma classe Java chamada `HiddenPictureDemo`. As primeiras linhas importam as classes necessárias e **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Por que isso importa:* `Document` representa o arquivo `.docx` completo, enquanto `DocumentBuilder` fornece uma API fluente para adicionar conteúdo como parágrafos, tabelas e formas.

## Etapa 2: Inserir forma de imagem no documento Word

A próxima operação demonstra **how to insert image** como uma forma. Usar `DocumentBuilder.insertImage` retorna um objeto `Shape` que você pode manipular ainda mais.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*Por que usar uma forma:* Uma imagem inserida como forma lhe dá acesso a propriedades de layout como visibilidade, quebra de texto e posicionamento, que são essenciais para ocultar a imagem posteriormente.

## Etapa 3: Ocultar a forma para que não apareça no layout

Agora respondemos **how to hide shape**. Definir a propriedade `Hidden` como `true` remove a forma do layout visual enquanto a mantém na estrutura do documento.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*Explicação:* `setHidden(true)` indica ao Word que trate a forma como invisível. O adicional `setWrapType(WrapType.NONE)` garante que a imagem oculta não reserve espaço, preservando o fluxo original do documento.

## Etapa 4: Salvar o documento e verificar a imagem oculta

Finalmente, persista o arquivo no disco. A imagem oculta permanece parte do documento, mas não é exibida quando o arquivo é aberto no Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

Ao abrir `HiddenShape.docx` no Word, você verá uma página normal e limpa sem logotipo visível, porém a imagem está armazenada dentro do arquivo. Você pode verificar sua presença abrindo o `.docx` como um arquivo zip e inspecionando a pasta `word/media`.

### Saída esperada

Executar o programa imprime:

```
Document created successfully with a hidden picture.
```

Abrir o `HiddenShape.docx` gerado mostra uma página vazia (ou qualquer conteúdo que você adicionou em outro lugar) e nenhuma imagem visível. Se você descompactar o `.docx`, encontrará `logo.png` dentro de `word/media`, confirmando que a imagem foi **add hidden picture** corretamente.

## Como inserir imagem em outros contextos

Se você precisar **insert image shape** em um parágrafo específico ao invés da posição atual do cursor, pode mover o builder primeiro:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

Esse padrão funciona para cabeçalhos, rodapés ou tabelas—basta mover o builder para o nó alvo antes de chamar `insertImage`.

## Variações comuns e casos extremos

| Cenário | O que ajustar |
|----------|----------------|
| **Múltiplas imagens ocultas** | Repita as etapas 2‑3 para cada imagem. Cada `Shape` pode ser ocultada independentemente. |
| **Formatos de imagem diferentes** | Aspose.Words suporta PNG, JPEG, BMP, GIF e TIFF. Use a extensão de arquivo apropriada no caminho. |
| **Documentos grandes** | Crie o documento uma vez, depois reutilize o mesmo `DocumentBuilder` para inserir imagens ocultas em vários locais. |
| **Visibilidade condicional** | Use `shape.setVisible(false)` junto com `shape.setHidden(true)` se precisar alternar a visibilidade via macros do Word posteriormente. |
| **Compatibilidade com versões antigas do Word** | Salve como `doc.save("file.doc", SaveFormat.DOC)` se precisar suportar Word 2003‑2007. Formas ocultas se comportam da mesma forma. |

## Dicas práticas da experiência

* **Manipulação de caminhos:** Use `Paths.get("...").toAbsolutePath().toString()` para evitar surpresas com caminhos relativos ao executar a partir de uma IDE versus um JAR empacotado.
* **Desempenho:** Inserir muitas imagens grandes pode aumentar o uso de memória. Considere redimensionar a imagem (`setWidth`/`setHeight`) antes de ocultá‑la.
* **Teste:** Automatize uma verificação rápida carregando o documento salvo e chamando `doc.getChildNodes(NodeType.SHAPE, true).getCount()` para garantir que o número esperado de formas exista, mesmo que estejam ocultas.

## Conclusão

Agora você sabe como **create new Word document**, **insert image shape**, e **how to hide shape** para que a imagem permaneça invisível—efetivamente **add hidden picture** em qualquer arquivo Word usando Aspose.Words for Java. Essa técnica é útil para incorporar marcas d'água, ativos de branding ou imagens de metadados que não devem interromper o layout do documento.

### Próximos passos

* Explore outras propriedades de forma como rotação, bordas e hyperlinks.
* Combine imagens ocultas com propriedades de documento personalizadas para armazenar metadados adicionais.
* Investigue **how to insert image** em cabeçalhos ou rodapés para branding consistente em todas as páginas.

Sinta-se à vontade para experimentar diferentes tamanhos, posições e configurações de visibilidade de imagem. Se encontrar algum problema, a documentação Aspose.Words for Java fornece referências detalhadas da API e projetos de exemplo. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma retangular no Word com Java – Guia Completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Adicionar sombra à forma no Word – Guia Completo Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}