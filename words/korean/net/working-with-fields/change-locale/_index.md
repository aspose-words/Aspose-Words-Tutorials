---
title: 로케일 변경
linktitle: 로케일 변경
second_title: Aspose.Words 문서 처리 API
description: 이 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 로캘을 변경하는 방법을 알아보세요. 국제 고객과 프로젝트를 처리하는 데 적합합니다.
weight: 10
url: /ko/net/working-with-fields/change-locale/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 로케일 변경

## 소개

Word 문서로 작업하려면 종종 약간의 섬세함이 필요한데, 특히 다양한 로케일과 문화를 다룰 때 그렇습니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 Word 문서의 로케일을 변경하는 방법을 살펴보겠습니다. 글로벌 대상을 위한 문서를 만들든 날짜 형식을 바꿔야 하든 이 가이드가 도와드리겠습니다.

## 필수 조건

본격적으로 들어가기 전에 필요한 모든 것이 있는지 확인해 보겠습니다.

-  .NET용 Aspose.Words: 여기에서 다운로드할 수 있습니다.[여기](https://releases.aspose.com/words/net/).
- Visual Studio: .NET Framework를 지원하는 모든 버전.
- C#에 대한 기본 지식: C#과 .NET의 기본에 대한 이해가 따라가는 데 도움이 됩니다.

 Aspose.Words for .NET을 설치했는지 확인하세요. 설치하지 않았다면 무료 평가판을 받을 수 있습니다.[여기](https://releases.aspose.com/) 아니면 사세요[여기](https://purchase.aspose.com/buy).

## 네임스페이스 가져오기

코딩을 시작하기 전에 필요한 네임스페이스를 가져와야 합니다. 이는 레시피의 재료와 같아서 모든 것이 원활하게 작동하도록 합니다.

```csharp
using System.Globalization;
using System.Threading;
using Aspose.Words;
using Aspose.Words.Fields;
```

Word 문서에서 로캘을 변경하는 것은 간단한 과정입니다. 단계별로 나누어 보겠습니다.

## 1단계: 문서 설정

우선, 문서와 문서 빌더를 설정해 보겠습니다. 이는 요리를 시작하기 전에 작업 공간을 설정하는 것과 같습니다.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2단계: 병합 필드 삽입

이제 날짜에 대한 병합 필드를 삽입합니다. 여기서 로케일이 작용합니다.

```csharp
builder.InsertField("MERGEFIELD Date");
```

## 3단계: 현재 문화 저장

로케일을 변경하기 전에 현재 문화를 저장해야 합니다. 이것은 다른 장으로 이동하기 전에 장소를 북마크하는 것으로 생각하세요.

```csharp
CultureInfo currentCulture = Thread.CurrentThread.CurrentCulture;
```

## 4단계: 로케일 변경

다음으로, 스레드의 현재 문화를 독일어("de-DE")로 변경합니다. 이는 휴대폰의 언어 설정을 전환하는 것과 같습니다.

```csharp
Thread.CurrentThread.CurrentCulture = new CultureInfo("de-DE");
```

## 5단계: 메일 병합 실행

이제 현재 날짜로 메일 병합을 실행합니다. 그러면 날짜 형식에 새 로캘이 적용됩니다.

```csharp
doc.MailMerge.Execute(new[] { "Date" }, new object[] { DateTime.Now });
```

## 6단계: 원래 문화 복원

메일 병합을 실행한 후 원래 문화를 복원합니다. 이는 선호하는 언어 설정으로 다시 전환하는 것과 같습니다.

```csharp
Thread.CurrentThread.CurrentCulture = currentCulture;
```

## 7단계: 문서 저장

마지막으로, 지정된 디렉토리에 문서를 저장합니다.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeLocale.docx");
```

이제 Aspose.Words for .NET을 사용하여 Word 문서의 로캘을 성공적으로 변경했습니다.

## 결론

Word 문서에서 로캘을 변경하는 것은 특히 국제 고객이나 프로젝트를 다룰 때 매우 유용할 수 있습니다. Aspose.Words for .NET을 사용하면 이 작업이 아주 쉬워집니다. 다음 단계를 따르면 로캘을 손쉽게 전환할 수 있습니다.

## 자주 묻는 질문

### 로케일을 다른 언어로 변경할 수 있나요?
네, Aspose.Words for .NET은 .NET에서 지원하는 모든 언어로 로캘을 변경하는 것을 지원합니다.

### 이것이 문서의 다른 부분에도 영향을 미칠까요?
로케일을 변경하면 주로 날짜 및 숫자 형식에 영향을 미칩니다. 다른 텍스트는 변경되지 않습니다.

### Aspose.Words for .NET을 사용하려면 특별한 라이선스가 필요합니까?
 무료 체험판으로 시작할 수 있지만 계속 사용하려면 라이선스를 구매해야 합니다.[여기](https://purchase.aspose.com/buy).

### 문제가 발생하면 원래 로케일로 돌아갈 수 있나요?
네, 원래 문화를 저장한 다음 나중에 복원하면 원래 로케일로 되돌릴 수 있습니다.

### 문제가 발생하면 어디에서 지원을 받을 수 있나요?
 Aspose 커뮤니티에서 지원을 받을 수 있습니다.[여기](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
