---
date: '2026-02-06'
description: Aspose.Words for Java를 사용하여 HTML VML을 로드하고, HTML Java 파일을 암호화하며, HTML
  기본 URI를 설정하고, HTML 컨트롤 옵션을 구성하는 방법을 배웁니다.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Aspose.Words for Java를 사용하여 HTML VML 로드 – 완전 가이드
url: /ko/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 활용한 전체인 HTML 기능: 개발자 가이드

## 소개

문서 처리의 복잡한 세계를 탐색하는 분야 중 특히 다양한 HTML 기능을 사용할 수 있는 경우가 있습니다. VML(Vector Markup Language) 지원, 메일화된 문서 또는 특정 HTML 가져오기 기능을 가지고 있음, **Aspose.Words for Java**는 강력한 솔루션을 제공합니다. 이 가이드에서는 **html vml을 로드하는 방법**을 반응하고 안전하게 활동하는 방법을 배우며, **html java 암호화**, **html 기본 uri 설정**, **html 컨트롤 구성** 옵션과 같은 관련 작업도 다뤄요.

**배우게 될 내용:**
- VML 지원이 포함된 HTML 문서를 로드하는 방법
- 고정 페이지 HTML 및 공지사항을 공지합니다.
- 압축으로 보호된 HTML 문서를 로드하고 로드하는 방법
- HTML 로드 옵션에서 기본 URI 활용
- HTML 입력 요소를 구조화된 문서 태그 또는 폼 필드로 가져오기
- HTML 로드 시 `<noscript>` 요소 무시하기
- HTML 구조 반대를 제어하는 ​​블록 가져오기 모드 구성
- 사용자 표기법 `@font-face` 지원 규칙

## 빠른 답변
- **HTML을 로드할 때 VML을 활성화하는 기본 방법은 무엇입니까?** `loadOptions.setSupportVml(true)`를 설정하세요.
- **비밀번호로 보호된 HTML 파일을 로드할 수 있습니까?** 예, 'HtmlLoadOptions'에 비밀번호를 전달합니다.
- **상대 이미지 경로를 어떻게 확인하나요?** `loadOptions.setBaseUri("your/base/uri")`를 사용하세요.
- **`<select>`를 양식 필드로 가져올 수 있습니까?** `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`을 설정하세요.
- **로드 중에 경고를 캡처하는 클래스는 무엇입니까?** 'IWarningCallback'을 구현하고 이를 'loadOptions.setWarningCallback(...)'에 할당합니다.

## 전제조건

Aspose.Words for Java와 다양한 HTML을 구현하기 위해 환경을 조정하도록 확인하십시오:

- **필수 라이브러리:** Aspose.Words 서버 버전 25.3이 필요합니다.
- **개발 환경:** 이 가이드는 Maven 또는 Gradle을 사용하여 의존성을 관리해야 합니다.
- **지식 기반:** Java 기본 지식과 HTML 문서에 대한 이해가 필요하면 도움이 됩니다.

## Aspose.Words 설정

Aspose.Words를 프로젝트에 참여하려면 먼저 준비해야 합니다. 아래는 Maven과 Gradle을 이용한 설정 방법입니다.

### 메이븐

`pom.xml` 파일에 다음 의존성을 추가하십시오:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

`build.gradle` 파일에 다음을 포함하십시오:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 라이선스 취득

Aspose.Words는 전체 기능을 사용하려면 라이선스가 필요합니다. 무료 체험판을 받거나 임시 라이선스를 요청하거나 영구 라이선스를 구매할 수 있습니다. 자세한 내용은 [purchase page](https://purchase.aspose.com/buy)를 방문하십시오.

Java 프로젝트에서 Aspose.Words를 초기화하려면 라이선스를 올바르게 설정했는지 확인하십시오:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## 구현 가이드

우리는 존재하고자 하는 기능을 섹션을 나누어 설명합니다.

### Aspose.Words를 사용하여 html vml을 로드하는 방법

**개요:**
VML 지원이 포함된 HTML 문서를 로드하면 차트와 도형 같은 벡터 그래픽을 범위 있게 저장할 수 있습니다. 핵심 키워드 **load html vml**에 해당하는 핵심 단계입니다.

#### 단계별

1. **로드 옵션 설정**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **문서 로드**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **이미지 유형 확인**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### HTML 수정 로드 및 경고 처리

**개요:**
고정된 페이지의 HTML 문서를 로드하면 처리를 위해 관리해야 할 일이 발생할 수 있습니다.

#### 단계별

1. **경고 콜백 정의**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **로드 옵션 구성**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **문서 로드 및 경고 확인**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### HTML 문서 암호화

**개요:**
HTML 문서를 포그로 라이브러리에 추가하면 안전하게 보호할 수 있습니다. 이는 **encrypt html java**에 해당됩니다.

#### 단계별

1. **디지털 서명 옵션 준비**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **문서 서명 및 암호화**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **암호화된 문서 로드**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### HTML 로드 옵션의 기본 URI

**개요:**
**set html base uri**를 지정하면 이미지나 기타 연결 위치의 상대 URI를 고정할 수 있습니다.

#### 단계별

1. **기본 URI로 로드 옵션 구성**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **문서 로드 및 이미지 확인**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### HTML 가져오기 구조화된 문서 태그로 선택

**개요:**
**html 컨트롤 구성** 동작을 조정하려면 `<select>` 요소를 구조화된 문서 태그로 연결하세요. Word 문서 내 폼 필드를 보다 세밀하게 제어할 수 있습니다.

#### 단계별

1. **선호하는 제어 유형 설정**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **문서 로드 및 구조 확인**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## 일반적인 문제 및 해결 방법

| 이슈 | 이유 | 수정 |
|-------|---------|-----|
| VML 그래픽이 나타나지 않음 | `supportVml` 호출이 있습니다(`false`)로 남아 있습니다 | 로드하기 전에 `loadOptions.setSupportVml(true)`를 설정하시기 바랍니다. |
| 로드 후 이미지 누락 | 별칭을 해석할 수 없습니다 | **set html base uri**(`loadOptions.setBaseUri(...)`)를 사용하여 사용자를 폴더를 보호하십시오. |
| 비밀번호로 보호된 HTML에서 예외가 발생함 | 포스틱을 제공하지 않는 경우 | `new HtmlLoadOptions("yourPassword")`에 포스틱을 전달해주세요. |
| 양식 컨트롤이 일반 텍스트로 나타납니다 | 잘못된 `HtmlControlType` 설정 | 필요에 따라 `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` 또는 `FormField`로 설정하십시오. |
| 예상치 못한 경고 | 처리되지 않은 HTML 요소 | `IWarningCallback`을 구현하여 경고를 캡처하고 확인하십시오.

## 자주 묻는 질문

**Q: VML과 최신 SVG 그래픽이 모두 포함된 HTML 파일을 로드할 수 있습니까?**
A: 예. `setSupportVml(true)`를 사용하여 VML을 활성화하면 Aspose.Words에서 SVG를 자동으로 처리합니다.

**Q: 디지털 인증서를 사용하지 않고 HTML 문서를 암호화하려면 어떻게 해야 합니까?**
A: 암호를 허용하는 `HtmlLoadOptions` 생성자를 사용하고 암호를 설정한 후 `Document.save(..., SaveFormat.HTML)`로 문서를 저장하십시오.

**Q: 기본 URI가 존재하지 않는 폴더를 가리키면 어떻게 됩니까?**
A: Aspose.Words는 누락된 리소스에 대해 `FileNotFoundException`을 발생시킵니다. 로드하기 전에 경로를 확인하십시오.

**Q: 모든 HTML 폼 요소의 기본 컨트롤 유형을 변경할 수 있습니까?**
A: 예. `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`를 사용하여 전역적으로 적용할 수 있습니다.

**질문: 경고 콜백은 스레드 안전한가요?**
답변: 문서를 동시에 로드할 계획이라면 콜백 구현은 스레드 안전해야 합니다. 동기화된 컬렉션이나 스레드 로컬 스토리지를 사용하세요.

---

**최종 업데이트:** 2026년 2월 6일
**테스트 환경:** Aspose.Words for Java 25.3
**작성자:** Aspose 

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}