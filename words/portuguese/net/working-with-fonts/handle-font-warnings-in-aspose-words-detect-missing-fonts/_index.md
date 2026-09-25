---
category: general
date: 2026-02-28
description: Aprenda a lidar com avisos de fontes e detectar fontes ausentes no Aspose.Words
  usando C#. Guia completo passo a passo com código completo.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: pt
og_description: Manipule avisos de fontes no Aspose.Words e detecte fontes ausentes
  com um exemplo C# pronto para executar. Siga os passos e veja o resultado.
og_title: Tratar avisos de fontes no Aspose.Words – Guia completo
tags:
- Aspose.Words
- C#
- Document Loading
title: Tratar avisos de fontes no Aspose.Words – Detectar fontes ausentes
url: /pt/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manipular Avisos de Fonte no Aspose.Words – Detectar Fontes Ausentes

Já precisou **manipular avisos de fonte** ao carregar um documento Word e se perguntou por que algum texto parece estranho? Você não está sozinho. Fontes ausentes geram avisos de substituição que podem corromper silenciosamente o layout visual, e se você não **detecta fontes ausentes** nunca saberá o que deu errado.

Neste tutorial vamos mostrar uma forma prática de **manipular avisos de fonte** usando o `IWarningCallback` do Aspose.Words. Ao final do guia você será capaz de identificar cada evento de substituição de fonte, registrá‑lo e até decidir se aborta o carregamento. Sem documentação externa, apenas um exemplo pronto para copiar‑colar.

## O que você vai aprender

- Configurar um manipulador de avisos personalizado que reage apenas a alertas de substituição de fonte.  
- Anexar o manipulador ao `LoadOptions` para que cada carregamento de documento passe por ele.  
- Verificar a saída no console e entender o que cada aviso significa.  

**Pré‑requisitos**

- .NET 6.0 ou superior (o código também funciona com .NET Framework 4.6+).  
- Aspose.Words for .NET instalado via NuGet (`Install-Package Aspose.Words`).  
- Um arquivo Word que faça referência a uma fonte que não esteja instalada na sua máquina (por exemplo, uma fonte corporativa personalizada).  

Se estiver faltando algum desses itens, obtenha-os agora — caso contrário, vamos começar.

## Como manipular avisos de fonte no Aspose.Words

Abaixo está o programa completo e executável. Ele inclui tudo, desde as declarações `using` até o método `Main`, para que você possa inseri‑lo em um aplicativo console e pressionar **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Saída esperada no console** (supondo que o documento use uma fonte que você não tem instalada):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Se o documento **não contiver fontes ausentes**, a linha de aviso nunca aparecerá — assim você **detectou fontes ausentes** apenas quando necessário.

### Por que isso funciona

Aspose.Words gera um `WarningInfo` para cada problema não crítico encontrado ao analisar um arquivo. Ao implementar `IWarningCallback` você obtém um ponto de extensão nesse pipeline. O sinalizador `WarningType.FontSubstitution` indica exatamente quando a biblioteca precisou substituir uma fonte solicitada por uma alternativa. Essa é a forma mais confiável de **manipular avisos de fonte**, pois ocorre *durante* o carregamento, antes mesmo de você tocar no modelo de objeto do documento.

## Detectar fontes ausentes sem quebrar seu aplicativo

Às vezes você pode querer tratar uma fonte ausente como um erro fatal — talvez as diretrizes de branding proíbam qualquer substituição. Você pode modificar o manipulador para lançar uma exceção em vez de apenas registrar:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Agora o bloco `try…catch` ao redor de `new Document(...)` capturará o problema, permitindo que você decida se aborta, faz fallback ou solicita ao usuário.

## Bônus: Visualizando avisos em um aplicativo UI

Se você estiver construindo um app WinForms ou WPF, substitua `Console.WriteLine` por uma chamada amigável à UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Dessa forma, os usuários finais veem o aviso imediatamente, e você ainda **manipula avisos de fonte** de forma consistente em todas as plataformas.

## Armadilhas comuns & Dicas profissionais

- **Armadilha:** Esquecer de definir `WarningCallback`. O comportamento padrão é ignorar avisos de fonte, então você nunca os verá.  
  **Dica:** Sempre crie uma instância de `LoadOptions` mesmo que precise apenas do manipulador de avisos. É barato e explícito.  

- **Armadilha:** Usar o separador de caminho errado em sistemas não Windows.  
  **Dica:** Use `Path.Combine` ou uma string literal bruta (`@"C:\Docs\MissingFont.docx"` funciona no Windows; no Linux use `"/home/user/docs/MissingFont.docx"`).  

- **Armadilha:** Supor que o aviso será disparado para fontes incorporadas.  
  **Dica:** Fontes incorporadas são consideradas presentes, portanto nenhum aviso de substituição aparece. Teste com fontes realmente *ausentes* para ver o manipulador em ação.  

- **Armadilha:** Registrar excessivamente todos os tipos de aviso.  
  **Dica:** Filtre por `WarningType.FontSubstitution` como mostrado — isso mantém o console limpo e foca no cenário de **detectar fontes ausentes**.

## Recapitulação do Exemplo Completo

Aqui está o programa inteiro novamente, desta vez sem comentários para quem prefere uma visualização limpa:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Copie, cole, execute — seu console agora **manipulará avisos de fonte** e **detectará fontes ausentes** automaticamente.

## Próximos passos

- **Log em arquivo:** Substitua `Console.WriteLine` por um logger (por exemplo, NLog) para rastreamento em produção.  
- **Processamento em lote:** Percorra uma pasta de documentos, coletando todos os eventos de substituição de fonte em um relatório CSV.  
- **Instalação automática de fontes:** Conecte‑se ao manipulador de avisos para baixar fontes ausentes de um repositório corporativo antes que o carregamento continue.  

Cada uma dessas extensões se baseia na ideia central de **manipular avisos de fonte** de forma limpa e reutilizável.

---

*Feliz codificação! Se encontrar alguma particularidade ao tentar **detectar fontes ausentes**, deixe um comentário abaixo. Ficarei feliz em ajudar a solucionar o problema.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}