---
category: general
date: 2026-04-21
description: Crie um documento Word com um retângulo estilizado e sombra. Aprenda
  como adicionar sombra, inserir forma de retângulo, definir a cor da sombra e muito
  mais em C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: pt
og_description: Crie um documento Word e adicione uma forma de retângulo com sombra
  em C#. Siga este guia para definir a cor da sombra, o desfoque e os deslocamentos
  facilmente.
og_title: Criar documento Word com retângulo sombreado – passo a passo
tags:
- Aspose.Words
- C#
- Document Automation
title: Criar documento Word com retângulo sombreado – Guia completo
url: /pt/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Criar Documento Word com Retângulo com Sombra – Guia Completo

Já precisou **criar documento Word** que pareça um pouco mais refinado do que uma página simples de texto? Talvez você esteja criando um modelo de relatório ou um folheto e um retângulo simples com uma sombra sutil resolva. Neste tutorial vamos percorrer exatamente isso—como inserir uma forma de retângulo, ativar a sombra e personalizar sua cor, desfoque e deslocamentos—tudo com C# e Aspose.Words.

Também abordaremos **como adicionar sombra** de forma que funcione tanto para Word 2016, 2019 ou a versão mais recente do Office 365. Ao final, você terá um arquivo *.docx* pronto‑para‑salvar que exibe um retângulo bem sombreado, e entenderá o “porquê” de cada propriedade definida.

## Pré-requisitos

- .NET 6 (ou qualquer versão recente do .NET Framework)  
- Pacote NuGet Aspose.Words para .NET (`Install-Package Aspose.Words`)  
- Familiaridade básica com a sintaxe C#  
- Uma IDE como Visual Studio (mas qualquer editor serve)

Nenhuma biblioteca adicional é necessária; todo o resto está dentro do Aspose.Words.

## Etapa 1 – Inicializar o Documento e o Builder (Criar Documento Word)

Para **criar documento Word** programaticamente você começa com a classe `Document`. O `DocumentBuilder` é seu pincel; ele permite adicionar texto, formas e outros elementos.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Por que isso importa:* O objeto `Document` representa o arquivo .docx completo. Sem ele você não tem onde anexar o retângulo ou sua sombra.

## Etapa 2 – Inserir uma Forma de Retângulo (Inserir Forma de Retângulo)

Agora vamos realmente **inserir forma de retângulo**. O método `InsertShape` recebe um enum `ShapeType`, além da largura e altura em pontos.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Dica profissional:* 1 ponto ≈ 1/72 polegada, então 200 pts correspondem a aproximadamente 2,78 polegadas de largura. Ajuste esses números para se adequar ao seu layout.

## Etapa 3 – Ativar a Sombra (Como Adicionar Sombra)

Sombras são desativadas por padrão. Alterne a flag `Visible` para ativá‑la.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*O que está acontecendo?* Quando `Visible` é true, o Word renderiza uma sombra projetada com base nas outras propriedades que você definirá a seguir.

## Etapa 4 – Personalizar a Aparência da Sombra (Definir Cor da Sombra, Desfoque, Deslocamentos)

É aqui que você **define a cor da sombra**, o raio de desfoque e os deslocamentos X/Y. Sinta‑se à vontade para experimentar—valores diferentes proporcionam um brilho suave, uma sombra profunda ou até um efeito “flutuante”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Por que esses números?* Um desfoque de 5 pts produz uma borda suave, enquanto um deslocamento de 4 pts move a sombra para baixo‑direita, imitando uma fonte de luz do canto superior esquerdo. Altere `Color` para `Color.Black` para um contraste mais forte, ou use `Color.FromArgb(128, 0, 0, 0)` para um preto semitransparente.

### Casos de Borda & Variações

- **Sem desfoque:** Defina `Blur = 0` para uma sombra nítida e de borda dura.  
- **Deslocamentos negativos:** Use `OffsetX = -4` para empurrar a sombra para a esquerda.  
- **Formas diferentes:** As mesmas propriedades de sombra funcionam para círculos, triângulos ou até formas desenhadas livremente—basta mudar `ShapeType` na Etapa 2.  
- **Compatibilidade:** Aspose.Words grava os dados da sombra no formato Office Open XML, que funciona em Word 2010‑2021 e Office 365.

## Etapa 5 – Salvar o Documento (Criar Documento Word)

Finalmente, persista o arquivo no disco. Você pode escolher qualquer formato suportado (`.docx`, `.pdf`, `.odt`, …) mas para este guia usaremos o formato clássico do Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Ao abrir **ShadowRectangle.docx** no Microsoft Word você verá um retângulo cinza com uma sombra sutil e desfocada deslocada para a parte inferior‑direita—exatamente o que scriptamos.

### Saída Esperada

- Um arquivo *.docx* de uma única página.  
- Um retângulo de 200 pt × 100 pt centralizado onde o cursor estava quando `InsertShape` foi chamado.  
- Uma sombra cinza que aparece 4 pts à direita e 4 pts abaixo, com desfoque de 5 pts.

Se a forma parecer fora do centro, você pode mover o cursor com `builder.MoveTo` antes de inserir, ou ajustar as propriedades `Left` e `Top` da forma após a inserção.

## Perguntas Frequentes & Solução de Problemas

**Q: A sombra não está aparecendo no Word.**  
A: Certifique‑se de que `ShadowFormat.Visible` está `true`. Também verifique se está usando uma versão recente do Aspose.Words (o recurso de sombra foi adicionado na versão 20.3).  

**Q: Posso aplicar um degradê à sombra?**  
A: Não diretamente via `ShadowFormat`. A interface do Word suporta sombras em degradê, mas o esquema Open XML (que o Aspose.Words segue) só expõe sombras de cor sólida. Você precisaria editar o XML subjacente manualmente—um cenário mais avançado.  

**Q: E se eu precisar de um retângulo transparente com apenas a sombra?**  
A: Defina `rectangle.FillColor = Color.Transparent;` após a inserção. A sombra ainda será renderizada porque é independente do preenchimento.

## Dicas Profissionais para Código de Produção

- **Reutilize o builder:** Se estiver adicionando várias formas, mantenha a mesma instância de `DocumentBuilder`—criar uma nova para cada forma adiciona sobrecarga desnecessária.  
- **Salvamentos em lote:** Salve uma única vez após todas as modificações; I/O frequente desacelera a geração de documentos grandes.  
- **Tratamento de erros:** Envolva todo o bloco em um `try / catch` e registre as exceções `Aspose.Words`; elas costumam conter números de linha úteis se o modelo de documento estiver corrompido.

## Próximos Passos (Tópicos Relacionados)

- **Como adicionar sombra** a imagens ou caixas de texto (uso similar de `ShadowFormat`).  
- **Inserir forma de retângulo** dentro de uma célula de tabela para estilização personalizada da célula.  
- **Criar retângulo no Word** usando o XML nativo do Word (para quem prefere Open XML bruto).  
- **Definir cor da sombra** dinamicamente com base na entrada do usuário ou nas cores do tema.

Experimente diferentes cores, raios de desfoque e deslocamentos—talvez um brilho azul suave para um relatório corporativo, ou uma sombra preta profunda para um folheto dramático. As possibilidades são infinitas, e as alterações no código são mínimas.

---

### Resumo Rápido

- Nós **criamos um documento Word** do zero.  
- Nós **inserimos uma forma de retângulo** e ativamos sua sombra.  
- Nós **definimos a cor da sombra**, desfoque e deslocamentos para obter um visual profissional.  
- Nós salvamos o arquivo, pronto para distribuição.

Agora você tem uma base sólida para adicionar recursos visuais a qualquer projeto de automação Word. Tem mais ideias? Deixe um comentário, e vamos continuar a conversa. Feliz codificação!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}