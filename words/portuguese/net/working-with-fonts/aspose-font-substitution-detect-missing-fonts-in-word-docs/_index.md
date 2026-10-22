---
category: general
date: 2026-05-04
description: Aprenda a usar a substituição de fontes da Aspose para detectar fontes
  ausentes ao carregar um documento Word e recuperar os detalhes das fontes faltantes
  — guia passo a passo.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: pt
og_description: Domine a substituição de fontes do Aspose para detectar fontes ausentes
  ao carregar um documento Word e recuperar informações sobre fontes faltantes com
  código C# completo.
og_title: Substituição de Fonte Aspose – Detectar Fontes Ausentes em Documentos Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Substituição de Fonte Aspose: Detectar Fontes Ausentes em Documentos Word'
url: /pt/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Detectar Fontes Ausentes em Documentos Word

Já se perguntou por que um documento Word parece errado em outra máquina? Frequentemente o culpado é uma fonte ausente, e **Aspose font substitution** é a ferramenta que permite identificar essas lacunas antes que se tornem um desastre visual. Neste tutorial, vamos percorrer como **detect missing fonts** no momento em que você **load a Word document**, e então **retrieve missing font** detalhes para que você possa corrigir ou substituir.

Cobriremos tudo, desde a configuração do callback de aviso até a obtenção de uma lista limpa de fontes ausentes. Ao final, você terá um trecho de código C# pronto‑para‑executar que informa exatamente quais fontes não foram encontradas, e entenderá por que isso é importante para a fidelidade do documento.

---

## Pré-requisitos – O que Você Precisa Antes de Começar

- **Aspose.Words for .NET** (v23.12 ou posterior recomendado).  
- Um ambiente de desenvolvimento .NET (Visual Studio, Rider ou a CLI `dotnet`).  
- Um DOCX de exemplo que intencionalmente usa uma fonte que você não tem instalada — chame-o de `DocumentWithMissingFont.docx`.  
- Conhecimento básico de C# — nada sofisticado, apenas a capacidade de executar um aplicativo de console.

Se algum desses lhe for desconhecido, pause e instale o pacote NuGet:

```bash
dotnet add package Aspose.Words
```

É isso. Sem fontes extras, sem serviços externos.

---

## Etapa 1: Carregar o Documento Word (e Acionar Verificações de Fonte)

A primeira coisa que você faz é **load a Word document**. Aspose.Words analisa o arquivo e, se não conseguir localizar uma fonte referenciada, coloca na fila um aviso de *FontSubstitution*. Aqui está o código que faz o carregamento:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Por que isso importa:** Carregar o documento antecipadamente dá ao Aspose a chance de analisar cada trecho de texto, estilo e objeto incorporado. Se uma fonte não for encontrada no sistema ou na pasta de fontes personalizada, você receberá um aviso posteriormente.

---

## Etapa 2: Anexar um Callback de Aviso para Capturar Eventos de Substituição

Aspose.Words usa um mecanismo de callback para informá-lo sobre problemas como fontes ausentes. Ao atribuir uma implementação de `IWarningCallback` a `doc.WarningCallback`, você pode interceptar cada aviso à medida que ocorre.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Dica profissional:** Você pode anexar múltiplos callbacks (por exemplo, registro, atualizações de UI) encapsulando-os em um padrão composto, mas para este tutorial um único callback mantém as coisas claras.

---

## Etapa 3: Implementar o Callback de Aviso de Substituição de Fonte

Agora definimos a classe que realmente faz o trabalho. O callback recebe um objeto `WarningInfo`; filtramos por `WarningType.FontSubstitution` e armazenamos a descrição para uso posterior.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **O que está acontecendo:** Quando o Aspose encontra uma fonte ausente, ele cria um aviso como “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Nosso callback imprime essa linha e a salva.

---

## Etapa 4: Processar o Documento (Opcional) e Coletar Fontes Ausentes

Se você só precisa **detect missing fonts**, a etapa de carregamento já é suficiente — os avisos são disparados automaticamente. Contudo, muitos desenvolvedores também precisam **retrieve missing font** informações após executar algumas operações (por exemplo, salvar, converter). Abaixo forçamos uma pequena operação — salvar em PDF — para garantir que todos os avisos sejam emitidos, então extraímos as mensagens coletadas.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Saída esperada no console** (exemplo):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Observe como cada linha indica claramente a fonte original e a fonte de fallback que o Aspose escolheu. Esse é o núcleo do relatório de **aspose font substitution**.

---

## Etapa 5: Avançado – Usando Fontes Personalizadas para Reduzir Substituições

Às vezes você *tem* as fontes ausentes, apenas não estão na pasta padrão do sistema. Aspose.Words permite apontar para um diretório personalizado via `FontSettings`. Adicionar esta etapa pode reduzir drasticamente o número de avisos de substituição.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Por que adicionar isso?** Se você está distribuindo documentos entre máquinas, agrupar as fontes necessárias em uma pasta conhecida garante a mesma aparência visual em todos os lugares. Também torna sua rotina de **detect missing fonts** mais precisa porque o Aspose verifica essa pasta antes de recorrer ao fallback.

---

## Exemplo Completo Funcional

Juntando tudo, aqui está um único programa de console pronto para copiar‑colar. Salve como `Program.cs` e execute com `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**O que você deve ver:** Se o DOCX de origem referencia fontes que você não tem, o console imprime cada linha de substituição seguida por um resumo conciso. Se todas as fontes estiverem presentes, você receberá a mensagem “No missing fonts were detected.”

---

## Armadilhas Comuns & Como Evitá‑las

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| **Nenhum aviso aparece** | O documento usa apenas fontes do sistema, ou você já adicionou uma pasta personalizada contendo as fontes ausentes. | Verifique se o DOCX realmente referencia uma fonte indisponível. Você pode abri‑lo no Word e mudar um parágrafo para uma fonte rara (ex.: “Papyrus”). |
| **Mensagens duplicadas** | A mesma fonte é usada em múltiplas execuções, gerando vários avisos. | De‑duplicate a lista com `Distinct()` se você precisar apenas de um conjunto único. |
| **Queda de desempenho em documentos grandes** | Cada aviso é processado na thread da UI. | Execute o carregamento em uma tarefa em segundo plano ou use `Parallel.ForEach` para o pós‑processamento. |
| **Fonte de fallback incorreta** | O fallback padrão do Aspose pode não corresponder à sua identidade visual. | Defina `FontSettings.SubstitutionSettings.DefaultFontName` para um fallback preferido (ex.: “Calibri”). |

---

## Expandindo a Solução – Exportando Fontes Ausentes para JSON

Se você está construindo um serviço web que precisa relatar fontes ausentes de volta a um cliente, serializar a lista é trivial:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Agora sua API pode retornar um payload JSON limpo que outro sistema pode consumir.

---

## Conclusão

Neste guia demonstramos **Aspose font substitution** do início ao fim: carregando um documento Word, anexando um callback de aviso, capturando cada evento de *detect missing fonts*, e finalmente **retrieve missing font** informações para relatório ou correção. Ao adicionar pastas de fontes personalizadas opcionais, você pode reduzir a lista de substituições, e com algumas linhas extras pode até exportar os resultados como JSON.

Lembre‑se, a integridade visual dos seus documentos depende das fontes que eles utilizam. Com a técnica mostrada aqui, você nunca será surpreendido por um fallback inesperado novamente.  

Pronto para dar o próximo passo? Tente integrar essa lógica em um pipeline maior de processamento de documentos, ou explore outros recursos do Aspose.Words como incorporação de fontes (`doc.FontSettings.EmbeddedFonts`). As possibilidades são infinitas, e seus usuários agradecerão pela saída refinada.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}