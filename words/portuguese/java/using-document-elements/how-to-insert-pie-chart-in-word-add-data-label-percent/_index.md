---
category: general
date: 2026-07-20
description: como inserir um gráfico de pizza no Word com Aspose.Words. Aprenda a
  adicionar rótulo de dados em percentual e exibir porcentagens no gráfico para documentos
  profissionais.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: pt
lastmod: 2026-07-20
og_description: como inserir um gráfico de pizza no Word usando Aspose.Words. Este
  guia mostra como adicionar a porcentagem ao rótulo de dados e exibir as porcentagens
  no gráfico em apenas algumas linhas.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: como inserir gráfico de pizza no Word – guia rápido
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: como inserir gráfico de pizza no Word – adicionar percentual ao rótulo de dados
url: /pt/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como inserir gráfico de pizza no Word – adicionar rótulo de dados percentual

Já se perguntou **como inserir gráfico de pizza** em um documento Word sem lutar com a interface? Você não está sozinho. Em muitos cenários de relatórios você precisa *adicionar gráfico de pizza ao Word* e, mais importante, **exibir porcentagem no gráfico de pizza** para que os leitores compreendam instantaneamente a distribuição dos dados.

Neste tutorial vamos percorrer todo o processo usando Aspose.Words for Java. Ao final, você saberá exatamente como **add data label percent**, **display percentages on chart**, e obter um gráfico de pizza polido que fica correto na primeira vez. Sem plugins extras, sem ajustes manuais — apenas código limpo que você pode inserir em qualquer projeto.

---

## Pré-requisitos

- Java 17 (ou superior) – a versão LTS atual que o Aspose.Words suporta.
- Aspose.Words for Java 24.x (a mais recente no momento da escrita, julho 2026).
- Uma configuração básica de Maven ou Gradle para obter a biblioteca.
- Uma IDE de sua preferência (IntelliJ IDEA, Eclipse, VS Code… qualquer serve).

Se você já tem isso, ótimo — vamos mergulhar.

---

## Etapa 1: Configurar o projeto e importar a biblioteca

Primeiro, adicione a dependência do Aspose.Words ao seu `pom.xml` (Maven) ou `build.gradle` (Gradle). Isso lhe dá acesso às classes `Document`, `DocumentBuilder` e de gráficos.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Mantenha o número da versão atualizado; lançamentos mais recentes costumam adicionar correções relacionadas a gráficos que tornam **display percentages on chart** mais confiável.

---

## Etapa 2: Criar um novo documento Word e um builder

O builder é sua ferramenta multifuncional para inserir conteúdo. Aqui criamos um documento novo e anexamos um `DocumentBuilder` a ele.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Por que precisamos de um builder? Ele abstrai as estruturas OpenXML de baixo nível, permitindo que nos concentremos no *que* queremos — como **add pie chart to word** — em vez de *como* o XML se parece.

---

## Etapa 3: Inserir o gráfico de pizza

Agora vem o núcleo de **how to insert pie chart**. Pedimos ao builder que coloque um gráfico de pizza de tamanho específico. As dimensões são em pontos (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Neste ponto o gráfico está vazio, mas o espaço reservado já está no documento. Você acabou de **add pie chart to word** programaticamente.

---

## Etapa 4: Preencher o gráfico com dados

Um gráfico de pizza precisa de ao menos uma série de valores. Vamos alimentá-lo com alguns dados de exemplo que representam participação de mercado.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Se você precisar de múltiplas séries (pizzas empilhadas, rosquinhas, etc.) pode chamar `pieChart.getSeries().add()` e repetir os passos. A mesma lógica se aplica quando você quiser **display percentages on chart** para cada fatia.

---

## Etapa 5: **add data label percent** – exibir as porcentagens nas fatias

Esta é a parte que a maioria dos desenvolvedores esquece: configurar os rótulos de dados para mostrar porcentagens. Sem isso, o gráfico mostra apenas números brutos, o que pode ser ambíguo.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

A chamada `setShowPercent(true)` indica ao Aspose.Words que renderize o rótulo como “30 %”, “45 %”, etc. É exatamente assim que você **show percent on pie chart** sem nenhum trabalho extra de formatação.

---

## Etapa 6: Salvar o documento

Finalmente, escreva o documento no disco. Você pode escolher `.docx`, `.pdf` ou até `.html`. Para este guia, vamos ficar com o formato moderno `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Execute o programa, abra `PieChartDemo.docx` e você verá um gráfico de pizza bem renderizado com rótulos de porcentagem em cada fatia.

---

## Saída esperada

Abaixo está uma captura de tela do arquivo Word gerado. Observe como cada fatia exibe sua parte como porcentagem — exatamente o que queríamos ao definir **add data label percent**.

![Captura de tela de um documento Word contendo um gráfico de pizza com rótulos de porcentagem](/images/pie-chart-percent.png){.center width=600px alt="Captura de tela mostrando como inserir gráfico de pizza no Word com rótulos de porcentagem"}

*O texto alternativo inclui a palavra‑chave principal, atendendo tanto ao SEO quanto à acessibilidade.*

---

## Perguntas comuns e tratamento de casos extremos

| Question | Answer |
|----------|--------|
| **Posso mudar a fonte dos rótulos de porcentagem?** | Sim. Após habilitar `setShowPercent(true)`, recupere o objeto `DataLabel` e ajuste sua propriedade `Font` (`dataLabel.getFont().setSize(10);`). |
| **E se eu precisar de um gráfico de rosca em vez de pizza?** | Substitua `ChartType.PIE` por `ChartType.DOUGHNUT` na chamada `insertChart`. A mesma lógica **add data label percent** funciona. |
| **As versões mais antigas do Word (2007‑2010) exibem as porcentagens corretamente?** | Aspose.Words grava o XML subjacente de forma independente de versão, portanto as porcentagens aparecem em qualquer Word que suporte gráficos (2007+). |
| **Como adicionar um título ao gráfico?** | Use `pieChart.getTitle().setText("Market Share");` antes de salvar. |
| **Posso inserir o gráfico em um parágrafo ou célula de tabela específicos?** | Com certeza. Mova o `DocumentBuilder` para o local desejado (`builder.moveToParagraph(index, true);` ou `builder.moveToCell(table, row, column, true);`) antes de chamar `insertChart`. |

---

## Dicas e truques do campo

- **Dica profissional:** Se você planeja gerar muitos gráficos em um loop, reutilize uma única instância de `DocumentBuilder`; isso reduz o consumo de memória.
- **Atenção:** Fatias muito pequenas (< 2 %). Aspose.Words pode omitir o rótulo para evitar confusão; você pode forçar com `dataLabel.setShowLabel(true);`.
- **Nota de desempenho:** A renderização de gráficos consome muita CPU. Para geração em massa de relatórios, considere multithreading, mas garanta que cada thread trabalhe em sua própria instância de `Document`.
- **Verificação de versão:** O método `setShowPercent` foi introduzido no Aspose.Words 22.8. Se você estiver em uma versão mais antiga, atualize ou calcule manualmente as porcentagens e defina-as como rótulos personalizados.

---

## Recapitulação

Cobremos **how to insert pie chart** em um documento Word usando Aspose.Words, mostramos como **add data label percent**, e demonstramos a maneira mais simples de **display percentages on chart**. Com apenas algumas linhas de Java você pode **add pie chart to word** e **show percent on pie chart**, transformando números brutos em visualizações instantaneamente legíveis.

---

## O que vem a seguir?

- Experimente outros tipos de gráfico (`BAR`, `LINE`, `AREA`) e veja como a mesma lógica **add data label percent** se aplica.
- Combine gráficos com tabelas para relatórios mais ricos — Aspose.Words facilita colocar um gráfico ao lado de uma tabela de dados.
- Explore exportar o mesmo documento para PDF ou HTML e veja como as porcentagens são renderizadas em diferentes formatos.

Sinta‑se à vontade para ajustar dimensões, cores ou a fonte de dados (por exemplo, uma consulta ao banco de dados) e observar seus relatórios Word ganharem vida. Se encontrar algum problema, deixe um comentário abaixo — boa criação de gráficos!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Inserir gráfico de colunas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserir gráfico de área no documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Inserir um gráfico de bolhas no Word usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}