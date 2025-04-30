---
"description": "Aprenda a habilitar ou desabilitar a substituição de fontes em documentos do Word usando o Aspose.Words para .NET. Garanta a consistência da aparência dos seus documentos em todas as plataformas."
"linktitle": "Habilitar Desabilitar Substituição de Fonte"
"second_title": "API de processamento de documentos Aspose.Words"
"title": "Habilitar Desabilitar Substituição de Fonte"
"url": "/pt/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar Desabilitar Substituição de Fonte

## Introdução

Já se viu em uma situação em que suas fontes meticulosamente selecionadas em um documento do Word são substituídas quando visualizadas em outro computador? Irritante, não é? Isso acontece devido à substituição de fontes, um processo em que o sistema substitui uma fonte ausente por uma disponível. Mas não se preocupe! Com o Aspose.Words para .NET, você pode gerenciar e controlar facilmente a substituição de fontes. Neste tutorial, mostraremos os passos para habilitar ou desabilitar a substituição de fontes em seus documentos do Word, garantindo que seus documentos sempre tenham a aparência que você deseja.

## Pré-requisitos

Antes de começarmos, vamos garantir que você tenha tudo o que precisa:

- Aspose.Words para .NET: Baixe a versão mais recente [aqui](https://releases.aspose.com/words/net/).
- Visual Studio: qualquer versão com suporte ao .NET.
- Conhecimento básico de C#: Isso ajudará você a acompanhar os exemplos de codificação.

## Importar namespaces

Para começar, certifique-se de ter os namespaces necessários importados para o seu projeto. Adicione-os no início do seu arquivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Agora, vamos dividir o processo em etapas simples e gerenciáveis.

## Etapa 1: Configure seu projeto

Primeiro, configure um novo projeto no Visual Studio e adicione uma referência à biblioteca Aspose.Words para .NET. Se ainda não o fez, baixe-a do [Site Aspose](https://releases.aspose.com/words/net/).

## Etapa 2: carregue seu documento

Em seguida, carregue o documento com o qual deseja trabalhar. Veja como fazer:

```csharp
// Caminho para o diretório do seu documento 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Substituir `"YOUR DOCUMENT DIRECTORY"` com o caminho real para o diretório do seu documento. Este código carrega o documento na memória para que você possa manipulá-lo.

## Etapa 3: Configurar as configurações de fonte

Agora, vamos criar um `FontSettings` objeto para gerenciar as configurações de substituição de fonte:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Etapa 4: definir a substituição de fonte padrão

Defina a substituição de fonte padrão para uma fonte de sua escolha. Esta fonte será usada caso a fonte original não esteja disponível:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Neste exemplo, estamos usando Arial como fonte padrão.

## Etapa 5: Desabilitar a substituição de informações da fonte

Para desabilitar a substituição de informações de fonte, o que impede o sistema de substituir fontes ausentes por fontes disponíveis, use o seguinte código:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Etapa 6: aplicar configurações de fonte ao documento

Agora, aplique estas configurações ao seu documento:

```csharp
doc.FontSettings = fontSettings;
```

## Etapa 7: Salve seu documento

Por fim, salve o documento modificado. Você pode salvá-lo em qualquer formato que desejar. Para este tutorial, salvaremos como PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusão

Pronto! Seguindo estes passos, você pode controlar facilmente a substituição de fontes em seus documentos do Word usando o Aspose.Words para .NET. Isso garante que seus documentos mantenham a aparência original, independentemente de onde sejam visualizados.

## Perguntas frequentes

### Posso usar outras fontes além da Arial para substituição?

Com certeza! Você pode especificar qualquer fonte disponível em seu sistema alterando o nome da fonte no `DefaultFontName` propriedade.

### que acontece se a fonte padrão especificada não estiver disponível?

Se a fonte padrão não estiver disponível, o Aspose.Words usará um mecanismo de fallback do sistema para encontrar uma substituição apropriada.

### Posso habilitar a substituição de fonte novamente depois de desabilitá-la?

Sim, você pode alternar o `Enabled` propriedade de `FontInfoSubstitution` de volta para `true` se você quiser habilitar a substituição de fonte novamente.

### Existe uma maneira de verificar quais fontes estão sendo substituídas?

Sim, o Aspose.Words fornece métodos para registrar e rastrear a substituição de fontes, permitindo que você veja quais fontes estão sendo substituídas.

### Posso usar esse método para outros formatos de documento além de DOCX?

Com certeza! O Aspose.Words suporta vários formatos, e você pode aplicar essas configurações de fonte a qualquer formato compatível.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}