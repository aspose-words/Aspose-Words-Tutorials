---
title: 문서 작성기 없이 TOA 필드 삽입
linktitle: 문서 작성기 없이 TOA 필드 삽입
second_title: Aspose.Words 문서 처리 API
description: Aspose.Words for .NET에서 문서 빌더를 사용하지 않고 TOA 필드를 삽입하는 방법을 알아보세요. 단계별 가이드를 따라 법적 인용문을 효율적으로 관리하세요.
weight: 10
url: /ko/net/working-with-fields/insert-toafield-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서 작성기 없이 TOA 필드 삽입

## 소개

Word 문서에서 TOA(권한 표) 필드를 만드는 것은 복잡한 퍼즐을 조각 맞추는 것처럼 느껴질 수 있습니다. 그러나 Aspose.Words for .NET의 도움으로 프로세스가 매끄럽고 간단해집니다. 이 문서에서는 문서 빌더를 사용하지 않고 TOA 필드를 삽입하는 단계를 안내하여 Word 문서 내에서 인용문과 법적 참조를 쉽게 관리할 수 있도록 합니다.

## 필수 조건

튜토리얼을 시작하기에 앞서, 꼭 필요한 필수 사항을 살펴보겠습니다.

-  Aspose.Words for .NET: 최신 버전이 설치되어 있는지 확인하세요. 다음에서 다운로드할 수 있습니다.[Aspose 웹사이트](https://releases.aspose.com/words/net/).
- 개발 환경: Visual Studio와 같은 .NET 호환 IDE.
- 기본 C# 지식: 기본 C# 구문과 개념을 이해하는 것이 도움이 됩니다.
- 샘플 Word 문서: TOA 필드를 삽입할 위치에 샘플 문서를 만들거나 준비하세요.

## 네임스페이스 가져오기

시작하려면 Aspose.Words 라이브러리에서 필요한 네임스페이스를 가져와야 합니다. 이 설정은 문서 조작에 필요한 모든 클래스와 메서드에 액세스할 수 있도록 보장합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

이 과정을 간단하고 따라하기 쉬운 단계로 나누어 보겠습니다. 각 단계를 안내하고 각 코드의 역할과 TOA 필드 생성에 어떻게 기여하는지 설명하겠습니다.

## 1단계: 문서 초기화

 먼저 인스턴스를 생성해야 합니다.`Document` 클래스. 이 객체는 당신이 작업하고 있는 Word 문서를 나타냅니다.

```csharp
// 문서 디렉토리의 경로입니다.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

이 코드는 새 Word 문서를 초기화합니다. 콘텐츠를 추가할 빈 캔버스를 만드는 것으로 생각할 수 있습니다.

## 2단계: TA 필드 생성 및 구성

다음으로, TA(권위 표) 필드를 추가합니다. 이 필드는 TOA에 나타날 항목을 표시합니다.

```csharp
Paragraph para = new Paragraph(doc);

// TA와 TOA 필드를 다음과 같이 삽입하고 싶습니다.
// { TA \c 1 \l "값 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

자세한 내용은 다음과 같습니다.
- 문단 para = new Paragraph(doc);: 문서 내에 새로운 문단을 만듭니다.
-  FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: 단락에 TA 필드를 추가합니다. 그만큼`FieldType.FieldTOAEntry` 이는 TOA 항목 필드임을 지정합니다.
- fieldTA.EntryCategory = "1";: 항목 카테고리를 설정합니다. 이는 다양한 유형의 항목을 분류하는 데 유용합니다.
- fieldTA.LongCitation = "Value 0";: 긴 인용 텍스트를 지정합니다. 이는 TOA에 나타날 텍스트입니다.
- doc.FirstSection.Body.AppendChild(para);: TA 필드가 있는 문단을 문서 본문에 추가합니다.

## 3단계: TOA 필드 추가

이제 모든 TA 항목을 표로 정리하는 실제 TOA 필드를 삽입해 보겠습니다.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

이 단계에서는:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: 단락에 TOA 필드를 추가합니다.
- fieldToa.EntryCategory = "1";: 카테고리 "1"로 표시된 항목만 포함하도록 필터링합니다.

## 4단계: TOA 필드 업데이트

TOA 필드를 삽입한 후에는 최신 항목이 반영되도록 업데이트해야 합니다.

```csharp
fieldToa.Update();
```

이 명령은 TOA 필드를 새로 고쳐서 표시된 모든 항목이 표에 올바르게 표시되도록 합니다.

## 5단계: 문서 저장

마지막으로 새로 추가된 TOA 필드와 함께 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

 이 코드 줄은 문서를 지정된 디렉토리에 저장합니다. 다음을 반드시 바꾸십시오.`"YOUR DOCUMENT DIRECTORY"` 파일을 저장하려는 실제 경로를 입력하세요.

## 결론

이제 다 되었습니다! 문서 빌더를 사용하지 않고도 Word 문서에 TOA 필드를 성공적으로 추가했습니다. 이러한 단계를 따르면 인용문을 효율적으로 관리하고 법률 문서에서 포괄적인 권위 표를 만들 수 있습니다. Aspose.Words for .NET은 이 프로세스를 원활하고 효율적으로 만들어 복잡한 문서 작업을 쉽게 처리할 수 있는 도구를 제공합니다.

## 자주 묻는 질문

### 다양한 카테고리를 가진 여러 TA 필드를 추가할 수 있나요?
 예, 다음을 설정하여 다양한 범주를 가진 여러 TA 필드를 추가할 수 있습니다.`EntryCategory`이에 따라 재산을 소유합니다.

### TOA의 모양을 어떻게 사용자 지정할 수 있나요?
TOA 필드의 속성(항목 형식 및 범주 레이블 등)을 수정하여 TOA의 모양을 사용자 지정할 수 있습니다.

### TOA 필드를 자동으로 업데이트할 수 있나요?
 TOA 필드를 수동으로 업데이트할 수 있습니다.`Update` 메서드, Aspose.Words는 현재 문서 변경 사항에 대한 자동 업데이트를 지원하지 않습니다.

### 문서의 특정 부분에 TA 필드를 프로그래밍 방식으로 추가할 수 있습니까?
네, 원하는 문단이나 섹션에 삽입하여 특정 위치에 TA 필드를 추가할 수 있습니다.

### 하나의 문서에서 여러 TOA 필드를 어떻게 처리합니까?
 다양한 TOA 필드를 할당하여 여러 TOA 필드를 관리할 수 있습니다.`EntryCategory` 값을 지정하고 각 TOA 필드가 해당 범주에 따라 항목을 필터링하도록 합니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
