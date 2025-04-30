---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에서 도형의 가로 세로 비율을 고정하는 방법을 알아보세요. 이 단계별 가이드를 따라 이미지와 도형의 비율을 유지하세요."
"linktitle": "종횡비 잠금"
"second_title": "Aspose.Words 문서 처리 API"
"title": "종횡비 잠금"
"url": "/ko/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 종횡비 잠금

## 소개

Word 문서에서 이미지와 도형의 완벽한 비율을 유지하는 방법이 궁금했던 적 있으신가요? 때로는 이미지와 도형의 크기를 조정할 때 왜곡되지 않도록 해야 할 때가 있습니다. 이럴 때 가로 세로 비율 고정 기능이 유용합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 도형의 가로 세로 비율을 설정하는 방법을 살펴보겠습니다. 따라 하기 쉬운 단계로 나누어 설명하므로, 이러한 기술을 프로젝트에 자신 있게 적용할 수 있습니다.

## 필수 조건

코드를 살펴보기 전에 시작하는 데 필요한 사항을 살펴보겠습니다.

- Aspose.Words for .NET 라이브러리: Aspose.Words for .NET이 설치되어 있어야 합니다. 아직 설치되어 있지 않다면 [여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: .NET 개발 환경이 설정되어 있는지 확인하세요. Visual Studio가 많이 사용됩니다.
- C#에 대한 기본 지식: C# 프로그래밍에 대한 약간의 지식이 도움이 됩니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져오겠습니다. 이 네임스페이스를 통해 Word 문서와 도형 작업에 필요한 클래스와 메서드에 접근할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1단계: 문서 디렉터리 설정

도형을 조작하기 전에 문서를 저장할 디렉터리를 설정해야 합니다. 편의상 자리 표시자를 사용하겠습니다. `YOUR DOCUMENT DIRECTORY`이것을 문서 디렉터리의 실제 경로로 바꾸세요.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 새 문서 만들기

다음으로 Aspose.Words를 사용하여 새 Word 문서를 만들어 보겠습니다. 이 문서는 도형과 이미지를 추가하는 캔버스 역할을 할 것입니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

여기서 우리는 인스턴스를 생성합니다. `Document` 클래스와 사용 `DocumentBuilder` 문서 내용을 작성하는 데 도움이 됩니다.

## 3단계: 이미지 삽입

이제 문서에 이미지를 삽입해 보겠습니다. `InsertImage` 방법 `DocumentBuilder` 클래스. 지정된 디렉토리에 이미지가 있는지 확인하세요.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

바꾸다 `dataDir + "Transparent background logo.png"` 이미지 파일의 경로를 포함합니다.

## 4단계: 화면 비율 잠금

이미지를 삽입한 후에는 가로 세로 비율을 고정할 수 있습니다. 가로 세로 비율을 고정하면 크기를 조정할 때 이미지의 비율이 일정하게 유지됩니다.

```csharp
shape.AspectRatioLocked = true;
```

환경 `AspectRatioLocked` 에게 `true` 이미지가 원래 종횡비를 유지하도록 보장합니다.

## 5단계: 문서 저장

마지막으로, 문서를 지정된 디렉터리에 저장합니다. 이 단계에서는 문서 파일에 적용된 모든 변경 사항이 기록됩니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서에서 도형의 가로 세로 비율을 설정하는 방법을 성공적으로 익히셨습니다. 이 단계를 따라 하면 이미지와 도형의 비율을 유지하여 문서를 전문적이고 세련되게 만들 수 있습니다. 다양한 이미지와 도형을 사용하여 가로 세로 비율 잠금 기능이 다양한 상황에서 어떻게 작동하는지 확인해 보세요.

## 자주 묻는 질문

### 잠금을 해제한 후에 화면 비율을 다시 잠금 해제할 수 있나요?
예, 종횡비를 설정하여 잠금 해제할 수 있습니다. `shape.AspectRatioLocked = false`.

### 고정된 종횡비로 이미지 크기를 조정하면 어떻게 되나요?
이미지는 원래의 너비 대 높이 비율을 유지하면서 비례적으로 크기가 조절됩니다.

### 이미지 외에 다른 모양에도 적용할 수 있나요?
물론입니다! 가로 세로 비율 잠금 기능은 사각형, 원 등 어떤 모양에도 적용할 수 있습니다.

### Aspose.Words for .NET은 .NET Core와 호환됩니까?
네, Aspose.Words for .NET은 .NET Framework와 .NET Core를 모두 지원합니다.

### Aspose.Words for .NET에 대한 추가 문서는 어디에서 찾을 수 있나요?
포괄적인 문서를 찾을 수 있습니다 [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}