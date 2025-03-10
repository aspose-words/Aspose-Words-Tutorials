---
title: Hifenização de retorno de chamada
linktitle: Hifenização de retorno de chamada
second_title: API de processamento de documentos Aspose.Words
description: Aprenda a implementar o retorno de chamada de hifenização no Aspose.Words para .NET para melhorar a formatação de documentos com este guia passo a passo abrangente.
weight: 10
url: /pt/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hifenização de retorno de chamada


## Introdução

Olá! Já se viu enredado nas complexidades da formatação de texto, especialmente ao lidar com idiomas que exigem hifenização? Você não está sozinho. A hifenização, embora crucial para o layout adequado do texto, pode ser uma dor de cabeça. Mas adivinhe? O Aspose.Words para .NET está aqui para ajudar. Esta biblioteca poderosa permite que você gerencie a formatação de texto perfeitamente, incluindo o tratamento de hifenização por meio de um mecanismo de retorno de chamada. Intrigado? Vamos mergulhar nos detalhes de como você pode implementar um retorno de chamada de hifenização usando o Aspose.Words para .NET.

## Pré-requisitos

Antes de colocarmos a mão na massa com o código, vamos garantir que você tenha tudo o que precisa:

1. Aspose.Words para .NET: Certifique-se de ter a biblioteca. Você pode[baixe aqui](https://releases.aspose.com/words/net/).
2. IDE: Um ambiente de desenvolvimento como o Visual Studio.
3. Conhecimento básico de C#: compreensão do C# e do framework .NET.
4. Dicionários de hifenização: dicionários de hifenização para os idiomas que você planeja usar.
5.  Licença Aspose: Uma licença Aspose válida. Você pode obter uma[licença temporária](https://purchase.aspose.com/temporary-license/) se você não tiver um.

## Importar namespaces

Primeiro, vamos importar os namespaces necessários. Isso garante que nosso código tenha acesso a todas as classes e métodos que precisamos do Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Etapa 1: registre o retorno de chamada de hifenização

Para começar, precisamos registrar nosso callback de hifenização. É aqui que dizemos ao Aspose.Words para usar nossa lógica de hifenização personalizada.

```csharp
try
{
    // Registrar retorno de chamada de hifenização.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Aqui, estamos criando uma instância do nosso retorno de chamada personalizado e atribuindo-a a`Hyphenation.Callback`.

## Etapa 2: Defina o caminho do documento

Em seguida, precisamos definir o diretório onde nossos documentos estão armazenados. Isso é crucial, pois carregaremos e salvaremos documentos desse caminho.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Substituir`"YOUR DOCUMENT DIRECTORY"` com o caminho real para seus documentos.

## Etapa 3: Carregue o documento

Agora, vamos carregar o documento que requer hifenização.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Aqui, estamos carregando um documento de texto em alemão. Você pode substituir`"German text.docx"` com o nome do arquivo do seu documento.

## Etapa 4: Salve o documento

Após carregar o documento, salvamos ele em um novo arquivo, aplicando o retorno de chamada de hifenização no processo.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Esta linha salva o documento como um PDF com hifenização aplicada.

## Etapa 5: Lidar com a exceção do dicionário de hifenização ausente

Às vezes, você pode se deparar com um problema em que o dicionário de hifenização está faltando. Vamos lidar com isso.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Neste bloco, capturamos a exceção específica relacionada a dicionários ausentes e imprimimos a mensagem.

## Etapa 6: Implementar a classe de retorno de chamada de hifenização personalizada

 Agora, vamos implementar o`CustomHyphenationCallback` classe que manipula a solicitação de dicionários de hifenização.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Registre o dicionário para o idioma solicitado.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 Nesta aula, o`RequestDictionary` O método é chamado sempre que um dicionário de hifenização é necessário. Ele verifica o idioma e registra o dicionário apropriado.

## Conclusão

aí está! Você acabou de aprender como implementar um callback de hifenização no Aspose.Words para .NET. Seguindo essas etapas, você pode garantir que seus documentos estejam lindamente formatados, independentemente do idioma. Não importa se você está lidando com inglês, alemão ou qualquer outro idioma, esse método permite que você lide com a hifenização sem esforço.

## Perguntas frequentes

### O que é Aspose.Words para .NET?
Aspose.Words para .NET é uma poderosa biblioteca de manipulação de documentos que permite aos desenvolvedores criar, modificar e converter documentos programaticamente.

### Por que a hifenização é importante na formatação de documentos?
A hifenização melhora o layout do texto ao dividir as palavras em lugares apropriados, garantindo um documento mais legível e visualmente atraente.

### Posso usar o Aspose.Words gratuitamente?
 Aspose.Words oferece um teste gratuito. Você pode obtê-lo[aqui](https://releases.aspose.com/).

### Como obtenho um dicionário de hifenização?
Você pode baixar dicionários de hifenização de vários recursos online ou criar o seu próprio, se necessário.

### O que acontece se um dicionário de hifenização estiver faltando?
 Se faltar um dicionário, o`RequestDictionary` método lança uma exceção, que você pode manipular para informar o usuário ou fornecer um fallback.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
