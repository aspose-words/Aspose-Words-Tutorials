---
title: 수직 앵커
linktitle: 수직 앵커
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서의 텍스트 상자에 대한 수직 앵커 위치를 설정하는 방법을 알아보세요. 쉬운 단계별 가이드가 포함되어 있습니다.
weight: 10
url: /ko/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 수직 앵커

## 소개

Word 문서에서 텍스트 상자 안에 텍스트가 정확히 어디에 나타나는지 제어해야 하는 경우가 있었나요? 텍스트 상자의 상단, 중간 또는 하단에 텍스트를 고정하고 싶으신가요? 그렇다면 올바른 위치에 있습니다! 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 텍스트 상자의 수직 앵커를 설정하는 방법을 살펴보겠습니다. 수직 앵커링은 컨테이너 내에서 원하는 위치에 텍스트를 정확하게 배치하는 마법의 지팡이라고 생각하면 됩니다. 시작할 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

수직 고정의 세부 사항을 살펴보기 전에 몇 가지 사항을 준비해야 합니다.

1.  Aspose.Words for .NET: Aspose.Words for .NET 라이브러리가 설치되어 있는지 확인하세요. 아직 설치되어 있지 않으면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
2. Visual Studio: 이 튜토리얼에서는 코딩을 위해 Visual Studio나 다른 .NET IDE를 사용한다고 가정합니다.
3. C#에 대한 기본 지식: C#와 .NET에 익숙하면 원활하게 따라갈 수 있습니다.

## 네임스페이스 가져오기

시작하려면 C# 코드에서 필요한 네임스페이스를 가져와야 합니다. 여기서 애플리케이션에 사용할 클래스와 메서드를 찾을 위치를 알려줍니다. 방법은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

이러한 네임스페이스는 문서와 도형을 사용하는 데 필요한 클래스를 제공합니다.

## 1단계: 문서 초기화

가장 먼저 해야 할 일은 새 Word 문서를 만드는 것입니다. 이것은 그림을 그리기 전에 캔버스를 설정하는 것으로 생각하면 됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 여기,`Document` 당신의 빈 캔버스이고,`DocumentBuilder` 은 페인트브러시로, 모양과 텍스트를 추가할 수 있습니다.

## 2단계: 텍스트 상자 모양 삽입

이제 문서에 텍스트 상자를 추가해 보겠습니다. 여기에 텍스트가 들어갈 것입니다. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 이 예에서,`ShapeType.TextBox` 원하는 모양을 지정하고`200, 200` 텍스트 상자의 너비와 높이를 포인트로 나타냅니다.

## 3단계: 수직 앵커 설정

마법이 일어나는 곳이 바로 여기입니다! 텍스트 상자 내에서 텍스트의 수직 정렬을 설정할 수 있습니다. 이는 텍스트가 텍스트 상자의 상단, 중간 또는 하단에 고정되는지 여부를 결정합니다.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 이 경우에는,`TextBoxAnchor.Bottom`텍스트가 텍스트 상자의 맨 아래에 고정되도록 합니다. 가운데 정렬하거나 위쪽에 정렬하려면 다음을 사용합니다.`TextBoxAnchor.Center` 또는`TextBoxAnchor.Top`각각.

## 4단계: 텍스트 상자에 텍스트 추가

이제 텍스트 상자에 내용을 추가할 시간입니다. 캔버스에 마지막 터치를 채우는 것으로 생각하세요.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 여기,`MoveTo` 텍스트가 텍스트 상자에 삽입되었는지 확인합니다.`Write` 실제 텍스트를 추가합니다.

## 5단계: 문서 저장

마지막 단계는 문서를 저장하는 것입니다. 이는 완성된 그림을 액자에 넣는 것과 같습니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## 결론

이제 다 봤습니다! Aspose.Words for .NET을 사용하여 Word 문서의 텍스트 상자 내에서 텍스트의 수직 정렬을 제어하는 방법을 방금 배웠습니다. 텍스트를 위쪽, 가운데 또는 아래쪽에 고정하든 이 기능을 사용하면 문서의 레이아웃을 정확하게 제어할 수 있습니다. 따라서 다음에 문서의 텍스트 배치를 조정해야 할 때 무엇을 해야 할지 알게 될 것입니다!

## 자주 묻는 질문

### Word 문서의 수직 앵커링이란 무엇입니까?
수직 앵커링은 텍스트 상자 내에서 텍스트가 배치되는 위치(위쪽, 중간, 아래쪽 정렬 등)를 제어합니다.

### 텍스트 상자 외에 다른 모양을 사용할 수 있나요?
네, 다른 도형에도 수직 앵커링을 사용할 수 있지만 텍스트 상자가 가장 일반적으로 사용되는 사례입니다.

### 텍스트 상자를 만든 후 앵커 포인트를 변경하려면 어떻게 해야 하나요?
 앵커포인트를 설정하여 변경할 수 있습니다.`VerticalAnchor` 텍스트 상자 모양 개체의 속성입니다.

### 텍스트 상자의 중앙에 텍스트를 고정할 수 있나요?
 물론입니다! 그냥 사용하세요`TextBoxAnchor.Center` 텍스트 상자 내에서 텍스트를 수직으로 가운데 정렬합니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?
 확인해보세요[Aspose.Words 문서](https://reference.aspose.com/words/net/) 자세한 내용과 가이드는 여기에서 확인하세요.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
