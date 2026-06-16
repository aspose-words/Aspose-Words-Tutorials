---
category: general
date: 2026-06-08
description: Abra um arquivo Word corrompido em C# usando Aspose.Words. Aprenda como
  definir o modo de recuperação e recuperar o documento corrompido de forma eficiente.
draft: false
keywords:
- open corrupted word file
- set recovery mode
- recover corrupted document
- Aspose.Words recovery
- handling damaged docx
language: pt
og_description: Abra um arquivo Word corrompido em C# com Aspose.Words. Este guia
  mostra como definir o modo de recuperação e recuperar o documento corrompido com
  segurança.
og_title: Abrir arquivo Word corrompido em C# – Guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  headline: Open Corrupted Word File in C# – Complete Guide
  type: TechArticle
- description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  name: Open Corrupted Word File in C# – Complete Guide
  steps:
  - name: '**Create `LoadOptions`** – decide how strict the loader should be.'
    text: '**Create `LoadOptions`** – decide how strict the loader should be.'
  - name: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
    text: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
  - name: '**Load the document** – give the path and the options you just built.'
    text: '**Load the document** – give the path and the options you just built.'
  - name: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
    text: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
  type: HowTo
tags:
- C#
- Aspose.Words
- Document Recovery
title: Abrir arquivo Word corrompido em C# – Guia completo
url: /pt/net/programming-with-loadoptions/open-corrupted-word-file-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abrir Arquivo Word Corrompido em C# – Guia Completo

Já precisou **abrir um arquivo Word corrompido** em um projeto .NET e se perguntou se o arquivo está irrecuperável? Você não é o primeiro – a corrupção de documentos aparece mais vezes do que se imagina, especialmente quando os arquivos trafegam por redes instáveis ou são editados por versões antigas do Office.  

A boa notícia? Com Aspose.Words você pode **definir o modo de recuperação** para dizer à biblioteca exatamente como se comportar, e ainda pode **recuperar o conteúdo de documentos corrompidos** sem escrever um analisador personalizado. Neste tutorial vamos percorrer cada passo, desde a configuração das opções até a verificação de que o arquivo foi aberto corretamente.

> **O que você vai aprender**  
> • Um trecho de código C# que abre qualquer .docx, mesmo um quebrado.  
> • Entendimento dos três valores de `RecoveryMode` e quando usar cada um.  
> • Dicas para tratar exceções, testar o resultado e, opcionalmente, salvar uma cópia limpa.

## Como Abrir Arquivo Word Corrompido com Aspose.Words

Abaixo está uma visão de alto nível do fluxo.  
![Diagram illustrating open corrupted word file process](/images/open-corrupted-word-file-flow.png){: .center alt="diagrama de fluxo de abertura de arquivo Word corrompido"}

1. **Criar `LoadOptions`** – decida o quão rigoroso o carregador deve ser.  
2. **Escolher um `RecoveryMode`** – *Passthrough* para carregamento bruto, *Recover* para correção automática ou *Throw* para capturar problemas imediatamente.  
3. **Carregar o documento** – forneça o caminho e as opções que você acabou de criar.  
4. **Validar** – verifique se a árvore do documento não está vazia, opcionalmente salvando uma cópia reparada.

Vamos mergulhar em cada parte.

## Entendendo os Modos de Recuperação

Aspose.Words define três comportamentos distintos:

| Modo | O que faz | Quando usar |
|------|-----------|-------------|
| `RecoveryMode.Recover` | Tenta corrigir problemas estruturais, partes ausentes ou XML malformado. Este é o **padrão** e funciona na maioria das corrupções menores. | Você quer uma reparação de melhor esforço sem intervenção manual. |
| `RecoveryMode.Passthrough` | Carrega o arquivo **exatamente** como está, mesmo que contenha partes quebradas. Nenhum ajuste automático é aplicado. | Você precisa inspecionar o conteúdo bruto ou planeja aplicar lógica de recuperação personalizada depois. |
| `RecoveryMode.Throw` | Lança imediatamente uma exceção se qualquer problema for detectado. | Você prefere uma abordagem fail‑fast para rejeitar arquivos danificados de imediato. |

Escolher o modo correto é a essência de **definir o modo de recuperação** adequadamente. A maioria dos desenvolvedores começa com `Recover`, mas se você estiver depurando um arquivo teimoso, `Passthrough` pode dar visibilidade sobre o que deu errado.

## Passo a Passo: Definir o Modo de Recuperação

Abaixo está o primeiro bloco de código que você colará em um novo aplicativo console ou em qualquer projeto C# que já referencie `Aspose.Words`.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and choose a recovery behavior
LoadOptions loadOptions = new LoadOptions
{
    // Choose the desired recovery behavior:
    //   RecoveryMode.Recover      – attempt to fix the file (default)
    //   RecoveryMode.Passthrough – load the file exactly as it is
    //   RecoveryMode.Throw       – throw an exception if the file is damaged
    RecoveryMode = RecoveryMode.Passthrough   // <-- we are explicitly setting it
};
```

**Por que isso importa:** Ao atribuir explicitamente `RecoveryMode.Passthrough`, estamos dizendo ao Aspose.Words **definir o modo de recuperação** para um valor não‑padrão. Isso elimina suposições e deixa a intenção cristalina para futuros mantenedores.

> **Dica de especialista:** Se precisar voltar ao caminho de reparo automático, basta mudar o enum para `RecoveryMode.Recover` e executar novamente – nenhuma outra alteração de código é necessária.

## Carregando o Documento com Segurança

Agora que as opções estão prontas, o próximo passo é realmente **abrir um arquivo Word corrompido**. O trecho a seguir demonstra o processo de carregamento e inclui uma pequena verificação de sanidade.

```csharp
// Step 2: Load the possibly‑corrupted document using the configured options
try
{
    // Replace the path with the location of your damaged DOCX
    Document doc = new Document(@"C:\Temp\Corrupted.docx", loadOptions);

    // Quick validation – make sure the document contains at least one section
    if (doc.Sections.Count == 0)
    {
        Console.WriteLine("The document appears empty after loading. It may be severely corrupted.");
    }
    else
    {
        Console.WriteLine($"Successfully opened the file. Sections found: {doc.Sections.Count}");
    }
}
catch (Exception ex)
{
    // If you used RecoveryMode.Throw, you'll land here for any problem.
    Console.WriteLine($"Failed to open the file: {ex.Message}");
}
```

**Explicação:**  
* O bloco `try/catch` nos protege contra o modo `Throw`, mas também serve como rede de segurança para erros inesperados de I/O.  
* Após o carregamento, inspecionamos `doc.Sections.Count`. Uma contagem zero é um forte indicativo de que o arquivo não recuperou conteúdo significativo – perfeito para confirmar se **recuperar documento corrompido** realmente teve sucesso.

## Tratando Exceções e Verificando a Recuperação

Mesmo com `Passthrough`, a biblioteca ainda pode lançar uma exceção se o pacote ZIP subjacente for ilegível. Veja como diferenciar entre um problema *recuperável* e um *fatal*:

```csharp
catch (CorruptedFileException cfe)
{
    // This exception means the file's internal structure is broken.
    Console.WriteLine("CorruptedFileException caught – the file cannot be read at all.");
}
catch (Exception ex)
{
    // Any other exception (e.g., FileNotFound, UnauthorizedAccess)
    Console.WriteLine($"General error: {ex.GetType().Name} – {ex.Message}");
}
```

Se você encontrar uma `CorruptedFileException`, talvez queira recorrer a outra estratégia de recuperação, como:

* Tentar `RecoveryMode.Recover` em vez de `Passthrough`.  
* Usar uma ferramenta de reparo de ZIP de terceiros antes de passar o arquivo ao Aspose.Words.  
* Solicitar ao usuário que faça upload de uma nova cópia.

## Bônus: Salvando um Documento Reparado

Depois de **recuperar o conteúdo de um documento corrompido**, costuma‑se querer persistir uma versão limpa. O código a seguir grava o arquivo reparado em um novo local:

```csharp
// Assuming 'doc' was loaded successfully
string outputPath = @"C:\Temp\Repaired.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Repaired document saved to: {outputPath}");
```

Salvar também funciona como uma verificação implícita – se `doc.Save` lançar, ainda há algo errado na árvore interna de nós.

## Dicas para Cenários de Recuperação de Documentos Corrompidos

| Situação | Ação Recomendada |
|----------|-------------------|
| Pequeno erro de XML (ex.: tag de fechamento ausente) | Mantenha `RecoveryMode.Recover`; Aspose.Words corrigirá automaticamente. |
| Arquivo ZIP completamente quebrado | Use reparo externo de ZIP, depois carregue com `Passthrough`. |
| Modo misto (algumas partes boas, outras quebradas) | Carregue com `Passthrough`, inspecione os nós problemáticos e remova ou substitua manualmente. |
| Corrupção frequente de uma fonte específica | Automatize uma pré‑verificação que execute `RecoveryMode.Recover` e registre quaisquer `CorruptedFileException`. |

Lembre‑se, **definir o modo de recuperação** não é uma varinha mágica – entender a natureza da corrupção ajuda a escolher a estratégia correta.

## Exemplo Completo Funcional

Juntando tudo, aqui está um aplicativo console autônomo que você pode colar em `Program.cs` e executar imediatamente (depois de adicionar o pacote NuGet Aspose.Words).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace OpenCorruptedWordFileDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure load options – we explicitly set the recovery mode.
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Passthrough // change to Recover if you prefer auto‑fix
            };

            // 2️⃣ Attempt to load the possibly damaged DOCX.
            string sourcePath = @"C:\Temp\Corrupted.docx";
            Document doc = null;

            try
            {
                doc = new Document(sourcePath, loadOptions);
                Console.WriteLine($"File loaded. Sections: {doc.Sections.Count}");
            }
            catch (CorruptedFileException)
            {
                Console.WriteLine("The file is too damaged to be opened even in Passthrough mode.");
                return;
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
                return;
            }

            // 3️⃣ Simple verification – ensure we have at least one paragraph.
            if (doc.GetChildNodes(NodeType.Paragraph, true).Count == 0)
            {
                Console.WriteLine("No paragraphs were recovered – the document may be empty.");
            }
            else
            {
                Console.WriteLine("Paragraphs recovered – the document appears usable.");
            }

            // 4️⃣ Optionally save a clean copy.
            string cleanPath = @"C:\Temp\Repaired.docx";
            doc.Save(cleanPath, SaveFormat.Docx);
            Console.WriteLine($"Clean copy saved to: {cleanPath}");
        }
    }
}
```

**Saída esperada (quando o arquivo pode ser aberto):**



## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [como recuperar docx – definir modo de recuperação & abrir arquivos Word corrompidos](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Recuperar Arquivo Word Danificado – Guia Completo para Abrir DOCX Corrompido & Obter Página](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)
- [Recuperar Documento Word com Aspose.Words em C#](/words/english/net/programming-with-loadoptions/recover-word-document-with-aspose-words-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}