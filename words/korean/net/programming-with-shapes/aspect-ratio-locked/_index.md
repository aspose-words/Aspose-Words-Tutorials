---
title: 화면 비율 잠금
linktitle: 화면 비율 잠금
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET을 사용하여 Word 문서에서 모양의 종횡비를 잠그는 방법을 알아보세요. 이 단계별 가이드를 따라 이미지와 모양의 비율을 유지하세요.
weight: 10
url: /ko/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 화면 비율 잠금

## 소개

Word 문서에서 이미지와 도형의 완벽한 비율을 유지하는 방법에 대해 생각해 본 적이 있나요? 때로는 이미지와 도형이 크기를 조정할 때 왜곡되지 않도록 해야 합니다. 이때 종횡비 잠금이 유용합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에서 도형의 종횡비를 설정하는 방법을 살펴보겠습니다. 쉽게 따를 수 있는 단계로 나누어서 프로젝트에 이러한 기술을 자신 있게 적용할 수 있도록 하겠습니다.

## 필수 조건

코드를 살펴보기 전에 시작하는 데 필요한 사항을 살펴보겠습니다.

- Aspose.Words for .NET 라이브러리: Aspose.Words for .NET이 설치되어 있어야 합니다. 아직 설치되어 있지 않으면 다음을 수행할 수 있습니다.[여기서 다운로드하세요](https://releases.aspose.com/words/net/).
- 개발 환경: .NET 개발 환경이 설정되어 있는지 확인하세요. Visual Studio가 인기 있는 선택입니다.
- C#에 대한 기본 지식: C# 프로그래밍에 대한 지식이 있으면 도움이 됩니다.

## 네임스페이스 가져오기

우선, 필요한 네임스페이스를 임포트해 보겠습니다. 이러한 네임스페이스는 Word 문서와 도형을 사용하는 데 필요한 클래스와 메서드에 대한 액세스를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1단계: 문서 디렉토리 설정

 도형을 조작하기 전에 문서를 저장할 디렉토리를 설정해야 합니다. 단순성을 위해 플레이스홀더를 사용하겠습니다.`YOUR DOCUMENT DIRECTORY`. 이것을 문서 디렉토리의 실제 경로로 바꾸세요.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2단계: 새 문서 만들기

다음으로 Aspose.Words를 사용하여 새 Word 문서를 만듭니다. 이 문서는 모양과 이미지를 추가하기 위한 캔버스 역할을 합니다.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 여기서 우리는 인스턴스를 생성합니다`Document` 수업과 사용`DocumentBuilder` 문서 내용을 구축하는 데 도움이 됩니다.

## 3단계: 이미지 삽입

 이제 문서에 이미지를 삽입해 보겠습니다. 우리는 다음을 사용할 것입니다.`InsertImage` 의 방법`DocumentBuilder`클래스. 지정된 디렉토리에 이미지가 있는지 확인하세요.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 바꾸다`dataDir + "Transparent background logo.png"` 이미지 파일의 경로를 포함합니다.

## 4단계: 종횡비 잠금

이미지가 삽입되면 종횡비를 잠글 수 있습니다. 종횡비를 잠그면 크기를 조정할 때 이미지의 비율이 일정하게 유지됩니다.

```csharp
shape.AspectRatioLocked = true;
```

 환경`AspectRatioLocked` 에게`true` 이미지가 원래 종횡비를 유지하도록 보장합니다.

## 5단계: 문서 저장

마지막으로, 문서를 지정된 디렉토리에 저장합니다. 이 단계는 문서 파일에 대한 모든 변경 사항을 기록합니다.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 결론

축하합니다! Aspose.Words for .NET을 사용하여 Word 문서에서 도형의 종횡비를 설정하는 방법을 성공적으로 배웠습니다. 이러한 단계를 따르면 이미지와 도형이 비율을 유지하여 문서가 전문적이고 세련되게 보이게 할 수 있습니다. 다양한 이미지와 도형을 자유롭게 실험하여 다양한 시나리오에서 종횡비 잠금 기능이 어떻게 작동하는지 확인하세요.

## 자주 묻는 질문

### 잠금을 해제한 후 종횡비를 다시 잠금 해제할 수 있나요?
네, 종횡비를 설정하여 잠금 해제할 수 있습니다.`shape.AspectRatioLocked = false`.

### 잠긴 종횡비로 이미지 크기를 조정하면 어떻게 되나요?
이미지는 원래의 너비 대 높이 비율을 유지하면서 비례적으로 크기가 조절됩니다.

### 이미지 외에 다른 모양에도 적용할 수 있나요?
물론입니다! 종횡비 잠금 기능은 직사각형, 원 등 모든 모양에 적용할 수 있습니다.

### Aspose.Words for .NET은 .NET Core와 호환됩니까?
네, Aspose.Words for .NET은 .NET Framework와 .NET Core를 모두 지원합니다.

### .NET용 Aspose.Words에 대한 추가 문서는 어디에서 찾을 수 있나요?
 포괄적인 문서를 찾을 수 있습니다[여기](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
