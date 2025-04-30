---
"date": "2025-03-28"
"description": "Aspose.Words for Java를 사용하여 고정 형식 XAML로 문서를 저장하는 방법, 리소스 관리 및 성능 최적화 등을 알아봅니다."
"title": "Aspose.Words Java&#58; 링크된 리소스 관리를 통해 고정 형식 XAML 형식으로 문서 저장"
"url": "/ko/java/document-operations/aspose-words-java-fixed-form-xaml-saving/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 고정 형식 XAML 문서 저장을 위한 Aspose.Words Java 마스터링

## 소개

Java를 사용하여 고정 형식 XAML 형식으로 문서를 저장하는 데 어려움을 겪고 계신가요? 여러분만 그런 것이 아닙니다. 많은 개발자들이 복잡한 문서 저장 시나리오, 특히 이미지나 글꼴과 같은 링크된 리소스를 처리할 때 어려움을 겪습니다. 이 튜토리얼에서는 구성 및 사용 방법을 안내합니다. `XamlFixedSaveOptions` 이 문제를 효율적으로 해결하기 위해 Aspose.Words for Java의 클래스를 사용했습니다.

**배울 내용:**
- 구성 방법 `XamlFixedSaveOptions` 고정된 형태의 XAML 저장을 위해.
- 사용자 정의 리소스 절약 콜백 구현 `ResourceUriPrinter`.
- 문서 변환 중에 연결된 리소스를 관리하기 위한 모범 사례입니다.
- 실제 적용 사례와 성능 최적화 팁.

시작하기 전에 모든 것이 제대로 설정되어 있는지 확인해 봅시다. 바로 사전 준비 사항 섹션으로 넘어가 볼까요!

## 필수 조건

이 튜토리얼을 따라하려면 다음 사항이 있는지 확인하세요.

### 필수 라이브러리
- **Aspose.Words for Java**: 25.3 이상 버전을 사용하고 있는지 확인하세요.
  
### 환경 설정
- 작동하는 Java 개발 환경(JDK 8 이상 권장).
- IntelliJ IDEA나 Eclipse와 같은 IDE.

### 지식 전제 조건
- Java 프로그래밍과 객체 지향 개념에 대한 기본적인 이해가 있습니다.
- Java 애플리케이션에서 파일을 처리하는 데 익숙함.

## Aspose.Words 설정

시작하려면 프로젝트에 Aspose.Words 라이브러리를 추가해야 합니다. Maven이나 Gradle을 사용하여 추가하는 방법은 다음과 같습니다.

### 메이븐

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### 그래들

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 라이센스 취득 단계

1. **무료 체험**: ~로 시작하다 [무료 체험](https://releases.aspose.com/words/java/) 기능을 탐색해보세요.
2. **임시 면허**: 신청하세요 [임시 면허](https://purchase.aspose.com/temporary-license/) 제한 없이 Aspose.Words를 평가해야 하는 경우
3. **구입**: 만족하시면 전체 라이센스를 구매하세요. [Aspose 웹사이트](https://purchase.aspose.com/buy).

### 기본 초기화

위에 설명한 대로 라이브러리를 다운로드하고 환경을 설정하여 Java 프로젝트를 초기화합니다.

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("path/to/your/document.docx");
        System.out.println("Document loaded successfully!");
    }
}
```

## 구현 가이드

이 섹션은 프로세스의 각 부분을 이해하는 데 도움이 되도록 논리적 특징으로 구분되어 있습니다.

### XamlFixedSaveOptions 설정 및 사용

#### 개요
그만큼 `XamlFixedSaveOptions` 클래스를 사용하면 문서를 고정 형식 XAML 형식으로 저장하여 이미지 및 글꼴과 같은 연결된 리소스에 대한 제어 기능을 제공할 수 있습니다. 이 기능은 표준화된 파일 구조를 사용하여 다양한 플랫폼에서 일관성을 유지하는 데 도움이 됩니다.

#### 1단계: 문서 로드

먼저 XAML 형식으로 저장하려는 기존 문서를 로드합니다.

```java
import com.aspose.words.Document;

Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");
```

#### 2단계: 리소스 절약 콜백 설정

사용자 정의를 만듭니다 `ResourceUriPrinter` 저장 프로세스 중에 연결된 리소스를 처리하기 위한 콜백입니다.

```java
ResourceUriPrinter callback = new ResourceUriPrinter();
```

#### 3단계: XamlFixedSaveOptions 구성

다음으로 구성합니다. `XamlFixedSaveOptions` 귀하의 문서의 특정 요구 사항에 맞는 클래스를 선택하세요.

```java
import com.aspose.words.XamlFixedSaveOptions;

XamlFixedSaveOptions options = new XamlFixedSaveOptions();

assert SaveFormat.XAML_FIXED == options.getSaveFormat();
options.setResourcesFolder("YOUR_OUTPUT_DIRECTORY/XamlFixedResourceFolder");
options.setResourcesFolderAlias("YOUR_OUTPUT_DIRECTORY/XamlFixedFolderAlias");
options.setResourceSavingCallback(callback);

new File(options.getResourcesFolderAlias()).mkdir();
```

#### 4단계: 문서 저장

마지막으로 구성된 옵션을 사용하여 문서를 저장합니다.

```java
doc.save("YOUR_OUTPUT_DIRECTORY/XamlFixedSaveOptions.ResourceFolder.xaml", options);
```

### ResourceUriPrinter 구현

#### 개요
그만큼 `ResourceUriPrinter` 클래스는 변환 중에 연결된 리소스의 URI를 출력하는 사용자 지정 리소스 절약 콜백을 구현합니다. 이는 외부 자산을 추적하고 관리하는 데 매우 중요합니다.

#### 1단계: 콜백 구현

구현을 만듭니다. `IResourceSavingCallback` 인터페이스:

```java
import com.aspose.words.*;

private static class ResourceUriPrinter implements IResourceSavingCallback {
    public ResourceUriPrinter() {
        mResources = new ArrayList<>();
    }

    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        getResources().add(MessageFormat.format("Resource \"{0}\"\n\t{1}",
            args.getResourceFileName(), args.getResourceFileUri()));
        args.setResourceStream(new FileOutputStream(args.getResourceFileUri()));
        args.setKeepResourceStreamOpen(false);
    }

    public ArrayList<String> getResources() {
        return mResources;
    }

    private final ArrayList<String> mResources;
}
```

#### 2단계: 자원 절약 시뮬레이션

콜백 기능을 테스트하려면 리소스 절약 이벤트를 시뮬레이션하세요.

```java
ResourceUriPrinter printer = new ResourceUriPrinter();
ResourceSavingArgs exampleArgs = new ResourceSavingArgs() {
    public String getResourceFileName() { return "example.png"; }
    public String getResourceFileUri() { return "YOUR_OUTPUT_DIRECTORY/XamlFixedFolderAlias/example.png"; }

    @Override
    public void setResourceStream(java.io.OutputStream resourceStream) {}
};

try {
    printer.resourceSaving(exampleArgs);
    for (String resource : printer.getResources()) {
        System.out.println(resource);
    }
} catch (Exception e) {
    e.printStackTrace();
}
```

## 실제 응용 프로그램

다음은 몇 가지 실제 시나리오입니다. `XamlFixedSaveOptions` 특히 유용할 수 있습니다:

1. **문서 관리 시스템**: 여러 플랫폼에서 일관된 문서 렌더링을 보장합니다.
2. **크로스 플랫폼 퍼블리싱**: 표준화된 형식을 사용하여 출판 과정을 간소화합니다.
3. **엔터프라이즈 보고 도구**: 내장된 리소스를 통해 문서를 보고 도구에 원활하게 통합할 수 있습니다.

## 성능 고려 사항

대용량 문서를 저장할 때 성능을 최적화하려면:
- **자원 관리**링크된 리소스가 효율적으로 관리되고 적절한 디렉토리에 저장되도록 합니다.
- **스트림 처리**: 시스템 리소스를 확보하기 위해 사용 후 즉시 스트림을 닫으세요.
- **일괄 처리**: 해당되는 경우 멀티스레딩 기술을 활용하여 여러 문서를 동시에 처리합니다.

## 결론

이제 효과적으로 구현하는 방법을 배웠습니다. `XamlFixedSaveOptions` 문서를 고정 형식 XAML 형식으로 저장하기 위해 Aspose.Words for Java를 사용하는 클래스입니다. 이 설정을 통해 다양한 플랫폼에서 리소스 관리 및 문서 일관성을 정밀하게 제어할 수 있습니다.

### 다음 단계
- Aspose.Words가 제공하는 추가 구성을 실험해 보세요.
- 도서관에서 지원하는 다른 문서 형식을 살펴보세요.
- 이 기능을 기존 Java 애플리케이션에 통합하세요.

문서 처리 역량을 한 단계 끌어올릴 준비가 되셨나요? 지금 바로 이 솔루션을 구현해 보세요!

## FAQ 섹션

**1. Java용 Aspose.Words의 XamlFixedSaveOptions는 무엇입니까?**
`XamlFixedSaveOptions` 고정된 형식의 XAML 형식으로 문서를 저장할 수 있으므로 저장 프로세스 중에 연결된 리소스가 관리되는 방식을 제어할 수 있습니다.

**2. Aspose.Words를 사용할 때 예외를 어떻게 처리하나요?**
잠재적인 예외를 효과적으로 관리하고 기록하려면 코드 블록을 try-catch 문으로 감싸세요.

**3. 라이선스 없이 Aspose.Words for Java를 사용할 수 있나요?**
네, 하지만 문서에 워터마크가 표시되는 등의 제한이 있을 수 있습니다. [임시 면허](https://purchase.aspose.com/temporary-license/) 필요하다면.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}