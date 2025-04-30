---
"description": "Aspose.Words for .NET을 사용하여 Word 문서에 OLE 개체를 삽입하는 방법을 알아보세요. 자세한 단계별 가이드를 따라 파일을 원활하게 삽입하세요."
"linktitle": "OLE 패키지를 사용하여 Word에 OLE 개체 삽입"
"second_title": "Aspose.Words 문서 처리 API"
"title": "OLE 패키지를 사용하여 Word에 OLE 개체 삽입"
"url": "/ko/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# OLE 패키지를 사용하여 Word에 OLE 개체 삽입

## 소개

Word 문서에 파일을 삽입하고 싶었던 적이 있다면, 바로 여기가 정답입니다. ZIP 파일이든, Excel 시트든, 다른 어떤 파일 형식이든 Word 문서에 직접 삽입하면 매우 유용할 수 있습니다. 마치 문서 안에 온갖 보물을 숨겨둘 수 있는 비밀 공간이 있는 것처럼 말이죠. 오늘은 Aspose.Words for .NET을 사용하여 이 작업을 수행하는 방법을 살펴보겠습니다. Word 전문가가 될 준비가 되셨나요? 시작해 볼까요!

## 필수 조건

시작하기에 앞서 다음 사항이 있는지 확인하세요.

1. Aspose.Words for .NET: 아직 다운로드하지 않았다면 여기에서 다운로드하세요. [여기](https://releases.aspose.com/words/net/).
2. 개발 환경: Visual Studio 또는 기타 .NET 개발 환경.
3. C#에 대한 기본적인 이해: 전문가가 될 필요는 없지만, C#에 대한 지식이 있으면 도움이 됩니다.
4. 문서 디렉토리: 문서를 저장하고 검색할 수 있는 폴더입니다.

## 네임스페이스 가져오기

먼저 네임스페이스를 정리하겠습니다. 프로젝트에 다음 네임스페이스를 포함해야 합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

따라하기 쉽도록 작은 단계로 나누어 설명하겠습니다.

## 1단계: 문서 설정

빈 캔버스를 가진 예술가라고 상상해 보세요. 먼저 빈 캔버스, 즉 Word 문서가 필요합니다. 설정 방법은 다음과 같습니다.

```csharp
// 문서 디렉토리 경로
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

이 코드는 새 Word 문서를 초기화하고 문서에 내용을 삽입하는 데 사용할 DocumentBuilder를 설정합니다.

## 2단계: Ole 객체 읽기

다음으로, 임베드하려는 파일을 읽어 보겠습니다. 마치 비밀 보관함에 숨겨두고 싶은 보물을 꺼내는 것처럼 생각해 보세요.

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

이 줄은 ZIP 파일에서 모든 바이트를 읽어 바이트 배열에 저장합니다.

## 3단계: Ole 개체 삽입

이제 마법의 순간입니다. 파일을 Word 문서에 삽입해 보겠습니다.

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

여기서 우리는 바이트 배열에서 메모리 스트림을 생성하고 사용합니다. `InsertOleObject` 문서에 삽입하는 방법을 설정합니다. 또한 삽입된 객체의 파일 이름과 표시 이름도 설정합니다.

## 4단계: 문서 저장

마지막으로, 우리의 걸작을 저장해 보겠습니다.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

이렇게 하면 지정된 디렉토리에 내장된 파일이 있는 문서가 저장됩니다.

## 결론

자, 이제 완성했습니다! Aspose.Words for .NET을 사용하여 Word 문서에 OLE 개체를 성공적으로 삽입했습니다. 마치 문서 안에 숨겨진 보석을 추가하여 언제든지 열어 볼 수 있는 것과 같습니다. 이 기술은 기술 문서부터 동적 보고서까지 다양한 용도로 매우 유용하게 활용할 수 있습니다. 

## 자주 묻는 질문

### 이 방법을 사용하여 다른 파일 형식을 포함할 수 있나요?
네, Excel 시트, PDF, 이미지 등 다양한 파일 형식을 포함할 수 있습니다.

### Aspose.Words를 사용하려면 라이센스가 필요합니까?
네, 유효한 면허증이 필요합니다. [임시 면허](https://purchase.aspose.com/temporary-license/) 평가를 위해.

### OLE 개체의 표시 이름을 사용자 지정하려면 어떻게 해야 하나요?
설정할 수 있습니다 `DisplayName` 의 재산 `OlePackage` 사용자 정의하려면.

### Aspose.Words는 .NET Core와 호환됩니까?
네, Aspose.Words는 .NET Framework와 .NET Core를 모두 지원합니다.

### Word 문서에 포함된 OLE 개체를 편집할 수 있나요?
아니요, Word에서 OLE 개체를 직접 편집할 수 없습니다. 기본 응용 프로그램에서 열어야 합니다.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}