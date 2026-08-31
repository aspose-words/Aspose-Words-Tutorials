---
category: general
date: 2026-02-10
description: Defina o callback de aviso para monitorar alterações de fontes enquanto
  você configura a fonte padrão e define a fonte de importação padrão no Aspose.Words.
  Aprenda a solução completa passo a passo.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: pt
og_description: Defina o callback de aviso para monitorar alterações de fonte ao configurar
  a fonte padrão e definir a fonte de importação padrão. Siga o tutorial completo
  para Aspose.Words.
og_title: Definir callback de aviso em C# – Guia completo
tags:
- Aspose.Words
- C#
- Document Import
title: Definir callback de aviso em C# – Guia completo de manipulação de fontes
url: /pt/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Definir callback de aviso em C# – Guia Completo de Manipulação de Fontes

Já precisou **definir callback de aviso** ao carregar um documento Word e se perguntou como *configurar a fonte padrão* ao mesmo tempo? Você não está sozinho. Em muitos projetos reais—como geradores automáticos de relatórios ou pipelines de conversão de documentos—fontes ausentes podem quebrar o layout silenciosamente, e a única maneira de detectar esses problemas é **monitorar alterações de fontes** via um callback de aviso.

Neste tutorial vamos percorrer um exemplo prático que mostra como **definir callback de aviso**, **configurar fonte padrão** e ainda **definir fonte de importação padrão** usando Aspose.Words for .NET. Ao final você terá um trecho pronto‑para‑executar, entenderá por que cada parte importa e saberá como adaptá‑lo para casos extremos, como pastas de fontes personalizadas ou substituições silenciosas.

---

## Pré-requisitos

- .NET 6.0 ou posterior (o código também funciona no .NET Framework 4.6+)  
- Pacote NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Uma pasta que contenha a fonte de fallback que você deseja usar (ex.: `fonts/Arial.ttf`)  
- Familiaridade básica com aplicativos console C#  

Nenhuma biblioteca adicional é necessária.

---

## Etapa 1: Criar LoadOptions e **configurar fonte padrão**

A primeira coisa que você faz quando quer controlar o tratamento de fontes é criar uma instância de `LoadOptions`. Esse objeto informa ao Aspose.Words como tratar fontes ausentes durante a importação.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Por que isso importa:**  
Se o documento de origem referencia uma fonte que não está instalada no servidor, o Aspose.Words procurará na pasta que você forneceu. Esse é o núcleo de **definir fonte de importação padrão**—você está dizendo explicitamente à biblioteca onde encontrar um substituto antes mesmo de qualquer aviso ser gerado.

---

## Etapa 2: **Definir callback de aviso** para **monitorar alterações de fontes**

O Aspose.Words emite uma `WarningInfoCollection` sempre que precisa substituir uma fonte, entre outras coisas. Ao anexar um manipulador, você pode registrar ou reagir a cada substituição.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Por que isso importa:**  
Simplesmente **configurar fonte padrão** não é suficiente se você precisar auditar quais fontes foram realmente trocadas. O callback fornece um registro em tempo real, atendendo ao requisito de **monitorar alterações de fontes** e ajudando a detectar substituições inesperadas cedo em um pipeline de CI.

---

## Etapa 3: Carregar o documento com as opções preparadas

Agora que as opções de carregamento estão totalmente configuradas, você pode carregar com segurança qualquer arquivo `.docx`. O callback será disparado automaticamente se ocorrer uma substituição.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**O que você verá:**  
Se a fonte usada na origem não estiver presente, o console imprimirá algo como:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Essa saída confirma que você **definiu o callback de aviso** com sucesso e que a **fonte de importação padrão** entrou em vigor.

---

## Etapa 4: (Opcional) Ajustar finamente o comportamento de substituição de fontes

Às vezes você pode querer substituir *todas* as fontes ausentes por uma única família, independentemente da solicitação original. O Aspose.Words permite definir uma *fonte de fallback* globalmente.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Quando usar isso:**  
Se você está gerando PDFs para uma marca que permite apenas um conjunto limitado de fontes, isso garante consistência em todos os documentos, mesmo que a origem tente usar algo exótico.

---

## Etapa 5: Salvar ou processar o documento adicionalmente

Depois de carregar, você pode continuar com qualquer processamento necessário—edição, conversão para PDF, extração de texto, etc. Aqui está um exemplo rápido de como salvar o documento como PDF mantendo as fontes substituídas.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

O PDF resultante exibirá a fonte de fallback onde quer que tenha ocorrido uma substituição, proporcionando uma confirmação visual de que o **definir callback de aviso** funcionou como esperado.

---

## Armadilhas Comuns & Dicas Profissionais

| Armadilha | Por que acontece | Correção |
|-----------|------------------|----------|
| **Callback nunca dispara** | `LoadOptions.WarningCallback` não foi atribuído *antes* de carregar o documento. | Sempre anexe o callback **antes** de chamar `new Document(...)`. |
| **Pasta de fontes incorreta** | Erro de digitação no caminho ou permissões de leitura ausentes. | Verifique se a pasta existe e se o aplicativo tem acesso `Read`. Use caminhos absolutos para maior confiabilidade. |
| **Múltiplas substituições, saída ruidosa** | Documentos grandes com muitas fontes ausentes. | Filtre avisos por `WarningType.FontSubstitution` (como mostrado) ou escreva-os em um arquivo de log ao invés do console. |
| **Fonte de fallback não aplicada** | A fonte de fallback não está instalada na máquina. | Coloque o arquivo `.ttf`/`.otf` na pasta que você passou para `SetFontsFolder`. Aspose.Words o carrega diretamente, sem necessidade de instalação no SO. |

**Dica profissional:** Quando você estiver executando isso em um pipeline CI/CD, redirecione a saída do console para um artefato de build. Dessa forma você terá um registro de auditoria de cada substituição de fonte que ocorreu durante a compilação.

---

## Exemplo Completo Funcional (Pronto para Copiar‑Colar)

Abaixo está o programa completo que você pode inserir em um novo projeto Console App. Ele inclui todas as etapas, declarações `using` e comentários necessários.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Saída esperada no console** (supondo que `Times New Roman` estivesse ausente):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Execute o programa, abra `output.pdf` e você verá o documento renderizado com a fonte de fallback onde for necessário.

---

## Conclusão

Agora você possui um padrão sólido e pronto para produção de como **definir callback de aviso** em C#, **configurar fonte padrão**, **monitorar alterações de fontes** e **definir fonte de importação padrão** ao trabalhar com Aspose.Words. Ao anexar um coletor de avisos antes do carregamento, apontar `FontSettings` para uma pasta de fontes confiável e, opcionalmente, forçar um fallback global, você obtém total visibilidade e controle sobre a substituição de fontes—exatamente o que qualquer pipeline robusto de processamento de documentos precisa.

Pronto para o próximo nível? Experimente combinar esta abordagem com:

- **Carregamento dinâmico de fontes** a partir de um banco de dados (use `FontSettings.SetFontsFolder` em tempo de execução).  
- **Manipuladores de aviso personalizados** que escrevem em um log estruturado (JSON ou CSV) para análise.  
- **Processamento paralelo de documentos** onde cada thread recebe seu próprio `LoadOptions` para evitar interferências.

Sinta-se à vontade para experimentar, adaptar o código à sua arquitetura e compartilhar descobertas nos comentários. Feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}