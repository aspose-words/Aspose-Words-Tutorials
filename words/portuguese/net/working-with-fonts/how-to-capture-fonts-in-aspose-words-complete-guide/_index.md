---
category: general
date: 2026-01-05
description: Como capturar fontes rapidamente e lidar com fontes ausentes usando Aspose.Words.
  Aprenda uma solução passo a passo com código C# completo.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: pt
og_description: Como capturar fontes no Aspose.Words e lidar com fontes ausentes.
  Siga este guia detalhado para uma implementação confiável em C#.
og_title: Como Capturar Fontes no Aspose.Words – Tutorial Completo
tags:
- Aspose.Words
- C#
- Document Processing
title: Como Capturar Fontes no Aspose.Words – Guia Completo
url: /pt/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como Capturar Fontes no Aspose.Words – Guia Completo

Já se perguntou **como capturar fontes** ao carregar um documento Word com Aspose.Words? Você não está sozinho. Fontes ausentes podem causar pequenas falhas de layout, e sem um aviso adequado você pode nunca perceber até que o PDF final fique estranho. Neste tutorial vamos mostrar exatamente como capturar fontes **e** lidar com fontes ausentes para que sua saída permaneça pixel‑perfect.

Percorreremos um cenário do mundo real, configuraremos um callback de aviso e forneceremos um exemplo C# pronto‑para‑executar. Ao final, você saberá por que isso importa, como implementá‑lo e o que observar quando fontes desaparecem do seu ambiente.

## O que Você Vai Aprender

- Como configurar **LoadOptions** para ouvir avisos relacionados a fontes.  
- O papel de **IWarningCallback** e **WarningInfo** no Aspose.Words.  
- Dicas práticas para solução de problemas e registro de fontes ausentes.  
- Um exemplo de código completo e autocontido que você pode colar no Visual Studio e executar instantaneamente.

**Pré‑requisitos:** .NET 6+ (ou .NET Framework 4.7.2+), Aspose.Words para .NET instalado via NuGet, e familiaridade básica com C#. Nenhuma outra biblioteca é necessária.

---

## Etapa 1: Configurar Load Options para Capturar Fontes

A primeira coisa que precisamos é de uma instância **LoadOptions**. Esse objeto informa ao Aspose.Words como se comportar ao ler um documento. Ao atribuir um **IWarningCallback** personalizado, podemos interceptar quaisquer avisos de substituição de fonte que ocorram durante o processo de carregamento.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Por que isso importa:**  
Aspose.Words substitui silenciosamente fontes ausentes por uma padrão, a menos que você peça que ele avise. Ao conectar um callback, nós **capturamos** informações de fontes logo no momento do carregamento, nos dando a chance de registrar, substituir ou até abortar a operação.

> **Dica profissional:** Mantenha `loadOptions` como uma variável reutilizável se você processar muitos documentos em lote. Isso evita recriar o mesmo callback repetidamente.

---

## Etapa 2: Carregar o Documento com as Opções Configuradas

Agora que o callback está configurado, carregamos o documento. O construtor **Document** aceita o caminho e o **LoadOptions** que acabamos de configurar.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Se alguma fonte estiver ausente, o Aspose.Words disparará um aviso que nosso `FontWarningCollector` receberá. O documento em si ainda será carregado, mas você terá um registro claro de quais fontes foram substituídas.

---

## Etapa 3: Implementar o FontWarningCollector – Lidar com Fontes Ausentes

O coração de **como capturar fontes** está na classe `FontWarningCollector`. Ela implementa `IWarningCallback` e filtra apenas os eventos `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explicação:**  
- `info.Type` nos indica a categoria do aviso. Ao verificar `FontSubstitution` nós **lidamos com fontes ausentes** sem poluir a saída com mensagens não relacionadas (por exemplo, recursos obsoletos).  
- `info.Description` contém uma mensagem legível, como “Font 'Comic Sans MS' was substituted with 'Arial'.” Este é exatamente o dado que você precisa para auditar seu inventário de fontes.

> **Atenção:** Se precisar interromper o processamento quando uma fonte crítica estiver ausente, lance uma exceção dentro do bloco `if` ao invés de apenas imprimir.

---

## Etapa 4: Verificar a Saída – O Que Esperar

Execute o programa a partir de um console ou da sua IDE. Para cada fonte ausente, você verá uma linha como:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Se todas as fontes estiverem presentes, o callback permanecerá silencioso e o documento será carregado sem incidentes. Agora você pode continuar com segurança a salvar, converter ou imprimir o documento, confiante de que **capturou** informações sobre fontes.

---

## Etapa 5: Exemplo Completo Funcional (Todas as Partes Juntas)

Abaixo está o programa completo, pronto para copiar‑e‑colar. Ele inclui as diretivas `using`, a implementação do callback e uma pequena demonstração de como salvar o documento carregado como PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Executando o código:**  
1. Crie um novo projeto console (`dotnet new console -n FontCaptureDemo`).  
2. Adicione o pacote Aspose.Words (`dotnet add package Aspose.Words`).  
3. Substitua o `Program.cs` gerado pelo trecho acima.  
4. Coloque um DOCX que intencionalmente referencia uma fonte que você não possui (por exemplo, “Papyrus”).  
5. Execute (`dotnet run`). Observe o console para mensagens de substituição e, em seguida, abra `output.pdf` para verificar o layout.

---

## Perguntas Frequentes & Casos Limítrofes

### E se eu precisar da lista de fontes ausentes mais tarde?

Armazene as mensagens em um `List<string>` dentro de `FontWarningCollector` e exponha‑as via uma propriedade. Dessa forma, você pode gravar a lista em um arquivo de log após processar muitos documentos.

### Isso funciona com arquivos criptografados ou protegidos por senha?

Sim, mas você também deve fornecer a senha via `LoadOptions.Password`. O callback de aviso funciona da mesma forma depois que o documento é descriptografado.

### Posso substituir uma fonte ausente por um fallback personalizado?

Absolutamente. Dentro do método `Warning` você pode chamar `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Isso garante que a substituição seja determinística.

### Isso afetará o desempenho?

O overhead é mínimo — essencialmente uma chamada de método por aviso. Em um lote de milhares de documentos, o impacto é insignificante comparado ao custo de I/O de carregar cada arquivo.

---

## Conclusão

Cobremos **como capturar fontes** no Aspose.Words, mostramos como **lidar com fontes ausentes** usando um callback de aviso limpo e entregamos um exemplo completo e executável. Ao incorporar esse padrão ao seu pipeline de processamento de documentos, você nunca mais será surpreendido por substituições silenciosas de fontes.

Pronto para o próximo passo? Experimente estender o collector para gravar logs em JSON, integrar com um painel de monitoramento ou incorporar automaticamente fontes ausentes ao PDF de saída. As possibilidades são infinitas, e agora você tem uma base sólida.

Boa codificação! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}