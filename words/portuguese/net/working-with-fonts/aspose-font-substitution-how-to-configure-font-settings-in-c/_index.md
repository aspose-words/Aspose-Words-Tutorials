---
category: general
date: 2026-03-27
description: 'Substituição de fontes Aspose facilitada: aprenda a configurar as definições
  de fontes, capturar avisos e lidar com fontes ausentes em seus aplicativos .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: pt
og_description: Domine a substituição de fontes Aspose configurando as definições
  de fonte e tratando fontes ausentes com um callback de aviso. Guia completo em C#.
og_title: Substituição de Fonte Aspose – Configurar Configurações de Fonte em C#
tags:
- Aspose.Words
- C#
- Font Management
title: Substituição de Fonte Aspose – Como Configurar as Configurações de Fonte em
  C#
url: /pt/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Guia Completo para Configurar Configurações de Fonte

Já se deparou com um documento que de repente troca sua tipografia personalizada por algo genérico? Isso é **aspose font substitution** fazendo seu trabalho — substituindo fontes ausentes pela correspondência mais próxima que consegue encontrar. É útil, mas se você precisar saber *exatamente* qual fonte foi trocada, precisará acessar o sistema de avisos da biblioteca e configurar as configurações de fonte manualmente.

Neste tutorial vamos percorrer um cenário real: carregar um DOCX que referencia uma fonte que você não possui, capturar o evento de substituição e imprimir uma mensagem amigável no console. Ao final, você estará confortável com **configure font settings**, configurando um **Aspose.Words warning callback**, e estendendo o exemplo para se adequar a qualquer fluxo de trabalho.

> **O que você precisará**  
> • .NET 6+ (ou .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (último NuGet)  
> • Um DOCX que referencia uma fonte ausente (vamos chamá‑lo de `MissingFont.docx`)  

Vamos mergulhar.

---

## Step 1: Install Aspose.Words and Prepare the Project

Antes de escrever qualquer código, certifique‑se de que o pacote Aspose.Words está referenciado:

```bash
dotnet add package Aspose.Words
```

> **Dica profissional:** Use a versão estável mais recente; a partir de março 2026 é 23.11.0. Versões mais novas melhoram os algoritmos de correspondência de fontes e adicionam tipos extras de avisos.

Crie um novo aplicativo de console (ou insira o código em um projeto existente) e adicione as diretivas `using` habituais:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Esses namespaces nos dão acesso ao `Document`, `LoadOptions` e às classes relacionadas a fontes que precisaremos.

---

## Step 2: Configure Font Settings with LoadOptions

O coração do controle de **aspose font substitution** está em `LoadOptions.FontSettings`. Ao fornecer um objeto `FontSettings` vazio, instruímos o Aspose a usar seus caminhos de pesquisa padrão *e* a relatar qualquer substituição via um callback de aviso.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Por que não confiar apenas nos padrões? Porque anexar um callback de aviso (próximo passo) só funciona quando a propriedade `FontSettings` não é nula. Essa linha diminuta nos dá um ponto de conexão ao processo de substituição sem alterar o comportamento real de busca de fontes.

---

## Step 3: Attach a Warning Callback to Capture Substitutions

Aspose.Words implementa a interface `IWarningCallback`. Sempre que algo relevante acontece — como uma fonte ausente — ele chama nosso método `Warning`. Implementaremos um manipulador pequeno que filtra por `WarningType.FontSubstitution` e imprime a descrição.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

E aqui está o próprio manipulador:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Por que isso importa** – Sem o callback, o Aspose troca fontes silenciosamente, e você nunca sabe qual foi usada. O callback torna o processo transparente, o que é essencial para relatórios de conformidade ou para depuração de problemas de layout.

---

## Step 4: Load the Document Using the Configured Options

Agora finalmente carregamos o documento, passando o `loadOptions` que acabamos de preparar. Se o arquivo de origem referencia uma fonte que não está instalada, nosso manipulador será acionado.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Substitua `YOUR_DIRECTORY` pelo caminho real onde o `MissingFont.docx` está localizado. Quando você executar o programa, deverá ver uma saída semelhante a:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Essa linha informa exatamente qual fonte estava ausente e qual substituta o Aspose escolheu.

---

## Step 5: (Optional) Fine‑Tune Font Search Paths

Se você possui uma pasta privada com fontes corporativas, pode dizer ao Aspose onde procurar antes que ele recorra às fontes do sistema. Este é um uso avançado de **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Definir `recursive: true` faz o Aspose varrer subpastas também. Agora a biblioteca tentará suas fontes privadas primeiro, reduzindo a chance de substituição indesejada.

---

## Full Working Example

Juntando tudo, aqui está o programa completo, pronto‑para‑executar:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Saída esperada** (quando uma fonte ausente é encontrada):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Se todas as fontes estiverem presentes, o programa roda silenciosamente (sem avisos) e ainda produz o PDF.

---

## Common Questions & Edge Cases

### O que fazer se eu precisar *impedir* a substituição completamente?

Defina `FontSettings.SubstitutionSettings` como `null` ou use `FontSettings.FontSubstitutionSettings` para controlar o comportamento. Por exemplo:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Agora o Aspose lançará uma exceção em vez de substituir silenciosamente, a qual pode ser capturada e tratada.

### Isso funciona com outros formatos de arquivo (ex.: .doc, .rtf)?

Absolutamente. O mesmo objeto `LoadOptions` pode ser passado para qualquer construtor `Document` que aceite um caminho de arquivo. O callback de aviso será disparado para todos os formatos que dependem de fontes.

### Posso capturar o nome exato da fonte de substituição?

Sim. A string `info.Description` contém tanto a fonte ausente quanto a de substituição. Se precisar do nome programaticamente, pode analisá‑la ou usar o objeto `FontInfo` (disponível em versões mais recentes).

### Como isso se comporta em um ambiente multithread?

`FontSettings` **não** é thread‑safe. Crie um `LoadOptions` separado (com seu próprio `FontSettings`) por thread, ou proteja o acesso com um lock.

---

## Conclusion

Cobremos tudo o que você precisa para dominar **aspose font substitution** e **configure font settings** em uma aplicação C#:

1. Instale o Aspose.Words e adicione as declarações `using` necessárias.  
2. Crie um objeto `LoadOptions` com um `FontSettings` novo.  
3. Anexe um `IWarningCallback` personalizado para expor eventos de substituição.  
4. Carregue o documento, permitindo que o callback relate quaisquer fontes ausentes.  
5. (Opcional) Amplie o caminho de busca ou desative a substituição totalmente.

Com esse padrão, você pode registrar fontes ausentes para conformidade, alertar usuários em uma UI, ou incorporar fontes de fallback automaticamente antes da publicação. Em seguida, você pode explorar **políticas de substituição de fontes do Aspose.Words** ou integrar o fluxo de trabalho a um pipeline maior de processamento de documentos.

Feliz codificação, e que seus documentos sempre renderizem com a tipografia correta!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}