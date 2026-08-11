---
category: general
date: 2026-08-10
description: Inserir forma retangular no Word usando C#. Aprenda como ocultar a forma,
  ocultar a forma no Word e criar uma forma oculta com Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: pt
lastmod: 2026-08-10
og_description: Inserir forma retangular no Word usando C#. Este tutorial explica
  como ocultar forma, ocultar forma no Word e criar forma oculta com exemplos de código
  completos.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Inserir forma retangular no Word com C# – guia passo a passo
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Inserir forma de retângulo no Word com C# – guia completo
url: /pt/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserir forma retangular no Word com C# – guia completo

Se você precisa **inserir forma retangular** em um documento Word usando C#, este guia mostra os passos exatos. Você também aprenderá **como ocultar a forma** para que ela não apareça no arquivo final, respondendo à consulta comum **ocultar forma no Word** e demonstrando como **criar forma oculta** programaticamente.

O tutorial cobre tudo, desde a configuração do Aspose.Words SDK até a verificação de que a forma está oculta. Ao final do artigo você terá um trecho de código reutilizável que pode ser inserido em qualquer projeto .NET.

## Pré‑requisitos

Antes de começar, certifique‑se de que você tem:

- .NET 6.0 ou superior instalado (o código também funciona com .NET Framework 4.6+)
- Uma licença válida do Aspose.Words for .NET ou uma chave de avaliação temporária
- Visual Studio 2022 (ou qualquer IDE que suporte C#)
- Familiaridade básica com a sintaxe C# e o Document Object Model (DOM) de arquivos Word

Nenhum pacote NuGet adicional é necessário além do `Aspose.Words`.

## Etapa 1: Criar um novo documento em branco e um DocumentBuilder

A primeira operação é instanciar um objeto `Document`. O `DocumentBuilder` fornece uma API conveniente para inserir conteúdo como formas, parágrafos e tabelas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Por que isso importa:** `Document` representa todo o arquivo .docx, enquanto `DocumentBuilder` mantém um cursor que rastreia onde o próximo elemento será colocado. Inicializar ambos os objetos é a base para qualquer tarefa de automação do Word.

## Etapa 2: Inserir forma retangular

Agora você insere o retângulo. O método `InsertShape` requer o tipo da forma e suas dimensões em pontos (1 ponto ≈ 1/72 polegada). Um tamanho de **200 × 100 pontos** gera um retângulo de aproximadamente 2,78 × 1,39 polegadas.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Por que isso importa:** O objeto `Shape` que você recebe é totalmente configurável—cor, borda, texto e visibilidade podem ser alterados antes de salvar o documento.

## Etapa 3: Ocultar a forma

Para impedir que o retângulo seja exibido ou impresso, defina sua propriedade `Hidden` como `true`. Essa propriedade mapeia diretamente para o atributo “Hidden” do Word, que o Word respeita tanto na visualização quanto na impressão.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Por que isso importa:** Definir `Hidden` é a maneira padrão de **ocultar forma no Word** sem removê‑la da estrutura do documento. A forma permanece acessível ao código, permitindo manipulações posteriores, como formatação condicional ou alternância de visibilidade baseada em dados.

## Etapa 4: Salvar o documento

Por fim, persista o documento no disco. Escolha qualquer pasta que desejar; o exemplo usa um caminho de placeholder que você deve substituir por um caminho real.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Por que isso importa:** Salvar finaliza o arquivo e grava a flag oculta no Open XML subjacente. Quando você abrir o documento no Microsoft Word, o retângulo ficará invisível, confirmando que você **criou forma oculta** com sucesso.

## Etapa 5: Verificar a forma oculta

Abra o `HiddenShape.docx` gerado no Microsoft Word:

1. Acesse **Arquivo → Opções → Exibição** e certifique‑se de que *“Mostrar texto oculto”* esteja **desmarcado**.  
2. O retângulo não deve estar visível em nenhuma página.  
3. Para confirmar, habilite *“Mostrar texto oculto”*; o retângulo aparecerá com um contorno pontilhado suave, provando que a forma existe, mas está oculta.

Se o retângulo ainda estiver visível, verifique se você salvou o arquivo após definir `Hidden = true` e se está abrindo o arquivo correto.

## Exemplo completo executável

Abaixo está o programa completo que você pode copiar, colar e executar diretamente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Saída esperada:** O console imprime o caminho do arquivo e um pequeno lembrete. Quando o arquivo for aberto no Word, o retângulo ficará invisível a menos que o texto oculto esteja habilitado.

## Perguntas comuns e casos de borda

### Posso ocultar apenas o contorno e manter o preenchimento visível?

Sim. Em vez de definir `Hidden = true`, você pode definir `rectangle.LineFormat.Visible = false` para ocultar a borda enquanto mantém a cor de preenchimento. Essa é uma variação de **como ocultar forma** que preserva parte da aparência visual.

### O atributo oculto funciona em versões antigas do Word (2003, 2007)?

O atributo oculto faz parte da especificação Open XML introduzida no Word 2007. Documentos salvos no formato binário antigo `.doc` não preservam essa flag. Para suportar formatos legados, salve o documento como `.docx` e, se necessário, converta‑o posteriormente usando `SaveFormat.Doc` do Aspose.Words.

### E se eu precisar ocultar várias formas de uma vez?

Itere sobre a coleção `Document.GetChildNodes(NodeType.Shape, true)` e defina `Hidden = true` em cada forma que atender aos seus critérios (por exemplo, um `ShapeType` específico ou um valor customizado de `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Há impacto de desempenho ao ocultar formas?

A flag oculta adiciona um pequeno atributo XML; não afeta a velocidade de renderização. Contudo, um número muito grande de objetos ocultos pode aumentar marginalmente o tamanho do arquivo. Remova formas que nunca serão usadas para manter o documento enxuto.

## Dicas e boas práticas

- **Atribua um nome significativo à forma** usando `rectangle.Name = "MyHiddenRectangle"`; isso ajuda quando você precisar localizar a forma no DOM posteriormente.
- **Defina `AlternativeText`** com uma tag personalizada (ex.: `"HiddenShape"`). Isso permite localizar a forma sem depender de seu índice.
- **Envolva o código em um bloco try‑catch** para tratar erros de licença ou exceções de I/O de forma elegante.
- **Dispose do Document** após salvar se você estiver processando muitos arquivos em um loop, liberando recursos não gerenciados: `document.Dispose();`.

## Conclusão

Agora você sabe como **inserir forma retangular** em um documento Word com C#, como **ocultar forma no Word** e como **criar forma oculta** que permanece parte da estrutura do documento, porém invisível para os usuários finais. O exemplo completo e executável demonstra todo o fluxo de trabalho, desde a criação do documento até a verificação.

Em seguida, você pode explorar **como ocultar forma** com base na entrada do usuário ou combinar formas ocultas com controles de conteúdo para geração dinâmica de documentos. Também é possível aplicar a mesma técnica a outros tipos de forma, como elipses, setas ou desenhos personalizados.

Sinta‑se à vontade para experimentar diferentes dimensões, cores e configurações de visibilidade. Se encontrar algum problema, revise as etapas acima ou consulte a documentação do Aspose.Words para detalhes mais aprofundados da API. Boa codificação!

## O que você deve aprender a seguir?

Os tutoriais a seguir abordam tópicos intimamente relacionados que ampliam as técnicas demonstradas neste guia. Cada recurso inclui exemplos de código completos e funcionais com explicações passo a passo para ajudá‑lo a dominar recursos adicionais da API e explorar abordagens alternativas de implementação em seus próprios projetos.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}