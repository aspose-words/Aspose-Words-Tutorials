---
category: general
date: 2026-10-13
description: Aprenda substituição de fontes em documentos usando C#. Este guia mostra
  como definir a codificação big5, carregar um DOCX e substituir fontes legadas por
  fontes modernas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: pt
lastmod: 2026-10-13
og_description: A substituição de fontes em documentos é essencial ao trabalhar com
  arquivos chineses legados. Siga este tutorial passo a passo para carregar um DOCX
  com codificação big5 e substituir fontes antigas.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Substituição de fontes em documento com C# – guia completo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Como realizar substituição de fonte em documento com C#
url: /pt/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substituição de fonte em documento – tutorial completo em C#

Se você precisa de **substituição de fonte em documento** para renderizar arquivos chineses legados corretamente, este guia mostra exatamente como fazer isso. Ao configurar a codificação de texto correta e trocar uma fonte desatualizada por uma moderna, você garante que o DOCX final seja exibido como esperado.

O processamento de documentos costuma falhar quando a origem usa uma codificação antiga como **big5** ou faz referência a uma fonte que não existe mais no sistema. Este tutorial orienta você a carregar um DOCX com a **codificação big5** correta, aplicar **substituição de fonte legada** e gerar uma saída limpa que funciona em qualquer máquina Windows.

Você aprenderá:

* Como criar um objeto `LoadOptions` com **codificação big5**.  
* Como abrir um arquivo DOCX usando **C# LoadOptions**.  
* Como executar **substituição de fonte em documento** mapeando uma fonte antiga para um equivalente moderno.  
* Tratamento de casos extremos para fontes ausentes e múltiplas famílias de fontes.

Nenhuma ferramenta externa é necessária além da biblioteca Aspose.Words for .NET, e o código completo pode ser copiado para um projeto de console e executado imediatamente.

## Pré‑requisitos

* .NET 6.0 ou superior (o exemplo usa a sintaxe de console do .NET 6).  
* Aspose.Words for .NET – instale via `dotnet add package Aspose.Words`.  
* Um arquivo DOCX salvo com **codificação big5** que faça referência à fonte legada `MingLiU-ExtB`.  
* Familiaridade básica com C# e Visual Studio ou qualquer IDE de sua escolha.

## Etapa 1: Configurar o projeto e importar namespaces

Crie um novo aplicativo de console e adicione as diretivas `using` necessárias. Isso garante que o código compile sem modificações extras.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Dica profissional:** Mantenha o método `Main` o mais enxuto possível; isso melhora a legibilidade e facilita o acompanhamento do tutorial.

## Etapa 2: Definir opções de carregamento com a codificação de texto correta (big5 para Chinês Tradicional)

A classe `LoadOptions` informa ao Aspose.Words como interpretar os bytes brutos no arquivo de origem. Usar **codificação big5** é essencial para caracteres chineses tradicionais que foram salvos com essa página de código legada.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Por que isso importa:** Se você omitir a codificação ou usar o padrão UTF‑8, os caracteres podem aparecer como símbolos corrompidos (mojibake). Especificar `big5` preserva os glifos originais antes de qualquer substituição de fonte.

## Etapa 3: Carregar o arquivo DOCX usando a codificação especificada

Passe a instância `loadOptions` ao construtor `Document`. Isso carrega o arquivo respeitando a **codificação do documento para Chinês** que você definiu anteriormente.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Se o arquivo não for encontrado, o programa lançará uma `FileNotFoundException`. Verifique se o caminho está correto e se a aplicação tem permissão de leitura.

## Etapa 4: Substituir uma fonte legada por um equivalente moderno

Muitos documentos chineses antigos referenciam `MingLiU-ExtB`, que pode não estar presente em instalações mais recentes do Windows. Mapeá‑la para `Microsoft JhengHei` (uma fonte Unicode amplamente disponível) garante a renderização correta.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explicação:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registra uma regra global de substituição. Sempre que o Aspose.Words encontrar `MingLiU-ExtB`, ele a trocará por `Microsoft JhengHei`.  
* O loop opcional imprime o mapeamento, o que é útil para depuração em documentos grandes com várias famílias de fontes.

## Etapa 5: Salvar o documento processado

Após a substituição, grave o documento em um novo arquivo. A saída exibirá o texto chinês usando a fonte moderna, eliminando avisos de glifos ausentes.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Abra o arquivo resultante no Microsoft Word ou em qualquer visualizador de DOCX; você deverá ver os caracteres chineses tradicionais renderizados corretamente com `Microsoft JhengHei`.

## Tratamento de casos extremos e armadilhas comuns

| Situação | Abordagem recomendada |
|-----------|----------------------|
| **A fonte de origem não está listada no documento** | Use `doc.FontInfos.Substitution.Add` com um padrão curinga, por exemplo `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Várias fontes legadas precisam ser substituídas** | Chame `Add` para cada par, ou carregue um dicionário de substituição a partir de um arquivo de configuração. |
| **A fonte de destino não está disponível na máquina de destino** | Escolha uma fonte que venha com o Windows (por exemplo, `Arial Unicode MS`) ou incorpore a fonte usando `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Erros de codificação ainda aparecem** | Verifique se o arquivo de origem realmente usa **big5**; você pode inspecioná‑lo com um editor hexadecimal ou usar `File.ReadAllBytes` e comparar padrões de bytes. |

## Exemplo completo em funcionamento

Abaixo está o programa completo e autocontido. Copie‑o para `Program.cs`, ajuste os caminhos dos arquivos e execute.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Resultado esperado:** Ao abrir `big5_doc_fixed.docx` todos os caracteres chineses tradicionais são exibidos corretamente, sem avisos de glifos ausentes, porque `MingLiU-ExtB` foi substituída por `Microsoft JhengHei`.

## Conclusão

Agora você tem um método confiável para tarefas de **substituição de fonte em documento** usando C#. Ao configurar a **codificação big5**, carregar o DOCX com `LoadOptions` e mapear fontes legadas para equivalentes modernos, você elimina problemas de renderização que afetam arquivos chineses antigos.  

A partir daqui você pode:

* Expandir o mapa de substituição para cobrir fontes legadas adicionais.  
* Automatizar o processo para lotes de documentos (percorrer um diretório).  
* Combinar substituição de fonte com outras transformações de documento, como marca d'água ou conversão para PDF.

Sinta‑se à vontade para experimentar diferentes fontes de destino ou incorporar fontes personalizadas para total portabilidade. Se encontrar algum problema, revise a tabela de casos extremos acima ou consulte a documentação do Aspose.Words para tratamento avançado de fontes.

Happy coding!


## O que você deve aprender a seguir?


Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}