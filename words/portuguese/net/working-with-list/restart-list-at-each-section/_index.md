---
title: Reiniciar lista em cada seção
linktitle: Reiniciar lista em cada seção
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como reiniciar listas em cada seção em documentos do Word usando o Aspose.Words para .NET. Siga nosso guia detalhado passo a passo para gerenciar listas de forma eficaz.
weight: 10
url: /pt/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reiniciar lista em cada seção

## Introdução

Criar documentos estruturados e bem organizados pode, às vezes, parecer a solução de um quebra-cabeça complexo. Uma parte desse quebra-cabeça é gerenciar listas de forma eficaz, especialmente quando você quer que elas reiniciem em cada seção. Com o Aspose.Words para .NET, você pode fazer isso perfeitamente. Vamos mergulhar em como você pode reiniciar listas em cada seção em seus documentos do Word usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Baixe e instale a versão mais recente do[Lançamentos Aspose](https://releases.aspose.com/words/net/) página.
2. Ambiente .NET: configure seu ambiente de desenvolvimento com o .NET instalado.
3. Conhecimento básico de C#: Recomenda-se familiaridade com a linguagem de programação C#.
4.  Licença Aspose: Você pode optar por uma[licença temporária](https://purchase.aspose.com/temporary-license/) se você não tiver um.

## Importar namespaces

Antes de escrever o código, certifique-se de importar os namespaces necessários:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Agora, vamos dividir o processo em várias etapas para torná-lo fácil de seguir.

## Etapa 1: Inicializar o documento

Primeiro, você precisará criar uma nova instância de documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Etapa 2: Adicionar uma lista numerada

Em seguida, adicione uma lista numerada ao documento. Essa lista seguirá um formato de numeração padrão.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## Etapa 3: Acesse a lista e defina a propriedade Restart

Recupere a lista que você acabou de criar e defina-a`IsRestartAtEachSection`propriedade para`true`. Isso garante que a lista reinicie a numeração em cada nova seção.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## Etapa 4: Crie um Document Builder e associe a lista

 Criar um`DocumentBuilder` para inserir conteúdo no documento e associá-lo à lista.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## Etapa 5: Adicionar itens de lista e inserir quebra de seção

Agora, adicione itens à lista. Para ilustrar a funcionalidade de reinicialização, inseriremos uma quebra de seção após um certo número de itens.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## Etapa 6: Salve o documento

Por fim, salve o documento com as opções apropriadas para garantir a conformidade.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## Conclusão

E aí está! Seguindo esses passos, você pode facilmente reiniciar listas em cada seção em seus documentos do Word usando o Aspose.Words para .NET. Esse recurso é incrivelmente útil para criar documentos bem estruturados que exigem seções separadas com sua própria numeração de lista. Com o Aspose.Words, lidar com essas tarefas se torna moleza, permitindo que você se concentre em criar conteúdo de alta qualidade.

## Perguntas frequentes

### Posso reiniciar listas em cada seção para diferentes tipos de lista?
Sim, o Aspose.Words para .NET permite que você reinicie vários tipos de listas, incluindo listas com marcadores e numeradas.

### E se eu quiser personalizar o formato de numeração?
 Você pode personalizar o formato de numeração modificando o`ListTemplate` propriedade ao criar a lista.

### Existe um limite para o número de itens em uma lista?
Não, não há um limite específico para o número de itens que você pode ter em uma lista usando o Aspose.Words para .NET.

### Posso usar esse recurso em outros formatos de documento, como PDF?
Sim, você pode usar o Aspose.Words para converter documentos do Word para outros formatos, como PDF, mantendo a estrutura da lista.

### Como posso obter uma avaliação gratuita do Aspose.Words para .NET?
 Você pode obter uma avaliação gratuita no[Lançamentos Aspose](https://releases.aspose.com/) página.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
