---
"description": "Aprenda a inserir um campo TOA sem usar um construtor de documentos no Aspose.Words para .NET. Siga nosso guia passo a passo para gerenciar citações legais com eficiência."
"linktitle": "Inserir campo TOA sem o Construtor de Documentos"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Inserir campo TOA sem o Construtor de Documentos"
"url": "/pt/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserir campo TOA sem o Construtor de Documentos

## Introdução

Criar um campo de Índice de Autoridades (TOA) em um documento do Word pode parecer a tarefa de montar um quebra-cabeça complexo. No entanto, com a ajuda do Aspose.Words para .NET, o processo se torna simples e direto. Neste artigo, guiaremos você pelas etapas para inserir um campo de Índice de Autoridades sem usar um construtor de documentos, facilitando o gerenciamento de citações e referências jurídicas em seus documentos do Word.

## Pré-requisitos

Antes de começar o tutorial, vamos abordar os itens essenciais que você precisa:

- Aspose.Words para .NET: Certifique-se de ter a versão mais recente instalada. Você pode baixá-la do site [Site Aspose](https://releases.aspose.com/words/net/).
- Ambiente de desenvolvimento: um IDE compatível com .NET, como o Visual Studio.
- Conhecimento básico de C#: entender a sintaxe e os conceitos básicos de C# será útil.
- Documento de exemplo do Word: crie ou tenha um documento de exemplo pronto onde você deseja inserir o campo TOA.

## Importar namespaces

Para começar, você precisará importar os namespaces necessários da biblioteca Aspose.Words. Essa configuração garante que você tenha acesso a todas as classes e métodos necessários para a manipulação de documentos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Vamos dividir o processo em etapas simples e fáceis de seguir. Guiaremos você por cada etapa, explicando o que cada trecho de código faz e como ele contribui para a criação do campo TOA.

## Etapa 1: Inicializar o documento

Primeiro, você precisa criar uma instância do `Document` classe. Este objeto representa o documento do Word no qual você está trabalhando.

```csharp
// O caminho para o diretório de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Este código inicializa um novo documento do Word. Você pode pensar nisso como a criação de uma tela em branco à qual adicionará seu conteúdo.

## Etapa 2: Criar e configurar o campo TA

Em seguida, adicionaremos um campo TA (Tabela de Autoridades). Este campo marca as entradas que aparecerão na Tabela de Autoridades.

```csharp
Paragraph para = new Paragraph(doc);

// Queremos inserir campos TA e TOA assim:
// { TA \c 1 \l "Valor 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Aqui está uma análise:
- Paragraph para = new Paragraph(doc);: Cria um novo parágrafo dentro do documento.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Adiciona um campo TA ao parágrafo. O `FieldType.FieldTOAEntry` especifica que este é um campo de entrada TOA.
- fieldTA.EntryCategory = "1";: Define a categoria da entrada. Isso é útil para categorizar diferentes tipos de entradas.
- fieldTA.LongCitation = "Valor 0";: Especifica o texto longo da citação. Este é o texto que aparecerá no TOA.
- doc.FirstSection.Body.AppendChild(para);: Acrescenta o parágrafo com o campo TA ao corpo do documento.

## Etapa 3: adicione o campo TOA

Agora, vamos inserir o campo TOA real que compila todas as entradas TA em uma tabela.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Nesta etapa:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Adiciona um campo TOA ao parágrafo.
- fieldToa.EntryCategory = "1";: Filtra as entradas para incluir apenas aquelas marcadas com a categoria "1".

## Etapa 4: Atualizar o campo TOA

Depois de inserir o campo TOA, você precisa atualizá-lo para garantir que ele reflita as entradas mais recentes.

```csharp
fieldToa.Update();
```

Este comando atualiza o campo TOA, garantindo que todas as entradas marcadas sejam exibidas corretamente na tabela.

## Etapa 5: Salve o documento

Por fim, salve seu documento com o campo TOA recém-adicionado.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Esta linha de código salva o documento no diretório especificado. Certifique-se de substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real onde você deseja salvar seu arquivo.

## Conclusão

Pronto! Você adicionou com sucesso um campo TOA a um documento do Word sem usar um construtor de documentos. Seguindo estes passos, você pode gerenciar citações com eficiência e criar tabelas de autoridades abrangentes em seus documentos jurídicos. O Aspose.Words para .NET torna esse processo simples e eficiente, oferecendo as ferramentas necessárias para lidar com tarefas complexas de documentação com facilidade.

## Perguntas frequentes

### Posso adicionar vários campos de TA com categorias diferentes?
Sim, você pode adicionar vários campos TA com categorias diferentes definindo o `EntryCategory` propriedade de acordo.

### Como posso personalizar a aparência do TOA?
Você pode personalizar a aparência do TOA modificando as propriedades do campo TOA, como formatação de entrada e rótulos de categoria.

### É possível atualizar o campo TOA automaticamente?
Embora você possa atualizar manualmente o campo TOA usando o `Update` método, Aspose.Words atualmente não oferece suporte a atualizações automáticas em alterações em documentos.

### Posso adicionar campos TA programaticamente em partes específicas do documento?
Sim, você pode adicionar campos TA em locais específicos inserindo-os nos parágrafos ou seções desejados.

### Como lidar com vários campos TOA em um único documento?
Você pode gerenciar vários campos TOA atribuindo diferentes `EntryCategory` valores e garantindo que cada campo TOA filtre entradas com base em sua categoria.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}