---
category: general
date: 2026-09-27
description: Crie um gráfico radial em Java e insira o gráfico no Word. Aprenda como
  definir o tamanho do gráfico, adicionar séries de dados e gerar um documento Word
  em branco.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: pt
lastmod: 2026-09-27
og_description: Crie um gráfico radial em Java e, em seguida, insira o gráfico no
  Word. Este guia mostra como definir o tamanho do gráfico, adicionar séries de dados
  e criar um documento Word em branco.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Criar gráfico radial e inserir o gráfico no Word com Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Criar gráfico radial e inserir o gráfico no Word com Java
url: /pt/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar gráfico radial e inserir gráfico no Word com Java

Se você precisa **criar gráfico radial** em um arquivo Word usando Java, este tutorial mostra exatamente como fazer. Você verá como **inserir gráfico no Word**, definir as dimensões do gráfico e criar um **documento Word em branco** do zero.

Percorreremos cada passo necessário, desde a inicialização do documento até a adição de uma série de dados e a gravação do `.docx` final. Ao final, você terá um arquivo Word totalmente funcional contendo um gráfico radial, e entenderá **como definir o tamanho do gráfico** e **adicionar série de dados ao gráfico** para personalizações futuras.

## Pré-requisitos

* Java 17 ou superior (o código compila com qualquer JDK moderno)
* Aspose.Words for Java 24.9 ou mais recente – o método `setShowGraduations` está disponível apenas a partir desta versão
* Uma IDE ou ferramenta de build (Maven/Gradle) que possa incluir o JAR do Aspose.Words
* Familiaridade básica com a sintaxe Java e gerenciamento de dependências Maven/Gradle

> **Dica profissional:** Se você estiver usando Maven, adicione o seguinte ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Etapa 1: Criar um documento Word em branco

Um documento em branco é a tela onde o gráfico será colocado. A classe `Document` representa todo o arquivo `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Criar um documento em branco garante que nenhum conteúdo pré‑existente interfira no layout do gráfico.

## Etapa 2: Inicializar um DocumentBuilder

`DocumentBuilder` fornece métodos convenientes para inserir objetos, texto e outros elementos no documento.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

O builder será usado posteriormente para **inserir gráfico no Word**.

## Etapa 3: Construir o gráfico radial

Aspose.Words suporta vários tipos de gráfico; `ChartType.RADIAL` cria um gráfico radial (polar).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Neste ponto o gráfico existe, mas não tem dados, tamanho ou opções visuais.

## Etapa 4: Adicionar uma série de dados ao gráfico

Um gráfico sem uma série de dados está vazio. O método `add` recebe um nome de série e um array de valores.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Você pode adicionar várias séries chamando `add` repetidamente. Isso atende ao requisito de **adicionar série de dados ao gráfico**.

## Etapa 5: Habilitar graduações (opcional)

Graduações são as linhas de grade radiais que melhoram a legibilidade. Elas estão disponíveis apenas a partir da versão 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Se você usar uma versão mais antiga do Aspose.Words, esta linha lançará uma exceção—portanto, verifique primeiro a versão da sua biblioteca.

## Etapa 6: Definir as dimensões do gráfico

Controlar o tamanho do gráfico permite ajustá‑lo adequadamente dentro das margens da página. Isso aborda **como definir o tamanho do gráfico**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Você pode ajustar os valores de largura e altura para atender às necessidades do seu layout. Lembre‑se de que 1 ponto ≈ 1/72 polegada.

## Etapa 7: Inserir o gráfico no documento Word

Agora o gráfico está pronto para ser inserido. O método `insertChart` do `DocumentBuilder` cuida da inserção.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Este é o núcleo da operação de **inserir gráfico no Word**.

## Etapa 8: Salvar o documento

Finalmente, grave o documento no disco. O arquivo conterá o gráfico radial que você acabou de criar.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Executar o programa gera `RadialChart.docx` no diretório de trabalho do projeto. Abrir o arquivo no Microsoft Word exibe um gráfico radial com três pontos de dados e graduações visíveis.

### Saída esperada

* Um arquivo Word chamado `RadialChart.docx`
* Dentro do arquivo, uma única página contendo um gráfico radial com tamanho 400 × 300 pontos
* O gráfico exibe uma série intitulada **Series 1** com valores **10, 20, 30**
* Graduações (linhas de grade radiais) são visíveis ao redor do gráfico

## Variações comuns e casos de borda

| Situação | O que mudar | Motivo |
|----------|-------------|--------|
| **Múltiplas séries** | Chame `chart.getSeries().add(...)` para cada série | Permite visualização comparativa de dados |
| **Tipo de gráfico diferente** | Substitua `ChartType.RADIAL` por `ChartType.COLUMN` (ou outro) | Use o tipo de gráfico que melhor representa seus dados |
| **Cores personalizadas** | Acesse `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Melhora a identidade visual |
| **Versão mais antiga do Aspose.Words** | Omitir a linha `setShowGraduations` ou atualizar a biblioteca | Prevê `NoSuchMethodError` |
| **Salvar em formato diferente** | Use `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Gera um PDF em vez de um DOCX |

## Exemplo completo executável

Abaixo está o programa Java completo e autocontido. Copie‑o para um arquivo chamado `RadialChartExample.java`, adicione a dependência do Aspose.Words e execute‑o.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusão

Agora você sabe como **criar gráfico radial** programaticamente, **adicionar série de dados ao gráfico**, controlar **como definir o tamanho do gráfico**, e **inserir gráfico no Word** partindo de um **documento Word em branco**. O exemplo usa Aspose.Words for Java 24.9, mas os mesmos conceitos se aplicam a outras bibliotecas de gráficos que expõem uma API semelhante.

### Próximos passos

* Explore outros tipos de gráfico (`ChartType.PIE`, `ChartType.LINE`, etc.) – isso está relacionado à palavra‑chave secundária **insert chart into word**.
* Personalize rótulos de eixo, legendas e cores para corresponder às diretrizes da sua marca.
* Gere gráficos dinamicamente a partir de consultas ao banco de dados ou arquivos CSV.
* Converta o `.docx` resultante para PDF para distribuição (`doc.save("output.pdf", SaveFormat.PDF)`).

Sinta‑se à vontade para experimentar as dimensões, os dados das séries e as opções de estilo para criar a visualização exata que você precisa. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Criar documento Word Java – Adicionar forma retangular com efeito de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Inserir gráfico de área em um documento Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}