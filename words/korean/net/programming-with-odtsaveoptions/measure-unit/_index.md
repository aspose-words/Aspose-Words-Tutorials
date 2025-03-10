---
title: 측정 단위
linktitle: 측정 단위
second_title: Aspose.Words 문서 처리 API
description: ODT 변환 중에 문서 형식을 유지하기 위해 Aspose.Words for .NET에서 측정 단위 기능을 구성하는 방법을 알아보세요.
weight: 10
url: /ko/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 측정 단위

## 소개

Word 문서를 다른 형식으로 변환해야 했지만 레이아웃에 특정 측정 단위가 필요했던 적이 있나요? 인치, 센티미터 또는 포인트를 다루든 변환 프로세스 중에 문서의 무결성을 유지하는 것이 중요합니다. 이 튜토리얼에서는 Aspose.Words for .NET에서 측정 단위 기능을 구성하는 방법을 살펴보겠습니다. 이 강력한 기능은 ODT(Open Document Text) 형식으로 변환할 때 문서의 서식이 필요한 대로 정확하게 유지되도록 합니다.

## 필수 조건

코드를 살펴보기 전에 시작하는 데 필요한 몇 가지 사항이 있습니다.

1. Aspose.Words for .NET: 최신 버전의 Aspose.Words for .NET이 설치되어 있는지 확인하세요. 아직 설치되어 있지 않으면 다음에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
2. 개발 환경: C# 코드를 작성하고 실행하기 위한 Visual Studio와 같은 IDE.
3. C#에 대한 기본 지식: C#의 기본을 이해하면 튜토리얼을 따라가는 데 도움이 됩니다.
4. Word 문서: 변환에 사용할 수 있는 샘플 Word 문서를 준비하세요.

## 네임스페이스 가져오기

코딩을 시작하기 전에 필요한 네임스페이스를 가져왔는지 확인해 보겠습니다. 코드 파일 맨 위에 다음 using 지시문을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1단계: 문서 디렉토리 설정

먼저, 문서 디렉토리 경로를 정의해야 합니다. 여기가 Word 문서가 있는 위치이며 변환된 파일이 저장되는 위치입니다.

```csharp
// 문서 디렉토리로 가는 경로
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 바꾸다`"YOUR DOCUMENTS DIRECTORY"` 디렉토리의 실제 경로와 함께. 이렇게 하면 코드가 Word 문서를 어디에서 찾을 수 있는지 알 수 있습니다.

## 2단계: Word 문서 로드

 다음으로 변환하려는 Word 문서를 로드해야 합니다. 이는 다음을 사용하여 수행됩니다.`Document` Aspose.Words의 수업입니다.

```csharp
// Word 문서를 로드합니다
Document doc = new Document(dataDir + "Document.docx");
```

"Document.docx"라는 Word 문서가 지정된 디렉토리에 있는지 확인하세요.

## 3단계: 측정 단위 구성

 이제 ODT 변환을 위한 측정 단위를 구성해 보겠습니다. 여기서 마법이 일어납니다. 우리는 다음을 설정합니다.`OdtSaveOptions` 인치를 측정 단위로 사용합니다.

```csharp
// "측정 단위" 기능을 사용한 백업 옵션 구성
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 이 예에서 우리는 측정 단위를 인치로 설정합니다. 다음과 같은 다른 단위를 선택할 수도 있습니다.`OdtSaveMeasureUnit.Centimeters` 또는`OdtSaveMeasureUnit.Points` 귀하의 요구 사항에 따라 다릅니다.

## 4단계: 문서를 ODT로 변환

 마지막으로 구성된 것을 사용하여 Word 문서를 ODT 형식으로 변환합니다.`OdtSaveOptions`.

```csharp
// 문서를 ODT로 변환
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

이 코드 줄은 변환된 문서를 새로운 측정 단위가 적용된 지정된 디렉토리에 저장합니다.

## 결론

이제 다 됐습니다! 다음 단계를 따르면 Aspose.Words for .NET에서 측정 단위 기능을 쉽게 구성하여 변환 중에 문서의 레이아웃이 유지되도록 할 수 있습니다. 인치, 센티미터 또는 포인트로 작업하든 이 튜토리얼에서는 문서 서식을 쉽게 제어하는 방법을 보여주었습니다.

## 자주 묻는 질문

### .NET용 Aspose.Words란 무엇인가요?
Aspose.Words for .NET은 Word 문서를 프로그래밍 방식으로 작업하기 위한 강력한 라이브러리입니다. 개발자는 Microsoft Word가 없어도 Word 문서를 만들고, 수정하고, 변환하고, 처리할 수 있습니다.

### 인치 외에 다른 측정 단위를 사용할 수 있나요?
 예, Aspose.Words for .NET은 센티미터와 포인트와 같은 다른 측정 단위를 지원합니다. 다음을 사용하여 원하는 단위를 지정할 수 있습니다.`OdtSaveMeasureUnit` 열거.

### Aspose.Words for .NET에 대한 무료 평가판이 있나요?
 네, Aspose.Words for .NET의 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.aspose.com/).

### Aspose.Words for .NET에 대한 문서는 어디에서 찾을 수 있나요?
 Aspose.Words for .NET에 대한 포괄적인 설명서는 다음에서 볼 수 있습니다.[이 링크](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET에 대한 지원을 어떻게 받을 수 있나요?
 지원을 받으려면 Aspose.Words 포럼을 방문하세요.[이 링크](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
