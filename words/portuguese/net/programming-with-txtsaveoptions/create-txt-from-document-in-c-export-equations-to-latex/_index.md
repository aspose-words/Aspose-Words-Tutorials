---
category: general
date: 2026-06-02
description: Criar txt a partir de documento em C# e salvar texto simples do Word
  enquanto exporta equações em LaTeX usando Aspose.Words – guia passo a passo.
draft: false
keywords:
- create txt from document
- save word plain text
- export equations latex
language: pt
og_description: Crie um arquivo txt a partir de um documento em C# e salve o texto
  simples do Word ao exportar equações em LaTeX usando Aspose.Words – guia completo.
og_title: Criar txt a partir de documento em C# – Exportar equações para LaTeX
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  headline: Create txt from document in C# – Export equations to LaTeX
  type: TechArticle
- description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  name: Create txt from document in C# – Export equations to LaTeX
  steps:
  - name: What if I need **save word plain text** without any LaTeX conversion?
    text: Simply omit the `OfficeMathExportMode` line or set it to `OfficeMathExportMode.Text`.
      The equations will be rendered as plain Unicode characters (e.g., “x = (‑b ±
      √(b²‑4ac)) / 2a”).
  - name: Can I export to other formats (Markdown, HTML) while keeping LaTeX?
    text: Yes. Aspose.Words also supports `MarkdownSaveOptions` and `HtmlSaveOptions`
      with similar `OfficeMathExportMode` settings. Switch the options class, keep
      the `OfficeMathExportMode = OfficeMathExportMode.LaTeX`, and you’ll get LaTeX
      embedded in the target markup.
  - name: How do I handle large documents (hundreds of MB)?
    text: 'Use `LoadOptions` with `LoadFormat.Auto` and consider streaming the output:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LaTeX
title: Criar txt a partir de documento em C# – Exportar equações para LaTeX
url: /pt/net/programming-with-txtsaveoptions/create-txt-from-document-in-c-export-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar txt a partir de documento em C# – Exportar equações para LaTeX

Já se perguntou como **criar txt a partir de documento** sem perder a matemática que você passou horas digitando? Você não está sozinho. Em muitos pipelines de relatório você precisa de uma versão em texto simples de um arquivo Word, mas ainda quer que as equações sejam renderizadas como LaTeX para que ferramentas subsequentes possam processá‑las.  

Neste tutorial vamos percorrer os passos exatos para **salvar texto simples do Word** enquanto **exporta equações para LaTeX** usando a poderosa biblioteca Aspose.Words para .NET. Ao final, você terá um trecho pronto‑para‑executar que pode inserir em qualquer projeto C#.

## O que você aprenderá

- Instalar e referenciar Aspose.Words em um projeto .NET.  
- Carregar um `.docx` que contém objetos OfficeMath.  
- Configurar `TxtSaveOptions` para que o exportador gere LaTeX para cada equação.  
- Gravar o arquivo de texto simples resultante no disco.  
- Verificar se as equações aparecem como marcação LaTeX dentro do `.txt`.

Nenhuma experiência prévia com Aspose é necessária; basta um conhecimento básico de C# e Visual Studio.

---

## Pré‑requisitos

| Requisito | Por que importa |
|-----------|-----------------|
| .NET 6.0 ou posterior | Recursos de linguagem modernos e melhor desempenho |
| Visual Studio 2022 (ou VS Code) | Depuração conveniente e estruturação de projetos |
| Aspose.Words for .NET (NuGet) | A biblioteca que lida com a conversão OfficeMath → LaTeX |
| Um documento Word contendo equações | Para ver a exportação LaTeX em ação |

Se algum desses estiver faltando, pause agora e instale‑os — caso contrário o código não compilará.

---

## Etapa 1 – Instalar Aspose.Words via NuGet

Para começar, abra sua solução, clique com o botão direito no projeto e escolha **Manage NuGet Packages**. Procure por **Aspose.Words** e clique em **Install**.  

Ou, se preferir a linha de comando, execute:

```powershell
dotnet add package Aspose.Words
```

> **Dica profissional:** Use a versão estável mais recente; a partir de junho 2026 é **23.9.0**. Isso garante que você obtenha as melhorias mais recentes na exportação de OfficeMath.

---

## Etapa 2 – Carregar o Documento Word de Origem

Agora precisamos de um objeto `Document` que represente o `.docx` que você deseja converter. O trecho a seguir assume que o arquivo está em uma pasta chamada `Input`.

```csharp
using Aspose.Words;

// Load the Word file (change the path as needed)
Document doc = new Document(@"Input\sample_with_equations.docx");

// Quick sanity check – how many OfficeMath objects do we have?
int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
Console.WriteLine($"Found {equationCount} equation(s) to export.");
```

A chamada `GetChildNodes` é opcional, mas útil; ela indica se o documento realmente contém equações antes que você perca tempo exportando.

---

## Etapa 3 – Configurar TxtSaveOptions para **exportar equações latex**

Aqui está o ponto central. `TxtSaveOptions` permite ajustar como o texto simples é gerado. Definir `OfficeMathExportMode` como `LaTeX` indica ao Aspose que substitua cada objeto OfficeMath por sua representação LaTeX.

```csharp
using Aspose.Words.Saving;

// Step 3: Configure TXT save options to export OfficeMath as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This flag converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: Preserve line breaks exactly as they appear in Word.
    PreserveTableLayout = true
};
```

Por que se preocupar com `PreserveTableLayout`? Se seu documento mistura equações dentro de tabelas, essa flag mantém o alinhamento visual quando você visualizar o `.txt` posteriormente. Não é obrigatório, mas a maioria dos relatórios reais se beneficia disso.

---

## Etapa 4 – **Salvar texto simples do Word** usando as opções configuradas

Com as opções prontas, a gravação real é feita em uma única linha. Vamos gravar a saída em uma pasta `Output`.

```csharp
// Step 4: Save the document as a plain‑text file using the configured options
string outputPath = @"Output\exported.txt";
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved as plain text at: {outputPath}");
```

Quando você abrir `exported.txt`, verá parágrafos normais intercalados com fragmentos LaTeX como `\int_{0}^{\infty} e^{-x} dx`. O restante do conteúdo permanece intacto, proporcionando uma experiência real de **criar txt a partir de documento**.

---

## Etapa 5 – Verificar o Resultado (e uma dica rápida para depuração)

Abra o arquivo gerado em qualquer editor de texto. Você deve ver algo semelhante a:

```
This is a sample report.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another paragraph follows...
```

Se os trechos LaTeX estiverem ausentes, verifique se o documento de origem realmente contém objetos `OfficeMath` e se você referenciou a versão correta do Aspose. Também, assegure que a propriedade `OfficeMathExportMode` não foi sobrescrita em outro lugar no seu código.

---

## Perguntas Frequentes & Casos Limite

### E se eu precisar **salvar texto simples do Word** sem nenhuma conversão para LaTeX?

Basta omitir a linha `OfficeMathExportMode` ou defini‑la como `OfficeMathExportMode.Text`. As equações serão renderizadas como caracteres Unicode simples (por exemplo, “x = (‑b ± √(b²‑4ac)) / 2a”).

### Posso exportar para outros formatos (Markdown, HTML) mantendo LaTeX?

Sim. Aspose.Words também suporta `MarkdownSaveOptions` e `HtmlSaveOptions` com configurações semelhantes de `OfficeMathExportMode`. Troque a classe de opções, mantenha `OfficeMathExportMode = OfficeMathExportMode.LaTeX`, e você obterá LaTeX incorporado na marcação de destino.

### Como lidar com documentos grandes (centenas de MB)?

Use `LoadOptions` com `LoadFormat.Auto` e considere transmitir a saída:

```csharp
using (FileStream fs = new FileStream(outputPath, FileMode.Create))
{
    doc.Save(fs, txtOptions);
}
```

A transmissão reduz a pressão de memória e acelera o pipeline de **criar txt a partir de documento**.

---

## Exemplo Completo (Pronto para Copiar‑Colar)

Abaixo está o programa completo que você pode compilar e executar imediatamente. Ele reúne todas as etapas anteriores em um único método `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        string inputPath = @"Input\sample_with_equations.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Optional sanity check – count equations
        int eqCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
        Console.WriteLine($"Found {eqCount} equation(s).");

        // 3️⃣ Configure TxtSaveOptions to export equations as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true
        };

        // 4️⃣ Save as plain‑text file
        string outputPath = @"Output\exported.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Finished! Plain‑text saved to: {outputPath}");
    }
}
```

**Saída esperada no console:**

```
Found 3 equation(s).
✅ Finished! Plain‑text saved to: Output\exported.txt
```

Abra `exported.txt` e você verá os trechos LaTeX intercalados com texto regular — exatamente o que o requisito de **criar txt a partir de documento** pedia.

---

## Conclusão

Acabamos de demonstrar como **criar txt a partir de documento** em C# enquanto, de forma responsável, **salva texto simples do Word** e **exporta equações latex** usando Aspose.Words. O principal aprendizado? Algumas linhas de configuração (`TxtSaveOptions`) desbloqueiam a capacidade de manter a fidelidade matemática mesmo em um arquivo `.txt` simplificado.

A partir daqui você pode:

- Inserir o `.txt` gerado em um gerador de site estático que entende LaTeX.  
- Alimentá‑lo a um pipeline de publicação científica que espera marcação LaTeX bruta.  
- Estender o código para processar em lote dezenas de arquivos Word automaticamente.

Qualquer que seja o próximo passo, agora você tem uma base sólida e digna de citação. Tem mais perguntas? Deixe um comentário, e feliz codificação!  

![Create txt from document example](/images/create-txt-from-document.png "Screenshot showing the exported txt with LaTeX equations – create txt from document")

---

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos estreitamente relacionados que se baseiam nas técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens de implementação alternativas em seus próprios projetos.

- [Salvar Documento como Txt – Exportar Matemática do Word para LaTeX em C#](/words/english/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/)
- [Salvar docx como txt – Exportar Matemática do Word para LaTeX com C#](/words/english/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-with-c/)
- [Salvar Documento como TXT – Guia Completo em C# para Converter DOCX em Texto Simples](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}