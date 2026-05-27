---
category: general
date: 2026-05-26
description: Criar documento Word em C# com Aspose.Words, inserir forma retangular,
  definir cor de preenchimento e adicionar efeito de sombra – guia passo a passo.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: pt
og_description: Crie um documento Word em C# usando Aspose.Words. Aprenda como inserir
  uma forma retangular, definir sua cor de preenchimento e adicionar um efeito de
  sombra.
og_title: Criar documento Word – Inserir forma retangular e sombra em C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Criar documento Word – Inserir forma retangular e sombra em C#
url: /pt/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word – Inserir Forma Retangular e Sombra em C#

Já se perguntou como **criar um documento Word** programaticamente sem abrir o Microsoft Word primeiro? Você não está sozinho. Em muitos cenários de automação — pense em faturas, contratos ou geração em massa de relatórios — você precisa de uma forma confiável de gerar um arquivo .docx, inserir uma forma dentro dele, aplicar uma cor e, talvez, até uma sombra para um visual mais refinado.

Neste tutorial vamos percorrer exatamente isso: usar o Aspose.Words para .NET para **criar um documento Word**, **inserir uma forma retangular**, aplicar um preenchimento e **adicionar sombra**. Ao final, você terá um arquivo pronto‑para‑salvar que pode ser encaminhado para qualquer fluxo de trabalho subsequente.  

Também abordaremos **como inserir forma** de maneira flexível e por que **como definir preenchimento** é importante para a consistência visual. Sem enrolação, apenas o código que você pode copiar‑colar e executar.

## Pré‑requisitos

Antes de mergulharmos, certifique‑se de que você tem:

- .NET 6+ (ou .NET Framework 4.7+) instalado.
- Uma licença válida do Aspose.Words para .NET (ou uma chave de avaliação temporária).
- Visual Studio, Rider ou qualquer IDE C# de sua preferência.
- Familiaridade básica com a sintaxe C# — nada de avançado é necessário.

Tem tudo isso? Ótimo, vamos começar.

## Etapa 1 – Criar Documento Word

A primeira coisa que você precisa é um objeto de documento em branco. Essa é a tela onde tudo mais será inserido.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` representa o arquivo .docx na memória, enquanto `DocumentBuilder` nos fornece uma API prática para inserir texto, tabelas e formas. **Criar o documento Word** dessa forma é instantâneo — sem interface, sem interop COM, apenas .NET puro.

## Etapa 2 – Inserir Forma Retangular

Agora que temos um documento, vamos **inserir uma forma retangular**. O método `InsertShape` recebe um enum `ShapeType`, largura e altura (em pontos). Usaremos um retângulo com tamanho de 150 × 80 pontos, o que equivale aproximadamente a 2 × 1 polegada.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Nos bastidores, o Aspose cria um objeto `Shape`, o adiciona ao parágrafo atual e devolve uma referência que você pode estilizar. Esse é o núcleo de **como inserir forma** — apenas uma linha de código, mas incrivelmente poderosa.

## Etapa 3 – Como Definir Preenchimento

Uma forma sem preenchimento é invisível em uma página branca. Vamos dar a ela um fundo azul‑claro agradável.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Você também poderia usar gradientes, texturas ou até um preenchimento com imagem, mas uma cor sólida mantém o exemplo simples. Isso demonstra **como definir preenchimento** em qualquer forma que você crie, garantindo o indicativo visual que seus leitores esperam.

## Etapa 4 – Como Adicionar Sombra

Sombras adicionam profundidade e fazem a forma sobressair. O Aspose.Words expõe um objeto `ShadowFormat` onde você pode ativar a visibilidade, escolher uma cor e ajustar desfoque, distância e ângulo.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Por que esses valores específicos? Um ângulo de 45° fornece uma fonte de luz natural superior‑direita, um desfoque moderado mantém a sombra sutil e uma distância curta impede que a forma pareça desconectada. Sinta‑se à vontade para experimentar — mudar o ângulo para 135° fará a sombra cair para a parte inferior‑esquerda, por exemplo.

## Etapa 5 – Salvar o Documento

Todo o trabalho está concluído; agora gravamos o arquivo no disco. Escolha qualquer caminho que desejar; apenas certifique‑se de que a pasta exista.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Ao abrir `ShadowShape.docx` no Microsoft Word, você verá um retângulo azul‑claro com uma sombra cinza suave — exatamente o que scriptamos.

## Exemplo Completo Funcionando

Juntando tudo, aqui está o programa completo, pronto para copiar‑colar:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Resultado Esperado

- Um arquivo chamado **ShadowShape.docx** aparece na pasta de destino.
- Ao abri‑lo no Word, um retângulo azul‑claro está centralizado na primeira página.
- O retângulo projeta uma sombra cinza em ângulo de 45°, proporcionando um efeito 3‑D sutil.

## Perguntas Frequentes & Casos de Borda

**E se eu precisar de uma forma diferente?**  
Substitua `ShapeType.Rectangle` por qualquer outro valor do enum (`Ellipse`, `Star`, `Arrow`, etc.). O restante do código permanece o mesmo.

**Posso adicionar texto dentro da forma?**  
Sim — após criar a forma, chame `shape.AppendChild(new Paragraph(doc))` e então insira um `Run` com seu texto. Lembre‑se de definir as propriedades `shape.TextBox` se quiser que o texto faça wrap.

**E quanto a DPI ou unidades de medida?**  
O Aspose trabalha em pontos (1 pt = 1/72 polegada). Se preferir centímetros, multiplique por 28,35 (já que 1 cm ≈ 28,35 pt).

**Preciso de licença para que isso funcione?**  
A versão de avaliação adiciona uma marca d'água na primeira página. Uma licença adequada remove a marca e desbloqueia a API completa.

## Dicas & Armadilhas

- **Dica de especialista:** Chame `builder.MoveToDocumentEnd()` antes de inserir uma forma se quiser que ela fique no final do documento.
- **Cuidado com:** Salvar em uma pasta somente‑leitura lançará uma `UnauthorizedAccessException`. Garanta que sua aplicação tenha permissão de escrita.
- **Observação de desempenho:** Para geração em massa (centenas de documentos), reutilize uma única instância `Document` como modelo e clone‑a com `doc.Clone(true)` para evitar sobrecarga de inicialização repetida.

## Conclusão

Agora você sabe como **criar documento Word**, **inserir forma retangular**, **definir preenchimento** e **adicionar sombra** usando o Aspose.Words para .NET. O trecho acima é uma solução autônoma que você pode inserir em qualquer projeto C#, seja um aplicativo console, uma API web ou um serviço em segundo plano.

A partir daqui, você pode explorar:

- Adicionar múltiplas formas com cores variadas.
- Usar gradientes ou preenchimentos com imagem (`shape.FillColor = ...` → `shape.FillPattern`).
- Combinar formas com tabelas para layouts de relatórios mais complexos.

Experimente, ajuste os parâmetros e veja seus arquivos Word automatizados ficarem mais profissionais com apenas algumas linhas de código. Feliz codificação!

## Tutoriais Relacionados

- [Criar forma retangular no Word usando C# – Guia passo a passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial de Sombra em Forma do Aspose.Words – Adicionar Sombra a Forma Word em C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Criar Forma de Grupo em Documento Word Usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}