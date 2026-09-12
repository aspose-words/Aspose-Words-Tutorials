---
date: '2026-09-12'
description: Aspose.Words와 OpenAI GPT‑4, Google Gemini AI 모델을 사용하여 Java에서 텍스트를 요약하고
  문서를 번역하는 방법을 배웁니다.
keywords:
- how to summarize text
- how to translate documents
- java license aspose words
lastmod: '2026-09-12'
og_description: Aspose.Words와 AI 모델을 사용하여 Java에서 텍스트를 요약하는 방법. 이 가이드는 OpenAI GPT‑4와
  Google Gemini를 활용한 문서 번역 방법을 단계별로 보여주며, 실용적인 코드 스니펫과 성능 팁을 제공합니다.
og_image_alt: 'Developer guide: summarize text and translate documents in Java using
  Aspose.Words and AI'
og_title: Aspose.Words와 AI를 사용하여 Java에서 텍스트 요약하는 방법
schemas:
- author: Aspose
  dateModified: '2026-09-12'
  description: Learn how to summarize text and how to translate documents in Java
    using Aspose.Words with OpenAI GPT‑4 and Google Gemini AI models.
  headline: How to summarize text in Java with Aspose.Words and AI
  type: TechArticle
- description: Learn how to summarize text and how to translate documents in Java
    using Aspose.Words with OpenAI GPT‑4 and Google Gemini AI models.
  name: How to summarize text in Java with Aspose.Words and AI
  steps:
  - name: initialize the document and the AI model
    text: Document is a class representing a Word document that can be loaded, edited,
      and saved.
  - name: configure summarization options
    text: 'Specify the desired summary length and any additional prompts:'
  - name: save the summary
    text: 'Write the generated summary to a new file:'
  - name: load and prepare the document
    text: 'Open the document and extract its plain‑text representation:'
  - name: execute translation
    text: 'Send the text to Gemini, receive the translated output, and overwrite the
      document:'
  type: HowTo
- questions:
  - answer: JDK 8 or higher, 2 GB RAM minimum, and a compatible IDE such as IntelliJ
      IDEA or Eclipse.
    question: What are the system requirements for using Aspose.Words with Java?
  - answer: Sign up on the OpenAI or Google Cloud console, create a new project, and
      generate a secret key for the respective service.
    question: How do I obtain an API key for OpenAI or Google AI services?
  - answer: Yes, provided you have a valid commercial license; the free trial is limited
      to evaluation only.
    question: Can I use Aspose.Words for Java in commercial projects?
  - answer: Gemini 15 Flash supports more than 100 languages, including Arabic, French,
      Spanish, Chinese, and Hindi.
    question: What languages does the Gemini model support for translation?
  - answer: Split the document into sections of ≤ 10 000 characters, process each
      chunk separately, and re‑assemble the results to keep memory usage low.
    question: How should I handle very large documents efficiently?
  type: FAQPage
tags:
- text summarization
- Aspose.Words
- Java AI integration
title: Aspose.Words와 AI를 사용하여 Java에서 텍스트 요약하는 방법
url: /ko/java/ai-machine-learning-integration/java-aspose-words-text-processing/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java와 Aspose.Words 및 AI를 사용한 텍스트 요약 방법

**Java용 Aspose.Words와 OpenAI의 GPT‑4, Google의 Gemini 15 Flash와 같은 AI 모델을 통합하여 텍스트 요약 및 번역을 자동화합니다.**

## 소개

긴 보고서에서 가장 중요한 아이디어를 추출하거나 내용을 즉시 다른 언어로 번역해야 할 경우, Java에서 두 작업을 모두 자동화할 수 있습니다. 이 튜토리얼에서는 Aspose.Words for Java와 주요 AI 서비스를 결합하여 **텍스트 요약 방법**과 **문서 번역 방법**을 보여주며, 수작업 시간을 크게 절감할 수 있습니다.

## 빠른 답변
- **주요 이점은 무엇인가요?** Java 코드를 떠나지 않고 즉시 고품질 요약 및 번역을 제공합니다.  
- **사용되는 AI 모델은?** OpenAI GPT‑4와 Google Gemini 15 Flash.  
- **라이선스가 필요한가요?** 예 – 프로덕션 환경에서는 Aspose.Words용 Java 라이선스가 필요합니다.  
- **로컬에서 실행할 수 있나요?** 예, 모든 호출은 Java 애플리케이션에서 클라우드 API로 전송됩니다.  
- **보통 구현 시간은?** 기본 프로토타입의 경우 약 15‑20분 정도 소요됩니다.

## 텍스트 요약이란 무엇인가요?
**텍스트 요약**은 큰 문서에서 핵심 메시지를 유지하면서 간결한 버전을 프로그램적으로 추출하는 과정을 의미합니다. AI를 활용하면 보고서, 기사, 계약서 등의 핵심을 몇 초 만에 요약할 수 있습니다.

## 왜 Aspose.Words와 AI 모델을 함께 사용하나요?
Aspose.Words for Java는 **35개 이상의 입력 및 출력 형식**을 지원하며 표준 서버에서 **5초 미만에 500페이지 문서**를 처리할 수 있어 Microsoft Word가 필요하지 않습니다. GPT‑4가 **요청당 최대 8,192 토큰**을 처리할 수 있는 능력과 결합하면 품질을 손상시키지 않으면서 빠르고 정확한 요약 및 번역을 얻을 수 있습니다.

## 사전 요구 사항
- **Java Development Kit (JDK):** 버전 8 이상.  
- **빌드 도구:** Maven 또는 Gradle (선택 가능).  
- **IDE:** IntelliJ IDEA, Eclipse 또는 Java 호환 편집기.  
- **API 키:** OpenAI 및 Google Gemini 서비스에 대한 유효한 키.  
- **Aspose.Words 라이선스:** Java용 체험, 임시 또는 구매 라이선스.

## Aspose.Words 설정

`Aspose.Words for Java`는 Java 코드에서 직접 35개 이상의 파일 형식을 생성, 조작 및 변환할 수 있는 포괄적인 문서 처리 API입니다.

### Maven 의존성

Add this snippet to your `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle 의존성

Include this in your `build.gradle` file:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 라이선스 획득

Aspose.Words는 전체 기능을 사용하려면 라이선스가 필요합니다. 다음 방법으로 획득할 수 있습니다:
- 기능을 테스트할 수 있는 **무료 체험**.  
- 평가 기간을 연장할 수 있는 **임시 라이선스**.  
- 프로덕션 사용을 위한 **구매 라이선스**.

라이브러리를 초기화하고 라이선스를 설정합니다:

License는 Aspose.Words에서 라이선스 파일을 로드하고 적용하여 전체 기능을 활성화하는 클래스입니다.  
```java
License license = new License();
license.setLicense("path/to/your/license/file");
```

## 텍스트 요약 방법

소스 문서를 로드하고 해당 내용을 GPT‑4 모델에 전송한 뒤 반환된 요약을 새 Word 파일에 기록합니다. 이 두 단계 흐름은 텍스트를 관리 가능한 청크로 스트리밍하여 모든 크기의 문서를 처리합니다. 이 방법은 PDF, DOCX 및 기타 형식에서도 작동하여 문서 유형에 관계없이 일관된 결과를 제공합니다.

### 단계 1: 문서 및 AI 모델 초기화

Document는 로드, 편집 및 저장할 수 있는 Word 문서를 나타내는 클래스입니다.  
```java
document = new Document(getMyDir() + "Big document.docx");
IAiModelText model = ((OpenAiModel) AiModel.create(AiModelType.GPT_4_O_MINI).withApiKey(apiKey))
        .withOrganization("YourOrg")
        .withProject("YourProject");
```

### 단계 2: 요약 옵션 구성

원하는 요약 길이와 추가 프롬프트를 지정합니다:

```java
SummarizeOptions options = new SummarizeOptions();
options.setSummaryLength(SummaryLength.SHORT);
Document summarizedDoc = model.summarize(document, options);
```

### 단계 3: 요약 저장

생성된 요약을 새 파일에 기록합니다:

```java
summarizedDoc.save(getArtifactsDir() + "AI.AiSummarize.One.docx");
```

## 문서 번역 방법

Word 파일을 Gemini 15 Flash 모델에 텍스트를 전송하여 다른 언어로 번역한 뒤, 원본 내용을 번역된 버전으로 교체합니다. 이 방법은 서식을 유지하면서 지원되는 모든 언어에 대해 정확한 다국어 출력을 제공합니다.

### 단계 1: 문서 로드 및 준비

문서를 열고 순수 텍스트 형태로 추출합니다:

```java
document = new Document(getMyDir() + "Document.docx");
IAiModelText translator = (IAiModelText) AiModel.create(AiModelType.GEMINI_15_FLASH).withApiKey(apiKey);
```

### 단계 2: 번역 실행

텍스트를 Gemini에 전송하고 번역된 결과를 받아 문서를 덮어씁니다:

```java
Document translatedDoc = translator.translate(document, Language.ARABIC);
translatedDoc.save(getArtifactsDir() + "AI.AiTranslate.docx");
```

## Aspose.Words Java 라이선스 획득 방법

Aspose에서 라이선스를 구매하거나 요청한 뒤, `.lic` 파일을 프로젝트의 resources 폴더에 배치하고 `License license = new License(); license.setLicense("Aspose.Words.Java.lic");` 로 로드합니다. 이렇게 하면 전체 기능 모드가 활성화되고 평가 워터마크가 제거되며 프로덕션 작업에 필요한 고성능 처리가 가능해집니다. 라이선스 파일을 클래스패스에 두면 런타임 시 모든 환경에서 자동으로 찾을 수 있습니다.

## 실용적인 적용 사례
1. **비즈니스 보고서:** 분기별 PDF를 몇 초 만에 임원 수준의 요약으로 생성합니다.  
2. **고객 지원:** 들어오는 티켓을 지원팀의 모국어로 번역하여 신속한 해결을 돕습니다.  
3. **학술 연구:** 방대한 논문을 요약하여 관련 섹션을 빠르게 파악합니다.

## 성능 고려 사항
- **배치 API 호출:** 요청당 최대 10개의 문서를 그룹화하여 지연 시간을 줄입니다.  
- **리소스 모니터링:** 다수의 페이지를 가진 파일을 처리할 때 Java의 `Runtime.getRuntime().freeMemory()`를 사용해 힙 사용량을 확인합니다.  
- **캐싱:** 자주 요청되는 번역을 Redis 캐시에 저장하여 반복적인 AI 호출을 방지합니다.

## 자주 묻는 질문
**Q: Aspose.Words와 Java를 사용할 때 시스템 요구 사항은 무엇인가요?**  
A: JDK 8 이상, 최소 2 GB RAM, IntelliJ IDEA 또는 Eclipse와 같은 호환 IDE.

**Q: OpenAI 또는 Google AI 서비스의 API 키는 어떻게 얻나요?**  
A: OpenAI 또는 Google Cloud 콘솔에 가입하고 새 프로젝트를 만든 뒤 해당 서비스의 비밀 키를 생성합니다.

**Q: Aspose.Words for Java를 상업 프로젝트에 사용할 수 있나요?**  
A: 예, 유효한 상업용 라이선스가 있으면 사용 가능하며, 무료 체험은 평가 용도로만 제한됩니다.

**Q: Gemini 모델이 지원하는 번역 언어는 무엇인가요?**  
A: Gemini 15 Flash는 아랍어, 프랑스어, 스페인어, 중국어, 힌디어 등을 포함해 100개 이상의 언어를 지원합니다.

**Q: 매우 큰 문서를 효율적으로 처리하려면 어떻게 해야 하나요?**  
A: 문서를 ≤ 10 000자 섹션으로 나누고 각 청크를 별도로 처리한 뒤 결과를 재조합하여 메모리 사용량을 낮게 유지합니다.

## 리소스
- [Aspose.Words 문서](https://reference.aspose.com/words/java/)
- [Aspose.Words 다운로드](https://releases.aspose.com/words/java/)
- [라이선스 구매](https://purchase.aspose.com/buy)
- [무료 체험 버전](https://releases.aspose.com/words/java/)
- [임시 라이선스 요청](https://purchase.aspose.com/temporary-license/)
- [Aspose 커뮤니티 지원](https://forum.aspose.com/c/words/10)

---

**마지막 업데이트:** 2026-09-12  
**테스트 환경:** Aspose.Words for Java 25.3  
**작성자:** Aspose

## 관련 튜토리얼
- [Aspose.Words Java 튜토리얼: AI 및 ML 통합](/words/java/ai-machine-learning-integration/)
- [Aspose.Words for Java 고급 텍스트 처리 마스터](/words/java/advanced-text-processing/)
- [Aspose.Words for Java로 텍스트 파일 로드](/words/java/document-loading-and-saving/loading-text-files/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}