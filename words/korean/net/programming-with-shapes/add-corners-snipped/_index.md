---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 모서리가 잘린 모양을 추가하는 방법을 알아보세요. 이 단계별 가이드를 통해 문서를 쉽게 개선할 수 있습니다."
"linktitle": "모서리 잘라내기 추가"
"second_title": "Aspose.Words 문서 처리 API"
"title": "모서리 잘라내기 추가"
"url": "/ko/net/programming-with-shapes/add-corners-snipped/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 모서리 잘라내기 추가

## 소개

Word 문서에 사용자 지정 도형을 추가하면 중요한 정보를 강조하거나 콘텐츠에 개성을 더하는 재미있고 시각적으로 매력적인 방법이 될 수 있습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에 "모서리 잘라낸" 도형을 삽입하는 방법을 자세히 알아보겠습니다. 이 가이드에서는 모든 단계를 안내하여 이러한 도형을 손쉽게 추가하고 전문가처럼 문서를 사용자 지정할 수 있도록 도와드립니다.

## 필수 조건

코드로 넘어가기 전에 시작하는 데 필요한 모든 것이 있는지 확인해 보겠습니다.

1. .NET용 Aspose.Words: 아직 다운로드하지 않았다면 다음에서 최신 버전을 다운로드하세요. [Aspose 릴리스 페이지](https://releases.aspose.com/words/net/).
2. 개발 환경: 개발 환경을 설정하세요. Visual Studio가 널리 사용되지만, .NET을 지원하는 다른 IDE도 사용할 수 있습니다.
3. 라이센스: 실험만 하고 있다면 다음을 사용할 수 있습니다. [무료 체험](https://releases.aspose.com/) 또는 얻을 [임시 면허](https://purchase.aspose.com/temporary-license/) 모든 기능을 사용하려면.
4. C#에 대한 기본적인 이해: C# 프로그래밍에 대한 지식이 있으면 예제를 따라가는 데 도움이 됩니다.

## 네임스페이스 가져오기

Aspose.Words for .NET 작업을 시작하기 전에 필요한 네임스페이스를 가져와야 합니다. C# 파일 맨 위에 다음 네임스페이스를 추가하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

이제 "모서리 잘라내기" 도형을 추가하는 과정을 여러 단계로 나누어 살펴보겠습니다. 모든 것이 원활하게 진행되도록 다음 단계를 꼼꼼히 따르세요.

## 1단계: 문서 및 DocumentBuilder 초기화

우리가 가장 먼저 해야 할 일은 새 문서를 만들고 초기화하는 것입니다. `DocumentBuilder` 객체입니다. 이 빌더는 문서에 콘텐츠를 추가하는 데 도움이 됩니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 단계에서는 문서와 빌더를 설정했습니다. 다음을 생각해 보세요. `DocumentBuilder` 디지털 펜으로 Word 문서에 글을 쓰고 그림을 그릴 수 있습니다.

## 2단계: 모서리 잘라낸 모양 삽입

다음으로, 우리는 다음을 사용할 것입니다. `DocumentBuilder` "모서리 잘라내기" 도형을 삽입합니다. 이 도형 유형은 Aspose.Words에 미리 정의되어 있으며, 한 줄의 코드로 쉽게 삽입할 수 있습니다.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

여기서는 도형 유형과 크기(50x50)를 지정합니다. 문서에 작고 완벽하게 잘린 모서리 스티커를 붙인다고 상상해 보세요. 

## 3단계: 규정 준수를 위한 저장 옵션 정의

문서를 저장하기 전에 문서가 특정 표준을 준수하도록 저장 옵션을 정의해야 합니다. 여기서는 다음을 사용합니다. `OoxmlSaveOptions` 이에 대한 수업입니다.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

이러한 저장 옵션은 문서가 호환성과 문서 수명에 중요한 ISO/IEC 29500:2008 표준을 준수하도록 보장합니다.

## 4단계: 문서 저장

마지막으로, 앞서 정의한 저장 옵션을 사용하여 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

이렇게 하면 이제 문서에 필요한 규정 준수 옵션과 함께 저장된 사용자 지정 "모서리 잘라내기" 모양이 포함됩니다.

## 결론

자, 이제 완성입니다! Aspose.Words for .NET을 사용하여 Word 문서에 사용자 지정 도형을 추가하는 것은 간단하며, 문서의 시각적인 매력을 크게 향상시킬 수 있습니다. 다음 단계를 따라 하면 "모서리 잘라낸" 도형을 쉽게 삽입하고 문서가 필요한 기준을 충족하는지 확인할 수 있습니다. 즐거운 코딩 되세요!

## 자주 묻는 질문

### "모서리 잘라내기" 모양의 크기를 사용자 지정할 수 있나요?
네, 치수를 변경하여 크기를 조정할 수 있습니다. `InsertShape` 방법.

### 다른 유형의 모양을 추가하는 것은 가능합니까?
물론입니다! Aspose.Words는 다양한 모양을 지원합니다. `ShapeType` 원하는 모양으로 만들어보세요.

### Aspose.Words를 사용하려면 라이센스가 필요합니까?
무료 평가판이나 임시 라이선스를 사용할 수 있지만, 제한 없이 사용하려면 전체 라이선스가 필요합니다.

### 모양을 더욱 스타일리시하게 꾸미려면 어떻게 해야 하나요?
Aspose.Words가 제공하는 추가 속성과 메서드를 사용하여 모양의 모양과 동작을 사용자 지정할 수 있습니다.

### Aspose.Words는 다른 형식과 호환됩니까?
네, Aspose.Words는 DOCX, PDF, HTML 등 다양한 문서 형식을 지원합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}