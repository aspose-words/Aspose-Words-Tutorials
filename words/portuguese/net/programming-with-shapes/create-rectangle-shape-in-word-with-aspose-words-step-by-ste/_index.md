---
category: general
date: 2026-02-18
description: Crie uma forma retangular usando Aspose.Words e aprenda como adicionar
  sombra, definir o tamanho da forma e salvar o documento Word em poucos minutos.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: pt
og_description: Crie uma forma retangular em um arquivo Word, aprenda a adicionar
  sombra, definir o tamanho da forma e salvar o documento com Aspose.Words em C#.
og_title: Criar forma retangular no Word – Tutorial completo do Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Criar forma retangular no Word com Aspose.Words – Guia passo a passo
url: /pt/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

to keep all markdown formatting.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar forma retangular no Word com Aspose.Words – Guia passo a passo

Já precisou **criar forma retangular** em um arquivo Word mas não sabia por onde começar? Você não está sozinho—desenvolvedores frequentemente perguntam: “como adiciono uma sombra a uma forma e ainda mantenho o documento editável?” Neste tutorial vamos responder isso e também mostrar como **adicionar sombra**, **definir o tamanho da forma** e **salvar o documento Word** tudo em um fluxo contínuo.

Vamos percorrer tudo que você precisa, desde a inicialização de um novo documento (sim, esse é o primeiro passo para **como criar documento**) até persistir o *.docx* final no disco. Sem referências externas, apenas um exemplo autônomo que você pode copiar‑colar no Visual Studio e executar hoje.

---

## Pré-requisitos

- .NET 6+ (ou .NET Framework 4.7+). Aspose.Words funciona com qualquer runtime .NET recente.
- Uma licença válida do Aspose.Words (ou a chave de avaliação gratuita) – caso contrário, você verá uma marca d'água.
- Visual Studio, Rider ou qualquer editor C# que preferir.
- Conhecimento básico de C#—nada sofisticado, apenas a capacidade de executar um aplicativo de console.

> **Dica profissional:** Se você está em um Mac, o mesmo código roda sob .NET 6 com VS Code—apenas certifique‑se de referenciar o pacote NuGet `Aspose.Words`.

## Etapa 1: Inicializar o documento – a base de **como criar documento**

Antes de podermos desenhar qualquer coisa, precisamos de uma tela em branco. Aspose.Words chama isso de `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Por que isso importa:** O objeto `Document` representa todo o arquivo *.docx*. Todas as formas, parágrafos e seções que você adiciona tornam‑se filhos desse objeto. Começar com um documento limpo garante que nenhum estilo oculto interfira na sua forma retangular.

---

## Etapa 2: Definir o retângulo e **definir o tamanho da forma**

Um retângulo é apenas um `Shape` com `ShapeType.Rectangle`. Vamos atribuir dimensões explícitas para que ele apareça exatamente como desejado.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **O que os números significam:** Aspose.Words usa pontos (1 pt = 1/72 pol). Ajuste os valores para se adequar ao seu layout; para uma página A4 típica, 200 pt é uma largura confortável.

---

## Etapa 3: **Como adicionar sombra** – fazendo a forma se destacar

Sombras dão uma pista visual de que a forma está “elevada” da página. A propriedade `Shadow` permite ajustar cor, distância, transparência e desfoque.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Por que usar transparência?** Uma sombra totalmente opaca pode parecer agressiva. Definir para 0.4 torna o efeito sutil e profissional.

---

## Etapa 4: Posicionar o retângulo – fluxo inline com o texto ao redor

Se você quiser que a forma se comporte como um caractere em um parágrafo, defina seu `WrapType` como `Inline`. Isso mantém o layout previsível, especialmente quando o documento for editado posteriormente.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Caso extremo:** Se precisar que o retângulo flutue sobre o texto (por exemplo, uma marca d'água), altere `WrapType` para `Square` ou `BehindText`.

---

## Etapa 5: Inserir a forma no corpo do documento

Agora realmente colocamos o retângulo no primeiro parágrafo. Se o documento ainda não tem conteúdo, `FirstParagraph` é criado automaticamente.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Dica:** Você também pode criar um novo parágrafo primeiro e então anexar a forma—útil quando precisar de texto ao redor.

---

## Etapa 6: **Salvar documento Word** – a etapa final

Com tudo no lugar, persistir o arquivo é uma única linha de código. Escolha qualquer caminho que desejar; o exemplo usa um placeholder que você deve substituir pelo seu próprio diretório.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Resultado:** Abra o *.docx* gerado no Microsoft Word. Você verá um retângulo com sombra preta, 200 pt de largura e 100 pt de altura, posicionado inline com o primeiro parágrafo.

---

## Saída esperada

Ao abrir **ShadowShape.docx**, o documento exibe:

- Um único parágrafo contendo uma forma retangular.
- O retângulo tem uma sombra preta sutil deslocada em 5 pt.
- O tamanho da forma corresponde às dimensões definidas na Etapa 2.
- Nenhum texto extra aparece a menos que você o adicione manualmente.

Se a forma não aparecer, verifique novamente se você referenciou a versão correta do Aspose.Words e se sua licença (ou avaliação) está ativa.

---

## Perguntas comuns & variações

| Pergunta | Resposta |
|----------|----------|
| *Posso mudar a cor da sombra para algo diferente de preto?* | Absolutamente—defina `rectangleShape.Shadow.Color = Color.Blue;` ou qualquer `System.Drawing.Color`. |
| *E se eu precisar de um retângulo maior?* | Ajuste os valores de `Width` e `Height`. Lembre‑se de que eles estão em pontos; 72 pt = 1 pol. |
| *É possível posicionar a forma em uma posição absoluta?* | Sim—use `WrapType = WrapType.Absolute` e defina as propriedades `Top`/`Left`. |
| *Isso funciona com .NET Core?* | Funciona. Aspose.Words é multiplataforma; basta instalar o pacote NuGet para .NET Standard. |
| *Posso adicionar texto dentro do retângulo?* | Não diretamente; você precisaria inserir uma forma `TextBox` em vez de um retângulo simples. |

---

## Exemplo completo funcional (pronto para copiar‑colar)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Execute o programa, navegue até `C:\Temp\ShadowShape.docx` e você verá o retângulo com sombra exatamente como descrito.

---

## Conclusão

Agora você sabe como **criar forma retangular** em um arquivo Word usando Aspose.Words, como **definir o tamanho da forma**, **adicionar sombra**, e finalmente **salvar documento Word** com as alterações. Todo o processo—desde **como criar documento** até persistir o resultado—cabe em algumas linhas de C# e pode ser expandido para layouts mais complexos.

Pronto para o próximo desafio? Experimente substituir o retângulo por uma forma com cantos arredondados, experimente diferentes cores de sombra, ou incorpore a forma dentro de uma célula de tabela. Cada ajuste reforça os mesmos conceitos fundamentais que abordamos aqui.

Se você achou este guia útil, compartilhe, deixe um comentário com suas próprias variações, ou explore nossos outros tutoriais sobre automação Word, como inserir imagens ou gerar tabelas com Aspose.Words. Feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}