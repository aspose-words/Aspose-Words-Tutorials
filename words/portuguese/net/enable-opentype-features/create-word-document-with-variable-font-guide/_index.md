---
category: general
date: 2026-03-19
description: Crie um documento Word usando Aspose.Words e uma fonte variável. Aprenda
  como alterar o peso da fonte, definir a largura da fonte e especificar a variação
  da fonte em C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: pt
og_description: Crie um documento Word com uma fonte variável usando Aspose.Words.
  Este tutorial mostra como carregar a fonte, alterar o peso da fonte, definir a largura
  da fonte e especificar a variação da fonte.
og_title: Criar documento Word com fonte variável – Guia completo
tags:
- Aspose.Words
- C#
- Variable Font
title: Criar documento Word com fonte variável – Guia
url: /pt/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar documento Word com fonte variável – Guia

Já precisou **criar documento Word** que use uma fonte variável moderna, mas não sabia por onde começar? Você não está sozinho. Em muitos projetos — pense em relatórios dinâmicos ou brochuras consistentes com a marca — poder **alterar o peso da fonte** em tempo real é realmente transformador.  

Neste tutorial vamos percorrer todo o processo: desde o carregamento de uma fonte variável no Aspose.Words, até a definição de seu peso e largura, e finalmente salvar um DOCX que fique exatamente como você projetou. Sem referências vagas, apenas código concreto que você pode inserir no seu projeto C# agora mesmo.

## O que você aprenderá

- Como **carregar arquivos de fonte variável** no Aspose.Words usando `FontSettings`.
- A sintaxe para **definir variações de fonte** nos eixos como `wght` (peso) e `wdth` (largura).
- Formas de **definir a largura da fonte** e **alterar o peso da fonte** em um único `Run`.
- Dicas para solucionar armadilhas comuns (glifos ausentes, caminhos de pasta incorretos, etc.).
- Um exemplo completo e executável que você pode copiar‑colar e testar instantaneamente.

> **Pré-requisitos**: .NET 6+ (ou .NET Framework 4.6+), Aspose.Words para .NET instalado via NuGet, e um arquivo de fonte variável como *RobotoFlex.ttf* colocado em uma pasta local *Fonts*.

## Etapa 1 – Carregar a Fonte Variável no Aspose.Words

Primeiro, precisamos informar ao Aspose.Words onde procurar nossas fontes personalizadas. A classe `FontSettings` faz o trabalho pesado.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Por que isso importa**: Sem registrar a pasta, o Aspose.Words recorre às fontes do sistema e ignorará quaisquer dados de variação OpenType que você tente aplicar posteriormente. Ao apontar para um diretório específico, você garante que *RobotoFlex* (ou qualquer outra fonte variável) seja encontrada sempre que o código for executado.

> **Dica profissional**: Defina o segundo parâmetro de `SetFontsFolder` como `true` se quiser que o Aspose pesquise também subpastas. Isso ajuda quando você organiza fontes por estilo ou peso.

## Etapa 2 – Criar um Novo Documento e Adicionar Texto de Exemplo

Agora que o mecanismo de fontes sabe onde procurar, criamos um `Document` em branco e inserimos um parágrafo com um `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**O que está acontecendo**: `Run` representa um trecho contíguo de texto com formatação uniforme. Ao criá‑lo primeiro, mantemos a lógica de formatação isolada — perfeito para aplicar posteriormente diferentes eixos de variação a runs separados, se necessário.

## Etapa 3 – Definir os Eixos de Variação Desejados (Peso & Largura)

Fontes variáveis expõem *eixos* que podem ser ajustados em tempo de execução. Os dois mais comuns são `wght` (peso da fonte) e `wdth` (largura da fonte). O Aspose.Words modela isso com a coleção `OpenTypeFontVariation`.  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Por que esses números**: Na especificação OpenType, `wght` varia do peso mínimo ao máximo da fonte (geralmente 100–900). Um valor de **700** corresponde a uma aparência negrito. `wdth` funciona de forma semelhante; **100** significa a largura padrão (normal), enquanto valores abaixo de 100 condensam os glifos.  

> **Caso extremo**: Algumas fontes variáveis não suportam um determinado eixo. Se você fornecer uma tag não suportada, o Aspose a ignorará silenciosamente. Sempre verifique novamente a especificação da fonte (geralmente encontrada nos metadados do arquivo `.ttf` ou `.otf`).

## Etapa 4 – Aplicar a Variação ao Run Usando o Nome da Fonte

Agora vinculamos os dados de variação ao texto real. A classe `FontInfo` contém o nome da família da fonte e a coleção de eixos.  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explicação**: Ao definir `FontInfo`, contornamos a propriedade usual `Font.Name` e entregamos ao mecanismo uma configuração de fonte totalmente qualificada. Esta é a única maneira de dizer ao Aspose.Words para usar uma fonte variável com eixos personalizados.  

> **Erro comum**: Esquecer de corresponder exatamente ao nome da família dentro do arquivo de fonte (`RobotoFlex` neste exemplo). Um erro de digitação fará com que o Aspose recorra a uma fonte padrão, e sua variação será perdida.

## Etapa 5 – Salvar o Documento e Verificar o Resultado

Finalmente, grave o documento no disco. O DOCX gerado conterá as instruções da fonte variável, que o Microsoft Word (2016+) pode renderizar corretamente.  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Abra o arquivo resultante no Word, selecione o texto e observe a caixa de diálogo **Fonte**. Você deverá ver *Roboto Flex* listado, e o texto aparecerá mais negrito que o conteúdo ao redor — exatamente o que a configuração `wght = 700` solicitou.  

> **Dica de verificação**: Se o texto parecer inalterado, verifique novamente se o arquivo de fonte realmente suporta o eixo `wght`. Algumas fontes “variáveis” expõem apenas `ital` (itálico) ou `opsz` (tamanho óptico).

## Opcional: Adicionar Mais Variação – Alterar Largura Dinamicamente

Se você quiser *definir a largura da fonte* de forma diferente para outro parágrafo, basta repetir as etapas 3‑4 com uma nova coleção `OpenTypeFontVariation`.  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Agora você tem dois runs — um negrito, outro ligeiramente mais largo — demonstrando tanto **alterar o peso da fonte** quanto **definir a largura da fonte** no mesmo documento.

## Exemplo Completo Funcional

Copie o trecho abaixo para um novo aplicativo console (`Program.cs`) e execute‑o. Certifique‑se de que a pasta `Fonts` contenha `RobotoFlex.ttf` (ou qualquer fonte variável que preferir).  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Saída esperada**: Um arquivo `VariableFont.docx` onde a frase “Variable‑weight text” aparece em negrito, graças ao eixo `wght = 700`, mantendo a largura padrão.

## Perguntas Frequentes & Casos Limite

| Pergunta | Resposta |
|----------|----------|
| *E se a fonte não for encontrada?* | Verifique o caminho da pasta, assegure que o nome do arquivo corresponde e que o processo tem permissões de leitura. Você também pode chamar `fontSettings.GetFonts()` para listar as fontes detectadas. |
| *Posso combinar múltiplos runs com variações diferentes?* | Absolutamente. Cada `Run` pode carregar seu próprio `FontInfo`. Basta repetir as etapas 3‑4 para cada run. |
| *Versões mais antigas do Word suportam fontes variáveis?* | O Word 2016 (Build 16.0.8001) introduziu suporte básico. Se você direcionar versões mais antigas, o documento recairá para a instância estática mais próxima da fonte. |
| *Existe um limite para quantos eixos eu posso definir?* | Você pode definir qualquer número que a fonte especifica. Tags comuns são `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Fornecer uma tag não suportada simplesmente não tem efeito. |
| *Como depurar glifos ausentes?* | Use `FontSettings.GetFontSources()` para inspecionar as fontes carregadas e `FontInfo.HasGlyph(char)` para testar caracteres individuais. |

## Conclusão

Em poucos passos, mostramos **como criar documentos Word** que aproveitam o poder das fontes variáveis, permitindo que você **altere o peso da fonte**, **defina a largura da fonte**, **carregue arquivos de fonte variável** e **defina eixos de variação de fonte** — tudo com Aspose.Words para .NET.  

A ideia central é simples: registre a pasta de fontes, descreva os eixos desejados, anexe‑os a um `Run` e salve. A partir daqui você pode expandir a técnica para seções inteiras, tabelas ou até gerar programaticamente relatórios específicos de marca.  

**Próximos passos**: experimente substituir `RobotoFlex` por outra fonte variável, experimente o eixo `ital` (itálico), ou gere uma versão PDF do mesmo documento usando Aspose.PDF. O mesmo padrão se aplica — carregar, definir, aplicar, salvar.  

Feliz codificação, e aproveite a flexibilidade que as fontes variáveis trazem para seus projetos de automação Word!  

<img src="variable-font-demo.png" alt="Criar documento Word com exemplo de fonte variável">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}