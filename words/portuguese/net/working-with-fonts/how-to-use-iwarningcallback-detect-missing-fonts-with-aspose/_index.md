---
category: general
date: 2026-06-24
description: Como usar IWarningCallback para detectar fontes ausentes em documentos
  Aspose.Words. Aprenda um exemplo completo e executável e as melhores práticas.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: pt
og_description: Como usar IWarningCallback para detectar fontes ausentes no Aspose.Words.
  Siga o guia passo a passo para uma solução completa e pronta para produção.
og_title: Como usar IWarningCallback – Detectar fontes ausentes
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Como usar IWarningCallback – Detectar fontes ausentes com Aspose.Words
url: /pt/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Usar IWarningCallback – Detectar Fontes Ausentes com Aspose.Words

Usar **IWarningCallback** é essencial quando você trabalha com Aspose.Words e precisa **detectar fontes ausentes** em um arquivo DOCX. Neste guia, percorreremos um exemplo completo, pronto‑para‑copiar, que mostra exatamente como usar IWarningCallback para capturar avisos de substituição de fontes, por que isso é importante e o que fazer depois de capturá‑los.

Se você já abriu um documento e viu texto embaralhado porque uma fonte personalizada não estava instalada, conhece a frustração. Ao final deste tutorial, você terá uma maneira confiável de expor esses problemas programaticamente, registrá‑los ou até mesmo aplicar uma fonte de reserva automaticamente.

## O Que Você Vai Aprender

- O propósito do **IWarningCallback** e quando usá‑lo.  
- Como implementar um coletor de avisos personalizado que isola eventos de **detect missing fonts**.  
- Conectar o coletor ao **LoadOptions** para que cada carregamento de documento seja monitorado.  
- Verificar a saída e lidar com casos extremos (várias fontes ausentes, avisos silenciosos, etc.).  

### Pré‑requisitos

- .NET 6.0 ou superior (o código também funciona no .NET Framework 4.6+).  
- Aspose.Words para .NET instalado via NuGet (`Install-Package Aspose.Words`).  
- Um arquivo DOCX que referencia uma fonte não presente na máquina (por exemplo, `DocumentWithMissingFont.docx`).  

Nenhuma biblioteca adicional é necessária—tudo está dentro do Aspose.Words.

---

## Como Usar IWarningCallback para Detectar Fontes Ausentes no Aspose.Words

Abaixo está o **programa completo e executável**. Copie‑o para um novo projeto de console, ajuste o caminho do arquivo e execute. Você verá a saída no console para cada aviso de fonte ausente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Saída Esperada

Se `DocumentWithMissingFont.docx` referencia uma fonte chamada *“MyFancyFont”* que não está instalada, você verá algo como:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Cada linha prefixada com **[Missing Font]** é gerada pela nossa implementação de **IWarningCallback**, provando que detectamos com sucesso **detect missing fonts**.

---

## Etapa 1: Implementar a Interface IWarningCallback

Por que precisamos de uma classe personalizada? Aspose.Words gera **warnings** por várias razões—problemas de formato de arquivo, recursos obsoletos e, mais importante para nós, substituição de fontes. Ao implementar `IWarningCallback`, obtemos um hook que recebe cada aviso à medida que ocorre. Filtrar por `WarningType.FontSubstitution` isola o cenário específico onde uma fonte está ausente.

**Dica profissional:** Se precisar capturar *todos* os avisos para diagnóstico, basta remover a verificação `if` e registrar cada `info.Type`.

## Etapa 2: Conectar o Callback ao LoadOptions

`LoadOptions` é o ponto de entrada que informa ao Aspose.Words como tratar o documento de entrada. Definir `WarningCallback` para uma instância do nosso coletor garante que o callback esteja ativo durante toda a operação de carregamento. Você pode reutilizar o mesmo objeto `LoadOptions` para vários documentos, o que é útil em pipelines de processamento em lote.

**Pergunta comum:** *E se eu carregar um documento sem especificar LoadOptions?*  
Resposta: Aspose.Words ainda levantará avisos internamente, mas sem um callback eles são descartados silenciosamente, e você perde a chance de **detect missing fonts**.

## Etapa 3: Carregar um Documento e Capturar Avisos de Fonte Ausente

O construtor `Document` que recebe um caminho de arquivo e `LoadOptions` faz o trabalho pesado. À medida que o arquivo é analisado, qualquer fonte ausente aciona o método `FontWarningCollector.Warning`. A saída no console prova que o mecanismo funciona.

**Caso extremo:** Um único documento pode referenciar várias fontes ausentes. O callback é disparado uma vez por fonte ausente, então você verá múltiplas linhas—perfeito para construir um relatório abrangente.

## Por Que Usar IWarningCallback ao Invés de Verificações Manuais de Fontes?

Você poderia varrer manualmente as propriedades `Run.Font` do documento após o carregamento, mas isso exigiria que o documento fosse carregado com sucesso primeiro—algo que falha se a fonte estiver completamente indisponível. O sistema de avisos funciona **antes** de qualquer substituição ocorrer, fornecendo uma visão real do que está faltando.

Além disso, o callback é executado **como parte do pipeline de carregamento**, permitindo abortar cedo, substituir fontes em tempo real ou registrar diagnósticos detalhados sem passes extras sobre a árvore do documento.

## Lidando com Múltiplas Fontes Ausentes de Forma Elegante

Se você espera muitas fontes ausentes, considere agregá‑las em uma coleção:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Depois do carregamento, você pode iterar sobre `MissingFonts` e, por exemplo, gravá‑las em um arquivo CSV para a equipe de design.

## Bônus: Registrando Avisos em um Arquivo

A saída no console serve para demonstrações, mas código de produção geralmente registra em um armazenamento persistente. Substitua a chamada `Console.WriteLine` por algo como:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Agora você tem um registro de auditoria que pode ser revisado posteriormente, atendendo aos requisitos de conformidade.

## Conclusão

Cobrimos **como usar IWarningCallback** para **detect missing fonts** no Aspose.Words, desde a implementação do callback até sua conexão ao `LoadOptions` e o tratamento dos avisos resultantes. Essa abordagem fornece insight em tempo real sobre problemas relacionados a fontes, permitindo registrar, substituir ou alertar usuários antes que o documento seja renderizado.

Próximos passos que você pode explorar:

- **Fallback fonts:** atribuir programaticamente uma fonte padrão quando ocorre uma substituição.  
- **Batch processing:** percorrer uma pasta de documentos, reutilizando o mesmo `AggregatingFontCollector`.  
- **User feedback:** exibir avisos de fontes ausentes em uma interface de usuário ao invés do console.

Experimente em seu próprio projeto—chega de texto embaralhado misterioso, apenas diagnósticos claros e acionáveis. Feliz codificação!

## O Que Você Deve Aprender a Seguir?

Os tutoriais a seguir cobrem tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Como Carregar DOCX e Detectar Fontes Ausentes – Guia Completo em C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Como Detectar Fontes no Aspose.Words – Manipular Avisos & Configurações](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Como Usar LoadOptions no Aspose.Words – Guia Completo](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}