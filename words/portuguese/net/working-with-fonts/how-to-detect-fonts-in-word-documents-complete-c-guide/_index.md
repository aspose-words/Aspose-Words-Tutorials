---
category: general
date: 2026-02-24
description: Como detectar fontes em um documento Word usando Aspose.Words. Aprenda
  como definir o callback e carregar o documento Word com um exemplo completo de código.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: pt
og_description: Como detectar fontes em um documento Word usando um callback de aviso.
  Este guia mostra como definir o callback e carregar o documento Word com Aspose.Words.
og_title: Como Detectar Fontes em Documentos Word – Tutorial C# Passo a Passo
tags:
- C#
- Aspose.Words
- Document Processing
title: Como Detectar Fontes em Documentos Word – Guia Completo em C#
url: /pt/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Detectar Fontes em Documentos Word – Guia Completo em C#

Já se perguntou **como detectar fontes** que estão ausentes ao carregar um arquivo Word? Talvez você tenha encontrado um documento que parece correto no editor, mas o PDF que você gera troca algumas tipografias nos bastidores. Esse é um sintoma clássico de substituição de fontes, e detectá‑lo cedo pode evitar surpresas desagradáveis de layout.

Neste tutorial vamos percorrer uma solução prática: usar **Aspose.Words** para carregar um `.docx`, anexar um callback de aviso e **como definir o callback** que relata cada substituição de fonte. Ao final, você não só saberá **como detectar fontes** programaticamente, como também entenderá **como definir o callback** corretamente e **carregar documento Word** com segurança — tudo em um único exemplo C# executável.

> **O que você receberá**
> * Um exemplo de código completo, pronto para copiar e colar  
> * Explicação passo a passo de cada linha  
> * Dicas para lidar com casos extremos, como várias fontes ausentes ou pastas de fontes personalizadas  
> * Saída esperada no console para que você possa verificar se tudo funciona

---

## Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona com .NET Core)  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Um arquivo Word que referencie intencionalmente uma fonte que você não tem instalada (por exemplo, `MissingFont.docx`)  
- Visual Studio, Rider ou qualquer editor de sua preferência

Nenhuma outra biblioteca é necessária; todo o restante faz parte do runtime padrão do .NET.

---

## Como Detectar Fontes em um Documento Word

### Etapa 1: Criar Load Options e Anexar um Callback de Aviso

A primeira coisa que fazemos é dizer ao Aspose.Words que queremos ser notificados sobre quaisquer problemas que surgirem ao carregar o arquivo. É aqui que **como definir o callback** entra em ação.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Por que isso importa:**  
`LoadOptions` é a porta de entrada para personalizar o processo de carregamento. Ao atribuir uma instância de `FontWarningCollector` a `WarningCallback`, o Aspose.Words invocará nosso método `Warning` toda vez que substituir uma fonte ausente por uma alternativa. Esse é o núcleo de **como detectar fontes** que não estão presentes na máquina.

---

### Etapa 2: Preparar a Instância de LoadOptions

Agora instanciamos `LoadOptions` e conectamos nosso callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Dica profissional:** Se precisar controlar *onde* o Aspose procura fontes de substituição, você também pode definir `loadOptions.FontSettings` aqui. Isso é útil quando há uma pasta de fontes privada no servidor.

---

### Etapa 3: Carregar o Documento Word

Com as opções prontas, finalmente **carregamos o documento Word**. Este é o momento em que o Aspose analisa o DOCX e, se houver fontes ausentes, nosso callback é disparado.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**O que acontece nos bastidores?**  
Aspose.Words lê as partes XML do DOCX, resolve cada referência `<w:font>` e verifica a coleção de fontes do sistema. Sempre que uma referência não pode ser satisfeita, ele substitui pela primeira fonte fallback compatível e gera um aviso `FontSubstitution`.

---

### Etapa 4: Verificar a Saída

Execute o programa e observe o console. Para cada fonte ausente você verá uma linha como:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Se o documento não contiver fontes ausentes, o console permanecerá silencioso — significando que **como detectar fontes** não encontrou nenhum caso.

---

### Etapa 5: Exemplo Completo (Aplicação Console)

Abaixo está um `Program.cs` autônomo que você pode colocar em um novo projeto console. Ele inclui todas as partes que discutimos, além de um pequeno helper para manter a janela do console aberta durante a depuração.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Saída esperada no console** (exemplo):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Se você substituir `MissingFont.docx` por um arquivo que use apenas fontes instaladas, verá apenas a linha “Press any key…” — confirmando que a lógica de detecção funciona como esperado.

---

## Perguntas Frequentes & Casos de Borda

### E se eu precisar capturar *todos* os avisos, não apenas substituição de fontes?

Basta remover a verificação `if (info.Type == WarningType.FontSubstitution)`. O objeto `WarningInfo` contém um enum `Type` que você pode usar em um `switch` para outros cenários (por exemplo, `DocumentStructure`, `ImageLoading`).

### Posso registrar avisos em um arquivo ao invés do console?

Com certeza. Substitua `Console.WriteLine` por qualquer chamada a um framework de logging (`Serilog`, `NLog`, etc.). O callback roda na mesma thread que carrega o documento, então certifique‑se de que seu logger seja thread‑safe.

### Como isso se comporta em uma aplicação web?

No ASP.NET Core você normalmente injeta uma implementação singleton de `IWarningCallback` e a passa via `LoadOptions`. Lembre‑se de evitar escrever diretamente no stream de resposta — registre em um banco de dados ou em uma coleção em memória que você pode expor depois por meio de um endpoint de API.

### E quanto a fontes personalizadas armazenadas em uma pasta fora do sistema?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Agora o Aspose.Words buscará em `C:\MyCustomFonts` antes de recorrer às fontes do SO, reduzindo o número de avisos de substituição que você vê.

---

## Resumo Visual

![Detect fonts warning callback in Aspose.Words](/images/font-warning-callback.png "How to detect fonts using a warning callback")

*A captura de tela mostra a saída do console quando uma fonte ausente é substituída. O texto alternativo contém a palavra‑chave principal para SEO.*

---

## Conclusão

Agora você possui um padrão sólido e pronto para produção de **como detectar fontes** em qualquer arquivo Word carregado com Aspose.Words. Ao **como definir o callback** você obtém insight em tempo real sobre tipografias ausentes ou substituídas, e aprendeu a maneira correta de **carregar documento Word** mantendo seu código limpo e sustentável.

Próximos passos? Experimente estender o callback para coletar avisos em uma lista e exibi‑los em uma UI ou relatório automatizado. Você também pode explorar `FontSettings.SubstitutionSettings` para controlar *quais* fontes são escolhidas como fallback.

Sinta‑se à vontade para experimentar — troque o documento, adicione mais fontes ausentes ou integre a lógica a um pipeline maior de processamento de documentos. Se encontrar algum obstáculo, deixe um comentário abaixo ou me chame no GitHub.

Bom código, e que seus documentos sempre renderizem com as fontes esperadas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}