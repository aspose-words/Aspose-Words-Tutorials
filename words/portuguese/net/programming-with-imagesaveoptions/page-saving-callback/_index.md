---
title: Retorno de chamada para salvar página
linktitle: Retorno de chamada para salvar página
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a salvar cada página de um documento do Word como uma imagem PNG separada usando o Aspose.Words para .NET com nosso guia detalhado passo a passo.
weight: 10
url: /pt/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Retorno de chamada para salvar página

## Introdução

Olá! Já sentiu a necessidade de salvar cada página de um documento do Word como imagens separadas? Talvez você queira dividir um relatório grande em visuais de fácil digestão, ou talvez precise criar miniaturas para uma prévia. Seja qual for o seu motivo, usar o Aspose.Words para .NET torna essa tarefa muito fácil. Neste guia, vamos orientá-lo no processo de configuração de um retorno de chamada de salvamento de página para salvar cada página de um documento como uma imagem PNG individual. Vamos direto ao assunto!

## Pré-requisitos

Antes de começar, certifique-se de ter o seguinte:

1.  Aspose.Words para .NET: Se você ainda não fez isso, baixe e instale-o em[aqui](https://releases.aspose.com/words/net/).
2. Visual Studio: Qualquer versão deve funcionar, mas usarei o Visual Studio 2019 para este guia.
3. Conhecimento básico de C#: você precisará de um conhecimento básico de C# para acompanhar.

## Importar namespaces

Primeiro, precisamos importar os namespaces necessários. Isso nos ajuda a acessar as classes e métodos necessários sem precisar digitar o namespace completo toda vez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Etapa 1: configure seu diretório de documentos

Certo, vamos começar definindo o caminho para o diretório do seu documento. É aqui que seu documento Word de entrada está localizado e onde as imagens de saída serão salvas.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Etapa 2: Carregue seu documento

Em seguida, carregaremos o documento que você quer processar. Certifique-se de que seu documento ("Rendering.docx") esteja no diretório especificado.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Etapa 3: Configurar opções de salvamento de imagem

Precisamos configurar as opções para salvar imagens. Neste caso, estamos salvando as páginas como arquivos PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Aqui,`PageSet` especifica o intervalo de páginas a serem salvas e`PageSavingCallback` aponta para nossa classe de retorno de chamada personalizada.

## Etapa 4: Implementar o retorno de chamada de salvamento de página

Agora, vamos implementar a classe de retorno de chamada que manipula como cada página é salva.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Esta classe implementa o`IPageSavingCallback` interface e dentro do`PageSaving` método, definimos o padrão de nomenclatura para cada página salva.

## Etapa 5: Salve o documento como imagens

Por fim, salvamos o documento usando as opções configuradas.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusão

E aí está! Você configurou com sucesso um callback de salvamento de página para salvar cada página de um documento do Word como uma imagem PNG separada usando o Aspose.Words para .NET. Essa técnica é incrivelmente útil para vários aplicativos, desde a criação de visualizações de página até a geração de imagens de página individuais para relatórios. 

Boa codificação!

## Perguntas frequentes

### Posso salvar páginas em formatos diferentes de PNG?  
 Sim, você pode salvar páginas em diferentes formatos, como JPEG, BMP e TIFF, alterando o`SaveFormat` em`ImageSaveOptions`.

### E se eu quiser salvar apenas páginas específicas?  
 Você pode especificar as páginas que deseja salvar ajustando o`PageSet` parâmetro em`ImageSaveOptions`.

### É possível personalizar a qualidade da imagem?  
 Absolutamente! Você pode definir propriedades como`ImageSaveOptions.JpegQuality` para controlar a qualidade das imagens de saída.

### Como posso lidar com documentos grandes de forma eficiente?  
Para documentos grandes, considere processar páginas em lotes para gerenciar o uso de memória de forma eficaz.

### Onde posso encontrar mais informações sobre o Aspose.Words para .NET?  
 Confira o[documentação](https://reference.aspose.com/words/net/) para guias e exemplos abrangentes.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
