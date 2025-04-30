---
"description": "Aprenda a atualizar a propriedade de tempo salvo pela última vez em documentos do Word usando o Aspose.Words para .NET. Siga nosso guia passo a passo detalhado."
"linktitle": "Atualizar a última propriedade de tempo salva"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Atualizar a última propriedade de tempo salva"
"url": "/pt/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Atualizar a última propriedade de tempo salva

## Introdução

Já se perguntou como controlar a última propriedade de tempo salva em seus documentos do Word programaticamente? Se você estiver lidando com vários documentos e precisar manter seus metadados, atualizar a última propriedade de tempo salva pode ser bastante útil. Hoje, vou mostrar esse processo usando o Aspose.Words para .NET. Então, apertem os cintos e vamos começar!

## Pré-requisitos

Antes de começarmos o guia passo a passo, há algumas coisas que você precisa:

1. Aspose.Words para .NET: Certifique-se de ter o Aspose.Words para .NET instalado. Caso não tenha, você pode [baixe aqui](https://releases.aspose.com/words/net/).
2. Ambiente de desenvolvimento: Um ambiente de desenvolvimento como o Visual Studio.
3. Conhecimento básico de C#: entender os conceitos básicos de programação em C# será útil.

## Importar namespaces

Para começar, certifique-se de importar os namespaces necessários para o seu projeto. Isso permitirá que você acesse as classes e métodos necessários para manipular documentos do Word.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Agora, vamos dividir o processo em etapas simples. Cada etapa guiará você pelo processo de atualização da última propriedade de tempo salva no seu documento do Word.

## Etapa 1: configure seu diretório de documentos

Primeiro, você precisa especificar o caminho para o diretório do seu documento. É lá que o documento atual está armazenado e onde o documento atualizado será salvo.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real para seu diretório.

## Etapa 2: carregue seu documento do Word

Em seguida, carregue o documento do Word que deseja atualizar. Você pode fazer isso criando uma instância do `Document` classe e passando o caminho do seu documento.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Certifique-se de que o documento nomeado `Document.docx` está presente no diretório especificado.

## Etapa 3: Configurar opções de salvamento

Agora, crie uma instância do `OoxmlSaveOptions` classe. Esta classe permite que você especifique opções para salvar seu documento no formato Office Open XML (OOXML). Aqui, você definirá o `UpdateLastSavedTimeProperty` para `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Isso informa ao Aspose.Words para atualizar a última propriedade de tempo salva do documento.

## Etapa 4: Salve o documento atualizado

Por fim, salve o documento usando o `Save` método do `Document` classe, passando o caminho onde você deseja salvar o documento atualizado e as opções de salvamento.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Isso salvará o documento com a última propriedade de tempo salva atualizada.

## Conclusão

Pronto! Seguindo estes passos, você pode atualizar facilmente a propriedade de tempo salvo pela última vez nos seus documentos do Word usando o Aspose.Words para .NET. Isso é especialmente útil para manter metadados precisos em seus documentos, o que pode ser crucial para sistemas de gerenciamento de documentos e diversos outros aplicativos.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma biblioteca poderosa para criar, editar e converter documentos do Word em aplicativos .NET.

### Por que devo atualizar a última propriedade de tempo salva?
Atualizar a última propriedade de tempo salva ajuda a manter metadados precisos, o que é essencial para o rastreamento e gerenciamento de documentos.

### Posso atualizar outras propriedades usando o Aspose.Words para .NET?
Sim, o Aspose.Words para .NET permite que você atualize várias propriedades do documento, como título, autor e assunto.

### Aspose.Words para .NET é gratuito?
O Aspose.Words para .NET oferece um teste gratuito, mas para funcionalidade completa, é necessária uma licença. Você pode obter uma licença [aqui](https://purchase.aspose.com/buy).

### Onde posso encontrar mais tutoriais sobre Aspose.Words para .NET?
Você pode encontrar mais tutoriais e documentação [aqui](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}