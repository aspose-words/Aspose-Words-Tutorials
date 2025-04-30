---
"description": "Aprenda a modificar tags estruturadas de documentos no Word usando o Aspose.Words para .NET. Atualize texto, menus suspensos e imagens passo a passo."
"linktitle": "Modificar controles de conteúdo"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Modificar controles de conteúdo"
"url": "/pt/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Modificar controles de conteúdo

## Introdução

Se você já trabalhou com documentos do Word e precisou modificar controles de conteúdo estruturados — como texto simples, listas suspensas ou imagens — usando o Aspose.Words para .NET, você está no lugar certo! As Marcas de Documento Estruturadas (SDTs) são ferramentas poderosas que tornam a automação de documentos mais fácil e flexível. Neste tutorial, veremos como você pode modificar essas SDTs para atender às suas necessidades. Seja para atualizar texto, alterar seleções de menus suspensos ou substituir imagens, este guia o guiará pelo processo passo a passo.

## Pré-requisitos

Antes de começarmos a detalhar a modificação dos controles de conteúdo, certifique-se de ter o seguinte:

1. Aspose.Words para .NET instalado: Certifique-se de ter a biblioteca Aspose.Words instalada. Caso contrário, você pode [baixe aqui](https://releases.aspose.com/words/net/).

2. Conhecimento básico de C#: Este tutorial pressupõe que você esteja familiarizado com os conceitos básicos de programação em C#.

3. Um ambiente de desenvolvimento .NET: você deve ter um IDE como o Visual Studio configurado para executar aplicativos .NET.

4. Um Documento de Exemplo: Usaremos um documento de exemplo do Word com vários tipos de SDTs. Você pode usar o do exemplo ou criar o seu próprio.

5. Acesso à documentação do Aspose: Para obter informações mais detalhadas, consulte o [Documentação do Aspose.Words](https://reference.aspose.com/words/net/).

## Importar namespaces

Para começar a trabalhar com o Aspose.Words, você precisa importar os namespaces relevantes para o seu projeto C#. Veja como fazer:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Esses namespaces darão acesso às classes e métodos necessários para manipular tags de documentos estruturados em seus documentos do Word.

## Etapa 1: configure o caminho do documento

Antes de fazer qualquer alteração, você precisa especificar o caminho para o seu documento. Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real onde seu documento está armazenado.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Etapa 2: Percorrer as tags do documento estruturado

Para modificar SDTs, primeiro você precisa percorrer todos os SDTs do documento. Isso é feito usando o comando `GetChildNodes` método para obter todos os nós do tipo `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modifique os SDTs com base em seu tipo
}
```

## Etapa 3: Modificar SDTs de texto simples

Se o SDT for do tipo texto simples, você pode substituir seu conteúdo. Primeiro, limpe o conteúdo existente e, em seguida, adicione o novo texto.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Explicação: Aqui, `RemoveAllChildren()` limpa o conteúdo existente do SDT. Em seguida, criamos um novo `Paragraph` e `Run` objeto para inserir o novo texto.

## Etapa 4: Modificar SDTs da lista suspensa

Para SDTs de lista suspensa, você pode alterar o item selecionado acessando o `ListItems` coleção. Aqui, selecionamos o terceiro item da lista.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Explicação: Este trecho de código seleciona o item no índice 2 (terceiro item) da lista suspensa. Ajuste o índice de acordo com suas necessidades.

## Etapa 5: Modificar SDTs de imagem

Para atualizar uma imagem dentro de um SDT de imagem, você pode substituir a imagem existente por uma nova.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

Explicação: Este código verifica se a forma contém uma imagem e a substitui por uma nova imagem localizada em `ImagesDir`.

## Etapa 6: Salve seu documento modificado

Depois de fazer todas as alterações necessárias, salve o documento modificado com um novo nome para manter o documento original intacto.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Explicação: Isso salva o documento com um novo nome de arquivo para que você possa diferenciá-lo facilmente do original.

## Conclusão

Modificar controles de conteúdo em um documento do Word usando o Aspose.Words para .NET é simples, desde que você entenda as etapas envolvidas. Seja para atualizar texto, alterar seleções de menus suspensos ou trocar imagens, o Aspose.Words fornece uma API robusta para essas tarefas. Seguindo este tutorial, você poderá gerenciar e personalizar com eficácia os controles de conteúdo estruturados do seu documento, tornando-o mais dinâmico e adequado às suas necessidades.

## Perguntas frequentes

1. O que é uma Tag de Documento Estruturado (SDT)?

SDTs são elementos em documentos do Word que ajudam a gerenciar e formatar o conteúdo do documento, como caixas de texto, listas suspensas ou imagens.

2. Como posso adicionar um novo item suspenso a um SDT?

Para adicionar um novo item, use o `ListItems` propriedade e anexar um novo `SdtListItem` para a coleção.

3. Posso usar o Aspose.Words para remover SDTs de um documento?

Sim, você pode remover SDTs acessando os nós do documento e excluindo o SDT desejado.

4. Como lidar com SDTs aninhados em outros elementos?

Use o `GetChildNodes` método com parâmetros apropriados para acessar SDTs aninhados.

5. O que devo fazer se o SDT que preciso modificar não estiver visível no documento?

Certifique-se de que o SDT não esteja oculto ou protegido. Verifique as configurações do documento e certifique-se de que seu código esteja direcionado corretamente ao tipo de SDT.


### Exemplo de código-fonte para modificar controles de conteúdo usando Aspose.Words para .NET 

```csharp
// Caminho para o diretório do seu documento 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Pronto! Você modificou com sucesso diferentes tipos de controles de conteúdo no seu documento do Word usando o Aspose.Words para .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}