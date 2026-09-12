---
category: general
date: 2026-09-11
description: Salve o documento Word após editar um gráfico de rosca com Aspose.Words
  para Java. Aprenda a mudar o tamanho do buraco da rosca, girar o gráfico de rosca
  e editar as propriedades do gráfico de rosca.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: pt
lastmod: 2026-09-11
og_description: Salve o documento Word após editar um gráfico de rosca usando Aspose.Words
  for Java. Este tutorial mostra como alterar o tamanho do furo da rosca, girar o
  gráfico de rosca e personalizar a aparência do gráfico.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Salvar documento Word após editar gráfico de rosca – Guia Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Salvar documento Word após editar gráfico de rosca em Java
url: /pt/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvar documento Word após editar gráfico de rosquinha em Java

Se você precisa **salvar documento Word** que contém um gráfico de rosquinha personalizado, este guia mostra exatamente como fazer. Em apenas algumas linhas de Java você pode alterar o buraco da rosquinha, girar o gráfico de rosquinha e, em seguida, gravar o resultado de volta no disco.

Você verá um exemplo completo e executável que usa Aspose.Words for Java, além de dicas para lidar com vários gráficos, verificar tipos de nós e evitar armadilhas comuns. Nenhuma referência externa é necessária — tudo o que você precisa está incluído.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

- Java 17 ou mais recente instalado
- Maven ou Gradle para gerenciar dependências
- Aspose.Words for Java (versão 23.9 ou posterior) adicionada ao seu projeto  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Um arquivo Word (`input.docx`) que contém um único gráfico de rosquinha

## Etapa 1: Carregar o documento Word

A primeira etapa é abrir o arquivo de origem. Esta etapa é essencial porque toda operação subsequente trabalha no objeto `Document` em memória.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Por quê?** Carregar o documento cria uma representação DOM que permite percorrer formas, tabelas e gráficos. Se o arquivo não puder ser aberto, Aspose.Words lança uma exceção, de modo que você sabe imediatamente que o caminho está errado.

## Etapa 2: Localizar a forma do gráfico de rosquinha

Um gráfico é armazenado dentro de um nó `Shape`. Recuperamos a primeira forma que contém um gráfico e convertemos seu renderizador para `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Por quê?** Verificar `isChart()` impede um `ClassCastException` quando o documento contém imagens ou outras formas antes do gráfico. Isso torna o código robusto para documentos com conteúdo misto.

## Etapa 3: Alterar o tamanho do buraco da rosquinha  

Agora editamos o buraco da rosquinha. O método `setHoleSize` espera uma porcentagem do raio do gráfico (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Por quê?** Alterar o buraco da rosquinha (`change doughnut hole` / `change chart hole size`) permite enfatizar ou des‑enfatizar a área central. Valores fora de 10‑90 % são ignorados pela API.

## Etapa 4: Girar o gráfico de rosquinha  

Para controlar onde a primeira fatia começa, defina o ângulo da primeira fatia. Isso efetivamente **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Por quê?** Girar o gráfico é útil quando você deseja que uma fatia específica apareça no topo ou para atender a uma especificação de design.

## Etapa 5: Salvar o documento atualizado  

Finalmente, grave as alterações em um novo arquivo. Este é o momento em que você **save Word document** com o gráfico editado.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Resultado esperado:** `output.docx` contém o conteúdo original, mas o gráfico de rosquinha agora tem um buraco de 30 % e sua primeira fatia começa em 45 °. Abrir o arquivo no Microsoft Word exibirá o gráfico transformado.

## Exemplo completo em funcionamento

Abaixo está o programa completo que você pode copiar‑colar em sua IDE. Ele inclui todas as importações e o tratamento de erros necessários para **edit doughnut chart** e **save Word document** com segurança.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Saída esperada

Ao abrir `output.docx`:

- O buraco central do gráfico de rosquinha ocupa aproximadamente um terço do raio do gráfico.  
- A primeira fatia começa na posição de 45 graus, deslocando todo o gráfico no sentido horário.  

Ambas as alterações visuais são refletidas instantaneamente no Word.

## Variações comuns e casos de borda

| Situação | Como lidar |
|-----------|----------------|
| **Múltiplos gráficos** | Iterar através de `doc.getChildNodes(NodeType.SHAPE, true)` e filtrar `shape.isChart()`; aplicar `setHoleSize` / `setFirstSliceAngle` a cada `Chart`. |
| **O gráfico não é uma rosquinha** | Verificar `chart.getType()`; chamar `setHoleSize` somente quando `chart.getType() == ChartType.DOUGHNUT`. |
| **Necessidade de alterar o tamanho do buraco dinamicamente** | Calcular a porcentagem desejada com base nos valores dos dados e, em seguida, chamar `setHoleSize(computedValue)`. |
| **Salvar em um stream** | Use |

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Save Word with Password using Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}