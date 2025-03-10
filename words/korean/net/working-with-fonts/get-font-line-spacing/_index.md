---
title: 글꼴 줄 간격 가져오기
linktitle: 글꼴 줄 간격 가져오기
second_title: Aspose.Words 문서 처리 API
description: 이 단계별 튜토리얼을 통해 Aspose.Words for .NET을 사용하여 글꼴 줄 간격을 가져오는 방법을 알아보세요. 개발자에게 완벽합니다.
weight: 10
url: /ko/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 글꼴 줄 간격 가져오기

## 소개

Aspose.Words for .NET은 Word 문서를 프로그래밍 방식으로 만들고, 조작하고, 변환할 수 있는 강력한 라이브러리입니다. 수행해야 할 수 있는 일반적인 작업 중 하나는 문서에서 특정 글꼴의 줄 간격을 검색하는 것입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 글꼴 줄 간격을 쉽게 얻을 수 있도록 단계별로 프로세스를 안내합니다. 

## 필수 조건

코드를 살펴보기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1.  Aspose.Words for .NET 라이브러리: 최신 버전을 다운로드하여 설치하세요.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 IDE가 설정되어 있는지 확인하세요.
3. C#에 대한 기본 지식: 이 튜토리얼에서는 사용자가 C# 프로그래밍에 대한 기본적인 이해가 있다고 가정합니다.

## 네임스페이스 가져오기

먼저, C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다. 이러한 네임스페이스를 통해 Aspose.Words 기능에 액세스할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

글꼴 줄 간격을 조정하는 과정을 간단하고 관리하기 쉬운 단계로 나누어 보겠습니다.

## 1단계: 새 문서 만들기

첫 번째 단계는 Aspose.Words for .NET을 사용하여 새 Word 문서 인스턴스를 만드는 것입니다.

```csharp
Document doc = new Document();
```

## 2단계: DocumentBuilder 초기화

다음으로, 우리는 초기화해야 합니다.`DocumentBuilder` 객체. 이 객체는 문서 콘텐츠를 구성하고 조작하는 데 도움이 됩니다.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3단계: 글꼴 속성 설정

이제 삽입하려는 텍스트의 글꼴 속성을 설정합니다. 이 예에서는 "Calibri" 글꼴을 사용합니다.

```csharp
builder.Font.Name = "Calibri";
```

## 4단계: 문서에 텍스트 쓰기

 사용하여`DocumentBuilder` 객체, 문서에 텍스트를 씁니다. 이 텍스트는 이전 단계에서 설정한 글꼴 속성을 사용합니다.

```csharp
builder.Writeln("Sample Text");
```

## 5단계: 글꼴 개체 검색

줄 간격을 얻으려면 방금 추가한 텍스트의 글꼴 객체에 액세스해야 합니다. 이는 문서 구조를 탐색하여 첫 번째 문단 런으로 이동하면 됩니다.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## 6단계: 줄 간격 얻기

마지막으로 글꼴 객체에서 줄 간격을 검색하여 콘솔에 출력합니다.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## 결론

그리고 이제 알겠습니다! Aspose.Words for .NET을 사용하여 글꼴 줄 간격을 검색하는 것은 이러한 간단한 단계로 나누면 간단합니다. 새 문서를 만들든 기존 문서에서 작업하든 Aspose.Words는 글꼴 속성을 효율적으로 관리하는 데 필요한 모든 도구를 제공합니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 개발자가 C#을 사용하여 프로그래밍 방식으로 Word 문서를 만들고, 조작하고, 변환할 수 있는 강력한 라이브러리입니다.

### Aspose.Words for .NET을 다른 .NET 언어에서 사용할 수 있나요?
네, VB.NET 및 F#을 포함한 모든 .NET 언어에서 Aspose.Words for .NET을 사용할 수 있습니다.

### Aspose.Words for .NET을 어떻게 다운로드할 수 있나요?
 .NET용 Aspose.Words의 최신 버전은 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).

### Aspose.Words for .NET에 대한 무료 평가판이 있나요?
 네, 무료 체험판을 받으실 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Words for .NET에 대한 설명서는 어디에서 찾을 수 있나요?
 .NET용 Aspose.Words 설명서를 사용할 수 있습니다.[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
