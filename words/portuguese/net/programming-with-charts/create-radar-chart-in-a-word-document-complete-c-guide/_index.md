---
category: general
date: 2026-08-10
description: Crie um gráfico de radar rapidamente e aprenda como inserir o gráfico
  em um documento Word usando Aspose.Words. Siga este guia passo a passo para obter
  resultados confiáveis.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- insert chart into word document
- how to insert radar chart
language: pt
lastmod: 2026-08-10
og_description: Crie um gráfico de radar em um arquivo Word com Aspose.Words. Este
  guia mostra como inserir o gráfico no documento Word e personalizá‑lo para uma apresentação
  clara.
og_image_alt: Radar chart created in a Word document using Aspose.Words
og_title: criar gráfico de radar no Word – implementação completa em C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  headline: create radar chart in a Word document – complete C# guide
  type: TechArticle
- description: create radar chart quickly and learn how to insert chart into word
    document using Aspose.Words. Follow this step‑by‑step guide for reliable results.
  name: create radar chart in a Word document – complete C# guide
  steps:
  - name: Set up the project and add Aspose.Words
    text: '1. Open a new Console App project in Visual Studio. 2. Add the Aspose.Words
      package via NuGet:'
  - name: Create a blank document and a builder
    text: A `Document` represents the .docx file, while `DocumentBuilder` provides
      methods to add content.
  - name: Insert radar chart and obtain the Chart object
    text: The `InsertChart` method inserts a chart placeholder and returns a `Shape`.
      Access the underlying `Chart` to modify its settings.
  - name: Enable graduations on both axes for better readability
    text: Graduations (tick marks) improve data interpretation, especially on radar
      charts where radial spacing matters.
  - name: Define the data series for the radar chart
    text: A radar chart requires a category axis (labels) and one or more data series.
      The example adds a single series named *Series 1*.
  - name: Save the document containing the radar chart
    text: Choose a folder where the output should reside. The file extension `.docx`
      ensures compatibility with Microsoft Word, Google Docs, and LibreOffice.
  type: HowTo
tags:
- Aspose.Words
- C#
- Radar chart
- Word automation
title: criar gráfico de radar em um documento Word – guia completo de C#
url: /pt/net/programming-with-charts/create-radar-chart-in-a-word-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# criar radar chart em um documento Word – guia completo C#  

Se você precisar **criar radar chart** em um arquivo Word, este tutorial mostra as etapas exatas. Você verá como **insert chart into word document** com Aspose.Words, configurar graduações dos eixos e adicionar séries de dados para que o gráfico esteja pronto para apresentação.

Gerar um radar chart programaticamente elimina o esforço manual de desenhar formas e alinhar dados. Ao final deste guia você será capaz de responder **how to insert radar chart** em qualquer arquivo .docx, personalizar sua aparência e salvar o resultado com uma única linha de código.

## Pré-requisitos

* .NET 6.0 ou posterior instalado  
* Visual Studio 2022 (ou qualquer editor C#)  
* Uma licença do Aspose.Words para .NET (a avaliação gratuita funciona para testes)  

Nenhum pacote NuGet adicional é necessário além de `Aspose.Words`. O código funciona no Windows, macOS e Linux porque o Aspose.Words é multiplataforma.

## Como criar radar chart em um documento Word

Esta seção percorre cada operação necessária para **criar radar chart** do zero. A abordagem segue o fluxo de trabalho típico recomendado pelo Aspose.Words: criar um `Document`, obter um `DocumentBuilder`, inserir o gráfico, configurar suas propriedades e, finalmente, salvar o arquivo.

### Etapa 1: Configurar o projeto e adicionar Aspose.Words

1. Abra um novo projeto Console App no Visual Studio.  
2. Adicione o pacote Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

3. Se você possui um arquivo de licença, carregue‑o no início do `Main` para evitar marcas d'água de avaliação:

```csharp
// Load license (optional)
Aspose.Words.License license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

**Por que isso importa:** Carregar a licença desativa o banner de avaliação e desbloqueia todas as capacidades de renderização de gráficos.

### Etapa 2: Criar um documento em branco e um builder

Um `Document` representa o arquivo .docx, enquanto `DocumentBuilder` fornece métodos para adicionar conteúdo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new empty document
Document document = new Document();

// Obtain a builder linked to the document
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

**Explicação:** O builder funciona como um cursor; cada comando de inserção escreve na posição atual. Começar com um documento vazio garante que o radar chart seja o primeiro elemento visual.

### Etapa 3: Inserir radar chart e obter o objeto Chart

O método `InsertChart` insere um espaço reservado para o gráfico e retorna um `Shape`. Acesse o `Chart` subjacente para modificar suas configurações.

```csharp
// Insert a radar chart of 400x300 points
Chart radarChart = docBuilder.InsertChart(ChartType.Radar, 400, 300).Chart;
```

**Por que isso funciona:** `ChartType.Radar` indica ao Aspose.Words para gerar um radar (spider) chart. Os parâmetros de tamanho controlam a área visual na página.

### Etapa 4: Habilitar graduações em ambos os eixos para melhor legibilidade

Graduações (marcadores) melhoram a interpretação dos dados, especialmente em radar charts onde o espaçamento radial é importante.

```csharp
// Enable graduations on the radial (X) axis
radarChart.AxisX.HasGraduations = true;
radarChart.AxisX.GraduationLineStyle = LineStyle.Thick;

// Enable graduations on the value (Y) axis
radarChart.AxisY.HasGraduations = true;
radarChart.AxisY.GraduationLineStyle = LineStyle.Thick;
```

**Dica profissional:** Usar `LineStyle.Thick` faz com que os marcadores se destaquem quando o documento é impresso ou visualizado em telas de alta resolução.

### Etapa 5: Definir as séries de dados para o radar chart

Um radar chart requer um eixo de categoria (rótulos) e uma ou mais séries de dados. O exemplo adiciona uma única série chamada *Series 1*.

```csharp
// Remove any default series
radarChart.Series.Clear();

// Add a new series with three categories
radarChart.Series.Add(
    "Series 1",                     // Series name
    new[] { "A", "B", "C" },        // Category labels
    new[] { 10, 20, 15 }            // Corresponding values
);
```

**Explicação:** `Series.Add` mapeia cada rótulo para um valor numérico. O gráfico conecta automaticamente os pontos, formando a característica forma de aranha.

### Etapa 6: Salvar o documento contendo o radar chart

Escolha uma pasta onde a saída deve ser armazenada. A extensão de arquivo `.docx` garante compatibilidade com Microsoft Word, Google Docs e LibreOffice.

```csharp
// Save the document with the radar chart
document.Save("RadialChartGraduations.docx");
```

Após executar o programa, abra `RadialChartGraduations.docx`. Você verá um radar chart com graduações espessas em ambos os eixos e a série de dados exibida como um polígono fechado.

![Radar chart with graduations](/images/radar-chart.png){: .align-center alt="Gráfico de radar criado em um documento Word usando Aspose.Words" }

**Saída esperada:**  

* Um documento Word de uma única página.  
* Um radar chart de 400 × 300 pontos centralizado na página.  
* Marcadores espessos nos eixos radial e de valores.  
* Uma série de dados rotulada “Series 1” com valores 10, 20, 15.

## Como inserir chart into word document – personalização adicional

Embora as etapas principais acima respondam **how to insert radar chart**, você frequentemente precisa de ajustes extras:

| Personalização | Trecho de código | Quando usar |
|---|---|---|
| Alterar título do gráfico | `radarChart.Title.Text = "Performance Overview";` | Para dar contexto aos leitores |
| Definir cor de fundo | `radarChart.ChartArea.FillFormat.Color = Color.LightYellow;` | Para branding ou contraste visual |
| Adicionar uma segunda série | `radarChart.Series.Add("Series 2", new[] {"A","B","C"}, new[] {12,18,22});` | Ao comparar múltiplos conjuntos de dados |
| Ajustar limites dos eixos | `radarChart.AxisY.Minimum = 0; radarChart.AxisY.Maximum = 30;` | Para manter o gráfico dentro de um intervalo conhecido |

Esses trechos podem ser inseridos após **Step 5** e antes de salvar o documento. Eles ilustram variações comuns que os desenvolvedores perguntam ao buscar **insert chart into word document**.

## Armadilhas comuns e como evitá‑las

* **Licença ausente** – O gráfico é renderizado, mas aparece uma marca d'água de avaliação. Carregue uma licença válida no início do `Main`.  
* **Tamanho de gráfico incorreto** – Usar valores em pixels em vez de pontos gera saída distorcida. Aspose.Words espera pontos (1 pt ≈ 1/72 in).  
* **Série vazia** – Esquecer de chamar `Series.Clear()` pode deixar dados de espaço reservado que sobrescrevem sua série personalizada.  

Resolver esses problemas garante que o radar chart apareça exatamente como esperado.

## Conclusão

Agora você sabe como **criar radar chart** em um arquivo Word usando Aspose.Words para .NET. O tutorial cobriu todas as etapas, desde a configuração do projeto até a gravação do documento final, demonstrou **how to insert radar chart** e mostrou como **insert chart into word document** com graduações dos eixos e dados personalizados. Experimente séries adicionais, títulos e estilos para adaptar o gráfico às suas necessidades de relatório.

**Próximos passos**

* Explore outros tipos de gráficos (`ChartType.Pie`, `ChartType.Column`) para ampliar seu conjunto de ferramentas de automação.  
* Combine a geração de gráficos com mail merge para relatórios personalizados.  
* Revise a documentação do Aspose.Words sobre formatação de gráficos para opções avançadas de estilo.  

Feliz codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Inserir Gráfico de Área em Documento Word | Aspose.Words para .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Inserir Gráfico de Coluna em Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Criar Gráfico de Dispersão Word Usando Aspose.Words para .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}