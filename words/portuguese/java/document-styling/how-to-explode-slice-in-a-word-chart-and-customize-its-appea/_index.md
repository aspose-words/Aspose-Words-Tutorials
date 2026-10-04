---
category: general
date: 2026-10-04
description: Aprenda a explodir fatias em um gráfico do Word, explodir fatias de gráfico
  de pizza e alterar o tamanho de um gráfico de rosca com um exemplo Java passo a
  passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: pt
lastmod: 2026-10-04
og_description: Como explodir uma fatia em um gráfico do Word e personalizar gráficos
  de pizza ou donut com Java. Siga o exemplo completo para modificar o gráfico no
  Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Como explodir uma fatia em um gráfico do Word – guia completo em Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Como explodir uma fatia em um gráfico do Word e personalizar sua aparência
url: /pt/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como explodir fatia em um gráfico do Word e personalizar sua aparência

Se você precisa **how to explode slice** em um gráfico do Word, este guia mostra exatamente como. Seja preparando uma apresentação de vendas ou um relatório financeiro, explodir uma fatia de gráfico de pizza ou ajustar o buraco de um gráfico de rosquinha pode fazer os dados mais importantes se destacarem. Nas seções a seguir, você também aprenderá como **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, e **customize pie chart word** documentos usando Aspose.Words for Java.

Você concluirá este tutorial com um programa Java completo, pronto‑para‑executar, que carrega um arquivo `.docx`, explode a primeira fatia de um gráfico de pizza, altera o tamanho do buraco da rosquinha e salva o resultado. Nenhum script externo ou edição manual é necessário.

## Pré-requisitos

- Java 17 ou posterior instalado na sua máquina de desenvolvimento.  
- Maven 3.6+ (ou Gradle) para gerenciar dependências.  
- Biblioteca Aspose.Words for Java (a avaliação gratuita funciona para desenvolvimento).  
- Um documento Word (`input.docx`) que contém ao menos um gráfico (pizza ou rosquinha).

## Etapa 1: Adicionar Aspose.Words ao seu projeto

Se você usa Maven, adicione a dependência a seguir ao seu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Para Gradle, coloque isto em `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Dica profissional:** Mantenha a versão da sua biblioteca atualizada; lançamentos mais recentes adicionam suporte a tipos de gráfico adicionais e melhoram o desempenho.

## Etapa 2: Carregar o documento Word que contém um gráfico

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Por que isso importa:** Carregar o documento cria uma representação em memória que o Aspose.Words pode percorrer. Sem esse objeto você não pode acessar os nós do gráfico.

## Etapa 3: Recuperar o primeiro gráfico no documento

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explicação:** `NodeType.SHAPE` cobre todos os objetos de desenho, incluindo gráficos. O argumento `true` indica ao Aspose que procure recursivamente, garantindo que o primeiro gráfico seja encontrado mesmo que esteja aninhado dentro de uma tabela.

## Etapa 4: Explodir a primeira fatia de um gráfico de pizza

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Como funciona:** O método `setExplosion` recebe um valor numérico que determina o quão longe a fatia se afasta do centro. Um valor de `20` é visualmente perceptível sem quebrar o layout do gráfico.

## Etapa 5: Ajustar o tamanho do buraco da rosquinha para um gráfico de rosquinha

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Por que isso ajuda:** Um buraco de rosquinha maior pode melhorar a legibilidade quando você tem muitos pontos de dados. O método `setDoughnutHoleSize` espera uma porcentagem (0‑100).

## Etapa 6: Salvar o documento modificado

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Saída esperada

- A primeira fatia do primeiro gráfico de pizza é deslocada para fora, fazendo-a se destacar.
- Se o gráfico for uma rosquinha, o buraco central expande para 40 % do raio do gráfico.
- O arquivo resultante `PieChart.docx` pode ser aberto no Microsoft Word, LibreOffice ou qualquer visualizador compatível, mostrando as alterações visuais aplicadas programaticamente.

## Exemplo completo e executável

Abaixo está o programa inteiro em um bloco. Copie-o para `ChartExploder.java`, ajuste os caminhos dos arquivos e execute-o com `mvn compile exec:java` (ou a configuração de execução da sua IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Executar este código **modificará o gráfico no Word**, **explodirá a fatia do gráfico de pizza** e **alterará o tamanho da rosquinha** automaticamente.

## Perguntas comuns e casos extremos

| Pergunta | Resposta |
|----------|--------|
| *E se o documento contiver vários gráficos?* | O exemplo direciona ao gráfico **primeiro** (`NodeType.SHAPE, 0`). Para trabalhar com outros gráficos, altere o índice ou itere através de `doc.getChildNodes(NodeType.SHAPE, true)` e filtre por `shape.getChart() != null`. |
| *Posso explodir uma fatia que não seja a primeira?* | Sim. Acesse a série desejada via `chart.getSeries().get(seriesIndex)` e chame `setExplosion(value)`. Os índices começam em zero. |
| *Isso funciona com arquivos Word 2007‑2021?* | Aspose.Words suporta `.doc`, `.docx`, `.dot` e `.dotx`. O mesmo código funciona em todas as versões porque a biblioteca abstrai o formato do arquivo. |
| *E se o gráfico for de barras ou linhas?* | `setExplosion` e `setDoughnutHoleSize` são aplicáveis apenas a gráficos do tipo pizza. O código ignora com segurança essas operações quando o tipo de gráfico difere. |
| *Preciso de uma licença para Aspose.Words?* | Uma licença de avaliação gratuita remove o limite de 30 dias, mas adiciona uma marca d'água. Para produção, adquira uma licença para remover a marca d'água e desbloquear todas as funcionalidades. |

## Conclusão

Agora você sabe **how to explode slice** em um gráfico do Word, como **modify chart in Word**, e como **change doughnut chart size** usando Aspose.Words for Java. O exemplo completo demonstra o fluxo de trabalho completo — desde carregar um documento, localizar o gráfico, aplicar ajustes visuais, até salvar o resultado — para que você possa integrar essas etapas em qualquer pipeline de relatórios ou geração de documentos.

**Próximos passos**

- Explore outras personalizações de gráficos, como mudar cores, adicionar rótulos de dados ou trocar o tipo de gráfico (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Combine esta lógica com Aspose.PDF para gerar uma versão PDF do mesmo relatório.  
- Automatize o processo para um lote de documentos percorrendo os arquivos em um diretório.

Sinta-se à vontade para experimentar diferentes valores de explosão ou porcentagens de buraco da rosquinha para atender às diretrizes de design. Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá-lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Como criar gráfico de colunas usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ocultar eixo do gráfico em um documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Inserir gráfico de bolhas em documento Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}