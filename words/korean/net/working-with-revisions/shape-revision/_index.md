---
title: 모양 수정
linktitle: 모양 수정
second_title: Aspose.Words 문서 처리 API
description: 이 포괄적인 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 모양 수정을 처리하는 방법을 알아보세요. 변경 사항 추적, 모양 삽입 등을 마스터하세요.
weight: 10
url: /ko/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 모양 수정

## 소개

Word 문서를 프로그래밍 방식으로 편집하는 것은 어려운 작업일 수 있으며, 특히 모양을 처리하는 경우 더욱 그렇습니다. 보고서를 만들거나, 템플릿을 디자인하거나, 단순히 문서 생성을 자동화하든 모양 수정을 추적하고 관리하는 기능은 매우 중요합니다. Aspose.Words for .NET은 이 프로세스를 원활하고 효율적으로 만드는 강력한 API를 제공합니다. 이 튜토리얼에서는 Word 문서에서 모양을 수정하는 세부 사항을 살펴보고, 문서를 쉽게 관리할 수 있는 도구와 지식을 갖추도록 하겠습니다.

## 필수 조건

코드를 살펴보기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

-  .NET용 Aspose.Words: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 개발 환경을 설정해야 합니다.
- C#에 대한 기본적인 이해: C# 프로그래밍 언어와 객체 지향 프로그래밍의 기본 개념에 익숙합니다.
- Word 문서: 작업할 Word 문서이지만, 튜토리얼을 진행하는 동안 직접 만들 수도 있습니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 임포트해 보겠습니다. 이를 통해 Word 문서와 도형을 처리하는 데 필요한 클래스와 메서드에 액세스할 수 있습니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1단계: 문서 디렉토리 설정

도형 작업을 시작하기 전에 문서 디렉토리 경로를 정의해야 합니다. 여기서 수정된 문서를 저장할 것입니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 새 문서 만들기

도형을 삽입하고 수정할 새 Word 문서를 만들어 보겠습니다.

```csharp
Document doc = new Document();
```

## 3단계: 인라인 모양 삽입

수정 사항을 추적하지 않고 문서에 인라인 모양을 삽입하는 것으로 시작하겠습니다. 인라인 모양은 텍스트와 함께 흐르는 모양입니다.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 4단계: 수정 사항 추적 시작

문서의 변경 사항을 추적하려면 개정 추적을 활성화해야 합니다. 이는 모양에 대한 수정 사항을 식별하는 데 필수적입니다.

```csharp
doc.StartTrackRevisions("John Doe");
```

## 5단계: 수정 사항이 있는 다른 모양 삽입

이제 개정 추적이 활성화되었으므로 다른 모양을 삽입해 보겠습니다. 이번에는 모든 변경 사항이 추적됩니다.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 6단계: 모양 검색 및 수정

문서의 모든 모양을 검색하여 필요에 따라 수정할 수 있습니다. 여기서 모양을 가져와서 첫 번째 모양을 제거합니다.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 7단계: 문서 저장

변경한 후에는 문서를 저장해야 합니다. 이렇게 하면 모든 개정 및 수정 사항이 저장됩니다.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 8단계: 모양 이동 수정 처리

모양이 이동되면 Aspose.Words는 이를 수정으로 추적합니다. 즉, 모양이 두 개 있는 것입니다. 하나는 원래 위치에 있고 다른 하나는 새 위치에 있습니다.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 결론

이제 Aspose.Words for .NET을 사용하여 Word 문서에서 모양 수정을 처리하는 방법을 성공적으로 배웠습니다. 문서 템플릿을 관리하든, 보고서를 자동화하든, 단순히 변경 사항을 추적하든, 이러한 기술은 매우 귀중합니다. 이 단계별 가이드를 따르면 기본 사항을 마스터했을 뿐만 아니라 보다 고급 문서 처리 기술에 대한 통찰력도 얻었습니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 개발자가 C#을 사용하여 프로그래밍 방식으로 Word 문서를 만들고, 수정하고, 변환할 수 있는 강력한 라이브러리입니다.

### Word 문서에서 다른 요소에 대한 변경 사항을 추적할 수 있나요?
네, Aspose.Words for .NET은 텍스트, 표 등 다양한 요소에 대한 변경 사항 추적을 지원합니다.

### Aspose.Words for .NET의 무료 평가판을 어떻게 받을 수 있나요?
 Aspose.Words for .NET의 무료 평가판을 받으실 수 있습니다.[여기](https://releases.aspose.com/).

### 프로그래밍 방식으로 수정 사항을 승인하거나 거부할 수 있나요?
네, Aspose.Words for .NET은 프로그래밍 방식으로 수정 내용을 수락하거나 거부하는 방법을 제공합니다.

### C# 외의 다른 .NET 언어에서도 Aspose.Words for .NET을 사용할 수 있나요?
물론입니다! Aspose.Words for .NET은 VB.NET 및 F#을 포함한 모든 .NET 언어와 함께 사용할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
