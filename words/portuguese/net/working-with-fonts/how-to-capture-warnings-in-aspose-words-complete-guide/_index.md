---
category: general
date: 2026-03-13
description: Como capturar avisos ao carregar documentos com Aspose.Words, além de
  dicas para lidar com fontes ausentes e definir configurações de fontes personalizadas.
  Aprenda uma solução completa em C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: pt
og_description: Como capturar avisos ao carregar arquivos Word com Aspose.Words, além
  de maneiras práticas de lidar com fontes ausentes e definir configurações de fonte
  personalizadas.
og_title: Como Capturar Avisos no Aspose.Words – Guia Completo
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Capturar Avisos no Aspose.Words – Guia Completo
url: /pt/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

preserving markdown.

Let's craft translation.

Be careful with bold and italics.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Avisos no Aspose.Words – Guia Completo

Já se perguntou **como capturar avisos** que aparecem quando o Aspose.Words carrega um documento? Em muitos projetos do mundo real você verá alertas de substituição de fonte, notas sobre recursos obsoletos ou até mensagens relacionadas à segurança. Ignorá‑los é como dirigir com o para‑brisa trincado — você pode chegar ao destino, mas nunca saberá quando algo está prestes a quebrar.

A boa notícia é que o Aspose.Words oferece uma forma limpa, baseada em callbacks, de interceptar essas mensagens. Neste tutorial vamos percorrer um **exemplo completo em C#** que não só captura avisos, mas também mostra como **lidar com fontes ausentes** e **definir configurações de fonte personalizadas** para que seus documentos sejam renderizados exatamente como você espera.

---

## O que Você Vai Aprender

- Configurar `LoadOptions` para inserir um objeto `FontSettings` personalizado.  
- Registrar um callback de aviso que filtra eventos `FontSubstitution`.  
- Exibir detalhes do aviso no console (ou em qualquer logger que preferir).  
- Expandir a solução para lidar graciosamente com fontes ausentes em diferentes plataformas.  

Ao final deste guia você terá um trecho pronto‑para‑executar que pode ser inserido em qualquer projeto .NET, além de várias dicas práticas para evitar armadilhas comuns.

---

## Pré‑requisitos

| Requisito | Por que é importante |
|-----------|----------------------|
| **Aspose.Words for .NET** (v23.12 ou superior) | A API que usamos (`LoadOptions`, `IWarningCallback`) está aqui. |
| **.NET 6+** (ou .NET Framework 4.7.2+) | Recursos de linguagem modernos deixam o código mais limpo. |
| **Um DOCX de exemplo** (nomeado `input.docx`) colocado em uma pasta conhecida | Precisamos de algo para carregar e disparar um aviso. |
| **Um console ou framework de logging** (opcional) | Para ver os avisos capturados em ação. |

Nenhum pacote NuGet adicional é necessário além do próprio Aspose.Words.

---

## Etapa 1: Configurar Configurações de Fonte Personalizadas  

Antes de carregar um documento, você pode informar ao Aspose.Words onde procurar fontes. Esta é a parte de **definir configurações de fonte personalizadas** do quebra‑cabeça.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Por que isso importa:**  
Se um DOCX referencia uma fonte que não está instalada na máquina, o Aspose.Words substituirá silenciosamente por uma fonte padrão *a menos que* você tenha configurado uma pasta com as fontes necessárias. Ao definir uma pasta personalizada, você reduz a chance de avisos de “substituição de fonte” desde o início.

> **Dica profissional:** No Linux pode ser necessário adicionar o pacote `fonts-dejavu-core` ou qualquer coleção TrueType da qual seus documentos dependam.

---

## Etapa 2: Registrar um Callback de Aviso  

O Aspose.Words implementa `IWarningCallback`. Criaremos um pequeno manipulador que imprime apenas os avisos que nos interessam: fontes ausentes ou substituídas.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Por que isso importa:**  
O cenário de **lidar com fontes ausentes** agora está visível para você. Em vez de adivinhar qual fonte foi trocada, você obtém uma descrição clara como “Font 'Calibri' was substituted with 'Arial'”. Isso é inestimável ao depurar problemas de layout em PDFs gerados ou relatórios impressos.

---

## Etapa 3: Carregar o Documento com as Opções Configuradas  

Agora finalmente trazemos o documento para a memória, usando o `LoadOptions` que preparamos.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Se o arquivo de origem usar uma fonte que não esteja presente em `C:\MyFonts`, você verá uma saída semelhante a:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Essa linha é o resultado do **como capturar avisos** que você buscava.

---

## Etapa 4: Exemplo Completo Funcional (Pronto para Copiar e Colar)

A seguir está o programa inteiro, pronto para compilar. Cole-o em um novo projeto de console e execute — apenas certifique‑se de que os caminhos apontem para locais reais na sua máquina.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Saída esperada:**  

- Se todas as fontes estiverem disponíveis:  
  `Document processed. Check console for any warning messages.`  

- Se uma fonte estiver ausente:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Etapa 5: Variações Comuns e Casos de Borda  

| Situação | O que Ajustar |
|----------|--------------|
| **Múltiplas pastas de fontes** | Chame `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` para cada localização adicional. |
| **Suprimir todos os avisos** | Implemente `Warn` mas deixe o corpo vazio, ou defina `loadOptions.WarningCallback = null;`. |
| **Capturar outros tipos de aviso** | Verifique `info.WarningType` contra `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, etc. |
| **Executando no Linux/macOS** | Garanta que a pasta de fontes contenha arquivos `.ttf`/`.otf` compatíveis com Linux; pode ser necessário instalar `libfontconfig`. |
| **Documentos grandes** | Considere fazer streaming do documento (`LoadOptions.LoadFormat = LoadFormat.Docx;`) para reduzir a pressão de memória. |

Ao antecipar esses cenários, você evitará surpresas ao migrar de uma máquina de desenvolvimento para um pipeline CI ou uma VM na nuvem.

---

## Etapa 6: Confirmação Visual (Opcional)

Se preferir um indicativo visual rápido, pode exportar os avisos capturados para um pequeno relatório HTML. Aqui está um snippet diminuto que grava as mensagens em `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Depois de carregar o documento, chame `handler.WriteReport(@"C:\Docs\warnings.html");` e abra no navegador. A imagem abaixo mostra como o relatório pode ficar:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Texto alternativo:* **como capturar avisos** – captura de tela da saída do console e do relatório HTML.

---

## Conclusão  

Cobremos **como capturar avisos** no Aspose.Words, demonstramos uma forma confiável de **lidar com fontes ausentes** e mostramos como **definir configurações de fonte personalizadas** para renderização determinística. O exemplo completo está pronto para ser inserido em qualquer solução .NET, e o módulo `FontWarningHandler` pode ser estendido para se adequar à sua estratégia de logging ou telemetria.

Próximos passos? Experimente substituir as chamadas `Console.WriteLine` por um logger estruturado como o Serilog, ou envie os avisos para o Application Insights para monitoramento em tempo real. Você também pode explorar o padrão `DocumentVisitor` caso precise inspecionar o conteúdo do documento após o carregamento.

Tem perguntas sobre outros tipos de aviso ou estratégias de incorporação de fontes? Deixe um comentário abaixo — feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}