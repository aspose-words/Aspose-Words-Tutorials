---
title: Word 문서의 문단에 테두리와 음영 적용
linktitle: Word 문서의 문단에 테두리와 음영 적용
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서의 문단에 테두리와 음영을 적용합니다. 단계별 가이드를 따라 문서 서식을 개선하세요.
weight: 10
url: /ko/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서의 문단에 테두리와 음영 적용

## 소개

안녕하세요, Word 문서에 멋진 테두리와 음영을 넣어 돋보이게 하는 방법을 생각해 본 적이 있나요? 글쎄요, 당신은 올바른 곳에 있습니다! 오늘은 Aspose.Words for .NET의 세계로 뛰어들어 문단을 멋지게 꾸며보겠습니다. 몇 줄의 코드만으로 전문 디자이너의 작품처럼 매끈하게 보이는 문서를 상상해보세요. 시작할 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

소매를 걷어붙이고 코딩에 뛰어들기 전에 필요한 모든 것이 있는지 확인해 보겠습니다. 간단한 체크리스트는 다음과 같습니다.

-  Aspose.Words for .NET: 이 라이브러리를 설치해야 합니다. 다음에서 다운로드할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio 또는 .NET을 지원하는 다른 IDE.
- C#에 대한 기본 지식: 코드 조각을 이해하고 수정하는 데 필요한 지식입니다.
- 유효한 라이센스:[임시 면허](https://purchase.aspose.com/temporary-license/) 또는 구매한 것[추정하다](https://purchase.aspose.com/buy).

## 네임스페이스 가져오기

코드로 넘어가기 전에, 우리는 프로젝트에 필요한 네임스페이스를 가져왔는지 확인해야 합니다. 이렇게 하면 Aspose.Words의 모든 멋진 기능을 사용할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

이제 프로세스를 한 입 크기 단계로 나누어 보겠습니다. 각 단계에는 제목과 자세한 설명이 있습니다. 준비되셨나요? 시작해 봅시다!

## 1단계: 문서 디렉토리 설정

우선, 우리는 아름답게 포맷된 문서를 저장할 장소가 필요합니다. 문서 디렉토리로 경로를 설정해 보겠습니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 이 디렉토리는 최종 문서가 저장되는 곳입니다. 바꾸기`"YOUR DOCUMENT DIRECTORY"` 컴퓨터의 실제 경로와 일치합니다.

## 2단계: 새 문서 및 DocumentBuilder 만들기

 다음으로 새 문서를 만들어야 합니다.`DocumentBuilder` 객체.`DocumentBuilder` 문서를 조작할 수 있는 마법의 지팡이입니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 그만큼`Document` 객체는 전체 Word 문서를 나타내며`DocumentBuilder` 콘텐츠를 추가하고 형식을 지정하는 데 도움이 됩니다.

## 3단계: 문단 테두리 정의

이제 문단에 스타일리시한 테두리를 추가해 보겠습니다. 텍스트와의 거리를 정의하고 다양한 테두리 스타일을 설정하겠습니다.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

여기서는 텍스트와 테두리 사이에 20포인트 간격을 설정합니다. 모든 면(왼쪽, 오른쪽, 위, 아래)의 테두리는 두 줄로 설정됩니다. 멋지죠?

## 4단계: 문단에 음영 적용

테두리는 좋지만, 음영을 넣어 한 단계 더 높여 봅시다. 우리는 색상을 혼합한 대각선 교차 패턴을 사용하여 문단을 돋보이게 만들 것입니다.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

이 단계에서는 배경색으로 밝은 산호색, 전경색으로 밝은 연어색을 사용하여 대각선 십자가 텍스처를 적용했습니다. 마치 문단에 디자이너 옷을 입히는 것과 같습니다!

## 5단계: 문단에 텍스트 추가

텍스트가 없는 문단이란 무엇인가? 우리의 서식이 실제로 어떻게 적용되는지 보기 위해 샘플 문장을 추가해 보자.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

이 줄은 우리의 텍스트를 문서에 삽입합니다. 간단하지만, 지금은 세련된 프레임과 음영이 있는 배경으로 감싸져 있습니다.

## 6단계: 문서 저장

마지막으로, 작업을 저장할 시간입니다. 설명적인 이름으로 지정된 디렉토리에 문서를 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 이렇게 하면 문서가 다음 이름으로 저장됩니다.`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` 이전에 지정한 디렉토리에 있습니다.

## 결론

이제 다 됐습니다! 몇 줄의 코드만으로 평범한 문단을 시각적으로 매력적인 콘텐츠로 변환했습니다. Aspose.Words for .NET을 사용하면 문서에 전문적인 서식을 추가하는 것이 매우 쉽습니다. 보고서, 편지 또는 문서를 준비하든 이러한 요령을 사용하면 좋은 인상을 남길 수 있습니다. 계속해서 시도해 보고 문서가 생동감 있게 표현되는 것을 지켜보세요!

## 자주 묻는 질문

### 각 테두리에 다른 선 스타일을 사용할 수 있나요?  
 물론입니다! Aspose.Words for .NET을 사용하면 각 테두리를 개별적으로 사용자 지정할 수 있습니다.`LineStyle` 가이드에 표시된 대로 각 테두리 유형에 맞게.

### 다른 음영 텍스처는 무엇이 있나요?  
 사용할 수 있는 텍스처는 단색, 가로줄무늬, 세로줄무늬 등 여러 가지가 있습니다. 다음을 확인하세요.[Aspose 문서](https://reference.aspose.com/words/net/) 전체 목록은 여기에서 확인하세요.

### 테두리 색상을 어떻게 바꿀 수 있나요?  
 테두리 색상은 다음을 사용하여 설정할 수 있습니다.`Color` 각 테두리에 대한 속성입니다. 예를 들어,`borders[BorderType.Left].Color = Color.Red;`.

### 텍스트의 특정 부분에 테두리와 음영을 적용할 수 있나요?  
 예, 다음을 사용하여 특정 텍스트 실행에 테두리와 음영을 적용할 수 있습니다.`Run` 객체 내부`DocumentBuilder`.

### 여러 문단에 대해 이 과정을 자동화할 수 있나요?  
물론이죠! 문단을 반복해서 살펴보고 동일한 테두리와 음영 설정을 프로그래밍 방식으로 적용할 수 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
