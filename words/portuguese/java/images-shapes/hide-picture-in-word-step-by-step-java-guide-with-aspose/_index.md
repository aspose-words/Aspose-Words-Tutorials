---
category: general
date: 2026-08-14
description: Ocultar imagem no Word usando Java. Aprenda como ocultar imagem, ocultar
  foto, definir a propriedade hidden e ocultar forma no Word com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: pt
lastmod: 2026-08-14
og_description: Ocultar imagem no Word usando Java e Aspose.Words. Este tutorial mostra
  como definir a propriedade oculta em uma imagem, ocultar forma no Word e salvar
  o documento em segundos.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Ocultar imagem no Word – guia passo a passo em Java com Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Ocultar imagem no Word – guia passo a passo em Java com Aspose
url: /pt/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar imagem no Word – guia passo a passo em Java com Aspose

Se você precisar **ocultar imagem no Word** programaticamente, este guia mostra a solução completa. Você verá como localizar uma imagem, aplicar a marcação de oculto e gravar o arquivo atualizado de volta ao disco.

Ocultar um gráfico é uma necessidade comum quando você gera relatórios, cria modelos ou prepara documentos para revisão de conformidade. O exemplo abaixo demonstra **como ocultar imagem** usando Aspose.Words para Java, mas os mesmos conceitos se aplicam a qualquer biblioteca de processamento de Word que exponha o método `setHidden` de uma forma.

## O que você alcançará

* Carregar um arquivo `.docx` com Aspose.Words.
* Encontrar a primeira forma de imagem no documento.
* **Definir a propriedade hidden** nessa forma para que ela não apareça quando o arquivo for aberto no Microsoft Word.
* Salvar o documento modificado sem alterar outro conteúdo.

O único pré-requisito é um ambiente de desenvolvimento Java (JDK 8 ou mais recente) e uma licença válida do Aspose.Words para Java. Nenhum plugin Maven adicional é necessário além da biblioteca principal.

## Ocultar imagem no Word com Aspose.Words

O primeiro passo é criar um objeto `Document` que representa o arquivo de origem. Aspose.Words lê todo o pacote Word para a memória, facilitando a travessia de nós como formas, parágrafos e tabelas.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Criar a instância `Document` valida o formato do arquivo e constrói uma árvore interna de nós. Essa árvore é a base para todas as operações subsequentes, incluindo **como ocultar objetos de imagem**.

## Como ocultar imagem usando a propriedade set hidden

Uma imagem em um arquivo Word é armazenada como um nó `Shape` com `ShapeType.IMAGE`. A biblioteca fornece o método `setHidden(boolean)` para controlar a visibilidade da forma. O fluxo a seguir filtra a coleção de nós para localizar a primeira forma de imagem.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

A chamada `getChildNodes` percorre toda a árvore do documento (`true` habilita a busca profunda). A expressão lambda verifica o `ShapeType` de cada nó. Esse padrão é a maneira recomendada de **como ocultar imagem** quando você precisa de controle preciso sobre a seleção de nós.

## Como ocultar imagem em um documento Word

Uma vez que a forma alvo é identificada, aplique a marcação de oculto. Definir essa propriedade não remove a imagem; apenas instrui o Word a tratar a forma como oculta durante a renderização.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

A chamada `setHidden(true)` mapeia diretamente para o atributo XML subjacente `w:hidden="true"`. O Word respeita esse atributo tanto nos editores desktop quanto online, garantindo que a imagem permaneça invisível para todos os visualizadores.

## Ocultar forma no Word – considerações adicionais

Embora o exemplo oculte apenas a primeira imagem, você pode estender a lógica para processar várias formas:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Desempenho** – Percorrer a árvore de nós é O(n); para documentos muito grandes, considere restringir a busca a seções específicas.
* **Compatibilidade** – A marcação de oculto funciona com Word 2007+ (`.docx`) e arquivos Word 97‑2003 (`.doc`).
* **Alternância de visibilidade** – Para tornar uma imagem oculta visível novamente, chame `shape.setHidden(false)`.

Essas dicas ajudam você a dominar cenários de **ocultar forma no Word** além do caso de uso básico.

## Salvar o documento modificado

Após atualizar a marcação de oculto, grave o documento de volta ao armazenamento. Aspose.Words preserva automaticamente todas as demais partes do documento, como estilos, cabeçalhos e rodapés.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

O método `save` suporta uma ampla variedade de formatos (PDF, HTML, ODT). Neste tutorial mantemos a saída como um arquivo Word para demonstrar diretamente o efeito da imagem oculta.

## Exemplo completo executável

Juntando todas as etapas, obtém‑se um programa autônomo que você pode compilar e executar imediatamente.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Resultado esperado:** Abra `output.docx` no Microsoft Word. A imagem original não será exibida, mas o restante do documento (texto, tabelas, outras imagens) permanecerá inalterado. Se você inspecionar o XML (`document.xml`) verá o atributo `w:hidden="true"` no elemento `<w:pict>` que corresponde à imagem oculta.

## Conclusão

Agora você sabe como **ocultar imagem no Word** usando Java, Aspose.Words e a propriedade `setHidden`. O tutorial abordou a localização de uma forma de imagem, a aplicação da marcação de oculto e a persistência das alterações. Com esses fundamentos, você também pode **ocultar forma no Word**, processar múltiplas imagens ou alternar a visibilidade com base em regras de negócio.

**Próximos passos**

* Explore **como ocultar imagem** de forma condicional com base em metadados (por exemplo, função do usuário).
* Combine esta técnica com mala‑direta para gerar documentos personalizados e conscientes de privacidade.
* Revise a referência da API Aspose.Words para manipulação avançada de formas, como alterar rotação ou aplicar marcas d'água.

Sinta‑se à vontade para experimentar variações, como ocultar gráficos ou objetos SmartArt, e compartilhe suas descobertas com a comunidade de desenvolvedores. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Ocultar eixo de gráfico em um documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Mostrar/Ocultar conteúdo marcado em documento Word](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Inserir imagem embutida em documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}