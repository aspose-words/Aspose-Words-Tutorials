---
date: 2025-12-20
description: Aspose.Words를 사용하여 Java에서 파일을 유형별로 정리하고 문서 형식을 감지하는 방법을 배워보세요. DOC, DOCX,
  RTF 등 다양한 형식을 지원합니다.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 파일을 유형별로 정리하기
url: /ko/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용한 파일 유형별 정리

Java 애플리케이션에서 **파일을 유형별로 정리**해야 할 때, 첫 번째 단계는 각 문서의 형식을 신뢰할 수 있게 판단하는 것입니다. Aspose.Words for Java는 DOC, DOCX, RTF, HTML, ODT 등 다양한 형식을 감지하도록 간편하게 해 주며, 암호화된 파일이나 알 수 없는 파일도 처리할 수 있습니다. 이 가이드에서는 폴더 설정, 파일 형식 감지, 자동 정리 방법을 단계별로 안내합니다.

## 빠른 답변
- **“파일을 유형별로 정리”란 무엇인가요?** 감지된 형식(DOCX, PDF, RTF 등)에 따라 문서를 자동으로 해당 폴더로 이동하는 것을 의미합니다.  
- **Java에서 파일 형식을 감지하는 라이브러리는?** Aspose.Words for Java의 `FileFormatUtil.detectFileFormat()` 메서드가 이를 제공합니다.  
- **알 수 없는 파일 유형도 식별할 수 있나요?** 네. 지원되지 않거나 인식할 수 없는 파일은 `LoadFormat.UNKNOWN`을 반환합니다.  
- **암호화된 문서 감지가 지원되나요?** 물론입니다. `FileFormatInfo.isEncrypted()` 플래그를 통해 파일이 비밀번호로 보호되었는지 확인할 수 있습니다.  
- **프로덕션 환경에서 라이선스가 필요하나요?** 상업적 배포 시 유효한 Aspose.Words 라이선스가 필요합니다.

## 소개: Aspose.Words for Java로 파일을 유형별로 정리하기

Java에서 문서 처리를 할 때 파일 형식을 정확히 파악하는 것이 중요합니다. Aspose.Words for Java는 **detect file format java** 기능을 강력하게 제공하며, 효율적인 파일 정리 과정을 안내합니다.

## 사전 요구 사항

시작하기 전에 다음 사항을 준비하세요:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 시스템에 설치된 Java Development Kit (JDK)
- Java 프로그래밍에 대한 기본 지식

## 단계 1: 디렉터리 설정

먼저 파일을 효과적으로 정리할 디렉터리를 설정해야 합니다. 문서 유형별로 디렉터리를 생성합니다.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

지원되는 파일, 알 수 없는 파일, 암호화된 파일, 그리고 pre‑97 문서 유형을 위한 디렉터리를 만들었습니다.

## 단계 2: 문서 형식 감지

이제 디렉터리 내 문서들의 형식을 감지합니다. Aspose.Words for Java를 활용합니다.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

이 코드 스니펫에서는 파일을 순회하면서 **detect file format java**를 수행하고, 적절한 폴더로 정리합니다.

## Aspose.Words for Java에서 문서 형식 판단을 위한 전체 소스 코드

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## File Format Java 감지 방법

`FileFormatUtil.detectFileFormat()` 메서드는 파일 헤더를 검사하고 `FileFormatInfo` 객체를 반환합니다. 이 객체는 **load format**, 파일이 암호화되었는지 여부 및 기타 메타데이터를 알려줍니다. 이를 활용해 프로그램적으로 **identify unknown file types**를 수행하고 각 파일을 어떻게 처리할지 결정할 수 있습니다.

## 알 수 없는 파일 유형 식별

API가 `LoadFormat.UNKNOWN`를 반환하면 파일이 손상되었거나 Aspose.Words가 지원하지 않는 형식임을 의미합니다. 샘플 코드에서는 이러한 파일을 **Unknown** 폴더로 이동시켜 나중에 검토할 수 있도록 합니다.

## 일반적인 문제와 해결책

| 문제 | 원인 | 해결 방법 |
|------|------|----------|
| 파일이 항상 *Supported* 폴더에 배치됨 | `FileFormatUtil`이 헤더를 읽지 못함(예: 파일이 비어 있음) | 올바른 파일 경로를 전달했는지, 파일이 0바이트가 아닌지 확인하세요. |
| 암호화된 파일에서 예외 발생 | 암호화를 처리하지 않고 읽으려 함 | 코드에 표시된 대로 `info.isEncrypted()` 검사를 먼저 수행하세요. |
| Pre‑97 Word 문서가 감지되지 않음 | 오래된 형식은 `DOC_PRE_WORD_60` 케이스가 필요함 | `case LoadFormat.DOC_PRE_WORD_60` 블록을 유지해 *Pre97* 폴더로 라우팅하세요. |

## 자주 묻는 질문

### Aspose.Words for Java를 어떻게 설치하나요?

[여기](https://releases.aspose.com/words/java/)에서 Aspose.Words for Java를 다운로드하고 제공된 설치 안내를 따르세요.

### 지원되는 문서 형식은 무엇인가요?

Aspose.Words for Java는 DOC, DOCX, RTF, HTML, ODT 등 다양한 형식을 지원합니다. 전체 목록은 공식 문서를 참고하세요.

### Aspose.Words for Java로 암호화된 문서를 어떻게 감지하나요?

`FileFormatUtil.detectFileFormat()` 메서드를 사용하면 반환된 `FileFormatInfo.isEncrypted()` 플래그가 암호화 여부를 알려줍니다. 이 가이드에 예시가 포함되어 있습니다.

### 오래된 문서 형식을 사용할 때 제한 사항이 있나요?

MS Word 6 또는 Word 95와 같은 오래된 형식은 최신 기능이 부족하고 호환성 문제가 발생할 수 있습니다. 가능하면 최신 형식으로 변환하는 것을 권장합니다.

### Java 애플리케이션에서 문서 형식 감지를 자동화할 수 있나요?

네. 제공된 코드를 애플리케이션의 처리 파이프라인에 삽입하면 감지된 형식에 따라 자동 정렬 및 처리가 가능합니다.

---

**최종 업데이트:** 2025-12-20  
**테스트 환경:** Aspose.Words for Java 24.12 (최신)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}