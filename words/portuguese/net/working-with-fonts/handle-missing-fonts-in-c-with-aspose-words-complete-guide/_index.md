---
category: general
date: 2026-02-26
description: Manipule fontes ausentes em C# usando Aspose.Words. Aprenda a capturar
  avisos de substituição de fontes, implementar IWarningCallback e manter seus documentos
  com a aparência correta.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: pt
og_description: Lide rapidamente com fontes ausentes em C#. Este guia mostra como
  capturar avisos de substituição de fontes com Aspose.Words, implementar IWarningCallback
  e verificar os resultados.
og_title: Lidar com fontes ausentes em C# – Tutorial passo a passo do Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Tratar fontes ausentes em C# com Aspose.Words – Guia completo
url: /pt/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lidar com Fontes Ausentes em C# com Aspose.Words – Guia Completo

Já precisou **lidar com fontes ausentes** ao carregar um documento Word em C# e se perguntou por que a saída ficou estranha? Você não está sozinho. Quando um arquivo de origem referencia uma fonte que não está instalada na máquina, o Aspose.Words substitui silenciosamente outra, o que pode quebrar seu layout ou identidade visual.  

A boa notícia? Ao configurar um **callback de aviso**, você pode capturar cada evento de substituição de fonte, registrá‑lo e decidir se fornece um substituto. Neste tutorial vamos percorrer todo o processo — desde a configuração do projeto até a verificação da saída no console — para que você nunca seja surpreendido por uma fonte invisível novamente.

> **O que você receberá**: Um aplicativo console C# pronto‑para‑executar que relata cada fonte ausente, explica por que o aviso ocorre e mostra como estender o manipulador para lógica personalizada.

---

## Pré‑requisitos

- .NET 6.0 ou superior (o código funciona tanto em .NET Core quanto em .NET Framework)
- Visual Studio 2022 (ou qualquer IDE de C# de sua preferência)
- Uma **licença** para Aspose.Words for .NET (a versão de avaliação gratuita serve para testes)
- Um documento Word que referencia uma fonte que você não tem instalada (por exemplo, *Comic Sans MS* em um ambiente Linux)

Se você tem tudo isso, vamos começar.

---

## Etapa 1: Criar um Novo Projeto Console e Adicionar Aspose.Words

Para manter as coisas organizadas, inicie com um projeto console novo.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Dica profissional**: Use a flag `--framework net6.0` se quiser direcionar um runtime específico.

Isso baixa o pacote NuGet mais recente do Aspose.Words, que contém os tipos `LoadOptions` e `IWarningCallback` que usaremos.

---

## Etapa 2: Implementar um Manipulador de Avisos (IWarningCallback)

O Aspose.Words gera um objeto `WarningInfo` para cada problema não crítico encontrado ao carregar um documento. Ao implementar `IWarningCallback`, você decide o que fazer com esses avisos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Por que isso importa**: Sem um manipulador, os avisos de substituição de fonte são ignorados silenciosamente. Ao imprimi‑los, você obtém visibilidade imediata de quais fontes estão faltando e qual fonte o Aspose.Words utilizou em seu lugar.

---

## Etapa 3: Configurar LoadOptions com o Callback de Aviso

Agora vinculamos o manipulador ao processo de carregamento do documento. `LoadOptions` permite conectar o callback antes que o arquivo seja analisado.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Observação**: Substitua `YOUR_DIRECTORY` pelo caminho real da pasta que contém seu arquivo de teste `.docx`. A instância de `LoadOptions` deve ser passada ao construtor `Document`; caso contrário, o comportamento padrão silencioso será usado.

---

## Etapa 4: Executar a Aplicação e Verificar a Saída

Compile e execute:

```bash
dotnet run
```

Se o documento referencia uma fonte que não está na sua máquina (por exemplo, *Papyrus*), você verá algo como:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Essa única linha informa exatamente qual fonte está ausente e qual substituta o Aspose.Words escolheu. Agora você pode decidir incorporar a fonte faltante, alterar o documento de origem ou aceitar a substituição.

---

## Etapa 5: Avançado – Coletar Avisos para Uso Posterior

Às vezes você quer armazenar os avisos em vez de imprimi‑los imediatamente. Abaixo está um ajuste rápido no manipulador que agrega as mensagens em uma lista.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

E atualize o `Main` de acordo:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Agora você tem uma lista reutilizável que pode ser gravada em um arquivo de log, enviada a um serviço de monitoramento ou exibida em uma UI.

---

## Etapa 6: Armadilhas Comuns & Como Evitá‑las

| Problema | Por que Acontece | Solução |
|----------|------------------|---------|
| **Nenhum aviso aparece** | O callback não foi anexado, ou o documento foi carregado sem `LoadOptions`. | Garanta que `LoadOptions.WarningCallback` esteja definido **antes** de chamar o construtor `Document`. |
| **Nome da fonte errado na mensagem** | Algumas fontes estão incorporadas no documento; o Aspose.Words relata o nome *original*, não o incorporado. | Verifique as referências de fonte do arquivo fonte; incorporar fontes elimina o aviso completamente. |
| **Impacto de desempenho** | Coletar avisos para milhares de documentos pode gerar sobrecarga. | Use um simples `Console.WriteLine` para depuração rápida; troque para um coletor somente quando precisar dos dados. |

---

## Resumo Visual

![Ilustração de tratamento de fontes ausentes mostrando fluxo de callback de aviso](/images/handle-missing-fonts.png "Diagrama de tratamento de fontes ausentes com Aspose.Words")

*O diagrama (texto alternativo inclui a palavra‑chave principal) visualiza como o callback de aviso intercepta eventos de substituição de fonte durante o carregamento do documento.*

---

## Conclusão

Agora você sabe **como lidar com fontes ausentes** em C# usando Aspose.Words. Ao conectar um `IWarningCallback` em `LoadOptions`, obtém total visibilidade de cada evento de substituição de fonte, pode registrá‑lo ou agir sobre ele e, em última análise, garante que seus documentos gerados mantenham a aparência e o estilo pretendidos.

> **Resumo rápido**:  
> 1. Adicione Aspose.Words a um aplicativo console.  
> 2. Implemente `FontWarningHandler` (ou um coletor).  
> 3. Passe‑o via `LoadOptions` ao carregar o documento.  
> 4. Verifique a saída no console ou os avisos armazenados.  

A partir daqui, você pode explorar **incorporar fontes ausentes** (`FontSettings.SubstitutionSettings`) ou **baixá‑las automaticamente de um servidor corporativo de fontes** — ambas extensões naturais do padrão que acabamos de construir.

Tem mais perguntas sobre **aviso de fonte do Aspose.Words**, **C# LoadOptions** ou **carregamento de documento com fontes ausentes**? Deixe um comentário, e feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}