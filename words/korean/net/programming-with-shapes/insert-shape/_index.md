---
title: 모양 삽입
linktitle: 모양 삽입
second_title: Aspose.Words 문서 처리 API
description: 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에 모양을 삽입하고 조작하는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-shapes/insert-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 모양 삽입

## 소개

시각적으로 매력적이고 잘 구성된 Word 문서를 만드는 데 있어서 모양은 중요한 역할을 할 수 있습니다. 화살표, 상자 또는 복잡한 사용자 지정 모양을 추가하든 이러한 요소를 프로그래밍 방식으로 조작하는 기능은 비교할 수 없는 유연성을 제공합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에 모양을 삽입하고 조작하는 방법을 살펴보겠습니다.

## 필수 조건

튜토리얼을 시작하기 전에 다음 필수 조건이 충족되었는지 확인하세요.

1.  .NET용 Aspose.Words: 다음에서 최신 버전을 다운로드하여 설치하세요.[Aspose 릴리스 페이지](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio와 같은 적합한 .NET 개발 환경.
3. C#에 대한 기본 지식: C# 프로그래밍 언어와 기본 개념에 익숙함.

## 네임스페이스 가져오기

시작하려면 C# 프로젝트에 필요한 네임스페이스를 가져와야 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1단계: 프로젝트 설정

도형 삽입을 시작하기 전에 프로젝트를 설정하고 Aspose.Words for .NET 라이브러리를 추가해야 합니다.

1. 새 프로젝트 만들기: Visual Studio를 열고 새 C# 콘솔 애플리케이션 프로젝트를 만듭니다.
2. Aspose.Words for .NET 추가: NuGet 패키지 관리자를 통해 Aspose.Words for .NET 라이브러리를 설치합니다.

```bash
Install-Package Aspose.Words
```

## 2단계: 문서 초기화

먼저, 새 문서와 문서 작성기를 초기화해야 합니다. 이는 문서 구성에 도움이 됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 새 문서 초기화
Document doc = new Document();

// 문서 작성을 돕기 위해 DocumentBuilder를 초기화합니다.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 3단계: 모양 삽입

이제 문서에 모양을 삽입해 보겠습니다. 간단한 텍스트 상자를 추가하는 것으로 시작하겠습니다.

```csharp
// 문서에 텍스트 상자 모양 삽입
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// 모양을 회전합니다
shape.Rotation = 30.0;
```

이 예에서 우리는 위치 (100, 100)에 각각 50단위의 너비와 높이를 가진 텍스트 상자를 삽입합니다. 또한 모양을 30도 회전합니다.

## 4단계: 다른 모양 추가

이번에는 위치를 지정하지 않고 문서에 다른 모양을 추가해 보겠습니다.

```csharp
// 다른 텍스트 상자 모양 추가
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// 모양을 회전합니다
secondShape.Rotation = 30.0;
```

이 코드 조각은 첫 번째 텍스트 상자와 동일한 크기와 회전을 갖는 다른 텍스트 상자를 삽입하지만 위치는 지정하지 않습니다.

## 5단계: 문서 저장

 모양을 추가한 후 마지막 단계는 문서를 저장하는 것입니다.`OoxmlSaveOptions` 저장 형식을 지정합니다.

```csharp
// 규정 준수를 통해 저장 옵션 정의
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// 문서를 저장하세요
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 결론

이제 다 됐습니다! Aspose.Words for .NET을 사용하여 Word 문서에 모양을 성공적으로 삽입하고 조작했습니다. 이 튜토리얼에서는 기본 사항을 다루었지만 Aspose.Words는 사용자 지정 스타일, 커넥터, 그룹 모양과 같은 모양을 작업하기 위한 훨씬 더 고급 기능을 제공합니다.

 더 자세한 정보는 다음을 방문하세요.[.NET 설명서를 위한 Aspose.Words](https://reference.aspose.com/words/net/).

## 자주 묻는 질문

### 다양한 유형의 모양을 삽입하려면 어떻게 해야 하나요?
변경할 수 있습니다`ShapeType` 에서`InsertShape` 원, 사각형, 화살표 등 다양한 도형을 삽입하는 방법입니다.

### 모양 안에 텍스트를 추가할 수 있나요?
 네, 사용할 수 있습니다`builder.Write` 모양을 삽입한 후 모양 안에 텍스트를 추가하는 방법입니다.

### 모양에 스타일을 적용할 수 있나요?
 예, 다음과 같은 속성을 설정하여 모양에 스타일을 지정할 수 있습니다.`FillColor`, `StrokeColor` , 그리고`StrokeWeight`.

### 다른 요소에 상대적으로 모양을 배치하려면 어떻게 해야 하나요?
 사용하세요`RelativeHorizontalPosition` 그리고`RelativeVerticalPosition` 문서 내 다른 요소에 상대적으로 모양을 배치하는 속성입니다.

### 여러 개의 모양을 함께 그룹화할 수 있나요?
 예, Aspose.Words for .NET을 사용하면 다음을 사용하여 모양을 그룹화할 수 있습니다.`GroupShape` 수업.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
