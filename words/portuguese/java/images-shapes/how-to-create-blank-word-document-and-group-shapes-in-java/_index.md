---
category: general
date: 2026-09-27
description: Crie um documento Word em branco em Java e agrupe formas usando Aspose.Words.
  Aprenda a definir o tamanho da forma, definir a cor de preenchimento da forma e
  anexar um filho ao grupo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: pt
lastmod: 2026-09-27
og_description: Crie um documento Word em branco em Java com Aspose.Words. Este tutorial
  mostra como agrupar formas no Word, definir o tamanho da forma, definir a cor de
  preenchimento da forma e adicionar um filho ao grupo.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crie um documento Word em branco e agrupe formas em Java – guia passo a
  passo
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Como criar um documento Word em branco e agrupar formas no Java
url: /pt/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar documento Word em branco e agrupar formas em Java

Se você precisa **criar documento Word em branco** programaticamente, este guia mostra exatamente como fazer isso com Aspose.Words for Java. Você também aprenderá a **agrupar formas no Word**, definir o tamanho de cada forma, aplicar uma cor de preenchimento e **adicionar filho ao grupo** para que os objetos se comportem como uma única unidade.

Trabalhar com arquivos Word a partir do código evita a formatação manual e permite gerar relatórios, contratos ou folhetos de marketing automaticamente. Ao final deste tutorial você terá um programa Java executável que produz um arquivo `.docx` contendo um retângulo azul e uma imagem, ambos agrupados juntos.

## Pré-requisitos

- Java 17 (ou qualquer JDK recente) instalado.
- Maven ou Gradle para gerenciar dependências.
- Uma licença Aspose.Words for Java (a avaliação gratuita funciona para testes).
- Um arquivo de imagem de exemplo (por exemplo, `sample.jpg`) colocado em uma pasta que você pode referenciar a partir do código.

> **Dica profissional:** Mantenha seus arquivos de imagem em um diretório `resources` e carregue-os com `ClassLoader.getResourceAsStream` para evitar caminhos absolutos codificados.

## Etapa 1: Criar um documento Word em branco e adicionar um GroupShape

O primeiro passo é instanciar um novo objeto `Document`, que representa um arquivo Word vazio, e então inserir um `GroupShape`. O grupo servirá como um contêiner para quaisquer formas que você adicionar posteriormente.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Por que isso importa:* Um `GroupShape` permite mover, girar ou formatar várias formas juntas, o que é essencial para layouts complexos como diagramas ou marcas d'água.

## Etapa 2: Inserir um retângulo e **definir tamanho da forma**

Em seguida, crie um retângulo, defina suas dimensões e adicione-o ao grupo. Isso demonstra a operação de **definir tamanho da forma**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explicação:* `setWidth` e `setHeight` controlam o tamanho exato da forma em pontos (1 ponto = 1/72 polegada). Ajuste esses valores para atender aos requisitos do seu layout.

## Etapa 3: **Definir cor de preenchimento da forma** para o retângulo

O fundo do retângulo é definido como azul usando `setFillColor`. Você pode usar qualquer constante `java.awt.Color` ou criar uma cor RGB personalizada.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Por que é útil:* Cores de preenchimento ajudam a diferenciar visualmente os objetos, especialmente quando você exporta o documento para PDF ou o imprime.

## Etapa 4: Inserir uma imagem e **adicionar filho ao grupo**

Agora adicione uma imagem ao mesmo `GroupShape`. A imagem é inserida via `DocumentBuilder.insertImage`, e então adicionada ao grupo para que se mova junto com o retângulo.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Caso extremo:* Se o caminho da imagem estiver errado, Aspose.Words lança `FileNotFoundException`. Use um caminho relativo ou carregue a imagem a partir dos recursos para evitar esse problema.

## Etapa 5: **Salvar o documento com as formas agrupadas**

Finalmente, grave o documento no disco. O arquivo resultante conterá o retângulo e a imagem agrupados juntos.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Saída esperada

- Um arquivo chamado `GroupShape.docx` aparece no diretório especificado.
- Abrir o arquivo no Microsoft Word mostra uma página em branco com um retângulo azul e a imagem escolhida, ambos selecionados como um único objeto (você pode mover ou redimensioná-los juntos).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*A captura de tela acima demonstra as formas agrupadas finais dentro do documento Word recém‑criado.*

## Variações comuns e dicas adicionais

| Situação | Como lidar |
|-----------|-----------------|
| **Múltiplas imagens** | Insira cada imagem com `builder.insertImage` e chame `group.appendChild(picture)` para cada uma. |
| **Tipos diferentes de forma** | Use `ShapeType.OVAL`, `ShapeType.LINE`, etc., ao construir o objeto `Shape`. |
| **Alterar posição do grupo** | Após adicionar todos os filhos, defina `group.setLeft(x)` e `group.setTop(y)` para mover todo o grupo. |
| **Exportar para PDF** | Chame `doc.save("output.pdf")` após agrupar; o PDF preservará o agrupamento. |
| **Aplicação de licença** | Se você executar a versão de avaliação, uma marca d'água aparecerá. Instale uma licença válida para removê‑la. |

## Conclusão

Agora você sabe como **criar documento Word em branco**, inserir um **GroupShape**, **definir tamanho da forma**, **definir cor de preenchimento da forma** e **adicionar filho ao grupo** usando Aspose.Words for Java. Esse padrão permite construir layouts complexos e programáticos que podem ser editados posteriormente no Word ou exportados para outros formatos.

Em seguida, explore como **agrupar formas no Word** com caixas de texto, adicionar hyperlinks às formas ou automatizar a geração de relatórios de várias páginas. Os mesmos princípios se aplicam — basta criar formas adicionais, configurar suas propriedades e adicioná‑las ao mesmo grupo.

Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar forma de retângulo no Word com Java – Guia Completo](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Criar Documento Word Java – Adicionar Forma de Retângulo com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}