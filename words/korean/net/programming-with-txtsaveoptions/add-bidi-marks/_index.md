---
title: Word 문서에 Bidi 마크 추가
linktitle: Word 문서에 Bidi 마크 추가
second_title: Aspose.Words 문서 처리 API
description: 이 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에 양방향(Bidi) 마크를 추가하는 방법을 알아보세요. 다국어 콘텐츠에 대한 적절한 텍스트 방향을 보장하세요.
weight: 10
url: /ko/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 Bidi 마크 추가

## 소개

문서 처리 분야에서 양방향(Bidi) 텍스트는 종종 관리하기 까다로울 수 있습니다. 특히 아랍어나 히브리어와 같이 텍스트 방향이 다른 언어를 다룰 때 그렇습니다. 다행히도 Aspose.Words for .NET을 사용하면 이러한 시나리오를 쉽게 처리할 수 있습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서에 Bidi 마크를 추가하는 방법을 살펴보겠습니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: Aspose.Words for .NET이 설치되어 있어야 합니다. 다음에서 다운로드할 수 있습니다.[Aspose 다운로드 페이지](https://releases.aspose.com/words/net/).
2. .NET Framework 또는 .NET Core: 예제를 실행하기 위해 호환되는 .NET 환경이 설정되어 있는지 확인하세요.
3. C#에 대한 기본 지식: C# 프로그래밍 언어와 .NET의 기본 작업에 익숙합니다.

## 네임스페이스 가져오기

시작하려면 필요한 네임스페이스를 가져와야 합니다. 프로젝트에 포함시키는 방법은 다음과 같습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Word 문서에 Bidi 마크를 추가하는 과정을 명확한 단계로 나누어 보겠습니다. 각 단계는 코드와 그 목적을 안내합니다.

## 1단계: 문서 설정

 새 인스턴스를 만드는 것으로 시작하세요.`Document` 클래스와`DocumentBuilder` 문서에 내용을 추가합니다.

```csharp
// 문서 디렉토리로 가는 경로
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// 문서를 만들고 내용을 추가하세요
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 이 단계에서는 새 Word 문서를 초기화하고 설정합니다.`DocumentBuilder` 콘텐츠 삽입을 용이하게 합니다.

## 2단계: 문서에 콘텐츠 추가

다음으로, 문서에 텍스트를 추가합니다. 여기서는 Bidi 텍스트 처리를 설명하기 위해 다양한 언어로 텍스트를 추가합니다.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

여기서 우리는 먼저 표준 영어 구문을 추가합니다. 그런 다음 히브리어와 아랍어로 쓰여진 후속 텍스트에 대해 Bidi 텍스트 서식을 활성화합니다. 이는 양방향 텍스트를 통합하는 방법을 보여줍니다.

## 3단계: Bidi 마크에 대한 저장 옵션 구성

 Bidi 마크가 문서에 올바르게 저장되도록 하려면 다음을 구성해야 합니다.`TxtSaveOptions` 그리고 활성화합니다`AddBidiMarks` 옵션.

```csharp
// 비디 마크 추가
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 이 단계에서는 인스턴스를 생성합니다.`TxtSaveOptions` 그리고 설정하다`AddBidiMarks`재산에`true`이렇게 하면 문서를 텍스트 파일로 저장할 때 Bidi 표시가 포함됩니다.

## 결론

Word 문서에 Bidi 마크를 추가하는 것은 텍스트 방향이 다른 언어를 포함하는 다국어 콘텐츠를 처리할 때 중요한 단계가 될 수 있습니다. Aspose.Words for .NET을 사용하면 이 프로세스가 간단하고 효율적입니다. 위에 설명된 단계를 따르면 문서가 Bidi 텍스트를 올바르게 표현하여 가독성과 정확성을 높일 수 있습니다.

## 자주 묻는 질문

### 비디 마크는 무엇이고 왜 중요한가요?
비디 마크는 문서에서 텍스트 방향을 제어하는 데 사용되는 특수 문자입니다. 아랍어와 히브리어처럼 오른쪽에서 왼쪽으로 읽는 언어를 올바르게 표시하는 데 필수적입니다.

### Aspose.Words for .NET을 사용하여 다른 유형의 텍스트 방향 문제를 처리할 수 있나요?
네, Aspose.Words for .NET은 오른쪽에서 왼쪽으로 쓰는 언어와 왼쪽에서 오른쪽으로 쓰는 언어를 포함하여 다양한 텍스트 방향 및 서식 요구 사항에 대한 포괄적인 지원을 제공합니다.

### 문서의 특정 부분에만 Bidi 서식을 적용할 수 있나요?
네, 필요에 따라 문서의 특정 문단이나 섹션에 Bidi 서식을 적용할 수 있습니다.

### Bidi 표시가 있는 문서를 어떤 형식으로 저장할 수 있나요?
제공된 예에서 문서는 텍스트 파일로 저장됩니다. 그러나 Aspose.Words는 Bidi 마크를 보존하면서 다양한 형식으로 문서를 저장하는 것도 지원합니다.

### Aspose.Words for .NET에 대한 자세한 정보는 어디에서 찾을 수 있나요?
 Aspose.Words for .NET에 대해 더 자세히 알아보려면 다음을 참조하세요.[Aspose 문서](https://reference.aspose.com/words/net/) 그리고 접근합니다[지원 포럼](https://forum.aspose.com/c/words/8) 추가 도움이 필요하면.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
