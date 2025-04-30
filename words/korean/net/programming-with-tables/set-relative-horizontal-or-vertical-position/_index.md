---
"description": "이 단계별 가이드를 통해 Aspose.Words for .NET을 사용하여 Word 문서에서 표의 상대적 수평 및 수직 위치를 설정하는 방법을 알아보세요."
"linktitle": "상대적 수평 또는 수직 위치 설정"
"second_title": "Aspose.Words 문서 처리 API"
"title": "상대적 수평 또는 수직 위치 설정"
"url": "/ko/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 상대적 수평 또는 수직 위치 설정

## 소개

Word 문서에서 표를 원하는 대로 배치하는 방법에 어려움을 느껴본 적이 있으신가요? 여러분만 그런 게 아닙니다. 전문적인 보고서든 세련된 브로셔든, 표를 정렬하는 것만으로도 엄청난 변화를 만들 수 있습니다. 바로 이럴 때 Aspose.Words for .NET이 유용합니다. 이 튜토리얼에서는 Word 문서에서 표의 상대적인 가로 또는 세로 위치를 설정하는 방법을 단계별로 안내합니다. 자, 시작해 볼까요!

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: 아직 다운로드하지 않았다면 지금 다운로드할 수 있습니다. [여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 호환 IDE.
3. C#에 대한 기본 지식: 이 튜토리얼은 독자가 C# 프로그래밍의 기본에 익숙하다고 가정합니다.

## 네임스페이스 가져오기

먼저 필요한 네임스페이스를 가져와야 합니다. 이는 Aspose.Words 기능에 접근하는 데 필수적입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1단계: 문서 로드

시작하려면 Word 문서를 프로그램에 불러와야 합니다. 방법은 다음과 같습니다.

```csharp
// 문서 디렉토리 경로 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

이 코드 조각은 문서 디렉터리 경로를 설정하고 작업하려는 특정 문서를 로드합니다. 로드 문제를 방지하려면 문서 경로가 올바른지 확인하세요.

## 2단계: 테이블에 접근하기

다음으로, 문서 내의 표에 접근해야 합니다. 일반적으로 본문 섹션의 첫 번째 표를 사용하는 것이 좋습니다.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

이 코드 줄은 문서 본문에서 첫 번째 표를 가져옵니다. 문서에 표가 여러 개 있는 경우, 색인을 적절히 조정할 수 있습니다.

## 3단계: 수평 위치 설정

이제 특정 요소를 기준으로 표의 가로 위치를 설정해 보겠습니다. 이 예제에서는 열을 기준으로 위치를 지정합니다.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

설정하여 `HorizontalAnchor` 에게 `RelativeHorizontalPosition.Column`, 테이블이 있는 열에 대해 수평으로 정렬되도록 지시하는 것입니다.

## 4단계: 수직 위치 설정

가로 위치와 마찬가지로 세로 위치도 설정할 수 있습니다. 여기서는 페이지를 기준으로 세로 위치를 지정하겠습니다.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

설정 `VerticalAnchor` 에게 `RelativeVerticalPosition.Page` 표가 페이지에 따라 수직으로 정렬되도록 합니다.

## 5단계: 문서 저장

마지막으로, 새 문서에 변경 사항을 저장합니다. 이는 변경 사항이 유지되도록 하는 데 중요한 단계입니다.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

이 명령을 사용하면 수정된 문서가 새 이름으로 저장되므로 원본 파일을 덮어쓰지 않습니다.

## 결론

자, 이제 완성했습니다! Aspose.Words for .NET을 사용하여 Word 문서에서 표의 상대적인 가로 및 세로 위치를 성공적으로 설정했습니다. 이 새로운 기술을 사용하면 문서의 레이아웃과 가독성을 향상시켜 더욱 전문적이고 세련된 느낌을 줄 수 있습니다. 다양한 위치를 계속 실험해 보고 필요에 가장 적합한 위치를 찾아보세요.

## 자주 묻는 질문

### 다른 요소를 기준으로 표를 배치할 수 있나요?  
네, Aspose.Words를 사용하면 여백, 페이지, 열 등 다양한 요소를 기준으로 표를 배치할 수 있습니다.

### Aspose.Words for .NET을 사용하려면 라이선스가 필요합니까?  
네, 라이센스를 구매할 수 있습니다. [여기](https://purchase.aspose.com/buy) 또는 임시 면허를 받으세요 [여기](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET에 대한 무료 평가판이 있나요?  
물론입니다! 무료 체험판을 다운로드하실 수 있습니다. [여기](https://releases.aspose.com/).

### Aspose.Words를 다른 프로그래밍 언어와 함께 사용할 수 있나요?  
Aspose.Words는 주로 .NET용으로 설계되었지만 Java, Python 및 기타 플랫폼용 버전도 있습니다.

### 더 자세한 문서는 어디에서 찾을 수 있나요?  
더 자세한 정보는 Aspose.Words 문서를 확인하세요. [여기](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}