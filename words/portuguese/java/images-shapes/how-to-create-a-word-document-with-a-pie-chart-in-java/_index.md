---
category: general
date: 2026-09-18
description: Aprenda a criar um documento Word e inserir um gráfico de pizza usando
  Aspose.Words para Java. Inclui etapas para girar o gráfico de pizza e gerar o arquivo
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: pt
lastmod: 2026-09-18
og_description: Crie um documento Word e insira um gráfico de pizza usando Java. Siga
  este guia para girar o gráfico de pizza, explodir fatias e gerar um arquivo Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Crie um documento Word com um gráfico de pizza – guia Java passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Como criar um documento Word com um gráfico de pizza em Java
url: /pt/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um documento Word com um gráfico de pizza em Java

Se você precisa **criar um documento Word** que visualize dados, este guia mostra como fazer isso com Aspose.Words para Java. Você aprenderá a inserir um gráfico de pizza, explodir uma fatia, girar o gráfico e, finalmente, **gerar um arquivo Word** que pode ser aberto no Microsoft Word.

Criar relatórios que combinam texto e gráficos não requer uma ferramenta gráfica separada. Ao final deste tutorial você terá um programa completo e executável que cria um arquivo .docx contendo um gráfico de pizza totalmente configurado.

## Pré‑requisitos

- Java 17 ou superior (o código também compila com Java 8+)
- Maven ou Gradle para gerenciamento de dependências
- Licença do Aspose.Words para Java (a versão de avaliação gratuita funciona para este exemplo)
- Familiaridade básica com a sintaxe Java

## Etapa 1: Configurar o projeto Maven

Crie um novo projeto Maven e adicione a dependência do Aspose.Words ao `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Dica:** Mantenha o número da versão atualizado; lançamentos mais recentes trazem melhorias nos tipos de gráficos e correções de bugs.

## Etapa 2: Criar um novo documento Word

A primeira operação ao **criar um documento Word** programaticamente é instanciar um objeto `Document`. Esse objeto representa todo o arquivo .docx na memória.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

A classe `Document` é o ponto de entrada para todos os recursos de processamento de texto. Nenhum arquivo é gravado em disco neste momento; tudo acontece na RAM até que você chame `save`.

## Etapa 3: Como inserir um gráfico de pizza

Um `DocumentBuilder` permite adicionar conteúdo ao documento. Com `insertChart` você pode **inserir objetos de gráfico de pizza** diretamente.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` indica ao Aspose.Words que deve criar um gráfico de pizza. As dimensões são expressas em pontos (1 pt ≈ 1/72 in). Após esta chamada o gráfico aparece em um novo parágrafo.

## Etapa 4: Preencher o gráfico com dados

Um gráfico de pizza precisa de uma série de valores. Aqui adicionamos três categorias: “Apples”, “Bananas” e “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

O método `add` constrói a série e cria automaticamente as entradas da legenda. Você pode reutilizar esse padrão para qualquer conjunto de dados numéricos.

## Etapa 5: Destacar a primeira fatia

Explodir uma fatia chama a atenção para um valor específico. A primeira fatia (índice 0) é explodida em 20 pontos.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Definir `explode` na série afeta todo o gráfico, portanto apenas o primeiro ponto de dados é deslocado.

## Etapa 6: Como girar um gráfico de pizza

Girar o gráfico melhora o equilíbrio visual, especialmente quando a maior fatia não está no topo. O método `setRotationAngle` recebe o ângulo em graus.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Uma rotação de 45° move o ângulo inicial no sentido horário, facilitando a leitura do gráfico em muitos layouts.

## Etapa 7: Salvar o documento e gerar um arquivo Word

Por fim, grave o documento no disco. Esta etapa **gera o arquivo Word** que pode ser aberto com Microsoft Word, LibreOffice ou qualquer visualizador compatível.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

O método `save` detecta automaticamente a extensão .docx e grava um pacote compatível com Word. A pasta `output` deve existir ou pode ser criada programaticamente.

### Saída esperada

Depois de executar o programa, abra `output/PieChart.docx`. Você deverá ver:

- Uma única página contendo um gráfico de pizza de 400 × 300 pt.
- A fatia “Apples” explodida para fora em 20 pt.
- Todo o gráfico girado 45° no sentido horário.
- Uma legenda correspondente às três categorias de frutas.

## Variações comuns e casos de borda

### Inserindo múltiplos gráficos

Se precisar de mais de um gráfico, chame `builder.insertChart` novamente após mover o cursor:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Alterando cores do gráfico

Você pode personalizar as cores das fatias através da coleção `getPoints()` da série:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Manipulando grandes conjuntos de dados

Para conjuntos de dados com mais de 10 fatias, considere usar um gráfico de rosquinha (`ChartType.DOUGHNUT`) para manter a visualização clara.

## Conclusão

Agora você sabe como **criar um documento Word**, **inserir gráfico de pizza**, **girar gráfico de pizza** e **gerar um arquivo Word** usando Aspose.Words para Java. A solução completa demonstra todo o fluxo de trabalho, desde a inicialização do documento até a saída final do arquivo, abordando tanto o “como” quanto o “por quê” de cada passo.

Em seguida, explore tópicos relacionados, como **como criar dados de gráfico de pizza** a partir de um banco de dados, adicionar rótulos de dados ou exportar o gráfico como imagem. Experimente diferentes tipos de gráficos (barra, linha, rosquinha) para ampliar seu conjunto de ferramentas de automação Word.

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}