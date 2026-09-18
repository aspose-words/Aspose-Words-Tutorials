---
category: general
date: 2026-09-18
description: Aprenda a criar um gráfico radial em um documento do Word usando Java,
  adicionar rótulos de dados ao gráfico e inserir dados de séries com um exemplo de
  código completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: pt
lastmod: 2026-09-18
og_description: Crie um gráfico radial em um documento Word usando Java, adicione
  rótulos de dados ao gráfico e insira dados de séries em um único tutorial.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Crie um gráfico radial no Word com Java – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Como criar um gráfico radial em um documento Word com Java
url: /pt/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico radial em um documento Word com Java

Se você precisa criar um gráfico radial em um documento Word, este guia mostra os passos exatos. Você também aprenderá como adicionar rótulos de dados ao gráfico e inserir dados de séries para que o gráfico esteja pronto para apresentação.

Gerar um gráfico programaticamente elimina o trabalho de formatação manual e garante consistência entre relatórios. O tutorial assume que você tem conhecimento básico de Java e uma versão recente da biblioteca Aspose.Words for Java instalada.

## O que você precisará

* Java 17 ou mais recente  
* Aspose.Words for Java (versão 23.12 ou posterior)  
* Uma IDE ou ferramenta de build que possa resolver dependências Maven/Gradle  

Ter esses pré‑requisitos instalados permite que você execute o exemplo sem configuração adicional.

## Como criar um gráfico radial em um documento Word

O primeiro passo é criar um arquivo Word em branco que hospedará o gráfico. Um documento em branco fornece uma tela limpa e evita estilos indesejados.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representa todo o arquivo .docx, enquanto `DocumentBuilder` fornece métodos para inserir elementos como parágrafos, tabelas e gráficos.

## Como inserir o gráfico

Em seguida, insira o próprio gráfico. O método `insertChart` cria um objeto de gráfico e o posiciona na posição atual do cursor do builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Um gráfico polar renderiza pontos de dados ao redor de um eixo central, o que é ideal para exibir informações cíclicas. As dimensões são expressas em pontos (1 pt ≈ 1/72 polegada).

## Adicionar dados de série ao gráfico

Um gráfico sem dados de série está vazio. Você pode adicionar uma série manualmente ou vinculá‑la a uma fonte de dados. O exemplo abaixo adiciona uma única série com três pontos de dados.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` recebe um nome de série, uma lista de rótulos de categoria e uma lista de valores numéricos correspondentes. Você pode repetir este bloco para adicionar séries adicionais (`addSeriesData`).

## Adicionar rótulos de dados ao primeiro série

Rótulos de dados tornam o gráfico legível sem precisar passar o mouse sobre os pontos. A linha a seguir habilita os rótulos de valor para o primeiro série.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Definir `showValue` como `true` exibe o valor de cada ponto diretamente no gráfico. Você também pode habilitar nomes de categoria, porcentagens ou linhas de ligação através do mesmo objeto `DataLabelFormat`.

## Salvar o arquivo Word

Depois que o gráfico estiver configurado, grave o documento no disco. Escolha um local que sua aplicação possa acessar.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

O arquivo `RadialChart.docx` agora contém um gráfico radial totalmente funcional com rótulos de dados.

## Exemplo completo funcional

Abaixo está um programa autocontido que você pode copiar, compilar e executar. Ele demonstra o fluxo completo, desde a criação de um documento Word em branco até a gravação de um gráfico radial com rótulos de dados.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Resultado esperado**

Ao abrir `output/RadialChart.docx` no Microsoft Word, você verá um gráfico radial intitulado *Quarterly Sales*. Cada ponto exibe seu valor numérico (por exemplo, “15000”) ao lado do marcador.

## Variações comuns e casos de borda

| Situação | Alteração recomendada |
|-----------|--------------------|
| Você precisa de um tipo de gráfico diferente | Substitua `ChartType.POLAR` por qualquer outro valor do enum `ChartType` (por exemplo, `ChartType.COLUMN`). |
| O gráfico deve usar um intervalo externo do Excel | Use `chart.setDataRange("Sheet1!A1:B5")` após criar o gráfico e carregar a planilha. |
| Você quer ocultar a legenda | `chart.getLegend().setVisible(false);` |
| O documento deve ser salvo como PDF | Chame `doc.save("RadialChart.pdf");` – Aspose.Words converte o gráfico automaticamente. |

Esses ajustes mantêm a lógica central intacta enquanto adaptam a saída a requisitos específicos.

## Dicas profissionais

* **Reutilize o builder** – Você pode inserir vários gráficos no mesmo documento chamando `builder.insertChart` repetidamente.
* **Desempenho** – Ao gerar muitos gráficos, crie uma única instância de `DocumentBuilder` e reutilize‑a para reduzir a sobrecarga de alocação de objetos.
* **Estilização** – A aparência do gráfico (cores, espessura da linha) é controlada pelos métodos `getSeries().get(i).getFormat()` do objeto `Chart`. Experimente essas configurações para combinar com a identidade visual da sua empresa.

## Conclusão

Agora você sabe como criar um gráfico radial em um documento Word com Java, adicionar dados de série e rótulos de dados ao gráfico antes de salvar o arquivo. O exemplo completo pode ser estendido para lidar com séries adicionais, estilos personalizados ou formatos de saída alternativos.

Explore tópicos relacionados, como **como inserir gráfico** a partir de fontes de dados externas, **criar documentos Word em branco** com modelos predefinidos e **adicionar dados de série** dinamicamente a partir de bancos de dados. Experimente diferentes tipos de gráficos para descobrir qual visual comunica melhor seus dados.

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Criar Documento Word Java – Adicionar Forma Retangular com Efeito de Sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Definir Opções Padrão para Rótulos de Dados em um Gráfico](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}