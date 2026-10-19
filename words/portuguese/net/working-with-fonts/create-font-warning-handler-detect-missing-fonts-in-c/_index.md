---
category: general
date: 2026-02-12
description: Crie um manipulador de avisos de fontes para detectar fontes ausentes
  e rastrear fontes ausentes no Aspose.Words. Aprenda a registrar avisos de forma
  eficiente.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: pt
og_description: Crie um manipulador de aviso de fonte em C# para detectar fontes ausentes
  e aprenda como registrar avisos quando o Aspose.Words substitui fontes.
og_title: Criar Manipulador de Avisos de Fonte – Detectar Fontes Ausentes
tags:
- Aspose.Words
- C#
- Document Processing
title: Criar Manipulador de Aviso de Fonte – Detectar Fontes Ausentes em C#
url: /pt/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Manipulador de Avisos de Fonte – Detectar Fontes Ausentes em C#

Já precisou **criar um manipulador de avisos de fonte** porque um documento Word trocou silenciosamente uma fonte que você não esperava? Você não está sozinho. Quando o Aspose.Words carrega um DOCX que referencia uma fonte ausente no servidor, ele recorre silenciosamente a uma fonte padrão—deixando seu layout sutilmente quebrado.  

Neste tutorial vamos mostrar exatamente como **detectar fontes ausentes**, **rastrear fontes ausentes** e **como registrar avisos** para que você possa identificar essas substituições antes que causem problemas. Ao final, você terá um manipulador de avisos reutilizável que imprime cada evento de substituição de fonte no console (ou em qualquer logger que preferir). Sem mistério, apenas código claro e acionável.

## Pré‑requisitos

- .NET 6.0 ou superior (a API é a mesma para .NET Framework 4.6+)
- Aspose.Words for .NET instalado (`dotnet add package Aspose.Words`)
- Um arquivo Word que referencia uma fonte não instalada na sua máquina (por exemplo, `MissingFont.docx`)

Se já tem isso, ótimo—vamos começar.

## Etapa 1: Configurar LoadOptions com um Callback de Aviso  

A primeira coisa que você faz ao **criar um manipulador de avisos de fonte** é dizer ao Aspose.Words para disparar um callback sempre que encontrar um problema. `LoadOptions` é o contêiner para essa configuração.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Por que isso importa:**  
`LoadOptions` é o único lugar onde você pode conectar um `IWarningCallback`. Sem ele, o Aspose.Words registra avisos internamente, mas você nunca os verá. Ao atribuir `FontWarningHandler` ganhamos controle total sobre o que acontece quando uma fonte ausente é substituída.

## Etapa 2: Implementar a Classe FontWarningHandler  

Agora realmente **criamos o manipulador de avisos de fonte**. A classe implementa `IWarningCallback` e recebe um objeto `WarningInfo` para cada aviso que o Aspose.Words gera.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explicação:**  
- `info.Type` indica a categoria do aviso. Nos interessamos por `WarningType.FontSubstitution`, pois é isso que sinaliza uma fonte ausente.  
- `info.Description` contém uma mensagem legível, como *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Ao escrever em `Console.WriteLine` **registramos avisos** instantaneamente. Em um aplicativo real você pode substituir isso por `ILogger`, um gravador de arquivos ou um serviço de telemetria.

> **Dica profissional:** Se precisar coletar todas as fontes ausentes para relatório posterior, armazene `info.Description` em um `List<string>` em vez de imprimi‑la.

## Etapa 3: Carregar o Documento Usando o LoadOptions Configurado  

Com o callback configurado, carregar um documento disparará automaticamente nosso manipulador sempre que uma fonte estiver ausente.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**O que você verá:**  
Executar o programa imprime algo semelhante a:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Essa linha confirma que você **detectou fontes ausentes** e agora está **rastreando fontes ausentes** em tempo real.

## Etapa 4: Verificar se o Manipulador Funciona em Diferentes Cenários  

É fácil assumir que o manipulador funciona apenas para arquivos DOCX, mas o Aspose.Words suporta muitos formatos. Tente carregar um PDF que referencia uma fonte incorporada, ou um arquivo `.doc` mais antigo. O mesmo callback é disparado para qualquer formato que passe pelo pipeline de resolução de fontes.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Se o PDF referencia uma fonte que não está instalada, você receberá a mesma saída no console. Isso demonstra que sua solução de **criar manipulador de avisos de fonte** é independente de formato.

## Etapa 5: Estendendo o Manipulador – Registrando em um Arquivo  

A saída no console é prática para demonstrações, mas código de produção costuma gravar em um arquivo de log. Aqui está um ajuste rápido.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Agora, toda vez que uma fonte for substituída, a mensagem é acrescentada a `font-warnings.log`. Isso atende à parte **como registrar avisos** do briefing e fornece um registro persistente.

## Etapa 6: Juntando Tudo – Exemplo Completo e Executável  

Abaixo está o programa completo que você pode copiar‑colar em um aplicativo console. Nenhum trecho está faltando; basta substituir o caminho do arquivo pelo seu documento.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Resultado esperado:**  

- O console imprime cada linha de substituição.  
- `font-warnings.log` agora contém um registro com timestamp de cada evento de fonte ausente.  
- O arquivo `output.pdf` é criado usando as fontes substituídas, garantindo que a conversão seja bem‑sucedida mesmo quando as fontes originais não estão disponíveis.

## Perguntas Frequentes & Casos de Borda  

| Pergunta | Resposta |
|----------|----------|
| *E se eu quiser ignorar certas fontes?* | Dentro de `Warning`, verifique `info.Description` para o nome da fonte e `return;` imediatamente para fontes que você considera aceitáveis. |
| *O manipulador será disparado para fontes incorporadas?* | Não—fontes incorporadas estão sempre disponíveis ao documento, portanto nenhum aviso de substituição ocorre. |
| *Posso capturar outros tipos de aviso (ex.: problemas de resolução de imagem)?* | Claro. Remova a verificação `if (info.Type == WarningType.FontSubstitution)` ou adicione blocos `if` adicionais para `WarningType.ImageResolution`. |
| *O manipulador é thread‑safe?* | A implementação padrão mostrada grava em um arquivo sem sincronização. Para cenários multithread, envolva gravações em arquivo em um lock ou use um logger concorrente. |

## Próximos Passos  

Agora que você sabe **como registrar avisos** para fontes ausentes, pode querer:

- **Detectar fontes ausentes** durante um processo de importação em lote e gerar um relatório resumido.  
- **Rastrear fontes ausentes** em vários documentos e enviar um alerta por e‑mail quando uma fonte específica aparecer com frequência.  
- **Integrar com um sistema de monitoramento** (ex.: Azure Application Insights) para exibir tendências de substituição de fontes ao longo do tempo.  

Todas essas extensões se baseiam na mesma fundação `IWarningCallback` que criamos.

---

*Boa codificação! Se encontrar peculiaridades—talvez uma pasta de fontes personalizada ou um compartilhamento de rede—deixe um comentário abaixo. A comunidade (e eu) estamos sempre felizes em ajudar a refinar sua estratégia de avisos de fonte.* 

![exemplo de criação de manipulador de avisos de fonte](image-placeholder.png "exemplo de criação de manipulador de avisos de fonte")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}