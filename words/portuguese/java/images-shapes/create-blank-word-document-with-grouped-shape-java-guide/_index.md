---
category: general
date: 2026-07-20
description: Criar documento Word em branco em Java usando Aspose.Words. Aprenda como
  criar um grupo, inserir uma forma retangular e incorporar uma imagem na forma.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: pt
lastmod: 2026-07-20
og_description: Criar documento Word em branco em Java com Aspose.Words. Este guia
  mostra como criar um grupo, inserir forma retangular e incorporar imagem na forma
  para arquivos Word dinâmicos.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Criar documento Word em branco com forma agrupada – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Criar documento Word em branco com forma agrupada – Guia Java
url: /pt/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word em branco com forma agrupada – Guia Java

Já se perguntou como **criar documento Word em branco** que já contenha uma forma agrupada de forma elegante? Talvez você esteja criando um modelo de relatório, ou precise de um espaço reservado para um logotipo e uma legenda. De qualquer forma, o problema é comum: você começa com um arquivo vazio, então precisa adicionar um grupo, inserir um retângulo dentro e, finalmente, incorporar uma imagem—tudo programaticamente.

Neste tutorial, percorreremos um exemplo Java completo, pronto‑para‑executar, que faz exatamente isso. Você aprenderá **como criar grupo**, **inserir forma retângulo** e **adicionar imagem ao documento Word** dentro do mesmo grupo. Ao final, você terá um arquivo Word que parece um modelo refinado, pronto para personalizações adicionais.

> **O que você receberá:** uma classe Java totalmente funcional, explicações passo a passo, dicas para lidar com caminhos de arquivos e uma pré‑visualização do resultado esperado. Nenhuma documentação externa necessária—tudo o que você precisa está aqui.

---

## Criar documento Word em branco – Visão geral passo a passo

A primeira coisa que precisamos é um arquivo Word realmente em branco. Aspose.Words torna isso trivial: basta instanciar a classe `Document` com seu construtor padrão. Isso fornece uma tela limpa, equivalente a abrir o Word e clicar em **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que começar com um documento em branco?**  
> Um documento em branco garante que nenhum estilo ou seção ocultos interfiram nas formas que você adicionará posteriormente. Também mantém o tamanho do arquivo mínimo, o que é útil quando você gera dezenas de arquivos em um trabalho em lote.

---

## Como criar grupo e adicionar formas

Uma **group shape** é essencialmente um contêiner que pode conter várias formas filhas—pense nisso como uma pasta para objetos de desenho. Ao agrupar, você pode mover, redimensionar ou girar todo o conjunto com um único comando.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

O método `insertGroupShape` retorna um objeto `GroupShape` que usaremos como pai para o retângulo e a imagem. O tamanho é expresso em pontos (1 ponto = 1/72 polegada), então 200 pontos dão aproximadamente uma caixa de 2,78 × 2,78 polegadas.

> **Dica profissional:** Se precisar que o grupo seja transparente, defina `group.setFillColor(Color.getWhite());` após a criação.

Agora que o grupo existe, precisamos dizer ao builder onde colocar as próximas formas. O cursor do builder deve estar posicionado dentro do primeiro parágrafo do grupo.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Inserir forma retângulo dentro do grupo

Um retângulo costuma ser usado como espaço reservado para texto ou como pista visual. Inseri‑lo como o **primeiro filho** do grupo garante que ele fique atrás de quaisquer imagens subsequentes.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

O retângulo herda o sistema de coordenadas do grupo, portanto seu tamanho de 100 × 50 pontos será centralizado por padrão. Você pode estilizar ainda mais—adicionar uma borda, mudar a cor de preenchimento ou aplicar uma sombra—acessando o objeto `Shape` retornado.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Adicionar imagem ao documento Word – incorporando imagem na forma

Agora vem a parte divertida: **incorporar imagem na forma**. Inseriremos uma imagem JPEG como o segundo filho do mesmo grupo. Como o cursor ainda está dentro do grupo, a imagem se tornará automaticamente um nó filho.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Se o arquivo de imagem não for encontrado, Aspose.Words lança uma `FileNotFoundException`. Para evitar isso, coloque `sample.jpg` no diretório de trabalho do projeto ou use um caminho absoluto.

> **E se você precisar de um formato de imagem diferente?**  
> Aspose.Words suporta PNG, BMP, GIF, TIFF e até SVG. Basta mudar a extensão do arquivo que a biblioteca cuidará da conversão.

---

## Salvar o documento e ver o resultado

Finalmente, persistimos o documento em memória no disco. O `.docx` resultante conterá uma única página com uma forma agrupada que contém tanto o retângulo quanto a imagem.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Ao abrir `output.docx` no Microsoft Word, você deverá ver um grupo de 200 × 200 pontos no canto superior esquerdo. Dentro do grupo, um retângulo cinza claro fica na parte superior, e diretamente abaixo dele a imagem especificada aparece, perfeitamente alinhada.

![Grouped shape example](grouped-shape.png){:alt="Captura de tela de um documento Word em branco com uma forma agrupada contendo um retângulo e uma imagem incorporada"}

---

## Variações comuns e tratamento de casos extremos

| Cenário | O que mudar | Por que isso importa |
|----------|----------------|----------------|
| **Tamanho de grupo diferente** | Ajuste os parâmetros de `insertGroupShape(width, height)` | Grupos maiores podem acomodar layouts mais complexos. |
| **Múltiplas imagens** | Chame `builder.insertImage()` repetidamente após mover para o parágrafo do grupo a cada vez | Cada chamada adiciona um novo filho; você também pode posicioná‑los usando `Shape.setLeft()` / `setTop()`. |
| **Caminhos de imagem dinâmicos** | Use `String.format("images/%s.jpg", imageName)` | Torna o código reutilizável para processamento em lote. |
| **Salvar como PDF** | Substitua `doc.save("output.pdf")` | Aspose.Words pode converter em tempo real, permitindo gerar PDFs diretamente. |
| **Rotacionar o grupo** | `group.setRotation(45);` | Útil para marcas d'água decorativas ou cabeçalhos estilizados. |

---

## Saída esperada e verificação

Depois de executar a classe:

1. `output.docx` aparece na pasta do projeto.  
2. Abrir o arquivo mostra uma única página com uma forma agrupada.  
3. Dentro do grupo, o retângulo está posicionado no canto superior esquerdo, e a imagem fica diretamente abaixo dele.  
4. Selecionar o grupo no Word destaca ambos os objetos filhos, confirmando que eles estão realmente agrupados.

Se algum desses passos falhar, verifique novamente o caminho da imagem e assegure que o JAR do Aspose.Words está no seu classpath.

---

## Conclusão

Agora você sabe **como criar documento Word em branco** e enriquecê‑lo com uma forma agrupada que contém um retângulo e uma imagem incorporada. Ao dominar **como criar grupo**, **inserir forma retângulo** e **adicionar imagem ao documento Word**, você pode construir modelos Word sofisticados inteiramente em código—sem necessidade de ajustes manuais.

Pronto para o próximo desafio? Tente adicionar caixas de texto dentro do mesmo grupo, ou experimente diferentes estilos de forma para combinar com a identidade visual da sua empresa. Você pode até gerar uma biblioteca inteira de relatórios onde cada documento começa com este layout exato.

Boa codificação, e sinta‑se à vontade para compartilhar suas próprias variações nos comentários abaixo!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retângulo com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como Criar Documentos PDF com Aspose.Words para Java | API de Processamento de Documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}