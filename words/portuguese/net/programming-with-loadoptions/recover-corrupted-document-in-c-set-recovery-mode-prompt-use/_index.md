---
category: general
date: 2026-01-11
description: Recupere documentos corrompidos em C# usando Aspose.Words. Aprenda como
  definir o modo de recuperação, carregar arquivos docx com recuperação e notificar
  o usuário em caso de erro em alguns passos simples.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: pt
og_description: Recupere documento corrompido em C# definindo o modo de recuperação,
  carregando um DOCX com recuperação e solicitando ao usuário em caso de erro. Tutorial
  completo passo a passo.
og_title: Recuperar Documento Corrompido em C# – Guia Rápido
tags:
- Aspose.Words
- C#
- Document Recovery
title: Recuperar Documento Corrompido em C# – Definir Modo de Recuperação e Solicitar
  ao Usuário
url: /pt/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recuperar Documento Corrompido em C# – Guia Completo

Já tentou abrir um DOCX que parece estar bem no Word, mas lança uma exceção no seu código? Você provavelmente está lidando com um cenário de **recuperar documento corrompido**. A boa notícia é que o Aspose.Words oferece controle detalhado sobre como lidar com esses arquivos problemáticos — seja para corrigi‑los silenciosamente, lançar uma exceção ou perguntar ao usuário o que fazer.

Neste tutorial vamos percorrer tudo o que você precisa para **recuperar documentos corrompidos**, desde a instalação da biblioteca até a escolha da opção correta de **definir modo de recuperação**, **carregar docx com recuperação**, e finalmente **solicitar ao usuário em caso de erro** quando algo der errado. Sem enrolação, apenas um exemplo completo e executável que você pode inserir em qualquer projeto .NET.

> **Pré‑visualização rápida:** Ao final você terá um aplicativo console que carrega um `corrupt.docx` possivelmente quebrado, registra quaisquer avisos e pergunta ao usuário se ele deseja continuar quando a recuperação falhar.

---

## O Que Você Precisa

- **.NET 6.0** ou superior (o código também funciona no .NET Framework 4.6+).  
- **Aspose.Words for .NET** – instale via NuGet (`Install-Package Aspose.Words`).  
- Um arquivo **DOCX corrompido** para teste (você pode danificar deliberadamente um arquivo abrindo‑o em um editor hexadecimal ou renomeando sua extensão).  
- Qualquer IDE de sua preferência — Visual Studio, Rider ou até mesmo VS Code serve.

> *Dica de especialista:* Mantenha um backup do arquivo original. A recuperação pode reescrever partes do documento, e você não quer perder os trechos bons.

---

## Etapa 1 – Instalar Aspose.Words e Adicionar Namespaces

Primeiro passo. Baixe a biblioteca do NuGet e traga os namespaces necessários para o escopo.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

É tudo que você precisa para o restante do guia. O namespace `Aspose.Words.Loading` contém a classe `LoadOptions`, que é a chave para **definir modo de recuperação**.

---

## Etapa 2 – Escolher um Modo de Recuperação (Primary H2 with Keyword)

### Recuperar Documento Corrompido – Definindo o Modo de Recuperação Correto

Aspose.Words oferece três comportamentos de recuperação:

| Modo | O Que Acontece | Quando Usar |
|------|----------------|-------------|
| **PromptUser** | Exibe um diálogo (ou você pode implementar seu próprio prompt) e tenta corrigir o arquivo. | Ideal para ferramentas interativas onde o usuário pode decidir. |
| **Silent** | Tenta corrigir automaticamente, sem UI. | Bom para jobs em lote ou serviços. |
| **ThrowException** | Interrompe o processamento e lança uma exceção. | Use quando precisar de validação estrita. |

Abaixo está como você **define o modo de recuperação** para `PromptUser`. Se preferir tratamento silencioso, basta trocar o valor do enum.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Por que isso importa:** Ao **definir modo de recuperação** explicitamente, você informa ao Aspose.Words quão agressiva deve ser a correção. O padrão é `PromptUser`, mas ser explícito deixa sua intenção cristalina — tanto para futuros mantenedores quanto para mecanismos de busca que analisam o código.

---

## Etapa 3 – Carregar o DOCX com Recuperação

Agora vamos **carregar docx com recuperação** usando o `LoadOptions` que acabamos de configurar. Se o arquivo estiver danificado, o Aspose.Words irá repará‑lo ou gerar um aviso, dependendo do modo.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

O construtor `Document` faz o trabalho pesado. No modo **PromptUser**, você verá um prompt no console (ou uma UI personalizada se conectar aos eventos de `LoadOptions`) perguntando se deve continuar. No modo **Silent**, o método simplesmente tenta ao máximo e segue em frente.

---

## Etapa 4 – Inspecionar Avisos e Solicitar ao Usuário

Aspose.Words registra quaisquer problemas encontrados na coleção `Warnings`. Vamos iterar sobre eles e dar ao usuário a chance de decidir o que fazer a seguir.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

O trecho acima **solicita ao usuário em caso de erro** de forma amigável ao console. Se você estiver construindo um aplicativo Windows Forms ou WPF, troque o `Console.ReadLine` por um `MessageBox` ou diálogo customizado.

---

## Etapa 5 – Trabalhar com o Documento Recuperado

Neste ponto o documento está na memória, reparado o melhor que o Aspose.Words conseguiu. Você pode ler seu conteúdo, salvar uma cópia limpa ou executar qualquer manipulação necessária.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Executar o programa completo contra um arquivo quebrado produzirá uma saída no console semelhante a esta:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Se o arquivo estiver realmente íntegro, você verá “Document loaded without any warnings.” e a cópia limpa será idêntica à origem.

---

## Exemplo Completo Funcional

Aqui está o programa inteiro em um só lugar. Copie‑e‑cole em um novo projeto console e pressione **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Execute, corrompa um arquivo de teste e observe a recuperação em ação. 🎉

---

## Casos de Borda & Variações

| Cenário | O Que Alterar | Por quê |
|----------|----------------|---------|
| **Processamento em lote** (sem interação) | Defina `RecoveryMode = RecoveryMode.Silent` e remova o prompt do console. | Mantém o pipeline avançando automaticamente. |
| **Validação estrita** (falha rápida) | Use `RecoveryMode.ThrowException`. Envolva a chamada de carregamento em try/catch e registre a exceção. | Garante que você nunca trabalhe com um arquivo parcialmente reparado. |
| **UI customizada** (WinForms/WPF) | Assine `LoadOptions.LoadingProgress` ou use eventos de `Document.LoadOptions` para exibir um diálogo. | Oferece uma experiência mais rica que o console. |
| **Documentos grandes** (restrições de memória) | Carregue com `LoadOptions.LoadFormat = LoadFormat.Docx` e considere `Document.SaveOptions` para streaming de saída. | Evita exceções OutOfMemory. |

---

## Dicas Práticas (Sinais E‑E‑A‑T)

- **Sempre mantenha um backup** antes de tentar a recuperação; o processo pode sobrescrever partes do arquivo.  
- **Registre avisos** em um arquivo para análise posterior; eles costumam indicar a causa raiz (ex.: partes ausentes, XML corrompido).  
- **Teste com múltiplos tipos de corrupção** – trunque o arquivo, corrompa tags XML ou altere a estrutura zip para ver como cada modo se comporta.  
- **Atualize o Aspose.Words regularmente**; versões mais recentes aprimoram os algoritmos de recuperação e adicionam novos tipos de aviso.  
- **Combine com validação** – após a recuperação, execute rapidamente `document.UpdateFields()` e `document.Save()` para garantir que o documento esteja totalmente funcional.

---

## Conclusão

Agora você sabe como **recuperar documentos corrompidos** em C# usando **definir modo de recuperação**, **carregar docx com recuperação** e **solicitar ao usuário em caso de erro** quando algo dá errado. O exemplo completo demonstra um fluxo limpo, de ponta a ponta, que funciona em aplicativos console, serviços ou projetos UI.

Próximos passos? Experimente substituir o prompt do console por um diálogo modal em um app WinForms, teste o modo **Silent** para jobs em segundo plano, ou integre a lógica de recuperação em um endpoint de upload ASP.NET para que usuários possam enviar DOCX quebrados e receber uma versão reparada instantaneamente.

Happy coding, and may your documents stay whole!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}