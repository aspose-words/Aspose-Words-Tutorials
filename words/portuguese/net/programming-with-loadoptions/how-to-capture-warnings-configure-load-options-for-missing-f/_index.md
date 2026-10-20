---
category: general
date: 2026-03-30
description: como capturar avisos ao carregar um arquivo DOCX – aprenda a detectar
  fontes ausentes, configurar as definições de fonte e definir opções de carregamento
  em C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: pt
og_description: como capturar avisos ao carregar um arquivo DOCX – guia passo a passo
  para detectar fontes ausentes e configurar as definições de fonte em C#.
og_title: como capturar avisos – configurar opções de carregamento para fontes ausentes
tags:
- Aspose.Words
- C#
- Font management
title: como capturar avisos – configurar opções de carregamento para fontes ausentes
url: /pt/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# como capturar avisos – configurar opções de carregamento para fontes ausentes

Já se perguntou **como capturar avisos** que aparecem quando um documento tenta usar uma fonte que você não tem instalada? É um cenário que confunde muitos desenvolvedores que trabalham com bibliotecas de processamento de texto, especialmente quando você precisa **detectar fontes ausentes** antes que elas quebrem seu pipeline de exportação de PDF.  

Neste tutorial, mostraremos uma solução prática e pronta‑para‑executar que **configura as definições de fonte**, **define opções de carregamento** e imprime cada aviso de substituição no console. Ao final, você saberá exatamente como **lidar com fontes ausentes** de maneira que mantenha sua aplicação robusta e seus usuários satisfeitos.

## O que você aprenderá

- Como **definir opções de carregamento** para que a biblioteca reporte problemas de fonte em vez de trocá‑las silenciosamente.
- Os passos exatos para **configurar as definições de fonte** para captura de avisos.
- Formas de **detectar fontes ausentes** programaticamente e reagir adequadamente.
- Um exemplo completo, pronto‑para‑copiar C# que funciona com o mais recente Aspose.Words for .NET (v24.10 na data deste tutorial).
- Dicas para estender a solução para registrar avisos, usar fontes personalizadas como fallback ou abortar o processamento quando fontes críticas estiverem ausentes.

> **Pré‑requisito:** Você precisa do pacote NuGet Aspose.Words for .NET instalado (`Install-Package Aspose.Words`). Nenhuma outra dependência externa é necessária.

---

## Etapa 1: Importar Namespaces e Preparar o Projeto

Primeiro, adicione as diretivas `using` essenciais. Isso não é apenas código padrão; informa ao compilador onde `LoadOptions`, `FontSettings` e `Document` estão definidos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Dica profissional:** Se você estiver usando .NET 6+ pode habilitar declarações *global using* para evitar repetir essas linhas em cada arquivo.

---

## Etapa 2: Definir Opções de Carregamento e Habilitar Avisos de Substituição de Fonte

O núcleo de **como capturar avisos** está no objeto `LoadOptions`. Ao criar uma nova instância de `FontSettings` e anexar um manipulador de evento a `SubstitutionWarning`, você instrui a biblioteca a emitir um aviso toda vez que não conseguir encontrar uma fonte solicitada.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Por que isso importa:** Sem a assinatura do evento, o Aspose.Words recorre silenciosamente a uma fonte padrão, e você nunca sabe quais glifos foram substituídos. Ao ouvir `SubstitutionWarning`, você obtém um registro completo—crucial para ambientes com alta exigência de conformidade.

---

## Etapa 3: Carregar o Documento Usando as Opções Configuradas

Agora que os avisos estão configurados, carregue seu DOCX (ou qualquer formato suportado) com o `loadOptions` que você acabou de preparar. O construtor `Document` acionará a lógica de verificação de fontes imediatamente.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Se o arquivo referenciar, por exemplo, *“Comic Sans MS”* em uma máquina que possui apenas *“Arial”*, você verá algo como:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Essa linha é impressa diretamente no console devido ao manipulador que anexamos anteriormente.

---

## Etapa 4: Verificar e Reagir aos Avisos Capturados

Capturar avisos é apenas metade da batalha; frequentemente você precisa decidir o que fazer a seguir. Abaixo está um padrão rápido que armazena os avisos em uma lista para análise posterior—perfeito se você quiser registrá‑los em um arquivo ou abortar a importação quando uma fonte crítica estiver ausente.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Tratamento de casos extremos:**  
- **Múltiplas fontes ausentes:** A lista conterá uma entrada por substituição, permitindo iterar e criar um relatório detalhado.  
- **Fontes de fallback personalizadas:** Se você possui seus próprios arquivos de fonte, adicione‑os ao `FontSettings` antes de carregar: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Os avisos então mostrarão o fallback personalizado em vez do padrão do sistema.  

---

## Etapa 5: Exemplo Completo Funcional (Pronto para Copiar e Colar)

Juntando tudo, aqui está um aplicativo de console autônomo que você pode compilar e executar agora mesmo.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Saída esperada no console** (quando o DOCX referencia uma fonte ausente):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Se uma fonte *crítica* como “Times New Roman” estiver ausente, você verá a mensagem de abortamento em vez disso.

---

## Perguntas Frequentes & Armadilhas

| Pergunta | Resposta |
|----------|----------|
| **Preciso chamar `SetFontsFolder` para capturar avisos?** | Não. O evento de aviso funciona com as fontes padrão do sistema. Use `SetFontsFolder` apenas quando quiser fornecer fontes de fallback adicionais. |
| **Isso funciona em .NET Core / .NET 5+?** | Absolutamente. Aspose.Words 24.10 suporta todas as runtimes .NET modernas. Apenas garanta que o pacote NuGet corresponda ao seu framework de destino. |
| **E se eu quiser registrar avisos em um arquivo ao invés do console?** | Substitua `Console.WriteLine(msg);` por qualquer chamada de framework de logging, por exemplo, `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Posso suprimir avisos para fontes específicas?** | Sim. Dentro do manipulador de evento você pode filtrar: `if (e.FontName == "SomeFont") return;`. Isso fornece controle granular. |
| **Existe uma forma de tratar fontes ausentes como erros?** | Lance uma exceção manualmente dentro do manipulador quando uma condição for atendida, ou defina uma flag e abortar após a construção do `Document`, como mostrado no exemplo. |

---

## Conclusão

Agora você tem um padrão sólido e pronto para produção para **como capturar avisos** que ocorrem ao carregar documentos com fontes ausentes. Ao **detectar fontes ausentes**, **configurar as definições de fonte** e **definir opções de carregamento** adequadamente, você obtém total visibilidade dos eventos de substituição de fontes e pode decidir se registra, usa fallback ou aborta.

Dê o próximo passo integrando essa lógica ao seu pipeline de conversão PDF, adicionando fontes de fallback personalizadas ou alimentando a lista de avisos em um sistema de monitoramento. A abordagem escala de pequenas utilidades a serviços de processamento de documentos de nível empresarial.

### Leituras Adicionais & Próximos Passos

- **Explore mais recursos do FontSettings** – incorporação de fontes personalizadas, controle da ordem de fallback e considerações de licenciamento.  
- **Combine com conversão PDF** – após capturar avisos, chame `doc.Save("output.pdf");` e verifique se o PDF usa as fontes esperadas.  
- **Automatize testes** – escreva testes unitários que carreguem documentos com fontes ausentes conhecidas e verifiquem se a lista de avisos contém as mensagens esperadas.  

Se você encontrar algum problema ou tiver ideias de melhoria, sinta‑se à vontade para deixar um comentário. Boa codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}