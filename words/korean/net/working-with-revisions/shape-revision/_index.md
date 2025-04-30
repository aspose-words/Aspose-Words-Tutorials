---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에서 도형 수정을 처리하는 방법을 이 포괄적인 가이드를 통해 알아보세요. 변경 내용 추적, 도형 삽입 등의 기능을 완벽하게 익힐 수 있습니다."
"linktitle": "모양 수정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "모양 수정"
"url": "/ko/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 모양 수정

## 소개

Word 문서를 프로그래밍 방식으로 편집하는 것은, 특히 도형을 다룰 때 매우 어려운 작업일 수 있습니다. 보고서 작성, 템플릿 디자인, 또는 단순히 문서 생성 자동화 등 어떤 작업을 하든 도형 수정 사항을 추적하고 관리하는 기능은 매우 중요합니다. Aspose.Words for .NET은 이 과정을 원활하고 효율적으로 만들어 주는 강력한 API를 제공합니다. 이 튜토리얼에서는 Word 문서에서 도형을 수정하는 구체적인 방법을 살펴보고, 문서를 손쉽게 관리할 수 있는 도구와 지식을 갖추도록 하겠습니다.

## 필수 조건

코드를 살펴보기 전에 먼저 필요한 모든 것이 있는지 확인해 보겠습니다.

- Aspose.Words for .NET: Aspose.Words 라이브러리가 설치되어 있는지 확인하세요. [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 개발 환경을 설정해야 합니다.
- C#에 대한 기본 이해: C# 프로그래밍 언어와 객체 지향 프로그래밍의 기본 개념에 익숙함.
- Word 문서: 작업할 Word 문서이거나 튜토리얼을 진행하는 동안 직접 만들 수 있습니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져오겠습니다. 이를 통해 Word 문서와 도형을 처리하는 데 필요한 클래스와 메서드에 접근할 수 있습니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1단계: 문서 디렉터리 설정

도형 작업을 시작하기 전에 문서 디렉터리 경로를 정의해야 합니다. 수정된 문서는 여기에 저장됩니다.

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

수정 사항을 추적하지 않고 문서에 인라인 도형을 삽입하는 것부터 시작해 보겠습니다. 인라인 도형은 텍스트와 함께 흐르는 도형입니다.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 4단계: 수정 사항 추적 시작

문서의 변경 사항을 추적하려면 수정 사항 추적을 활성화해야 합니다. 이는 도형의 수정 사항을 파악하는 데 필수적입니다.

```csharp
doc.StartTrackRevisions("John Doe");
```

## 5단계: 수정 사항을 적용한 다른 모양 삽입

이제 수정 내용 추적이 활성화되었으니, 다른 도형을 삽입해 보겠습니다. 이번에는 모든 변경 내용이 추적됩니다.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 6단계: 모양 검색 및 수정

문서의 모든 도형을 가져와 필요에 따라 수정할 수 있습니다. 여기서는 도형을 가져와서 첫 번째 도형을 제거합니다.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 7단계: 문서 저장

변경 사항을 적용한 후에는 문서를 저장해야 합니다. 이렇게 하면 모든 수정 사항과 변경 사항이 저장됩니다.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 8단계: 모양 이동 수정 처리

도형이 이동되면 Aspose.Words는 이를 수정 사항으로 추적합니다. 즉, 도형은 두 개로 생성됩니다. 하나는 원래 위치에, 다른 하나는 새 위치에 있습니다.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 결론

자, 이제 Aspose.Words for .NET을 사용하여 Word 문서의 도형 수정을 처리하는 방법을 성공적으로 익혔습니다. 문서 템플릿 관리, 보고서 자동화, 또는 단순히 변경 사항 추적 등 어떤 작업을 하든 이러한 기술은 매우 중요합니다. 이 단계별 가이드를 따라가면 기본 기능을 익힐 뿐만 아니라 고급 문서 처리 기술에 대한 통찰력도 얻을 수 있습니다.

## 자주 묻는 질문

### Aspose.Words for .NET이란 무엇인가요?
Aspose.Words for .NET은 개발자가 C#을 사용하여 Word 문서를 프로그래밍 방식으로 만들고, 수정하고, 변환할 수 있는 강력한 라이브러리입니다.

### Word 문서에서 다른 요소에 적용된 변경 사항을 추적할 수 있나요?
네, Aspose.Words for .NET은 텍스트, 표 등 다양한 요소의 변경 사항 추적을 지원합니다.

### Aspose.Words for .NET의 무료 평가판을 받으려면 어떻게 해야 하나요?
Aspose.Words for .NET의 무료 평가판을 받아보세요. [여기](https://releases.aspose.com/).

### 프로그래밍 방식으로 수정 사항을 승인하거나 거부할 수 있나요?
네, Aspose.Words for .NET은 프로그래밍 방식으로 수정 사항을 수락하거나 거부하는 방법을 제공합니다.

### C# 외의 다른 .NET 언어와 함께 Aspose.Words for .NET을 사용할 수 있나요?
물론입니다! Aspose.Words for .NET은 VB.NET과 F#을 포함한 모든 .NET 언어에서 사용할 수 있습니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}