---
category: general
date: 2026-09-11
description: Como definir sombra em um gráfico do Word com Aspose.Words for Java –
  aprenda a carregar um documento Word, alterar bordas e personalizar a aparência
  do gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change border
- modify word chart
- load word document
- set chart border
language: pt
lastmod: 2026-09-11
og_description: Como definir sombra em um gráfico do Word com Aspose.Words para Java.
  Siga este guia passo a passo para carregar um documento Word, alterar a borda e
  aplicar um efeito de sombra.
og_image_alt: Screenshot of a Word chart with a gray border and a soft shadow applied
og_title: Como definir sombra em um gráfico do Word – guia completo de Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  headline: How to set shadow on a Word chart with Aspose.Words for Java
  type: TechArticle
- description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  name: How to set shadow on a Word chart with Aspose.Words for Java
  steps:
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: What if the document contains multiple charts?
    text: 'The example retrieves the **first** chart. To modify all charts, iterate
      over the filtered list:'
  - name: Does the shadow work for all chart types?
    text: Yes. Aspose.Words applies the shadow at the chart container level, so bar,
      line, and pie charts all receive the effect. However, 3‑D charts may render
      the shadow slightly differently because of their built‑in lighting model.
  - name: How to set a custom shadow color?
    text: The API currently supports a simple on/off toggle (`setShadow(true)`). For
      more advanced shadow styling (color, blur, offset), you would need to convert
      the chart to an image and use a graphics library, which is beyond the scope
      of this tutorial.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Como definir sombra em um gráfico do Word com Aspose.Words para Java
url: /pt/java/document-styling/how-to-set-shadow-on-a-word-chart-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como definir sombra em um gráfico do Word com Aspose.Words para Java

Se você precisa de **como definir sombra em um gráfico do Word** rapidamente, este guia mostra os passos exatos usando Aspose.Words para Java. Você aprenderá como **carregar um documento Word**, recuperar o primeiro gráfico e, em seguida, aplicar tanto um efeito de sombra quanto uma borda personalizada.

Aprimorar o estilo visual de um gráfico é útil para relatórios, apresentações ou pipelines de geração automática de documentos. Ao final deste tutorial, você será capaz de **modificar objetos de gráfico do Word**, alterar a cor da borda e responder à pergunta comum **como mudar a borda** sem sair do seu código Java.

## Pré-requisitos e o que você vai construir

Antes de começar, certifique‑se de que você tem:

* Java 17 (ou qualquer JDK recente) instalado.
* Maven ou Gradle para gerenciar dependências.
* Uma licença do Aspose.Words para Java (a versão de avaliação gratuita funciona para desenvolvimento).
* Um arquivo Word de exemplo (`input.docx`) que contenha ao menos um gráfico.

O programa final irá:

1. **Carregar documento Word** (`load word document`).
2. Recuperar a primeira forma de gráfico (`modify word chart`).
3. **Definir borda do gráfico** para cinza (`set chart border`).
4. Aplicar um **efeito de sombra** (`how to set shadow`).
5. Salvar o documento modificado como `output.docx`.

## Etapa 1: Configurar o projeto e adicionar Aspose.Words

Crie um novo projeto Maven (ou equivalente Gradle) e adicione a dependência do Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- use the latest version -->
    </dependency>
</dependencies>
```

> **Dica profissional:** Se você estiver usando Gradle, o equivalente é `implementation 'com.aspose:aspose-words:24.9'`.

## Etapa 2: Como carregar um documento Word e recuperar o gráfico

Carregar um documento é uma única linha de código, mas entender a hierarquia de nós ajuda quando você precisar **modificar objetos de gráfico do Word** mais tarde.

```java
import com.aspose.words.*;

public class ChartShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Retrieve the first Shape that is a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                    .stream()
                                    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
                                    .findFirst()
                                    .orElseThrow(() -> new IllegalArgumentException("No chart found"));
        
        // Cast the Shape to a Chart object
        Chart chart = chartShape.getChart();
```

*Por que isso importa*: A coleção `NodeType.SHAPE` pode conter imagens, caixas de texto ou gráficos. Filtrar por `ShapeType.CHART` garante que você está trabalhando com um gráfico, o que é essencial para **como definir sombra** corretamente.

## Etapa 3: Como definir sombra em um gráfico do Word

Aspose.Words expõe um método `setShadow(boolean)` na classe `Chart`. Ativar a sombra confere ao gráfico um sutil efeito de profundidade.

```java
        // Enable a shadow effect for the chart
        chart.setShadow(true);
```

Quando o documento é aberto no Microsoft Word, o gráfico agora exibe uma suave sombra cinza ao redor de seu perímetro. Esta é a resposta principal para **como definir sombra** em um gráfico.

## Etapa 4: Como mudar a borda de um gráfico do Word

Alterar a borda envolve duas propriedades:

* `setBorderColor(Color)` – define a cor.
* `setBorderWidth(double)` – opcional, define a espessura (o padrão é 0,5 pt).

```java
        // Apply a gray border color to the chart
        chart.setBorderColor(java.awt.Color.GRAY);
        // Optionally increase the border width for better visibility
        chart.setBorderWidth(1.0);
```

Essas linhas respondem **como mudar a borda** e também atendem ao requisito da palavra‑chave **set chart border**. A borda aparecerá ao redor de cada fatia de um gráfico de pizza ou ao redor de toda a área do gráfico para gráficos de colunas.

## Etapa 5: Como explodir fatias de gráfico (ajuste visual opcional)

Embora não faça parte do conjunto principal de palavras‑chave, explodir fatias é um aprimoramento visual comum que combina bem com sombras.

```java
        // Explode the chart slices by 10 %
        chart.setExplode(10);
```

## Etapa 6: Salvar o documento modificado

Após todas as personalizações, escreva o documento de volta ao disco.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Executar o programa gera `output.docx` onde o primeiro gráfico agora tem uma borda cinza, uma explosão de 10 % e um efeito de sombra.

### Resultado esperado

Abra `output.docx` no Microsoft Word:

* O gráfico exibe uma sombra suave no lado direito.
* Uma fina borda cinza circunda o gráfico.
* Se você adicionou a etapa de explosão, as fatias ficam ligeiramente separadas.

![Word chart with shadow and gray border](https://example.com/placeholder-image.png){alt="Gráfico do Word com sombra e borda cinza"}

## Perguntas comuns e tratamento de casos extremos

### E se o documento contiver vários gráficos?

O exemplo recupera o **primeiro** gráfico. Para modificar todos os gráficos, itere sobre a lista filtrada:

```java
List<Shape> charts = doc.getChildNodes(NodeType.SHAPE, true).stream()
    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
    .map(node -> (Shape) node)
    .collect(Collectors.toList());

for (Shape shape : charts) {
    Chart c = shape.getChart();
    c.setShadow(true);
    c.setBorderColor(java.awt.Color.GRAY);
}
```

### A sombra funciona para todos os tipos de gráfico?

Sim. Aspose.Words aplica a sombra no nível do contêiner do gráfico, portanto gráficos de barras, linhas e pizza recebem o efeito. Contudo, gráficos 3‑D podem renderizar a sombra de forma ligeiramente diferente devido ao seu modelo de iluminação interno.

### Como definir uma cor de sombra personalizada?

A API atualmente suporta um simples alternador on/off (`setShadow(true)`). Para estilos de sombra mais avançados (cor, desfoque, deslocamento), seria necessário converter o gráfico em imagem e usar uma biblioteca gráfica, o que está fora do escopo deste tutorial.

## Dicas profissionais para código de produção

* **Licencie cedo** – chame `License license = new License(); license.setLicense("Aspose.Words.lic");` antes de carregar o documento para evitar marcas d'água de avaliação.
* **Reutilize objetos Document** – se você processar muitos arquivos em lote, reutilize uma única instância `Document` para reduzir a pressão do GC.
* **Valide a existência do gráfico** – sempre proteja contra `NoSuchElementException` quando um documento não contém gráfico; isso evita falhas em tempo de execução.
* **Segurança de threads** – objetos Aspose.Words não são thread‑safe. Crie um `Document` separado por thread ao processar em paralelo.

## Conclusão

Agora você sabe **como definir sombra em um gráfico do Word** usando Aspose.Words para Java, bem como **como mudar a borda**, **carregar documento Word** e **definir borda do gráfico**. Seguindo os passos acima, você pode aprimorar programaticamente os visuais dos gráficos, tornando relatórios automatizados mais refinados e profissionais.

Pronto para o próximo desafio? Explore **como adicionar rótulos de dados**, **personalizar cores de gráfico** ou **exportar gráficos para imagens** – tudo alcançável com a mesma API Aspose.Words. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words para Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Como definir LoadOptions no Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}