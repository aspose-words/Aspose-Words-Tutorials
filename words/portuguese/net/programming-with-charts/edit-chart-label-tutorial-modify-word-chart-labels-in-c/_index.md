---
category: general
date: 2026-09-11
description: Tutorial de edição de rótulo de gráfico mostrando como alterar a posição
  do rótulo, personalizar o rótulo de dados, ocultar o nome da categoria e exibir
  o valor do rótulo com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: pt
lastmod: 2026-09-11
og_description: O tutorial de edição de rótulo de gráfico orienta você a mudar a posição
  do rótulo do gráfico, personalizar o rótulo de dados do gráfico, ocultar o nome
  da categoria do gráfico e exibir o valor do rótulo do gráfico usando o Aspose.Words
  para .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Tutorial de edição de rótulo de gráfico – personalize rótulos de gráficos
  do Word em C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Tutorial de edição de rótulo de gráfico – modifique rótulos de gráfico do Word
  em C#
url: /pt/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial de edição de rótulo de gráfico – modificar rótulos de gráfico do Word em C#

Se você precisa **editar rótulo de gráfico tutorial** para um documento Word, este guia mostra exatamente como alterar a posição do rótulo do gráfico, personalizar o rótulo de dados do gráfico, ocultar o nome da categoria do gráfico e exibir o valor do rótulo do gráfico usando Aspose.Words para .NET. Você verá um exemplo completo e executável que pode ser inserido em qualquer projeto C#.

Trabalhar com rótulos de gráfico é uma necessidade comum ao gerar relatórios, faturas ou dashboards programaticamente. Este tutorial cobre cada passo — desde o carregamento do documento até a persistência das alterações — para que você possa produzir gráficos refinados sem edição manual.

## Pré-requisitos

Antes de começar, certifique‑se de que você tem:

* .NET 6.0 ou superior instalado  
* Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação temporária)  
* Visual Studio 2022 ou qualquer IDE compatível com C#  
* Um arquivo Word (`Chart.docx`) que contenha ao menos um gráfico  

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo aplicativo de console e adicione o pacote NuGet Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Abra `Program.cs` e importe os namespaces necessários:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Esses namespaces dão acesso à classe `Document` para manipular arquivos Word e às classes `Chart` para trabalhar com elementos de gráfico.

## Etapa 2: Carregar o documento Word que contém um gráfico

A primeira linha executável carrega o documento de origem. Substitua `YOUR_DIRECTORY` pelo caminho real onde `Chart.docx` está localizado.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Carregar o documento cria uma representação em memória que pode ser percorrida e modificada.

## Etapa 3: Recuperar o primeiro gráfico no documento

Os gráficos são armazenados como nós filhos do tipo `NodeType.Chart`. O método `GetChild` pesquisa a árvore do documento e devolve o gráfico que você deseja editar.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Se o documento contiver vários gráficos, você pode alterar o índice para direcionar outro.

## Etapa 4: Acessar e personalizar o rótulo de dados da primeira série

Cada série de gráfico possui um objeto `DataLabel` que controla como o rótulo aparece. O código abaixo demonstra as quatro personalizações principais exigidas pelas palavras‑chave secundárias do tutorial.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Por que essas configurações são importantes**

* `DataLabelPosition.Center` move o rótulo da posição padrão fora‑do‑ponto para o centro do ponto de dados, facilitando a leitura quando os pontos estão densamente agrupados.  
* Definir um `Separator` personalizado permite controlar como o nome da série, o valor e outras partes são concatenados.  
* Ocultar o nome da categoria (`ShowCategoryName = false`) reduz a desordem visual quando a categoria já está evidente no eixo.  
* Habilitar `ShowValue` garante que o valor real dos dados seja visível, o que costuma ser necessário em relatórios financeiros ou estatísticos.

## Etapa 5: Salvar o documento modificado

Após ajustar as propriedades do rótulo, persista as alterações em um novo arquivo:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

O novo arquivo (`CustomLabelChart.docx`) contém o mesmo layout de gráfico, mas com a aparência do rótulo que você definiu.

## Código‑fonte completo

Abaixo está o programa completo, pronto para ser executado. Copie‑o para `Program.cs`, ajuste os caminhos dos arquivos e execute o projeto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Resultado esperado

Abra `CustomLabelChart.docx` no Microsoft Word. Você deverá ver o rótulo da primeira série do gráfico centralizado em cada ponto de dados, exibindo apenas o valor numérico e usando “; ” como separador. Os nomes das categorias não aparecerão mais ao lado dos valores.

## Perguntas comuns e casos de borda

| Pergunta | Resposta |
|----------|----------|
| **E se o documento não contiver nenhum gráfico?** | O exemplo verifica se o gráfico é `null` e encerra graciosamente com uma mensagem no console. |
| **Posso editar rótulos de várias séries?** | Sim. Percorra `chart.Series` e aplique as mesmas configurações de `DataLabel` a cada `Series[i].DataLabel`. |
| **Como altero o estilo de fonte do rótulo?** | Use `label.Font` (por exemplo, `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **`DataLabelPosition.Center` é suportado por todos os tipos de gráfico?** | A maioria dos tipos de gráfico 2‑D suporta. Em gráficos 3‑D, algumas posições podem ser ignoradas pelo Word. |
| **Preciso de licença para Aspose.Words?** | O modo de avaliação funciona, mas adiciona marca d'água. Uma licença remove a marca d'água e desbloqueia todas as funcionalidades. |

## Dicas avançadas

* **Processamento em lote:** Encapsule a lógica de carregamento e salvamento em um método que aceite caminhos de entrada e saída. Isso facilita o processamento de dezenas de documentos em um loop.  
* **Desempenho:** Reutilize uma única instância de `Document` ao modificar vários gráficos no mesmo arquivo para evitar I/O repetido.  
* **Testes:** Verifique as alterações de rótulo automatizando uma comparação visual (por exemplo, usando um visualizador Word sem interface) se precisar validar a saída em pipelines de CI.

## Próximos passos

Agora que você domina os fundamentos do **editar rótulo de gráfico tutorial**, considere explorar:

* **Alterar a posição do rótulo do gráfico** para outras séries ou tipos de gráfico diferentes  
* **Personalizar a formatação do rótulo de dados do gráfico** como formatos numéricos, cores de fonte ou preenchimentos de fundo  
* **Ocultar o nome da categoria do gráfico** mantendo o nome da série para gráficos com várias séries  
* **Exibir o valor do rótulo do gráfico** junto com valores percentuais em gráficos de pizza  

Esses tópicos aprofundam seu controle sobre a estética de gráficos Word e preparam você para cenários avançados de geração de relatórios.

---

*Feliz codificação! Se este tutorial foi útil, compartilhe com colegas ou contribua com melhorias no GitHub.*

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}