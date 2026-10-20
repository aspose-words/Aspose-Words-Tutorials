---
category: general
date: 2026-09-11
description: Agrupe formas no Word e adicione uma forma retangular usando Aspose.Words
  para Java. Aprenda como definir o tamanho da forma, agrupar objetos e salvar o documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: pt
lastmod: 2026-09-11
og_description: Agrupe formas no Word e adicione uma forma retangular usando Aspose.Words
  para Java. Este tutorial mostra como definir o tamanho da forma, agrupar formas
  e exportar o documento.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Agrupar formas no Word – adicionar retângulo com Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Agrupar formas no Word e adicionar um retângulo com Aspose.Words
url: /pt/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agrupar formas no Word e adicionar um retângulo com Aspose.Words

Se você precisar **agrupar formas no Word** enquanto adiciona programaticamente um retângulo, este guia fornece uma solução completa, pronta‑para‑executar. Você verá exatamente como inserir um grupo de formas, adicionar um retângulo, definir o tamanho da forma e, finalmente, salvar o documento para visualizar o resultado instantaneamente.

Trabalhar com documentos Word frequentemente significa organizar múltiplos objetos—imagens, gráficos ou formas geométricas simples—em uma única unidade lógica. Agrupar esses objetos facilita movê‑los, girá‑los ou estiliza‑los juntos. Neste tutorial também abordaremos **como adicionar retângulo** e **definir o tamanho da forma** para controle perfeito de layout.

## O que você aprenderá

* Como criar um novo documento Word com Aspose.Words para Java.  
* **Como agrupar formas** para que se comportem como um único objeto.  
* **Adicionar forma de retângulo** a um grupo e inserir uma imagem no mesmo grupo.  
* **Definir o tamanho da forma** tanto para o retângulo quanto para a imagem.  
* Salvar o documento e abri‑lo no Microsoft Word para verificar o resultado.

### Pré-requisitos

* Java 17 ou superior instalado.  
* Maven ou Gradle para gerenciar dependências.  
* Uma licença válida do Aspose.Words para Java (ou uma chave de avaliação gratuita).  
* Um arquivo de imagem (`sample.png`) colocado em um diretório conhecido (substitua `YOUR_DIRECTORY` pelo seu caminho real).

---

## Como agrupar formas no Word usando Aspose.Words

O primeiro passo é criar um `Document` e um `DocumentBuilder`. O builder fornece uma API conveniente para inserir formas, texto e outros elementos.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Por que isso importa:** `DocumentBuilder` trabalha diretamente com o objeto `Document` subjacente, permitindo inserir formas sem manipular manualmente coleções de nós de baixo nível.

### Adicionar um grupo de formas

Um grupo de formas é um contêiner que pode conter outras formas. Pense nele como uma pasta para objetos de desenho.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

O método `insertGroupShape()` cria um nó `GroupShape` e o retorna para que você possa acrescentar formas filhas posteriormente.  

---

## Adicionar uma forma de retângulo ao grupo

Agora vamos **adicionar forma de retângulo** ao grupo criado anteriormente. O retângulo servirá como fundo ou borda para a imagem.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Dica:** Definir `FillColor` e `StrokeColor` torna o retângulo visível no documento final. Se você omitir essas propriedades, a forma pode aparecer transparente.

### Como adicionar retângulo

O código acima demonstra **como adicionar retângulo** criando uma instância `Shape` com `ShapeType.RECTANGLE` e, em seguida, anexando‑a ao `GroupShape`. Esse padrão funciona para qualquer outro tipo de forma (por exemplo, `ELLIPSE`, `POLYLINE`).

---

## Definir o tamanho da forma para retângulo e imagem

Um dimensionamento adequado garante que o retângulo e a imagem se alinhem corretamente. Aqui também **definimos o tamanho da forma** para a imagem que inseriremos a seguir.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Tanto o retângulo quanto a imagem agora compartilham as mesmas dimensões (100 × 50 points). Como pertencem ao mesmo grupo, mover ou girar o grupo afetará ambas as formas simultaneamente.

> **Por que combinar tamanhos?** Alinhar as dimensões garante que a imagem fique perfeitamente dentro do retângulo, criando um efeito limpo de “imagem emoldurada”.

---

## Salvar o documento e visualizar o resultado

Finalmente, gravamos o documento no disco. Abrir o arquivo no Microsoft Word mostra as formas agrupadas como um único objeto selecionável.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Ao abrir `output.docx`, você verá um retângulo com a imagem dentro dele. Clicar na forma seleciona tanto o retângulo quanto a imagem porque elas estão **agrupadas**.

![exemplo de formas agrupadas no Word](https://example.com/images/group-shapes-word.png "exemplo de formas agrupadas no Word")

*Texto alternativo da imagem:* *exemplo de formas agrupadas no Word* – um documento Word mostrando um retângulo e uma imagem agrupados.

---

## Perguntas comuns e tratamento de casos extremos

| Pergunta | Resposta |
|----------|----------|
| **E se eu precisar de um tamanho diferente para a imagem?** | Ajuste `picture.setWidth()` e `picture.setHeight()` após a inserção. O retângulo pode manter seu tamanho original, ou você também pode redimensioná‑lo para corresponder. |
| **Posso adicionar mais formas ao mesmo grupo?** | Sim. Chame `group.appendChild(newShape)` para quaisquer objetos `Shape` adicionais. |
| **Como rotacionar todo o grupo?** | Use `group.setRotationAngle(double angleInRadians)`. A rotação se aplica a cada forma filha. |
| **E se o arquivo de imagem estiver ausente?** | `insertImage` lança `FileNotFoundException`. Envolva a chamada em um bloco try‑catch e forneça uma forma de espaço reservado como fallback. |
| **É possível desagrupar mais tarde?** | Chame `group.removeAllChildren()` para separar os filhos, então insira‑os de volta no documento individualmente. |

---

## Conclusão

Agora você tem um exemplo completo e executável que mostra **como agrupar formas no Word**, **adicionar forma de retângulo**, **definir o tamanho da forma** e **salvar** o documento usando Aspose.Words para Java. Ao agrupar o retângulo e a imagem, você pode movê‑los, redimensioná‑los ou girá‑los como uma única unidade—exatamente o que muitos cenários de automação de documentos exigem.

A partir daqui, você pode explorar:

* Adicionar caixas de texto ao mesmo grupo (texto no estilo `how to add rectangle`).  
* Aplicar diferentes padrões de preenchimento ou gradientes (`set shape size` combinado com estilização).  
* Usar a mesma técnica para agrupar gráficos, tabelas ou SmartArt (`how to group shapes` em outros tipos de objetos).  

Sinta‑se à vontade para experimentar outros tipos de formas, cores e opções de layout. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Criar documento Word Java – Adicionar forma de retângulo com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como criar campos de formulário e adicionar conteúdo usando DocumentBuilder no Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Como converter Word para PDF usando Aspose.Words para Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}