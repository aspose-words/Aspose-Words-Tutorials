---
title: Word 문서에 떠있는 이미지 삽입
linktitle: Word 문서에 떠있는 이미지 삽입
second_title: Aspose.Words 문서 처리 API
description: 이 자세한 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에 떠 있는 이미지를 삽입하는 방법을 알아보세요. 문서를 향상시키는 데 완벽합니다.
weight: 10
url: /ko/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 떠있는 이미지 삽입

## 소개

이미지가 텍스트를 보완하도록 완벽하게 배치된 멋진 보고서나 제안서를 만드는 것을 상상해 보세요. Aspose.Words for .NET을 사용하면 손쉽게 이를 달성할 수 있습니다. 이 라이브러리는 문서 조작을 위한 강력한 기능을 제공하여 개발자에게 꼭 필요한 솔루션입니다. 이 튜토리얼에서는 DocumentBuilder 클래스를 사용하여 플로팅 이미지를 삽입하는 데 중점을 둡니다. 노련한 개발자이든 방금 시작한 개발자이든 이 가이드는 각 단계를 안내합니다.

## 필수 조건

본격적으로 시작하기에 앞서, 시작하는 데 필요한 모든 것이 있는지 확인해 보겠습니다.

1.  .NET용 Aspose.Words: 라이브러리를 다음에서 다운로드할 수 있습니다.[Aspose 릴리스 페이지](https://releases.aspose.com/words/net/).
2. Visual Studio: .NET 개발을 지원하는 모든 버전.
3. C#에 대한 기본 지식: C# 프로그래밍의 기본을 이해하는 것이 도움이 됩니다.
4. 이미지 파일: 로고나 그림 등 삽입하려는 이미지 파일입니다.

## 네임스페이스 가져오기

프로젝트에서 Aspose.Words를 사용하려면 필요한 네임스페이스를 가져와야 합니다. 이는 C# 파일 맨 위에 다음 줄을 추가하여 수행됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

이러한 필수 구성 요소와 네임스페이스가 준비되면 튜토리얼을 시작할 준비가 되었습니다.

Word 문서에 떠 있는 이미지를 삽입하는 과정을 관리 가능한 단계로 나누어 보겠습니다. 각 단계를 자세히 설명하여 아무런 문제 없이 따라갈 수 있도록 합니다.

## 1단계: 프로젝트 설정

먼저 Visual Studio에서 새 C# 프로젝트를 만듭니다. 단순성을 위해 콘솔 앱을 선택할 수 있습니다.

1. Visual Studio를 열고 새 프로젝트를 만듭니다.
2. "콘솔 앱(.NET Core)"을 선택하고 "다음"을 클릭합니다.
3. 프로젝트 이름을 지정하고 저장할 위치를 선택합니다. "생성"을 클릭합니다.
4. NuGet 패키지 관리자를 통해 Aspose.Words for .NET을 설치합니다. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 "NuGet 패키지 관리"를 선택한 다음 "Aspose.Words"를 검색합니다. 최신 버전을 설치합니다.

## 2단계: Document 및 DocumentBuilder 초기화

이제 프로젝트가 설정되었으니 Document 및 DocumentBuilder 객체를 초기화해 보겠습니다.

1.  새 인스턴스를 만듭니다.`Document` 수업:

```csharp
Document doc = new Document();
```

2. DocumentBuilder 객체를 초기화합니다.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 그만큼`Document` 개체는 Word 문서를 나타내며`DocumentBuilder` 콘텐츠를 추가하는 데 도움이 됩니다.

## 3단계: 이미지 경로 정의

다음으로, 이미지 파일의 경로를 지정합니다. 프로젝트 디렉토리에서 이미지에 액세스할 수 있는지 확인합니다.

이미지 디렉토리와 이미지 파일 이름을 정의합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 바꾸다`"YOUR DOCUMENT DIRECTORY"` 이미지가 저장된 실제 경로를 사용합니다.

## 4단계: 플로팅 이미지 삽입

모든 것이 설정되었으니, 떠 있는 이미지를 문서에 삽입해 보겠습니다.

 사용하세요`InsertImage` 의 방법`DocumentBuilder` 이미지를 삽입하는 클래스:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

각 매개변수의 의미는 다음과 같습니다.
- `imagePath`: 이미지 파일의 경로입니다.
- `RelativeHorizontalPosition.Margin`: 여백을 기준으로 한 수평 위치입니다.
- `100`: 여백으로부터의 수평 오프셋(포인트).
- `RelativeVerticalPosition.Margin`: 여백을 기준으로 한 수직 위치입니다.
- `100`: 여백으로부터의 수직 오프셋(포인트).
- `200`: 이미지의 너비(포인트)입니다.
- `100`: 이미지의 높이(포인트).
- `WrapType.Square`: 이미지 주위의 텍스트 배치 스타일입니다.

## 5단계: 문서 저장

마지막으로 원하는 위치에 문서를 저장합니다.

1. 출력 파일 경로를 지정하세요:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. 문서를 저장하세요:

```csharp
doc.Save(outputPath);
```

이제 떠 있는 이미지가 포함된 Word 문서가 준비되었습니다!

## 결론

Aspose.Words for .NET을 사용하여 Word 문서에 떠 있는 이미지를 삽입하는 것은 관리하기 쉬운 단계로 나누면 간단한 프로세스입니다. 이 가이드를 따르면 문서에 전문적인 이미지를 추가하여 시각적 매력을 높일 수 있습니다. Aspose.Words는 보고서, 제안서 또는 기타 문서 유형을 작업하든 문서 조작을 쉽게 만드는 강력한 API를 제공합니다.

## 자주 묻는 질문

### Aspose.Words for .NET을 사용하여 여러 이미지를 삽입할 수 있나요?

 네, 반복해서 여러 이미지를 삽입할 수 있습니다.`InsertImage` 원하는 매개변수를 사용하여 각 이미지에 대한 방법을 지정합니다.

### 이미지의 위치를 어떻게 바꾸나요?

 조정할 수 있습니다`RelativeHorizontalPosition`, `RelativeVerticalPosition`, 그리고 오프셋 매개변수를 사용하여 필요에 따라 이미지를 배치합니다.

### 이미지에 사용할 수 있는 다른 랩 유형은 무엇이 있나요?

 Aspose.Words는 다음과 같은 다양한 래핑 유형을 지원합니다.`Inline`, `TopBottom`, `Tight`, `Through`, 그리고 더 많은 것들. 문서 레이아웃에 가장 잘 맞는 것을 선택할 수 있습니다.

### 다양한 이미지 형식을 사용할 수 있나요?

네, Aspose.Words는 JPEG, PNG, BMP, GIF 등 다양한 이미지 포맷을 지원합니다.

### Aspose.Words for .NET의 무료 평가판을 받으려면 어떻게 해야 하나요?

 무료 체험판을 받아보실 수 있습니다.[Aspose 무료 체험 페이지](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
