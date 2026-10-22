---
category: general
date: 2026-09-24
description: Aprenda a criar gráficos no Word usando Java, inserir um gráfico radial
  e salvar o documento como docx com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: pt
lastmod: 2026-09-24
og_description: Crie gráfico no Word com Java e Aspose.Words. Este tutorial mostra
  como adicionar um gráfico radial, personalizar os dados e salvar o documento como
  docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Criar gráfico no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Como criar gráfico no Word com Java e Aspose.Words
url: /pt/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar gráfico no Word com Java e Aspose.Words

Se você precisa **criar gráfico no Word** a partir de uma aplicação Java, este guia o conduzirá por todo o processo. Você verá como adicionar um gráfico radial, opcionalmente preencher suas séries e, finalmente, **save document as docx** usando a biblioteca Aspose.Words for Java.

Gerar dados visuais dentro de um arquivo Word é uma necessidade comum para relatórios, faturamento ou geração automática de documentos. Ao final deste tutorial, você será capaz de criar projetos **create word document java** que **add chart to Word** arquivos sem nenhuma edição manual.

## Pré-requisitos

* Java Development Kit (JDK) 8 ou mais recente.
* Maven ou Gradle para gerenciamento de dependências.
* Uma IDE como IntelliJ IDEA, Eclipse ou VS Code.
* Uma licença válida do Aspose.Words for Java (a avaliação gratuita funciona para desenvolvimento).

Essas ferramentas fornecem a base para os exemplos de código que se seguem.

## Etapa 1: Configurar o projeto Maven

Crie um novo projeto Maven (ou atualize um existente) e adicione a dependência Aspose.Words ao seu `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Executar `mvn clean install` baixa a biblioteca e torna as classes como `Document`, `DocumentBuilder` e `ChartType` disponíveis no classpath.

> **Dica profissional:** Mantenha a versão da biblioteca atualizada. Novas versões adicionam tipos de gráficos e melhoram o desempenho de renderização.

## Etapa 2: Criar um novo documento Word

O primeiro passo programático para **create chart in Word** é instanciar um `Document` vazio. Esse objeto representa todo o pacote `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funciona como um cursor; ele conhece o ponto de inserção atual e fornece métodos para texto, tabelas e gráficos. Neste ponto, você tem **created word document java** – uma tela limpa pronta para conteúdo.

## Etapa 3: Inserir um gráfico radial

Aspose.Words suporta muitos tipos de gráficos. Para **insert radial chart**, chame `insertChart` com `ChartType.RADIAL`. O método também requer a largura e altura em pontos (1 ponto ≈ 1/72 polegada).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

O objeto `Shape` retornado contém o objeto de gráfico subjacente. O gráfico renderiza automaticamente graduações para um layout de 24,9°, que é o padrão para gráficos radiais no Word.

### Por que usar um gráfico radial?

Um gráfico radial visualiza dados que se enrolam ao redor de um círculo, tornando‑o ideal para mostrar padrões cíclicos (por exemplo, vendas mensais, métricas de relógio). A mesma API pode inserir gráficos de barras, pizza ou linha, mas o tipo radial adiciona um visual distintivo sem código de estilo extra.

## Etapa 4: (Opcional) Preencher os dados das séries do gráfico

Se você quiser que o gráfico exiba valores reais, é necessário adicionar séries e pontos. O trecho a seguir adiciona uma única série com três pontos de dados:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Você pode repetir as chamadas `add` para quantos pontos precisar. Aspose.Words atualiza automaticamente a representação visual, de modo que você vê as fatias radiais ajustarem‑se aos novos valores.

> **Pergunta comum:** *E se eu precisar vincular dados de um banco de dados?*  
> Recupere as linhas, itere sobre elas e chame `series.getDataPoints().add(value, label)` dentro do loop. A API é thread‑safe e funciona com qualquer `ResultSet` que você fornecer.

## Etapa 5: Salvar o documento como DOCX

Quando o gráfico estiver pronto, o passo final é **save document as docx**. O método `save` determina o formato de saída a partir da extensão do arquivo.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

O arquivo gerado contém um gráfico radial totalmente funcional que pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador que suporte o formato DOCX. Como usamos a extensão `.docx`, o Word salva o arquivo no formato Open XML, que é o padrão moderno para documentos Word.

### Verificando o resultado

Abra `RadialChartDemo.docx` no Word:

1. Você deve ver uma única página com um gráfico radial centralizado.
2. Se você adicionou dados de série, o gráfico exibe quatro fatias rotuladas Q1‑Q4.
3. Clique com o botão direito no gráfico → **Edit Data** para confirmar a tabela de dados subjacente.

Se o gráfico aparecer em branco, verifique se você chamou `chart.getChart()` antes de adicionar séries e assegure que o cursor do DocumentBuilder esteja posicionado onde você deseja o gráfico.

## Etapa 6: Dicas avançadas para trabalhar com gráficos

| Dica | Por que é importante |
|-----|----------------|
| **Definir estilo do gráfico** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Melhora a consistência visual sem formatar manualmente cada elemento. |
| **Redimensionar após inserção** – `chart.setWidth(500); chart.setHeight(350);` | Permite ajustar finamente o tamanho do gráfico com base no layout da página. |
| **Adicionar título** – `chart.getChart().getTitle().setText("Revenue Overview");` | Fornece contexto aos leitores que visualizam o documento sem o texto circundante. |
| **Exportar para PDF** – `doc.save("RadialChartDemo.pdf");` | Útil quando você precisa de uma versão não editável para distribuição. |
| **Gerenciamento de licença** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Previene a marca d'água de avaliação em builds de produção. |

Essas melhorias são opcionais, mas demonstram como você pode personalizar ainda mais o gráfico depois de aprender a **add chart to Word**.

## Conclusão

Agora você tem um exemplo completo e autônomo que mostra como **create chart in Word** usando Java, **insert radial chart**, opcionalmente preenchê‑lo com dados, e **save document as docx**. O mesmo padrão funciona para outros tipos de gráficos, então você pode estender este tutorial para gráficos de barras, linhas ou pizza conforme necessário.

Em seguida, você pode explorar:

* **create word document java** projetos que combinam tabelas, imagens e múltiplos gráficos.
* Usando **save document as docx** junto com **save document as pdf** para relatórios multi‑formato.
* Adicionando dados dinâmicos de APIs REST ou bancos de dados aos seus gráficos.

Sinta‑se à vontade para experimentar as opções de estilo, dimensões do gráfico e fontes de dados. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}