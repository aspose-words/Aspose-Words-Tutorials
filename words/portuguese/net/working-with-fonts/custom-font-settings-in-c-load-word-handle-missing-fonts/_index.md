---
category: general
date: 2026-03-08
description: Configurações de fonte personalizadas permitem definir as configurações
  de fonte, carregar documentos Word com segurança e lidar com fontes ausentes usando
  o Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: pt
og_description: Configurações de fonte personalizadas permitem definir configurações
  de fonte, carregar documentos Word com segurança e lidar com fontes ausentes usando
  o Aspose.Words.
og_title: Configurações de Fonte Personalizada em C# – Carregar Word e Lidar com Fontes
  Ausentes
tags:
- Aspose.Words
- C#
- Font Management
title: Configurações de Fonte Personalizadas em C# – Carregar Word e Lidar com Fontes
  Ausentes
url: /pt/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

– Configure LoadOptions" etc.

Also note "## Custom Font Settings – Configure LoadOptions" we translated to "## Configurações de Fonte Personalizadas – Configurar LoadOptions". Good.

Check for any stray formatting like "###" none.

Make sure we preserve blockquote formatting.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurações de Fonte Personalizadas em C# – Carregar Word e Tratar Fontes Ausentes

Já se perguntou como as **configurações de fonte personalizadas** funcionam quando um arquivo Word faz referência a fontes que você não tem instaladas? É um problema comum—seu documento parece bom em uma máquina, mas de repente todos os parágrafos mudam para uma fonte de fallback em outra.  

A boa notícia? Com Aspose.Words você pode **definir configurações de fonte**, **carregar o conteúdo de um documento Word** e **tratar fontes ausentes** tudo em um fluxo organizado. A seguir você encontrará um exemplo completo, pronto‑para‑executar, que mostra exatamente como fazer isso, além do “porquê” de cada passo.

## O que você aprenderá

* Criar um objeto `LoadOptions` e anexar uma instância `FontSettings`.  
* Registrar um callback de aviso para que você possa ver quais fontes são substituídas.  
* Carregar um arquivo DOCX que pode ter fontes ausentes e imprimir os detalhes da substituição no console.  

Ao final, você poderá distribuir seu aplicativo C# com confiança, sabendo que cada cenário de fonte ausente é registrado e pode ser tratado posteriormente.

> **Pré-requisito:** Aspose.Words for .NET (v23.12 ou mais recente) instalado via NuGet, e familiaridade básica com aplicativos console em C#.

---

## Configurações de Fonte Personalizadas – Configurar LoadOptions

A primeira coisa que você precisa é um objeto `LoadOptions`. Ele indica ao Aspose.Words como tratar o arquivo de entrada. Ao atribuir uma nova instância `FontSettings`, fornecemos à biblioteca um local para procurar fontes personalizadas.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Por que isso importa:**  
Se você omitir `FontSettings`, o Aspose.Words recorre à coleção de fontes padrão do sistema. Isso significa que qualquer fonte ausente será substituída silenciosamente, e você não saberá quais foram trocadas. Ao criar um contêiner explícito `FontSettings` você ganha controle total sobre o processo de busca.

---

## Definir Configurações de Fonte em LoadOptions

Agora que temos um objeto `FontSettings`, você pode se perguntar onde apontá‑lo. Normalmente você adicionaria uma pasta que contém as fontes que você entrega com sua aplicação:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Se você não tem uma pasta privada, pode omitir este bloco—o Aspose.Words ainda reportará fontes ausentes via o callback de aviso.*

**Dica profissional:** Use a flag `recursive: true` se suas fontes estiverem espalhadas por sub‑pastas. Isso evita que você tenha que adicionar cada caminho manualmente.

---

## Carregar Documento Word com Configurações de Fonte Personalizadas

Com as opções preparadas, carregar o documento é simples. O construtor `Document` aceita o caminho do arquivo e o `LoadOptions` que acabamos de criar.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**O que está acontecendo nos bastidores?**  
O Aspose.Words analisa o DOCX, verifica cada referência `<w:font>` e consulta as `FontSettings` fornecidas. Se uma fonte não for encontrada, ele dispara um aviso do tipo `FontSubstitution`. Nosso manipulador personalizado (mostrado a seguir) capturará esses avisos.

---

## Tratar Fontes Ausentes com Callback de Aviso

A interface `IWarningCallback` permite que você reaja a quaisquer problemas que surgirem durante o carregamento. Implementá‑la é simples:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Quando o documento é carregado, cada fonte ausente gerará uma linha como:

```
Font substituted: Arial -> Liberation Sans
```

**Por que você deve registrar isso:**  
Em produção, você pode redirecionar essas mensagens para um arquivo ou sistema de telemetria, facilitando a identificação de quais fontes precisam ser incluídas ou licenciadas.

---

## Exemplo Completo Funcional

Abaixo está um programa console autônomo que reúne tudo. Copie‑e cole em um novo projeto console .NET Core e pressione **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Saída esperada** (supondo que `input.docx` use uma fonte que você não possui):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Se todas as fontes estiverem presentes, você verá apenas a linha de confirmação final.

---

## Perguntas Frequentes & Casos Limite

| Pergunta | Resposta |
|----------|----------|
| **E se eu precisar incorporar as fontes ausentes no PDF?** | Após o carregamento, chame `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` e então habilite a incorporação com `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Posso suprimir os avisos ao invés de registrá‑los?** | Sim—defina `loadOptions.WarningCallback = null;` ou implemente o callback para ignorar avisos que não sejam de fonte. |
| **Isso funciona com arquivos `.doc` e `.rtf`?** | Absolutamente. O mesmo objeto `LoadOptions` se aplica a qualquer formato suportado pelo Aspose.Words. |
| **O callback é thread‑safe?** | O callback roda na mesma thread que carrega o documento, então você pode escrever com segurança no console. Para cenários multi‑thread, use uma coleção concorrente ou framework de logging. |

---

## Dicas Profissionais & Armadilhas

* **Dica profissional:** Se você distribuir uma fonte que não está instalada na máquina de destino, adicione‑a à pasta que você passa para `SetFontsFolder`. Isso garante renderização determinística.
* **Cuidado com licenças:** Algumas fontes exigem licenças comerciais para incorporação. Sempre verifique a EULA da fonte antes de incluí‑la.
* **Nota de desempenho:** Carregar grandes bibliotecas de fontes pode desacelerar a análise do documento. Mantenha a pasta enxuta—inclua apenas as fontes realmente necessárias.
* **Caso limite:** Quando um documento referencia uma fonte pelo seu *nome PostScript* ao invés do nome da família, o Aspose.Words ainda a resolve desde que o arquivo da fonte esteja presente no caminho de busca.

---

## Conclusão

Agora você tem um padrão completo e pronto para produção para usar **configurações de fonte personalizadas** em C#. Ao configurar `LoadOptions`, registrar um callback de aviso e, opcionalmente, apontar para uma pasta de fontes privada, você pode **definir configurações de fonte**, **carregar o conteúdo de documentos Word** de forma confiável

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}