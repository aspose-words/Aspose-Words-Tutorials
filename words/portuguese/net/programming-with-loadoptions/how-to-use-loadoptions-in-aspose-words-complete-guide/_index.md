---
category: general
date: 2026-01-10
description: Aprenda a usar LoadOptions para lidar com fontes ausentes no Aspose.Words.
  Código passo a passo, dicas e melhores práticas para um carregamento de documentos
  robusto.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: pt
og_description: Como usar LoadOptions para lidar com fontes ausentes no Aspose.Words.
  Obtenha um exemplo completo e executável com explicações e dicas práticas.
og_title: Como usar LoadOptions no Aspose.Words – Guia completo
tags:
- Aspose.Words
- C#
- .NET
title: Como usar LoadOptions no Aspose.Words – Guia completo
url: /pt/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como usar LoadOptions no Aspose.Words – Guia Completo

Já se perguntou **como usar LoadOptions** ao carregar um documento Word que pode estar faltando algumas fontes? Você não é o único a ficar coçando a cabeça com isso. Em muitos projetos do mundo real, os documentos circulam entre máquinas, e o sistema de destino frequentemente não possui as tipografias exatas usadas pelo autor. O resultado? Substituições de fonte inesperadas que podem quebrar o layout, ocultar caracteres importantes ou simplesmente parecer fora da identidade visual.

Felizmente, o Aspose.Words nos oferece uma maneira simples de *lidar com fontes ausentes* expondo um objeto `LoadOptions` com um callback de aviso. Neste tutorial você aprenderá exatamente **como usar LoadOptions** para capturar esses avisos de substituição de fonte, registrá‑los e manter seu pipeline de processamento robusto.

Vamos cobrir:

* Configurar a classe de callback de aviso  
* Configurar `LoadOptions` com esse callback  
* Carregar um documento enquanto rastreia fontes ausentes  
* Dicas para solução de problemas e extensão da solução  

Nenhuma documentação externa necessária — tudo o que você precisa está aqui.

---

## O que você precisará

Antes de começarmos, certifique‑se de que você tem:

* **Aspose.Words for .NET** (versão mais recente em 2026) instalado via NuGet  
* Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou VS Code)  
* Um DOCX de exemplo que referencia uma fonte que você não tem instalada (vamos chamá‑lo de `input.docx`)  

É só isso — nenhuma biblioteca adicional necessária.

---

## Etapa 1 – Definir um Callback de Aviso para Capturar Substituição de Fonte

A primeira peça do quebra‑cabeça é uma classe que implementa `IWarningCallback`. O Aspose.Words invocará seu método `Warning` sempre que encontrar algo relevante — como uma fonte ausente.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Por que isso importa:**  
Ao filtrar por `WarningType.FontSubstitution` evitamos a desordem de avisos não relacionados (por exemplo, recursos obsoletos). O callback lhe dá controle total — você pode registrar em um arquivo, lançar uma exceção ou até tentar incorporar programaticamente uma fonte de fallback.

---

## Etapa 2 – Configurar LoadOptions com o Callback

Agora que temos um manipulador, precisamos dizer ao Aspose.Words para usá‑lo. É aqui que **como usar LoadOptions** na prática.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Dica:** `LoadOptions` oferece muitas outras opções (por exemplo, `Password`, `LoadFormat`, `Encoding`). Você pode encadeá‑las, mas para lidar com fontes ausentes o `WarningCallback` é a estrela do show.

---

## Etapa 3 – Carregar o Documento Usando as Opções Configuradas

Com o `LoadOptions` pronto, carregar o documento é simples. O Aspose.Words invocará automaticamente o callback para qualquer fonte que não conseguir encontrar.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Saída esperada:**  

Se `input.docx` usar uma fonte chamada *“GothicBold”* que não está instalada, você verá algo como:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

A linha de aviso aparece **exatamente quando a fonte ausente é encontrada**, fornecendo feedback instantâneo.

---

## Etapa 4 – (Opcional) Continuar Processando o Documento

Normalmente você desejará fazer mais do que apenas carregar o arquivo. Abaixo estão algumas ações comuns pós‑carregamento que funcionam perfeitamente com nossa configuração de aviso.

### 4.1 Salvar o Documento como PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Substituir Fontes Ausentes por um Fallback Conhecido

Se você preferir um fallback específico (por exemplo, *“Calibri”*), pode ajustar o `FontSettings` antes de salvar:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Registrar Todos os Avisos em um Arquivo

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Esses trechos ilustram **como usar LoadOptions** além do caso básico, oferecendo flexibilidade para soluções de nível de produção.

---

## Armadilhas Comuns & Como **Lidar com Fontes Ausentes** de Forma Elegante

| Armadilha | Por que acontece | Como corrigir / mitigar |
|-----------|------------------|--------------------------|
| **Nenhum callback anexado** | Você esqueceu de definir `WarningCallback`. | Sempre crie uma instância de `LoadOptions` e atribua seu handler antes de carregar. |
| **Callback apenas imprime, nunca armazena** | Em um serviço web, a saída do console desaparece. | Substitua `Console.WriteLine` por um logger (Serilog, NLog) ou escreva em um armazenamento persistente. |
| **Múltiplas fontes ausentes, apenas a primeira é relatada** | Seu callback lança uma exceção no primeiro aviso. | Mantenha o callback leve; evite lançar exceções a menos que realmente queira abortar. |
| **Fonte substituída parece errada** | A substituição padrão pode escolher uma fonte visualmente diferente. | Use `FontSettings.SubstitutionSettings.FontSubstitutionRules` para priorizar seu fallback preferido. |
| **Impacto de desempenho em documentos enormes** | O callback de aviso é invocado milhares de vezes. | Agrupe avisos: colete-os em uma lista e processe após o carregamento, ou filtre apenas nomes de fontes únicos. |

---

## Exemplo Completo – Todas as Partes Juntas

Abaixo está o programa completo, pronto‑para‑executar, que demonstra todo o fluxo. Copie‑e‑cole em um projeto de console, adicione o pacote NuGet Aspose.Words e ele funcionará imediatamente.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Executar este programa** irá:

1. Imprimir quaisquer avisos de substituição de fonte no console.  
2. Salvar o layout original como `output.pdf`.  
3. Salvar um segundo PDF (`output-with-fallback.pdf`) que força o fallback para *Calibri* ou *Arial*.

---

## Perguntas Frequentes (FAQs)

**Q: Isso funciona para arquivos DOC, RTF ou HTML?**  
A: Sim. `LoadOptions` é independente de formato; desde que você forneça o caminho correto do arquivo, o callback de aviso será acionado para fontes ausentes em todos os formatos suportados.

**Q: Posso suprimir os avisos completamente?**  
A: Você pode atribuir um callback vazio (`new IWarningCallback { Warning = _ => {} }`) ou definir `LoadOptions.WarningCallback = null`. Contudo, perder a visibilidade pode fazer com que você perca problemas críticos de fontes.

**Q: E se eu precisar substituir fontes ausentes por fontes incorporadas?**  
A: Use `FontSettings` para incorporar um arquivo de fonte substituta (`AddFontSource`). Combine isso com as regras de substituição para uma experiência fluida.

**Q: O callback é thread‑safe?**  
A: O callback pode ser invocado por múltiplas threads ao carregar documentos grandes em paralelo. Garanta que quaisquer recursos compartilhados (por exemplo, arquivos de log) estejam sincronizados.

---

## Conclusão

Nós percorremos **como usar LoadOptions** no Aspose.Words para **lidar com fontes ausentes** de forma elegante. Definindo um `IWarningCallback` personalizado, vinculando‑o a uma instância de `LoadOptions` e carregando seu documento com essa configuração, você obtém insight em tempo real sobre quaisquer eventos de substituição de fonte. A partir daí, pode registrar, substituir ou incorporar fontes de fallback para que sua saída tenha exatamente a aparência desejada.

Lembre‑se, os passos principais são:

1. Implementar um callback de aviso que foque em `WarningType.FontSubstitution`.  
2. Conectar o callback a um objeto `LoadOptions`.  
3. Carregar seu documento com essas opções.  
4. (Opcional) Aplicar regras adicionais de substituição de fonte ou registro conforme necessário.

Sinta‑se à vontade para experimentar — troque o logger de console por um logger estruturado, adicione alertas por e‑mail para fontes ausentes críticas ou integre este padrão em um pipeline maior de processamento de documentos. A abordagem escala bem, seja ao lidar com um único arquivo ou processar milhares em um trabalho em lote.

Boa codificação, e que seus documentos sempre sejam renderizados com as tipografias corretas!

![exemplo de como usar loadoptions]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}