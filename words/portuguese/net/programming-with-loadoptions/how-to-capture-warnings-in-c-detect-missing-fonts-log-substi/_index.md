---
category: general
date: 2026-04-04
description: Aprenda como capturar avisos, detectar fontes ausentes e registrar eventos
  de substituição usando Aspose.Words LoadOptions em C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: pt
og_description: Como capturar avisos, detectar fontes ausentes e registrar eventos
  de substituição usando Aspose.Words LoadOptions em C#.
og_title: Como Capturar Avisos em C# – Detectar Fontes Ausentes e Registrar Substituição
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Como Capturar Avisos em C# – Detectar Fontes Ausentes e Registrar Substituição
url: /pt/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Avisos em C# – Detectar Fontes Ausentes e Registrar Substituição

Já se perguntou **como capturar avisos** que aparecem ao carregar um documento Word com fontes ausentes? Você não está sozinho. Em muitos projetos reais, as fontes se perdem durante a migração, e a substituição silenciosa pode quebrar o layout. A boa notícia? Aspose.Words oferece uma maneira limpa de ouvir esses avisos, detectar fontes ausentes e até registrar cada substituição para que você possa corrigir a origem mais tarde.

Neste tutorial, percorreremos uma solução completa, pronta‑para‑executar, que mostra **como capturar avisos**, demonstra **detectar fontes ausentes** e explica **como registrar eventos de substituição**. Ao final, você terá um manipulador de avisos reutilizável, um objeto `LoadOptions` totalmente configurado e um exemplo de saída de console que pode verificar.

> **Pré‑requisito:** Você precisa do Aspose.Words para .NET (v24.x ou superior) instalado via NuGet e um ambiente básico de desenvolvimento C# (Visual Studio 2022 ou VS Code funciona bem).

---

## Como Capturar Avisos ao Carregar Documentos

O núcleo da solução é uma classe que implementa `IWarningCallback`. Aspose.Words chama esse callback automaticamente para cada aviso gerado durante o carregamento do documento, incluindo avisos de substituição de fonte.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Por que esta etapa?**  
> Ao filtrar por `WarningType.FontSubstitution` evitamos a desordem de avisos não relacionados (como recursos obsoletos). Isso faz com que o log se concentre no problema exato que você se importa — fontes ausentes.

---

## Detectar Fontes Ausentes com Aspose.Words

Quando um documento referencia uma fonte que não está instalada na máquina, Aspose.Words substitui pela mais próxima e gera um aviso. Nosso manipulador acima capturará cada ocorrência, detectando efetivamente **fontes ausentes**.

Para ver isso em ação, precisamos configurar `LoadOptions` e anexar o manipulador:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Dica:** Se preferir coletar avisos para processamento posterior (por exemplo, gravar em um arquivo), substitua `Console.WriteLine` por código que adicione a mensagem a um `List<string>`.

---

## Como Registrar Eventos de Substituição

O registro é tão simples quanto direcionar a saída do aviso para um armazenamento persistente. Abaixo está um exemplo rápido que grava cada aviso de substituição em um arquivo de texto chamado `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Por que registrar em um arquivo?**  
> Logs persistentes permitem auditar problemas de fontes em várias execuções, automatizar alertas ou alimentar os dados em uma verificação de pipeline de build.

---

## Exemplo Completo Funcional

Juntando tudo, aqui está um aplicativo de console autônomo que você pode copiar, colar e executar. Ele demonstra **como capturar avisos**, **detectar fontes ausentes** e **como registrar substituições** de uma só vez.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Saída Esperada no Console

Se `input.docx` referencia uma fonte que não está instalada, você verá algo como:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Se você mudar para `FileLoggingWarningHandler`, as mesmas linhas aparecerão dentro de `font-warnings.log` com timestamps.

![how to capture warnings console output](image-placeholder.png)

---

## Perguntas Frequentes & Casos de Borda

### E se eu precisar capturar *todos* os avisos, não apenas substituição de fonte?

Basta remover a verificação `if (info.Type == WarningType.FontSubstitution)`. O callback receberá todos os tipos de aviso (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, etc.). Você pode então ramificar em `info.Type` para tratar cada caso de forma diferente.

### Isso funciona com PDFs ou apenas documentos Word?

`LoadOptions` e `IWarningCallback` fazem parte do Aspose.Words, portanto se aplicam a formatos compatíveis com Word (`.docx`, `.doc`, `.rtf`, `.html`). Para PDFs, você usaria os próprios mecanismos de aviso do Aspose.PDF.

### Como posso suprimir avisos ao invés de registrá‑los?

Defina `LoadOptions.WarningCallback = null` ou implemente o callback mas deixe o corpo do método vazio. A biblioteca ainda realizará a substituição silenciosamente.

### E quanto à segurança de thread?

A instância do callback é invocada na mesma thread que carrega o documento, portanto você não precisa de sincronização extra, a menos que compartilhe o manipulador entre carregamentos paralelos. Nesse caso, proteja recursos compartilhados (por exemplo, o arquivo de log) com um lock ou use coleções concorrentes.

---

## Conclusão

Cobrimos **como capturar avisos** do Aspose.Words, mostramos como **detectar fontes ausentes** e explicamos **como registrar substituições** para análise posterior. Ao conectar uma simples implementação de `IWarningCallback` ao `LoadOptions`, você obtém total visibilidade sobre problemas relacionados a fontes sem poluir sua base de código.

Próximos passos? Tente estender o logger para enviar e‑mails, integrar com Azure Monitor ou instalar automaticamente fontes ausentes em um servidor de build. Você também pode explorar outros tipos de aviso — `WarningType.DegradedDocument` pode alertá‑lo sobre recursos que não sobreviveram ao processo de conversão.

Tem mais perguntas sobre o gerenciamento de fontes ou Aspose.Words em geral? Deixe um comentário ou abra uma nova issue nos fóruns da Aspose. Boa codificação, e que seus documentos sempre renderizem com a tipografia correta!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}