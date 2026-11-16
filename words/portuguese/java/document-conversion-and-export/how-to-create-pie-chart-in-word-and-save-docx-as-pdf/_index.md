---
category: general
date: 2026-11-15
description: Aprenda como criar um gráfico de pizza em um documento Word e salvar
  o docx como PDF usando Java. Este guia também aborda como converter Word para PDF
  e como adicionar um gráfico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: pt
lastmod: 2026-11-15
og_description: Crie um gráfico de pizza em um arquivo Word e salve o docx como PDF
  com Java. Siga este tutorial passo a passo para converter Word em PDF e adicionar
  gráficos.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Criar um gráfico de pizza no Word e salvar o docx como PDF – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Como criar gráfico de pizza no Word e salvar docx como PDF
url: /pt/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como criar um gráfico de pizza no Word e salvar docx como PDF

Se você precisa **create pie chart** dentro de um documento Word e então **save docx as PDF**, este tutorial mostra exatamente como. Você verá um exemplo completo e executável que converte um arquivo .docx em PDF enquanto incorpora um gráfico de pizza, para que você possa responder “how to add chart” sem procurar trechos espalhados.

Neste guia você aprenderá a:

* Carregar um *.docx* existente (ou começar do zero)  
* Usar Aspose.Words for Java para **create pie chart** e preencher os dados  
* **Save docx as PDF** com o gráfico renderizado corretamente  
* Entender as nuances de **convert word to pdf** quando gráficos estão envolvidos  

Os passos funcionam com Aspose.Words 2024‑x.x e Java 17, mas os conceitos se aplicam a qualquer biblioteca que suporte manipulação de gráficos no Word.

## Pré-requisitos

| Requisito | Por que é importante |
|-------------|----------------|
| Java 17 (ou posterior) | Necessário pela última versão do Aspose.Words JAR |
| Ferramenta de construção Maven ou Gradle | Simplifica o gerenciamento de dependências |
| Aspose.Words for Java (versão mais recente) | Fornece as classes `Document`, `Chart` e `ChartType` |
| Um arquivo de entrada **.docx** (ou um documento em branco) | O gráfico será inserido neste arquivo |

Adicione a dependência do Aspose.Words ao seu `pom.xml` (Maven) ou `build.gradle` (Gradle). Exemplo para Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Etapa 1: Carregar o documento Word (ou criar um novo)

A primeira ação é obter uma instância de `Document`. Se você já tem um modelo, passe seu caminho; caso contrário, crie um documento vazio.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Por que esta etapa?* O objeto `Document` é o contêiner de todo o conteúdo do Word, incluindo gráficos. Carregar um arquivo existente permite que você preserve o texto e os estilos ao redor enquanto adiciona um novo elemento visual.

## Etapa 2: **Create pie chart** – o núcleo de “how to create chart”

Agora instanciamos um objeto `Chart` com `ChartType.PIE`. Isso cria automaticamente um espaço reservado para gráfico de pizza que você pode preencher com dados posteriormente.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explicação*: `ChartType.PIE` indica ao Aspose.Words para usar um modelo de gráfico de pizza. O gráfico é adicionado ao corpo do documento, portanto aparece onde você precisa. Isso satisfaz o requisito de “how to add chart” em uma única chamada.

## Etapa 3: Preencher o gráfico – respondendo “how to add chart” com dados

Um gráfico de pizza não tem sentido sem dados de séries. Use a coleção `Series` para adicionar categorias e valores.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Por que isso importa*: Cada chamada a `add` cria uma fatia da pizza. O primeiro argumento é o rótulo, o segundo é o valor numérico. Você pode substituir esses valores por dados dinâmicos de um banco de dados ou arquivo CSV.

### Opcional: Personalizar aparência (não obrigatório, mas útil)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Essas ajustes ilustram como você pode **how to create chart** com um visual profissional, sem sair do código Java.

## Etapa 4: **Save docx as PDF** – a parte final de “convert word to pdf”

Depois que o gráfico é incorporado, exporte o documento para PDF. Aspose.Words renderiza o gráfico como um vetor, preservando a qualidade.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Ponto chave*: O método `save` converte automaticamente o arquivo Word em PDF, lidando com a rasterização do gráfico, incorporação de fontes e layout de página. Isso cumpre o objetivo de **save docx as pdf** e demonstra uma forma confiável de **convert word to pdf** quando há gráficos presentes.

### Saída esperada

Executar o programa produz `output.pdf` que contém:

* O conteúdo original de `input.docx` (se houver)  
* Um gráfico de pizza totalmente renderizado intitulado *Sales Distribution Q1*  
* Percentuais de fatias precisos correspondentes aos dados (40 %, 30 %, 30 %)

Abra o PDF em qualquer visualizador e você deverá ver um gráfico de pizza nítido, idêntico ao que você veria no arquivo Word.

## Armadilhas comuns e como evitá‑las

| Problema | Causa | Correção |
|-------|-------|-----|
| Gráfico aparece em branco no PDF | Configurações de fonte ou renderização de gráfico ausentes | Certifique‑se de que está usando a versão mais recente do Aspose.Words; ela inclui as bibliotecas de renderização necessárias. |
| Valores de dados são arredondados incorretamente | Uso de valores inteiros com números grandes | Forneça valores `double` ou escale os números antes de adicioná‑los à série. |
| PDF de saída é enorme | Imagens incorporadas em alta DPI | Defina `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` se também incorporar imagens. |
| “convert word to pdf” lança `UnsupportedOperationException` | Uso de uma versão Java mais antiga (< 11) | Atualize para Java 17 ou posterior, que o Aspose.Words 24.x requer. |

## Dica profissional: Reutilizar a lógica de criação de gráfico

Se você precisar adicionar vários gráficos ao mesmo documento, extraia o código de construção do gráfico para um método auxiliar:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Agora você pode chamar `doc.getFirstSection().getBody().appendChild(createPieChart(...));` para cada conjunto de dados, mantendo seu código DRY (Don’t Repeat Yourself).

## Conclusão

Agora você sabe como **create pie chart** dentro de um documento Word, preenchê‑lo com dados e **save docx as PDF** usando Java. Este exemplo completo cobre todo o fluxo de trabalho **convert word to pdf**, responde **how to add chart** e demonstra **how to create chart** programaticamente.  

A partir daqui você pode explorar:

* Adicionar gráficos de barra ou linha (`ChartType.BAR`, `ChartType.LINE`) – outro cenário de **how to create chart**.  
* Exportar para outros formatos como PNG ou HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Gerar dinamicamente o documento de entrada com tabelas ou marcadores de posição antes de inserir gráficos.

Sinta‑se à vontade para experimentar diferentes conjuntos de dados, opções de estilo ou até mesmo incorporar vários gráficos por página. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}