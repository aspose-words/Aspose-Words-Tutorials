---
category: general
date: 2026-07-26
description: Inserir forma retangular em Java usando Aspose.Words. Aprenda como definir
  o tamanho da forma, posicionar a forma e como agrupar formas em um arquivo DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: pt
lastmod: 2026-07-26
og_description: Insira forma de retângulo em Java para criar gráficos DOCX ricos.
  Siga este guia passo a passo para definir o tamanho da forma, posicionar a forma
  e agrupar formas sem esforço.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Inserir Forma Retangular em Java – Domine Agrupamento e Posicionamento
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Inserir Forma Retangular em Java – Agrupar e Posicionar Formas
url: /pt/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir Forma Retangular em Java – Agrupar e Posicionar Formas

Já precisou **inserir forma retangular** em um documento Word enquanto escrevia código Java? Você não está sozinho—desenvolvedores que criam relatórios, faturas ou modelos personalizados enfrentam esse obstáculo o tempo todo. A boa notícia é que, com algumas linhas de Aspose.Words for Java, você pode **inserir forma retangular**, **definir o tamanho da forma**, **posicionar a forma** e até **como agrupar formas** para que se movam como uma única unidade.

Neste guia, percorreremos todo o processo, desde a criação de um documento em branco até a gravação de um `.docx` que contém dois retângulos agrupados de forma ordenada. Ao final, você saberá **como adicionar retângulo** objetos, controlar suas dimensões, posicioná-los exatamente onde desejar e agrupá-los em um grupo reutilizável. Nenhuma biblioteca externa além do Aspose.Words é necessária, e o código funciona com Java 8‑ou‑mais.

## Pré-requisitos

- Java 8 ou superior instalado (estou usando JDK 17, mas qualquer coisa que suporte Maven funciona)
- Aspose.Words for Java 23.9 ou posterior – adicione a dependência ao seu `pom.xml` ou faça o download do JAR
- Um entendimento básico da sintaxe Java (se você consegue escrever um método `main`, está pronto)
- Uma IDE ou editor de texto de sua escolha (IntelliJ IDEA, Eclipse, VS Code…)

> **Dica profissional:** Se você estiver usando Maven, a dependência se parece com isto:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Agora que estabelecemos a base, vamos mergulhar no código.

## Inserir Forma Retangular e Definir Seu Tamanho

A primeira coisa que você fará é criar um novo `Document` e um `DocumentBuilder`. O builder é sua “caneta” que desenha formas na página. Abaixo, nós **inserimos forma retangular** e imediatamente **definimos o tamanho da forma** para 100 × 80 pontos.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Observe como as chamadas `setWidth`/`setHeight` **definem o tamanho da forma** em pontos (1 pt ≈ 1/72 polegada). Você também poderia usar `setSize` se preferir um único método, mas as chamadas explícitas deixam a intenção bem clara.

## Posicionar a Forma na Página

Depois de termos o primeiro retângulo, precisamos **posicionar a forma** da segunda de modo que não sobreponha a primeira. O posicionamento funciona da mesma forma: você define as propriedades `Left` e `Top` relativas à origem do grupo.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Se você está se perguntando por que usamos `setLeft` em vez de `setX`, é porque o Aspose.Words adota o clássico sistema de coordenadas Windows GDI—`Left` é o deslocamento horizontal, `Top` é o deslocamento vertical. Alterar esses valores permite ajustar finamente o layout sem mexer em tabelas ou parágrafos.

## Como Agrupar Formas

Você pode se perguntar, “Por que se preocupar com um grupo?” Agrupar faz sentido quando você deseja que as formas se movam juntas, girem como uma unidade ou compartilhem um estilo comum. No trecho acima, já criamos um `GroupShape` via `builder.insertGroupShape`. Esse objeto é essencialmente um contêiner—pense nele como uma pasta que contém outros arquivos de forma.

> **Por que isso importa:** Se mais tarde você decidir adicionar uma legenda ou girar todo o diagrama, só precisará modificar o grupo, não cada retângulo individualmente.

## Como Adicionar Retângulo a um Grupo

O ato de **como adicionar retângulo** ao grupo consiste simplesmente em chamar `group.appendChild(rectangle)`. Nos bastidores, o Aspose.Words atualiza a coleção interna do grupo e recalcula automaticamente a caixa delimitadora para que o grupo ainda se ajuste à largura e altura declaradas.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Você pode experimentar outros `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, etc.—e o mesmo padrão `appendChild` funciona.

## Salvar o Documento

Finalmente, persistimos o documento no disco. O caminho pode ser absoluto ou relativo; apenas certifique-se de que a pasta exista.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Ao abrir `GroupShape.docx` no Microsoft Word, você verá dois retângulos lado a lado, ambos presos dentro de uma caixa cinza‑clara. Selecionar a caixa cinza destacará ambos os retângulos simultaneamente—prova de que **como agrupar formas** realmente funciona.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file"}

*Texto alternativo da imagem (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Saída Esperada

- Um arquivo `GroupShape.docx` localizado na pasta `output`.
- Dentro do documento: um grupo de 400 × 200 pt contendo dois retângulos (100 × 80 pt e 120 × 60 pt) posicionados em (20, 30) e (150, 50) respectivamente.
- O grupo tem uma borda preta fina e preenchimento cinza‑claro, tornando o agrupamento visualmente óbvio.

Abra o arquivo e tente arrastar a caixa cinza—ambos os retângulos devem mover-se juntos. Se não moverem, verifique novamente se você chamou `group.appendChild` para cada forma.

## Armadilhas Comuns & Casos Limítrofes

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| **Retângulos aparecem fora da página** | valores `Left`/`Top` excedem as dimensões do grupo | Aumente o tamanho do grupo (`insertGroupShape(width, height)`) ou reduza os deslocamentos |
| **Grupo desaparece após salvar** | O `Width`/`Height` do grupo está definido como 0 | Forneça dimensões diferentes de zero ao chamar `insertGroupShape` |
| **Cores da forma parecem erradas** | O preenchimento padrão é transparente; o Word pode renderizá-lo como branco | Defina explicitamente `setFillColor` ou use `ShapeStyle` |
| **Exceção `ArgumentOutOfRangeException`** | Uso de coordenadas negativas | Mantenha `Left` e `Top` não‑negativos |

Abordar esses pontos desde o início evita as dores de cabeça do “por que minha forma desapareceu?” que muitos iniciantes encontram.

## Recapitulação & Próximos Passos

Cobremos todo o ciclo de vida de **inserir forma retangular** em Java: criar um documento, **definir o tamanho da forma**, **posicionar a forma**, **como agrupar formas**, e **como adicionar retângulo** ao grupo. O exemplo completo e executável está no bloco de código acima, e você pode colá-lo diretamente em um projeto Maven para ver o resultado.

O que vem a seguir? Considere experimentar com:

- Adicionar texto dentro de cada retângulo via

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Criar Documento Word em Branco com Forma Retangular Sombreada – Guia Passo a Passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}