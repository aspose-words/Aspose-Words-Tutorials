---
title: Alterar Campo Atualizar Cultura Fonte
linktitle: Alterar Campo Atualizar Cultura Fonte
second_title: API de processamento de documentos Aspose.Words
description: Aprenda como alterar a fonte de cultura de atualização de campo no Aspose.Words para .NET com este guia. Controle a formatação de data com base em diferentes culturas facilmente.
weight: 10
url: /pt/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alterar Campo Atualizar Cultura Fonte

## Introdução

Neste tutorial, vamos mergulhar no mundo do Aspose.Words para .NET e explorar como alterar a fonte de cultura de atualização de campo. Se você estiver lidando com documentos do Word que incluem campos de data e precisa controlar como essas datas são formatadas com base em diferentes culturas, este guia é para você. Vamos percorrer o processo passo a passo, garantindo que você entenda cada conceito e possa aplicá-lo efetivamente em seus projetos.

## Pré-requisitos

Antes de começarmos o código, certifique-se de ter o seguinte:

-  Aspose.Words para .NET: Você pode baixá-lo em[aqui](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: qualquer IDE compatível com .NET (por exemplo, Visual Studio).
- Conhecimento básico de C#: Este tutorial pressupõe que você tenha um conhecimento fundamental de programação em C#.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários para nosso projeto. Isso garantirá que tenhamos acesso a todas as classes e métodos necessários fornecidos pelo Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Agora, vamos dividir o exemplo em várias etapas para ajudar você a entender como alterar a fonte de cultura de atualização de campo no Aspose.Words para .NET.

## Etapa 1: Inicializar o documento

 O primeiro passo é criar uma nova instância do`Document` classe e uma`DocumentBuilder`. Isso define a base para construir e manipular nosso documento do Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Etapa 2: Insira campos com localidade específica

Em seguida, precisamos inserir campos no documento. Para este exemplo, inseriremos dois campos de data. Definiremos a localidade da fonte para alemão (LocaleId = 1031) para demonstrar como a cultura afeta o formato da data.

```csharp
builder.Font.LocaleId = 1031; // Alemão
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Etapa 3: Definir fonte de cultura de atualização de campo

 Para controlar a cultura usada na atualização dos campos, definimos o`FieldUpdateCultureSource` propriedade do`FieldOptions`classe. Esta propriedade determina se a cultura é retirada do código do campo ou do documento.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Etapa 4: Executar mala direta

Agora precisamos executar uma mala direta para preencher os campos com dados reais. Neste exemplo, definiremos o segundo campo de data (`Date2`) até 1º de janeiro de 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Etapa 5: Salve o documento

Por fim, salvamos o documento no diretório especificado. Esta etapa conclui o processo de alteração da fonte de cultura de atualização de campo.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusão

E aí está! Você alterou com sucesso a fonte de cultura de atualização de campo no Aspose.Words para .NET. Seguindo essas etapas, você pode garantir que seus documentos do Word exibam datas e outros valores de campo de acordo com as configurações de cultura especificadas. Isso pode ser particularmente útil ao gerar documentos para um público internacional.

## Perguntas frequentes

###  Qual é o propósito de definir o`LocaleId`?
 O`LocaleId` especifica as configurações de cultura para o texto, o que afeta como as datas e outros dados sensíveis à localidade são formatados.

### Posso usar um idioma diferente do alemão?
 Sim, você pode definir o`LocaleId`para qualquer identificador de localidade válido. Por exemplo, 1033 para inglês (Estados Unidos).

###  O que acontece se eu não definir o`FieldUpdateCultureSource` property?
Se esta propriedade não estiver definida, as configurações de cultura padrão do documento serão usadas ao atualizar os campos.

### É possível atualizar campos com base na cultura do documento em vez do código do campo?
 Sim, você pode definir`FieldUpdateCultureSource` para`FieldUpdateCultureSource.Document` para usar as configurações de cultura do documento.

### Como posso formatar datas em um padrão diferente?
 Você pode alterar o padrão de formato de data no`InsertField` método modificando o`\\@` mudar valor.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
