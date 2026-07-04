---
category: general
date: 2026-06-02
description: Substitua texto em docx usando C#. Aprenda como substituir todas as ocorrências
  de palavras, realizar busca e substituição em documentos Word e domine como substituir
  texto em C# de forma eficiente.
draft: false
keywords:
- replace text in docx
- replace all occurrences word
- find and replace word document
- how to replace text c#
language: pt
og_description: Substitua texto em docx usando C#. Este tutorial mostra como substituir
  todas as ocorrências de uma palavra e realizar busca e substituição em documentos
  Word com exemplos de código claros.
og_title: Substitua texto em docx com C# – Guia Completo de Programação
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  headline: Replace text in docx with C# – Full Step‑by‑Step Guide
  type: TechArticle
- description: Replace text in docx using C#. Learn how to replace all occurrences
    word, perform find and replace word document, and master how to replace text c#
    efficiently.
  name: Replace text in docx with C# – Full Step‑by‑Step Guide
  steps:
  - name: 1. Case‑Insensitive Replacement
    text: 'If you need to ignore case (e.g., replace “Foo”, “FOO”, and “foo” alike),
      tweak the regex options:'
  - name: 2. Replacing Whole Words Only
    text: 'Sometimes “foo” appears inside another word like “food”. To avoid accidental
      changes, anchor the pattern with word boundaries:'
  - name: 3. Using a Callback for Conditional Replacement
    text: Aspose lets you supply a delegate to decide on‑the‑fly whether to replace
      a match. This is handy for scenarios like “replace only if the word is in a
      table”.
  - name: 4. Handling Large Documents Efficiently
    text: For multi‑gigabyte files, consider processing the document in chunks (e.g.,
      per section) to keep memory usage low. Aspose provides `Section` collections
      you can iterate over and call `Replace` on each individually.
  - name: 5. Preserving Formatting
    text: 'The replacement text inherits the formatting of the first character of
      the match. If you need to enforce a specific style (e.g., bold), apply it after
      the replacement:'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words treats `.doc` and `.docx` uniformly. Just change the
      file extension in the load/save paths.
    question: Does this work with `.doc` files?
  - answer: You’ll need to unprotect the document first (`doc.Protect(ProtectionType.NoProtection,
      "password")`) or supply the password when loading.
    question: What if the document contains protected sections?
  - answer: Absolutely. Use `new LoadOptions { Password = "yourPassword" }` when constructing
      the `Document`.
    question: Can I replace text in a password‑protected file?
  - answer: 'The Open XML SDK can perform find/replace, but it lacks the high‑level
      `Range.Replace` convenience and requires more boilerplate. For production‑grade
      reliability, Aspose remains the recommended choice. --- ## Next Steps & Related
      Topics Now that you’ve mastered **replace text in docx**, you might w'
    question: Is there a free alternative to Aspose.Words?
  type: FAQPage
tags:
- C#
- Word Automation
- FindReplace
title: Substitua texto em docx com C# – Guia completo passo a passo
url: /pt/net/find-and-replace-text/replace-text-in-docx-with-c-full-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substitua texto em docx com C# – Guia Completo Passo a Passo

Já precisou substituir texto em arquivos docx mas não sabia por onde começar? Você não está sozinho. Seja limpando um lote de contratos ou gerando cartas personalizadas automaticamente, aprender **replace text in docx** com C# pode economizar horas de edição manual.

Neste guia vamos percorrer uma solução completa, pronta‑para‑executar, que mostra como substituir todas as ocorrências de palavra, realizar uma busca e substituição robusta em documentos Word e responder de uma vez por todas à pergunta “how to replace text c#”. Sem referências vagas — apenas código sólido, explicações claras e algumas dicas profissionais que você gostaria de ter sabido antes.

## O que você vai precisar

Antes de mergulharmos, certifique‑se de que tem o seguinte:

- **.NET 6.0** ou superior (o exemplo também funciona com .NET Framework 4.6+).  
- **Aspose.Words for .NET** (ou qualquer biblioteca comparável que suporte `FindReplaceOptions`). Você pode obtê‑la via NuGet com `Install-Package Aspose.Words`.  
- Um entendimento básico da sintaxe C# — nada sofisticado, apenas as declarações `using` habituais e o método `Main`.  
- Um arquivo **.docx** de entrada colocado em uma pasta que você possa referenciar (vamos chamá‑lo de `YOUR_DIRECTORY/input.docx`).  

É isso. Nenhum arquivo de configuração extra, sem interop COM, e absolutamente sem necessidade de iniciar o Microsoft Office no servidor.

> **Pro tip:** Se você estiver em um pipeline CI/CD, fixe a versão do Aspose.Words no seu `csproj` para evitar alterações inesperadas.

## Etapa 1 – Carregar o Documento Fonte

A primeira coisa que fazemos é carregar o arquivo Word na memória. Pense nisso como abrir um caderno; a biblioteca nos fornece um objeto `Document` que representa todo o arquivo.

```csharp
using Aspose.Words;
using System.Text.RegularExpressions;

class Program
{
    static void Main()
    {
        // Load the source document (replace YOUR_DIRECTORY with your actual path)
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx");
```

Por que isso importa: ao carregar o documento cria‑se uma estrutura tipo DOM, permitindo percorrer parágrafos, tabelas, cabeçalhos e até objetos ocultos de Office Math. Se o arquivo não for encontrado, o Aspose lançará uma `FileNotFoundException` clara, então você saberá imediatamente onde está o problema.

## Etapa 2 – Configurar Opções de Busca/Substituição

Em seguida configuramos `FindReplaceOptions`. Esse objeto indica ao motor *o que* ignorar e *como* tratar as correspondências. Para a maioria dos cenários você pode manter os padrões, mas aqui demonstramos como desabilitar a busca dentro de objetos Office Math — algo que confunde muitos desenvolvedores.

```csharp
        // Create find/replace options
        FindReplaceOptions replaceOptions = new FindReplaceOptions();

        // Skip math objects during the search (optional but often useful)
        replaceOptions.IgnoreOfficeMath = true;
```

> **Por que ignorar Office Math?**  
> Equações matemáticas são armazenadas como fragmentos XML separados. Se você procurar um termo que aparece dentro de uma fórmula, o motor pode corromper a equação. Definir `IgnoreOfficeMath` como `true` evita esse risco enquanto ainda altera o texto regular.

## Etapa 3 – Substituir Todas as Ocorrências (Exemplo Regex)

Agora vem o núcleo do **replace text in docx**: realmente trocar a string antiga pela nova. O método `Range.Replace` aceita um `Regex`, uma string de substituição e as opções que acabamos de criar.

```csharp
        // Replace every occurrence of "foo" with "bar"
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
```

Alguns pontos a observar:

- O padrão `Regex` pode ser tão simples quanto uma string literal (`@"foo"`) ou uma expressão regular completa (`@"\bfoo\b"` para corresponder apenas palavras inteiras).  
- Como usamos `Range.Replace`, a busca cobre todo o documento — incluindo cabeçalhos, rodapés, notas de rodapé e até texto dentro de formas.  
- O método devolve o número de substituições realizadas, que você pode capturar caso precise registrar a operação:

```csharp
        int count = doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        Console.WriteLine($"{count} occurrence(s) replaced.");
```

Essa linha satisfaz diretamente o requisito **replace all occurrences word** mantendo a legibilidade.

## Etapa 4 – Salvar o Documento Modificado

Por fim, persistimos as alterações. Você pode sobrescrever o arquivo original ou gravar em um novo local. Sobrescrever funciona bem para scripts rápidos; para pipelines de produção, escreva em um novo arquivo para manter um registro de auditoria.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY/output.docx");
    }
}
```

Esse é todo o fluxo para **how to replace text c#** em um documento Word. Execute o programa e você verá `output.docx` com cada “foo” transformado em “bar”.

---

## Tópicos Avançados & Casos de Borda

### 1. Substituição Insensível a Maiúsculas/Minúsculas

Se precisar ignorar maiúsculas (ex.: substituir “Foo”, “FOO” e “foo” igualmente), ajuste as opções do regex:

```csharp
        var pattern = new Regex(@"foo", RegexOptions.IgnoreCase);
        doc.Range.Replace(pattern, "bar", replaceOptions);
```

### 2. Substituir Apenas Palavras Inteiras

Às vezes “foo” aparece dentro de outra palavra como “food”. Para evitar alterações acidentais, ancore o padrão com limites de palavra:

```csharp
        var wholeWord = new Regex(@"\bfoo\b");
        doc.Range.Replace(wholeWord, "bar", replaceOptions);
```

### 3. Usando um Callback para Substituição Condicional

O Aspose permite que você forneça um delegate para decidir em tempo real se deve substituir uma correspondência. Isso é útil para cenários como “substituir apenas se a palavra estiver em uma tabela”.

```csharp
        replaceOptions.ReplacingCallback = new ReplaceEvaluator((match, isInsideHeaderFooter, isInsideTable) =>
        {
            // Only replace when inside a table
            return isInsideTable ? "bar" : match.Value;
        });
        doc.Range.Replace(new Regex(@"foo"), "", replaceOptions);
```

### 4. Manipulando Grandes Documentos com Eficiência

Para arquivos de vários gigabytes, considere processar o documento em partes (ex.: por seção) para manter o uso de memória baixo. O Aspose fornece coleções `Section` que você pode iterar e chamar `Replace` em cada uma individualmente.

```csharp
        foreach (Section sec in doc.Sections)
        {
            sec.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        }
```

### 5. Preservando Formatação

O texto substituído herda a formatação do primeiro caractere da correspondência. Se precisar impor um estilo específico (ex.: negrito), aplique‑o após a substituição:

```csharp
        doc.Range.Replace(new Regex(@"foo"), "bar", replaceOptions);
        foreach (Run run in doc.GetChildNodes(NodeType.Run, true))
        {
            if (run.Text.Contains("bar"))
                run.Font.Bold = true; // Force bold on replaced text
        }
```

---

## Código Fonte Completo (Pronto para Copiar e Colar)

Abaixo está o programa completo, autocontido, que você pode colocar em um aplicativo console e executar imediatamente. Sem dependências ocultas, sem arquivos de configuração externos.

```csharp
using Aspose.Words;
using System;
using System.Text.RegularExpressions;

namespace DocxReplaceDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"YOUR_DIRECTORY/input.docx");

            // 2️⃣ Set up find/replace options
            FindReplaceOptions replaceOptions = new FindReplaceOptions
            {
                // Skip Office Math objects – optional but safe
                IgnoreOfficeMath = true
            };

            // 3️⃣ Perform the replacement (replace all occurrences word)
            // Change the pattern or replacement as needed
            var pattern = new Regex(@"foo", RegexOptions.IgnoreCase); // case‑insensitive
            int replacedCount = doc.Range.Replace(pattern, "bar", replaceOptions);

            Console.WriteLine($"{replacedCount} occurrence(s) replaced.");

            // 4️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY/output.docx");
        }
    }
}
```

**Saída esperada:**  
Se `input.docx` contiver três ocorrências de “foo” (em qualquer caso), o console imprimirá `3 occurrence(s) replaced.` e `output.docx` terá “bar” nesses três locais, preservando o estilo original.

---

## Perguntas Frequentes

**Q: Isso funciona com arquivos `.doc`?**  
A: Sim. Aspose.Words trata `.doc` e `.docx` de forma uniforme. Basta mudar a extensão nos caminhos de carga/salvamento.

**Q: E se o documento contiver seções protegidas?**  
A: Você precisará desproteger o documento primeiro (`doc.Protect(ProtectionType.NoProtection, "password")`) ou fornecer a senha ao carregar.

**Q: Posso substituir texto em um arquivo protegido por senha?**  
A: Absolutamente. Use `new LoadOptions { Password = "yourPassword" }` ao construir o `Document`.

**Q: Existe uma alternativa gratuita ao Aspose.Words?**  
A: O Open XML SDK pode realizar busca/substituição, mas carece da conveniência de alto nível `Range.Replace` e requer mais código boilerplate. Para confiabilidade em produção, o Aspose continua sendo a escolha recomendada.

---

## Próximos Passos & Tópicos Relacionados

Agora que você dominou **replace text in docx**, talvez queira explorar:

- **Inserir imagens programaticamente** – aprenda a incorporar fotos em placeholders.  
- **Criar tabelas dinamicamente** – útil para gerar faturas ou relatórios.  
- **Processamento em lote** – percorra uma pasta de arquivos `.docx` e aplique a mesma lógica de busca e substituição.  

Cada um desses tópicos se baseia no mesmo modelo de objeto `Document` que você acabou de usar, então você se sentirá em casa.

---

## Conclusão

Cobremos tudo o que você precisa saber sobre **replace text in docx** usando C#. Desde carregar um documento, configurar `FindReplaceOptions`, trocar cada ocorrência de uma palavra, até salvar o resultado — este tutorial oferece uma solução completa, pronta para copiar e colar. Você também viu como lidar com insensibilidade a maiúsculas, correspondências de palavra inteira e arquivos grandes, completando os cenários **replace all occurrences word** e **find and replace word document**.  

Experimente, ajuste os padrões regex e veja suas tarefas de automação Word passarem de horas para segundos. Tem alguma variação que está tentando implementar? Deixe um comentário — happy coding!

![Screenshot of C# code replacing text in a DOCX file](replace-text-in-docx.png "replace text in docx example")


## O que Você Deve Aprender a Seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código totalmente funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Simple Text Find And Replace In Word](/words/english/net/find-and-replace-text/simple-find-replace/)
- [Word Replace Text Containing Meta Characters](/words/english/net/find-and-replace-text/replace-text-containing-meta-characters/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}