---
"description": "이 가이드를 통해 Aspose.Words for .NET에서 필드 업데이트 문화권 소스를 변경하는 방법을 알아보세요. 다양한 문화권에 따라 날짜 형식을 쉽게 제어할 수 있습니다."
"linktitle": "필드 업데이트 문화 소스 변경"
"second_title": "Aspose.Words 문서 처리 API"
"title": "필드 업데이트 문화 소스 변경"
"url": "/ko/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 필드 업데이트 문화 소스 변경

## 소개

이 튜토리얼에서는 Aspose.Words for .NET의 세계를 자세히 살펴보고 필드 업데이트 문화권 소스를 변경하는 방법을 알아봅니다. 날짜 필드가 포함된 Word 문서를 다루고 있고 다양한 문화권에 따라 날짜 형식을 제어해야 하는 경우 이 가이드가 도움이 될 것입니다. 각 개념을 이해하고 프로젝트에 효과적으로 적용할 수 있도록 단계별로 프로세스를 안내해 드리겠습니다.

## 필수 조건

코드를 살펴보기 전에 다음 사항이 있는지 확인하세요.

- Aspose.Words for .NET: 여기에서 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
- 개발 환경: .NET 호환 IDE(예: Visual Studio).
- C#에 대한 기본 지식: 이 튜토리얼은 독자가 C# 프로그래밍에 대한 기본적인 이해가 있다고 가정합니다.

## 네임스페이스 가져오기

먼저 프로젝트에 필요한 네임스페이스를 임포트해 보겠습니다. 이렇게 하면 Aspose.Words에서 제공하는 모든 필수 클래스와 메서드에 접근할 수 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

이제 Aspose.Words for .NET에서 필드 업데이트 문화권 소스를 변경하는 방법을 이해하는 데 도움이 되도록 예제를 여러 단계로 나누어 보겠습니다.

## 1단계: 문서 초기화

첫 번째 단계는 새 인스턴스를 만드는 것입니다. `Document` 클래스와 `DocumentBuilder`. 이는 Word 문서를 작성하고 조작하기 위한 기반을 마련합니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 특정 로케일로 필드 삽입

다음으로, 문서에 필드를 삽입해야 합니다. 이 예제에서는 두 개의 날짜 필드를 삽입합니다. 글꼴의 로캘을 독일어(LocaleId = 1031)로 설정하여 문화권이 날짜 형식에 미치는 영향을 보여드리겠습니다.

```csharp
builder.Font.LocaleId = 1031; // 독일 사람
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## 3단계: 필드 업데이트 문화 소스 설정

필드를 업데이트할 때 사용되는 문화를 제어하려면 다음을 설정합니다. `FieldUpdateCultureSource` 의 재산 `FieldOptions` 클래스. 이 속성은 문화권을 필드 코드에서 가져올지, 문서에서 가져올지 결정합니다.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## 4단계: 메일 병합 실행

이제 실제 데이터로 필드를 채우기 위해 메일 병합을 실행해야 합니다. 이 예에서는 두 번째 날짜 필드(`Date2`)부터 2011년 1월 1일까지.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## 5단계: 문서 저장

마지막으로, 지정된 디렉터리에 문서를 저장합니다. 이 단계로 필드 업데이트 문화권 원본을 변경하는 과정이 완료됩니다.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## 결론

자, 이제 Aspose.Words for .NET에서 필드 업데이트 문화권 원본을 성공적으로 변경했습니다. 다음 단계를 따르면 Word 문서에 지정된 문화권 설정에 따라 날짜 및 기타 필드 값이 표시되도록 할 수 있습니다. 특히 국제 사용자를 대상으로 하는 문서를 생성할 때 유용합니다.

## 자주 묻는 질문

### 설정의 목적은 무엇입니까? `LocaleId`?
그만큼 `LocaleId` 텍스트에 대한 문화권 설정을 지정하며, 이는 날짜 및 기타 로캘에 따른 데이터의 형식 지정 방식에 영향을 미칩니다.

### 독일어 외에 다른 로케일을 사용할 수 있나요?
네, 설정할 수 있습니다 `LocaleId` 유효한 로캘 식별자로 지정합니다. 예를 들어, 영어(미국)의 경우 1033입니다.

### 설정하지 않으면 어떻게 되나요? `FieldUpdateCultureSource` 재산?
이 속성이 설정되지 않으면 필드를 업데이트할 때 문서의 기본 문화권 설정이 사용됩니다.

### 필드 코드 대신 문서의 문화권에 따라 필드를 업데이트하는 것이 가능합니까?
네, 설정할 수 있습니다 `FieldUpdateCultureSource` 에게 `FieldUpdateCultureSource.Document` 문서의 문화권 설정을 사용합니다.

### 날짜를 다른 패턴으로 포맷하려면 어떻게 해야 하나요?
날짜 형식 패턴을 변경할 수 있습니다. `InsertField` 수정하여 방법 `\\@` 스위치 값.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}