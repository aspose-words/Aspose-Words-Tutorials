---
category: general
date: 2026-07-06
description: Ative o modo de recuperação para abrir um arquivo docx corrompido com
  Aspose.Words. Aprenda como recuperar rapidamente um documento Word corrompido.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: pt
og_description: Ativar o modo de recuperação permite abrir um arquivo docx corrompido
  e tentar recuperar um documento Word danificado.
og_title: Ativar modo de recuperação – Recuperar documento Word corrompido
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Ativar modo de recuperação – Recuperar documento Word corrompido
url: /pt/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ativar modo de recuperação – Recuperar documento Word corrompido

Já tentou abrir um **docx corrompido** e viu a caixa de diálogo de erro encarando você? É frustrante, especialmente quando o arquivo contém semanas de trabalho. Felizmente, o Aspose.Words oferece uma forma de *ativar o modo de recuperação* para que você possa tentar salvar o conteúdo sem copiar‑colar manualmente.

Neste guia, percorreremos os passos exatos para **ativar o modo de recuperação**, carregar o arquivo quebrado e salvar uma cópia utilizável. Ao final, você saberá como *recuperar documentos Word corrompidos* programaticamente e até lidar com um cenário de *recuperar arquivo docx danificado* de forma elegante.

## O que você precisará

- .NET 6 (ou qualquer runtime .NET recente) – a biblioteca funciona também no .NET Framework.
- Visual Studio 2022 ou VS Code – seu IDE favorito serve.
- **Aspose.Words for .NET** pacote NuGet (`Install-Package Aspose.Words`) – esta é a única dependência externa.
- Um exemplo de `docx` corrompido (chamaremos de `corrupted.docx`).

É isso. Sem ferramentas extras, sem manipulação manual de XML. Apenas algumas linhas de C#.

![ativar modo de recuperação no Aspose.Words](image-url-placeholder.png)

*Texto alternativo da imagem: ativar modo de recuperação no Aspose.Words*

## Etapa 1: Instalar Aspose.Words e configurar o projeto

Abra seu terminal (ou o Console do Gerenciador de Pacotes) e execute:

```bash
dotnet add package Aspose.Words
```

Alternativamente, no Visual Studio abra **Tools → NuGet Package Manager → Manage NuGet Packages** e procure por *Aspose.Words*. Após a instalação, adicione o namespace no topo do seu arquivo:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Dica profissional:** Mantenha seus pacotes atualizados. A lógica de recuperação melhora a cada versão.

## Etapa 2: Ativar modo de recuperação usando `LoadOptions`

O coração da solução é a classe `LoadOptions`. Ao definir sua propriedade `RecoveryMode` para `RecoveryMode.Recover`, você indica ao Aspose.Words para *ativar o modo de recuperação* ao analisar o documento.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Por que isso importa? Sem o modo de recuperação, o Aspose.Words aborta ao primeiro sinal de corrupção. Com ele, a biblioteca tenta ao máximo pular partes quebradas e ainda produzir um objeto `Document` utilizável.

## Etapa 3: Carregar o arquivo potencialmente corrompido

Agora realmente carregamos o arquivo. Se o documento estiver irremediavelmente danificado, o Aspose.Words ainda retornará uma instância `Document`, porém alguns elementos podem estar ausentes.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Observe que o caminho é uma string absoluta; ajuste‑o para onde seu arquivo de teste está localizado. O construtor `Document` lê o arquivo **com o modo de recuperação ativado**, dando a você a chance de *recuperar o conteúdo de documentos Word corrompidos*.

## Etapa 4: Verificar o que foi recuperado (opcional, mas útil)

É uma boa prática inspecionar o documento carregado antes de decidir sobrescrever algo. Para uma verificação rápida, você pode imprimir os primeiros parágrafos no console:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Se você vir texto embaralhado ou muitas strings vazias, o arquivo pode estar **muito danificado**. Ainda assim, você agora tem um objeto `Document` que pode manipular — adicionar um cabeçalho, substituir imagens ausentes, etc.

## Etapa 5: Salvar o documento recuperado

Assumindo que a verificação de sanidade esteja ok, escreva a versão recuperada em um novo arquivo. Esta etapa efetivamente *recupera o arquivo docx danificado* e fornece uma cópia limpa que você pode abrir no Word.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Se o arquivo original era um `.doc` ou outro formato, você pode mudar `SaveFormat` adequadamente (por exemplo, `SaveFormat.Pdf` para saída PDF).

## Etapa 6: Tratamento de exceções e casos extremos

Mesmo com o modo de recuperação, algumas catástrofes são irrecuperáveis (por exemplo, estruturas zip completamente truncadas). Envolva o carregamento em um bloco try‑catch para expor esses problemas:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

Uma pergunta comum é **“como abrir docx corrompido”** quando o arquivo está protegido por senha. O modo de recuperação **não** contorna a criptografia; você ainda precisará da senha. Nesse caso, defina `LoadOptions.Password` antes de carregar.

## Perguntas Frequentes (FAQ)

**Q: Ativar o modo de recuperação modifica o arquivo original?**  
A: Não. Ele apenas afeta como a biblioteca lê o arquivo na memória. A origem permanece intacta a menos que você chame explicitamente `Save`.

**Q: Posso recuperar imagens que estavam incorporadas no docx corrompido?**  
A: Geralmente sim, desde que a entrada ZIP subjacente não esteja quebrada. Se um fluxo de imagem estiver ausente, o Aspose.Words o pulará e continuará.

**Q: O modo de recuperação é mais lento?**  
A: Um pouco, porque o analisador realiza verificações adicionais. O overhead é insignificante para documentos típicos (<10 MB).

**Q: Quais outras opções de recuperação existem?**  
A: `RecoveryMode.Auto` (padrão) tenta recuperar apenas quando ocorre um erro. `RecoveryMode.None` desabilita quaisquer tentativas de recuperação. `RecoveryMode.Recover` força a tentativa a cada vez.

## Exemplo Completo Funcional

Abaixo está um aplicativo de console autônomo que você pode copiar‑colar em um novo projeto .NET. Ele demonstra todo o fluxo — desde a instalação do pacote até a gravação do arquivo recuperado.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Saída esperada (supondo que a recuperação tenha sucesso):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Se o arquivo estiver irrecuperável, você verá uma mensagem de erro em vez da impressão dos parágrafos.

## Conclusão

Acabamos de mostrar como **ativar o modo de recuperação** no Aspose.Words, carregar um `docx` quebrado e **recuperar dados de documentos Word corrompidos** em um novo arquivo. O mesmo padrão permite *recuperar arquivos docx danificados* em trabalhos em lote, anexos de e‑mail automatizados, ou

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [como recuperar docx – definir modo de recuperação e abrir arquivos Word corrompidos](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [como recuperar docx com Aspose.Words – passo a passo](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Recuperar Arquivo Word Danificado – Guia Completo para Abrir DOCX Corrompido & Obter Página](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}