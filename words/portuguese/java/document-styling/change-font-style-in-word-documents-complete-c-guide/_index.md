---
category: general
date: 2026-06-27
description: Altere o estilo da fonte em documentos do Word com C#. Aprenda a definir
  o peso da fonte, aplicar negrito e ajustar a largura da fonte para uma tipografia
  precisa.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: pt
og_description: Altere o estilo da fonte em documentos do Word com C#. Descubra como
  definir o peso da fonte, aplicar negrito e ajustar a largura da fonte em alguns
  passos fáceis.
og_title: Alterar o estilo da fonte em documentos Word – Guia completo de C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Alterar o estilo da fonte em documentos Word – Guia completo de C#
url: /pt/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar Estilo de Fonte em Documentos Word – Guia Completo em C#

Já precisou **alterar o estilo de fonte** em um arquivo Word, mas não sabia qual chamada de API realmente faz isso? Você não está sozinho—a maioria dos desenvolvedores encontra essa barreira ao tentar ajustar tipografia programaticamente.

A boa notícia é que, com algumas linhas de C#, você pode **definir o peso da fonte**, até mesmo aumentar para um peso negrito, e ajustar a largura de cada glifo. Neste tutorial, percorreremos um exemplo completo e executável que modifica um arquivo `.docx` do início ao fim.

## O Que Este Guia Cobre

Começaremos carregando um documento existente, depois criaremos um objeto `FontSettings` que contém um `FontVariation`. A partir daí, **definiremos o peso da fonte**, **definiremos o peso negrito** e **ajustaremos a largura da fonte** antes de aplicar as alterações e salvar o resultado. Sem arquivos de configuração externos, sem strings mágicas—apenas C# puro e a biblioteca Aspose.Words. Ao final, você será capaz de **modificar fontes em documentos Word** com confiança, seja construindo um mecanismo de relatórios ou uma ferramenta de formatação em massa.

### Pré‑requisitos

- .NET 6.0 ou superior (o código também compila em .NET Core)  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Um arquivo de exemplo `input.docx` colocado em uma pasta que você possa referenciar (chamaremos de `YOUR_DIRECTORY`)  

Se você já tem esses itens, vamos mergulhar.

---

## Etapa 1: Alterar Estilo de Fonte – Carregar o Documento Word

A primeira coisa a fazer é trazer o arquivo alvo para a memória. Pense nisso como abrir uma tela em branco onde você pintará sua nova tipografia.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Dica:** Se você estiver executando isso em um servidor sem interface gráfica, certifique‑se de que a licença do Aspose.Words esteja configurada como avaliação ou que você tenha aplicado um arquivo de licença adequado para evitar mensagens de marca d'água.

---

## Etapa 2: Definir Peso da Fonte e Definir Peso Negrito

Agora que o documento está na memória, criamos um contêiner `FontSettings`. Esse objeto é a porta de entrada para cada ajuste de nível de fonte que você pode fazer.  

A classe `FontVariation` permite especificar três atributos principais:

| Propriedade | O que faz | Faixa típica |
|-------------|-----------|--------------|
| `Weight` | Controla o quão pesado o glifo parece. Um valor de **700** é o “negrito” padrão. | 100‑900 |
| `Width`  | Estica ou condensa o glifo horizontalmente. **100** significa largura normal. | 50‑200 |
| `Slant`  | Adiciona uma inclinação tipo itálico. Números positivos inclinam para a direita. | -90‑90 |

A seguir, **definimos o peso da fonte** para 700 (negrito) e também demonstramos como você poderia aumentá‑lo ainda mais caso sua fonte suporte um estilo “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Por que isso importa:** Definir o **peso negrito** diretamente via `SetWeight` elimina a necessidade de um objeto de estilo “Bold” separado, oferecendo controle pixel‑a‑pixel sobre a espessura dos traços.

---

## Etapa 3: Ajustar Largura da Fonte

Se você precisar deixar uma fonte mais compacta para um título ou mais espaçada para um parágrafo, ficará feliz em chegar a esta etapa. A propriedade `Width` faz exatamente isso.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Armadilha comum:** Nem toda família tipográfica respeita variações de largura. Se você não notar mudança visual, verifique se a família de fontes que está usando suporta glifos condensados/expandidos.

---

## Etapa 4: Aplicar as Configurações de Fonte – Modificar Fonte no Word

Com nosso `FontSettings` totalmente configurado, o passo final é instruir o documento a usá‑lo. É aqui que **modificamos a fonte no Word** ao nível do documento, afetando cada trecho de texto que herda o estilo padrão.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Se você quiser direcionar apenas um parágrafo ou trecho específico, pode recuperar esse nó e definir seu `FontSettings` individualmente. O exemplo acima demonstra a abordagem de grande alcance, ideal para cenários de formatação em massa.

---

## Etapa 5: Salvar e Verificar as Alterações

Salvar é a última, mas certamente não a menos importante, parte do fluxo de trabalho. Após persistir o arquivo, você pode abri‑lo no Microsoft Word para ver o novo estilo em ação.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Resultado Esperado

- Todo o texto do corpo que antes usava a fonte padrão agora aparece **negrito** (peso 700).  
- Se você experimentou `SetWidth(80)`, os caracteres ficarão um pouco mais compactos; `SetWidth(120)` os espalhará.  
- Nenhum outro conteúdo (imagens, tabelas, etc.) é alterado—apenas as características tipográficas dos trechos de texto.

Abra `output.docx` no Word, selecione um parágrafo e verifique a caixa de diálogo **Fonte**. Você verá a caixa **Negrito** marcada e a **Escala** (largura) refletindo o valor escolhido.

---

## Perguntas Frequentes & Casos Limite

### Posso mudar a família da fonte ao mesmo tempo?

Com certeza. Depois de definir o `FontVariation`, você também pode atribuir um novo `FontInfo` ao `FontSettings`:

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### E se eu precisar **definir peso negrito** apenas para cabeçalhos?

Recupere o nó de estilo de cabeçalho e aplique uma instância separada de `FontSettings`:

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Isso funciona com .NET Core no Linux?

Sim—Aspose.Words é multiplataforma. Apenas certifique‑se de ter as bibliotecas de runtime apropriadas instaladas (`libgdiplus` em algumas distribuições) se planeja renderizar o documento para PDF posteriormente.

---

## Conclusão

Acabamos de **alterar o estilo de fonte** em um documento Word do início ao fim, cobrindo como **definir peso da fonte**, **definir peso negrito** e **ajustar largura da fonte** usando C#. O exemplo completo e executável demonstra cada importação necessária, criação de objetos e chamada de método, para que você possa copiar‑colar em seu próprio projeto e ver a tipografia transformar instantaneamente.

Agora que você sabe como **modificar fontes no Word**, pode explorar tópicos relacionados como **incorporar fontes personalizadas**, **aplicar gradientes de cor** ou **criar tabelas dinâmicas**. Cada um desses se baseia na mesma fundação `FontSettings` que usamos aqui, então você já está um passo à frente.

Tem um cenário que não foi abordado? Deixe um comentário, e vamos analisá‑lo juntos. Boa codificação—e que seus documentos estejam sempre exatamente como você deseja!

![change font style example](placeholder.png){alt="exemplo de mudança de estilo de fonte"}

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que expandem as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Definir Marca de Ênfase da Fonte](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Definir Configurações de Substituição de Fonte](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Definir Formatação de Fonte](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}