---
category: general
date: 2026-06-02
description: Aprenda a usar fontes de peso variável em C# e definir o peso da fonte
  programaticamente enquanto altera o código de estiramento da fonte para tipografia
  dinâmica.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: pt
og_description: Use fonte de peso variável em C# para definir o peso da fonte programaticamente
  e alterar o código de estiramento da fonte, permitindo tipografia dinâmica em seus
  documentos.
og_title: Usar fonte de peso variável em C# – Guia completo
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Utilize fonte de peso variável em C# – Guia completo de programação
url: /pt/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usar Fonte de Peso Variável em C# – Guia Completo de Programação

Já precisou **usar fonte de peso variável** em um projeto .NET, mas não sabia como fazer o peso e o alongamento responderem à entrada do usuário? Você não está sozinho. Em muitos cenários de UI ou relatórios você quer que o texto se adapte — talvez um título leve que fique em negrito ao passar o mouse, ou um parágrafo que expanda sua largura para ênfase. A boa notícia é que, com Aspose.Words, você pode **definir o peso da fonte programaticamente** e até **alterar o código de alongamento da fonte** em tempo real.

Neste tutorial vamos percorrer um exemplo prático que mostra exatamente como carregar uma fonte de peso variável, aplicar um peso personalizado e ajustar a configuração de alongamento — tudo com código C# claro que você pode copiar‑colar. Ao final, você terá um aplicativo console executável que gera um PDF demonstrando o efeito.

---

## O que você precisará

- **Aspose.Words for .NET** (v23.12 ou posterior). A biblioteca inclui suporte total a fontes de peso variável.
- Uma pasta contendo ao menos um arquivo de fonte de peso variável, por exemplo *RobotoFlex‑Variable.ttf*. Você pode baixá‑lo no Google Fonts.
- .NET 6 SDK (ou qualquer versão recente do .NET) e um IDE de sua escolha.
- Conhecimento básico de C# — nada sofisticado, apenas algumas linhas de código.

É só isso. Nenhum pacote NuGet extra além do Aspose.Words, e nenhum arquivo de configuração obscuro.

---

![Exemplo de uso de fonte de peso variável](https://example.com/variable-weight-sample.png "Demonstração de uso de fonte de peso variável")

*Texto alternativo: captura de tela mostrando o uso de fonte de peso variável em um documento PDF gerado.*

---

## Etapa 1: Configurar FontSettings e apontar para sua pasta de fontes  

Primeiro de tudo — o Aspose.Words precisa saber onde suas fontes de peso variável estão armazenadas. Você faz isso criando um objeto `FontSettings` e anexando um `FolderFontSource`. O parâmetro `true` indica ao mecanismo que ele deve procurar também em subpastas, o que é útil se você mantiver várias famílias de fontes juntas.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Por que isso importa:** Sem registrar a pasta, o Aspose.Words recorre às fontes do sistema e ignora os dados de peso variável incorporados ao seu arquivo de fonte personalizado. Esta etapa é a base para tudo que segue.

---

## Etapa 2: Anexar FontSettings ao Documento  

Agora criamos um novo `Document` (ou carregamos um existente) e instruímos que ele use o `FontSettings` que acabamos de preparar. Essa vinculação é o que disponibiliza os dados de peso variável para cada `Run` que adicionarmos depois.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Se você já tem um modelo — por exemplo, um arquivo Word com marcadores — pode substituir `new Document()` por `new Document("Template.docx")`. O mesmo `FontSettings` será aplicado.

---

## Etapa 3: Adicionar um Run de Texto que Usará a Fonte de Peso Variável  

Um **Run** é a menor unidade de formatação de texto no Aspose.Words. Criaremos um, inseriremos em um novo parágrafo e, mais adiante, alteraremos seus atributos de fonte.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

Neste ponto o texto será renderizado usando a fonte padrão (geralmente Times New Roman). A mágica acontece quando atribuirmos a família de fonte de peso variável.

---

## Etapa 4: Escolher a Família de Fonte de Peso Variável  

Aqui é onde realmente **usamos fonte de peso variável**. Defina `Font.Name` para o nome exato da família definido dentro do arquivo de fonte variável. Para o Roboto Flex, o nome é `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Se não tiver certeza sobre o nome da família, abra o arquivo `.ttf` em um visualizador de fontes ou use o método `fontSettings.GetFonts()` para enumerar as famílias disponíveis.

---

## Etapa 5: Definir Peso e Alongamento da Fonte Programaticamente  

Agora o núcleo do tutorial: **definimos o peso da fonte programaticamente** e **alteramos o código de alongamento da fonte**. Ambas as propriedades aceitam valores inteiros que mapeiam para a especificação OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Escolha qualquer valor que a fonte variável suporte.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). O padrão é 100 (Normal).

> **Dica profissional:** Nem toda fonte variável expõe toda a faixa. Se você definir um valor que não seja suportado, o mecanismo o limitará ao peso ou alongamento mais próximo disponível.

---

## Etapa 6: Salvar o Documento e Verificar o Resultado  

Por fim, grave o documento em PDF (ou DOCX) e abra-o para ver o efeito. PDF é um formato excelente para verificação visual porque a renderização é consistente entre plataformas.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Ao abrir *VariableWeightDemo.pdf*, você deverá ver a frase “Variable‑weight text demo” renderizada em uma versão leve e ligeiramente expandida do Roboto Flex. Altere `FontWeight` para `700` e `FontStretch` para `80` e execute novamente — observe o texto ficar em negrito e mais condensado.

---

## Perguntas Frequentes & Casos de Borda  

### E se a fonte não aparecer de jeito nenhum?  

- **FontSettings ausente**: Verifique se `doc.FontSettings = fontSettings;` é executado **antes** de qualquer texto ser adicionado.
- **Nome de família incorreto**: Use `fontSettings.GetFonts()` para listar todas as famílias descobertas; copie a string exata.
- **Peso/alongamento não suportado**: Algumas fontes variáveis suportam apenas um subconjunto da faixa 100‑900. Use `run.Font.FontWeight = 400;` como fallback seguro.

### Posso mudar o peso depois que o documento for salvo?  

Sim. O objeto `Run` é mutável, então você pode ajustar `FontWeight` ou `FontStretch` a qualquer momento antes do `Save` final. Se precisar alternar pesos dinamicamente (por exemplo, com base na interação do usuário), considere gerar runs separados para cada estado.

### Isso funciona com saída DOCX?  

Absolutamente. Os metadados de peso variável são armazenados no OpenXML subjacente, e versões modernas do Word conseguem interpretá‑los. Contudo, versões mais antigas do Word podem ignorar a configuração de alongamento.

---

## Exemplo Completo Funcional  

Abaixo está um programa console completo que você pode compilar e executar imediatamente. Ele inclui todas as diretivas `using` necessárias, tratamento de erros e comentários.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Saída esperada:** O console imprime o caminho de salvamento, e o PDF gerado mostra o texto em um estilo leve e expandido — exatamente como configuramos.

---

## Recapitulação  

Cobremos como **usar fonte de peso variável** em C# com Aspose.Words, demonstramos como **definir o peso da fonte programaticamente** e mostramos o **código de alteração de alongamento da fonte** necessário para expandir ou condensar os glifos. Os passos são simples: configure `FontSettings`, anexe‑os a um `Document`, crie um `Run`, escolha a família de peso variável e, por fim, ajuste `FontWeight` e `FontStretch`.

---

## O que vem a seguir?  

- **Integração dinâmica de UI**: Conecte a mesma lógica a um aplicativo WinForms ou WPF para permitir que usuários escolham peso/alongamento via sliders.
- **Múltiplos runs**: Combine vários runs com pesos diferentes no mesmo parágrafo para hierarquias tipográficas ricas.
- **Eixos avançados**: Algumas fontes variáveis expõem eixos adicionais (por exemplo, slant, optical size). Use `run.Font.FontStyle` ou explore `FontVariationSettings` para controle ainda mais fino.
- **Dicas de desempenho**: Cache a instância `FontSettings` ao processar muitos documentos para evitar varreduras repetidas de pastas.

Sinta‑se à vontade para experimentar — troque *Roboto Flex* por *Inter Variable* ou qualquer outra OpenType variable font, e veja seus documentos ganharem um novo nível de flexibilidade visual. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas em seus próprios projetos.

- [Use Font From Target Machine](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Use Font From Target Machine](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}