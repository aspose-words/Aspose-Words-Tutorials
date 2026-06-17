---
category: general
date: 2026-06-02
description: Exiba a legenda do gráfico em um documento Word usando C#. Aprenda como
  adicionar a legenda, aplicar um estilo de gráfico pré-definido e personalizar os
  elementos visuais do gráfico no Word em minutos.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: pt
og_description: Exiba a legenda do gráfico em um documento do Word instantaneamente.
  Este guia orienta você a adicionar uma legenda, aplicar um estilo de gráfico predefinido
  e lidar com casos especiais.
og_title: Mostrar legenda do gráfico no Word – Tutorial completo em C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Exibir Legenda de Gráfico no Word com C# – Guia Completo Passo a Passo
url: /pt/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exibir Legenda do Gráfico no Word com C# – Guia Completo Passo a Passo

Já se perguntou **como adicionar legenda** a um gráfico que está dentro de um documento Word? Você não está sozinho. Em muitos relatórios, a falta de legenda torna os dados criptográficos, e corrigi‑la não deveria ser um problema.  

Neste tutorial, vamos **exibir a legenda do gráfico** em um arquivo Word usando Aspose.Words for .NET, aplicar um estilo de gráfico predefinido e garantir que a legenda apareça exatamente onde você precisa. Ao final, você terá um exemplo pronto‑para‑executar que pode inserir em qualquer projeto C#.

## O que este Guia Abrange

Vamos percorrer todo o fluxo de trabalho:

1. Carregar um *.docx* existente que já contém um gráfico.  
2. Recuperar o primeiro gráfico (ou qualquer gráfico que você desejar).  
3. **Aplicar estilo de gráfico predefinido** para dar ao visual um aspecto profissional.  
4. **Exibir a legenda do gráfico**, posicioná‑la à direita e lidar com casos especiais como gráficos Waterfall.  
5. Salvar o documento modificado.

Sem ferramentas externas, sem ajustes manuais na interface—apenas código puro. O único pré‑requisito é uma referência ao pacote NuGet Aspose.Words (versão 23.10 ou posterior) e um entendimento básico de C#.

---

## Pré‑requisitos

- .NET 6.0 ou posterior (o exemplo funciona também com .NET Framework 4.7.2).  
- Biblioteca Aspose.Words for .NET instalada (`Install-Package Aspose.Words`).  
- Um arquivo Word (`input.docx`) que já contém ao menos um gráfico.  
- Visual Studio, Rider ou qualquer IDE de sua preferência.

---

## Etapa 1: Configurar o Projeto e Carregar o Documento

Primeiro, crie um aplicativo console (ou integre o código em um projeto existente). Adicione as diretivas `using` e carregue o arquivo `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Por que isso importa:** Carregar o documento é a base. Sem uma instância de `Document` você não pode acessar os objetos de gráfico que o Aspose.Words expõe.

---

## Etapa 2: Recuperar o Gráfico Alvo

Os gráficos são armazenados como nós dentro da árvore do documento. O método `GetChild` realiza uma busca profunda, permitindo obter o primeiro gráfico independentemente de onde ele esteja (cabeçalho, corpo, rodapé, etc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Dica:** Se você tem vários gráficos, altere o índice `0` para `1`, `2`, … ou itere através de `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Etapa 3: Aplicar um Estilo Visual Predefinido

Um gráfico visualmente agradável geralmente começa com um estilo. O Aspose.Words vem com dezenas de estilos incorporados; `ChartStyle.Style12` é uma opção limpa e moderna.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Como funciona:** A propriedade `Style` corresponde aos estilos de gráfico incorporados do Word que você vê na interface. Escolher um predefinido evita que você precise definir manualmente cores, fontes e marcadores.

---

## Etapa 4: Habilitar a Legenda e Posicioná‑la

Agora, a estrela do espetáculo—**exibir a legenda do gráfico**. Ativamos a legenda e, em seguida, ancoramos‑a ao lado direito do gráfico.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Por que à direita?** Posicionar a legenda à direita mantém a área de dados ampla, o que é especialmente útil para gráficos de barras ou colunas.

---

## Etapa 5: Tratar Gráficos Waterfall (Caso Especial)

Gráficos Waterfall se comportam de forma um pouco diferente; a legenda pode ficar oculta por padrão. A cláusula de proteção a seguir garante que a legenda esteja visível quando o tipo de gráfico for Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Observação de caso extremo:** Algumas versões mais antigas do Word ignoram `HasLegend` para gráficos Waterfall, portanto definir explicitamente `Legend.Show` garante a visibilidade.

---

## Etapa 6: Salvar o Documento Modificado

Finalmente, grave as alterações de volta ao disco. Você pode sobrescrever o arquivo original ou criar um novo.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Executar o programa gerará `output.docx` com uma legenda visível à direita, estilizada com `Style12`. Abra o arquivo no Word para verificar o resultado.

---

## Exemplo Completo Funcional (Todas as Etapas Combinadas)

Abaixo está o código completo, pronto‑para‑executar. Copie‑e‑cole em `Program.cs` (ou em qualquer arquivo C#) e ajuste os caminhos dos arquivos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Saída esperada:** Ao abrir `output.docx` você verá o gráfico original com uma legenda alinhada à direita, estilizada com o moderno `Style12`. Todas as séries de dados estão claramente rotuladas, tornando o gráfico instantaneamente compreensível.

---

## Perguntas Frequentes (FAQ)

### Como adicionar legenda a um gráfico específico (não ao primeiro?)

Substitua o índice `0` em `GetChild(NodeType.Chart, 0, true)` pela posição baseada em zero do seu gráfico alvo, ou percorra todos os nós de gráfico:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Posso colocar a legenda na parte inferior em vez da direita?

Claro. Basta mudar o enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### E se o gráfico já tem legenda mas eu quiser ocultá‑la?

Defina `HasLegend` como `false`:

```csharp
chart.HasLegend = false;
```

### Isso funciona com Word 2010, 2016 e posteriores?

Sim. O Aspose.Words abstrai a versão subjacente do Word, portanto o mesmo código funciona em todos os arquivos .docx modernos.

---

## Dicas Profissionais & Armadilhas Comuns

- **Dica profissional:** Depois de aplicar um estilo, você ainda pode ajustar elementos individuais (cores, rótulos de dados) via a coleção `Chart.Series`. O estilo fornece uma base sólida.
- **Cuidado com:** Se o gráfico estiver dentro de uma célula de tabela, a legenda pode ficar apertada. Considere aumentar o tamanho do gráfico (`chart.Width`, `chart.Height`) antes de posicionar a legenda.
- **Nota de desempenho:** Carregar documentos grandes (centenas de MB) pode consumir muita memória. Use `LoadOptions` com `LoadFormat.Docx` para reduzir a sobrecarga se você precisar apenas manipular o gráfico.

---

## Próximos Passos

Agora que você sabe **como adicionar legenda** e **aplicar estilo de gráfico predefinido** no Word, pode explorar:

- **Cores de gráfico personalizadas** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formatação de rótulo de dados** (`chart.Series[i].HasDataLabel = true`).  
- **Exportar o gráfico como imagem** (`chart.ToImage()`), útil para incorporar em outros lugares.  

Cada um desses tópicos se baseia no mesmo modelo de objetos, portanto a curva de aprendizado será suave.

---

## Conclusão

Acabamos de demonstrar uma solução limpa e completa para **exibir a legenda do gráfico** em um documento Word usando C#. Ao carregar o documento, recuperar o gráfico, aplicar um estilo predefinido, habilitar a legenda e tratar as particularidades dos Waterfall, você obtém um gráfico refinado pronto para qualquer relatório empresarial.

Sinta‑se à vontade para experimentar outros valores de `ChartStyle` ou posições de legenda—suas visualizações de dados merecem a melhor apresentação. Se encontrar algum problema, deixe um comentário abaixo; feliz codificação!

## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Inserir Gráfico de Colunas em um Documento Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Ocultar Eixo do Gráfico em um Documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Usando a API de Gráficos do Word](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}