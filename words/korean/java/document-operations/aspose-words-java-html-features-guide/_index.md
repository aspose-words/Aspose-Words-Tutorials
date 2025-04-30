---
"date": "2025-03-28"
"description": "VML 지원, 암호화, HTML 가져오기 옵션 등을 포함하여 문서 처리를 마스터하기 위해 Aspose.Words for Java를 활용하는 방법을 알아보세요."
"title": "Aspose.Words for Java의 포괄적인 HTML 기능 및 문서 처리 가이드"
"url": "/ko/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Aspose.Words for Java를 통한 포괄적인 HTML 기능: 개발자 가이드

## 소개

복잡한 문서 처리 환경을 탐색하는 것은 어려울 수 있으며, 특히 다양한 HTML 기능을 다룰 때는 더욱 그렇습니다. VML(벡터 마크업 언어) 지원, 암호화된 문서, 특정 HTML 가져오기 동작 등 어떤 작업을 하든, **Aspose.Words for Java** 강력한 솔루션을 제공합니다. 이 가이드에서는 Aspose.Words를 사용하여 이러한 기능을 원활하게 구현하고 문서 처리 역량을 향상시키는 방법을 살펴보겠습니다.

**배울 내용:**
- VML 지원을 사용하여 HTML 문서를 로드하는 방법.
- 고정 페이지 HTML 및 경고를 처리하는 기술.
- 암호로 보호된 HTML 문서를 암호화하고 로딩하는 방법.
- HTML 로드 옵션에서 기본 URI 활용.
- HTML 입력 요소를 구조화된 문서 태그나 양식 필드로 가져옵니다.
- 묵살 `<noscript>` HTML 로드 중의 요소.
- HTML 구조 보존을 제어하기 위해 블록 가져오기 모드를 구성합니다.
- 지원 `@font-face` 사용자 정의 글꼴에 대한 규칙.

이러한 통찰력을 바탕으로 다양한 HTML 처리 작업을 처리할 수 있는 역량을 갖추게 될 것입니다. 먼저 필수 구성 요소와 설정을 살펴보겠습니다!

## 필수 조건

Aspose.Words for Java를 사용하여 다양한 HTML 기능을 구현하기 전에 환경이 올바르게 설정되어 있는지 확인하세요.

- **필수 라이브러리:** Aspose.Words 라이브러리 버전 25.3 이상이 필요합니다.
- **개발 환경:** 이 가이드에서는 종속성 관리를 위해 Maven이나 Gradle을 사용한다고 가정합니다.
- **지식 기반:** Java에 대한 기본적인 이해와 HTML 문서에 대한 친숙함이 도움이 될 것입니다.

## Aspose.Words 설정

Aspose.Words를 사용하려면 먼저 프로젝트에 Aspose.Words를 포함해야 합니다. Maven과 Gradle을 사용하여 라이브러리를 설정하는 단계는 다음과 같습니다.

### 메이븐

다음 종속성을 추가하세요. `pom.xml` 파일:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### 그래들

이것을 당신의 것에 포함시키세요 `build.gradle` 파일:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 라이센스 취득

Aspose.Words의 모든 기능을 사용하려면 라이선스가 필요합니다. 무료 체험판을 이용하거나, 임시 라이선스를 요청하거나, 영구 라이선스를 구매할 수 있습니다. [구매 페이지](https://purchase.aspose.com/buy) 자세한 내용은.

Java 프로젝트에서 Aspose.Words를 초기화하려면 라이선스를 올바르게 설정했는지 확인하세요.

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

구현하고자 하는 기능에 따라 구현을 섹션으로 나누겠습니다.

### HTML 문서에서 VML 지원

**개요:**
VML 지원 여부와 관계없이 HTML 문서를 로드하면 벡터 그래픽을 다양하게 렌더링할 수 있습니다. 이 기능은 차트나 도형과 같은 그래픽 요소가 포함된 문서를 다룰 때 매우 중요합니다.

#### 단계별 구현:

1. **로드 옵션 설정**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // VML 지원 활성화
   ```

2. **문서 로드**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **이미지 유형 확인**
   
   이미지 유형이 기대에 부합하는지 확인하세요.
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // 실제 논리에 따라 조정

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### HTML 고정 및 경고 처리 로드

**개요:**
고정 페이지 HTML 문서를 로드하면 정확한 처리를 위해 관리해야 하는 경고가 발생할 수 있습니다.

#### 단계별 구현:

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
HTML 문서를 비밀번호로 암호화하면 민감한 정보에 대한 안전한 액세스가 보장됩니다.

#### 단계별 구현:

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

### HTML 로드 옵션에 대한 기본 URI

**개요:**
기본 URI를 지정하면 상대 URI를 확인하는 데 도움이 되며, 특히 이미지나 다른 링크된 리소스를 처리할 때 유용합니다.

#### 단계별 구현:

1. **기본 URI를 사용하여 로드 옵션 구성**
   
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
수입 `<select>` 요소를 구조화된 문서 태그로 사용하면 Word 문서 내에서 보다 나은 제어와 서식 지정이 가능합니다.

#### 단계별 구현:

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

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}