---
"description": "Aspose.Words for Java를 사용하여 ODT 형식으로 문서를 저장하는 방법을 알아보세요. 오픈 소스 오피스 제품군과의 호환성을 보장합니다."
"linktitle": "ODT 형식으로 문서 저장"
"second_title": "Aspose.Words Java 문서 처리 API"
"title": "Java용 Aspose.Words에서 ODT 형식으로 문서 저장"
"url": "/ko/java/document-loading-and-saving/saving-documents-as-odt-format/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 ODT 형식으로 문서 저장


## Aspose.Words for Java에서 문서를 ODT 형식으로 저장하는 방법 소개

이 글에서는 Aspose.Words for Java를 사용하여 문서를 ODT(Open Document Text) 형식으로 저장하는 방법을 살펴보겠습니다. ODT는 OpenOffice와 LibreOffice를 포함한 다양한 오피스 제품군에서 사용되는 널리 사용되는 개방형 표준 문서 형식입니다. ODT 형식으로 문서를 저장하면 이러한 소프트웨어 패키지와의 호환성을 보장할 수 있습니다.

## 필수 조건

시작하기에 앞서 다음과 같은 전제 조건이 충족되었는지 확인하세요.

1. Java 개발 환경: 시스템에 Java Development Kit(JDK)가 설치되어 있는지 확인하세요.

2. Aspose.Words for Java: Aspose.Words for Java 라이브러리를 다운로드하여 설치하세요. 다운로드 링크는 다음과 같습니다. [여기](https://releases.aspose.com/words/java/).

3. 샘플 문서: ODT 형식으로 변환하려는 샘플 Word 문서(예: "Document.docx")가 있습니다.

## 1단계: 문서 로드

먼저, Aspose.Words for Java를 사용하여 Word 문서를 로드해 보겠습니다.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

여기, `"Your Directory Path"` 문서가 있는 디렉토리를 가리켜야 합니다.

## 2단계: ODT 저장 옵션 지정

문서를 ODT로 저장하려면 ODT 저장 옵션을 지정해야 합니다. 또한, 문서의 측정 단위를 설정할 수 있습니다. Open Office는 센티미터를 사용하는 반면, MS Office는 인치를 사용합니다. 여기서는 인치로 설정하겠습니다.

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## 3단계: 문서 저장

이제 ODT 형식으로 문서를 저장할 시간입니다.

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

여기, `"Your Directory Path"` 변환된 ODT 파일을 저장할 디렉토리를 가리켜야 합니다.

## Aspose.Words for Java에서 문서를 ODT 형식으로 저장하기 위한 전체 소스 코드

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office는 길이, 너비 및 기타 측정 가능한 서식을 지정할 때 센티미터를 사용합니다.
// 문서의 콘텐츠 속성과 달리 MS Office는 인치를 사용합니다.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## 결론

이 글에서는 Aspose.Words for Java를 사용하여 문서를 ODT 형식으로 저장하는 방법을 알아보았습니다. 이 기능은 OpenOffice나 LibreOffice와 같은 오픈소스 오피스 제품군과의 호환성을 유지해야 할 때 특히 유용합니다.

## 자주 묻는 질문

### Java용 Aspose.Words를 어떻게 다운로드할 수 있나요?

Aspose.Words for Java는 Aspose 웹사이트에서 다운로드할 수 있습니다. [이 링크](https://releases.aspose.com/words/java/) 다운로드 페이지에 접속하세요.

### ODT 형식으로 문서를 저장하면 어떤 이점이 있나요?

ODT 형식으로 문서를 저장하면 OpenOffice 및 LibreOffice와 같은 오픈 소스 오피스 제품군과의 호환성이 보장되어 이러한 소프트웨어 패키지를 사용하는 사용자가 문서에 쉽게 접근하여 편집할 수 있습니다.

### ODT 형식으로 저장할 때 측정 단위를 지정해야 합니까?

네, 측정 단위를 지정하는 것이 좋습니다. Open Office는 기본적으로 센티미터를 사용하므로 인치로 설정하면 일관된 서식을 유지할 수 있습니다.

### 여러 문서를 일괄 처리로 ODT 형식으로 변환할 수 있나요?

네, Aspose.Words for Java를 사용하여 여러 문서를 ODT 형식으로 변환하는 작업을 자동화할 수 있습니다. 문서 파일을 반복하고 변환 프로세스를 적용하면 됩니다.

### Aspose.Words for Java는 최신 Java 버전과 호환됩니까?

Aspose.Words for Java는 최신 Java 버전을 지원하도록 정기적으로 업데이트되어 호환성과 성능 향상을 보장합니다. 최신 정보를 확인하려면 설명서의 시스템 요구 사항을 확인하세요.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}