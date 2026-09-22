---
date: 2026-02-22
description: Aspose.Words를 사용하여 Java에서 문서 형식을 감지하고 형식별로 파일을 자동으로 이동하는 방법을 배웁니다. DOC,
  DOCX 등 다양한 형식을 식별합니다.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 이용한 문서 형식 감지
url: /ko/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용한 detect document format java

파일 배치를 할 때 **detect document format java**가 필요하면, 파일을 자동으로 올바른 폴더에 정렬하는 기능이 수작업 시간을 크게 절감해 줍니다. 이 튜토리얼에서는 Aspose.Words for Java를 사용해 Word, RTF, HTML, ODT 등 다양한 형식을 손쉽게 식별하고, **move files by format**을 통해 정리된 디렉터리로 이동하는 방법을 보여드립니다.

## Quick Answers
- **“detect document format java”는 무엇을 의미하나요?** Java 코드를 사용해 파일의 워드 프로세싱 형식(DOC, DOCX, RTF 등)을 프로그래밍 방식으로 식별하는 과정입니다.  
- **어떤 라이브러리가 이 기능을 제공하나요?** Aspose.Words for Java는 `FileFormatUtil.detectFileFormat` API를 제공합니다.  
- **암호화된 파일도 처리할 수 있나요?** 예 – `FileFormatInfo.isEncrypted()` 플래그를 통해 문서가 비밀번호로 보호되었는지 확인할 수 있습니다.  
- **프로덕션 사용에 라이선스가 필요하나요?** 평가용이 아닌 배포에는 상업용 Aspose.Words 라이선스가 필요합니다.  
- **감지 후 파일을 자동으로 이동할 수 있나요?** 물론입니다 – 감지 결과와 `FileUtils.copyFile`을 결합해 파일을 사용자 지정 폴더로 정렬할 수 있습니다.

## What is detect document format java?
`detect document format java`는 Java 코드를 사용해 파일의 바이너리 헤더를 검사하고 해당 파일이 어떤 워드 프로세싱 형식에 속하는지(DOC, DOCX, ODT 등) 판별하는 것을 의미합니다. Aspose.Words는 문서를 완전히 로드하지 않고 파일을 읽어 작업을 빠르고 메모리 효율적으로 수행합니다.

## Why move files by format?
문서를 원본 형식별로 정리하면 후속 처리 작업이 간편해집니다:

- **Batch conversions**: 모든 DOCX 파일이 하나의 폴더에 있으면 변환이 쉬워집니다.  
- **Legacy support**: 97 이전 Word 파일을 별도로 분리해 특수 처리를 할 수 있습니다.  
- **Security**: 암호화된 문서를 자동으로 격리할 수 있습니다.  

## Prerequisites

시작하기 전에 다음을 준비하세요:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (최신 버전 다운로드)  
- Java Development Kit (JDK) 8 이상 설치  
- Java I/O 및 스트림에 대한 기본 지식  

## Step 1: Set up directories for each format

먼저 감지된 파일이 이동될 깔끔한 폴더 구조를 만듭니다. 이렇게 하면 워크플로가 정돈되고 나중에 새로운 형식 카테고리를 추가하기도 쉽습니다.

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

> **Pro tip:** 절대 경로를 사용하거나 프로퍼티 파일을 통해 기본 디렉터리를 설정하면 프로덕션 코드에서 경로를 하드코딩하는 일을 피할 수 있습니다.

## Step 2: Detect the document format and move files

**detect document format java**의 핵심 로직은 아래 루프에 들어 있습니다. 모든 파일을 스캔하고 유형을 판단한 뒤, 해당 폴더로 복사합니다.

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

`switch` 블록은 필요에 따라 모든 형식을 커버하도록 확장할 수 있습니다. 각 케이스는 친절한 메시지를 출력하고 파일을 일치하는 폴더로 이동합니다.

## Complete source code for detecting document format java

아래는 디렉터리 설정과 감지 로직을 결합한 전체 실행 예제입니다. Java 클래스에 복사하고, 기본 경로를 조정한 뒤, 혼합 문서가 들어 있는 폴더에 대해 실행하세요.

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

## Common issues and troubleshooting

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | 파일이 손상되었거나 Word 형식이 아닌 경우. | 파일 확장자를 확인하거나, 샘플에 이미 포함된 *Unknown* 폴더로 이동하는 대체 로직을 추가하세요. |
| **Encrypted files throw an exception** | API가 암호화 여부를 확인하기 전에 내용을 읽으려 하기 때문. | 문서에 대한 다른 작업을 수행하기 전에 항상 `info.isEncrypted()`를 호출하세요. |
| **Directory creation fails on Linux** | 권한 부족 또는 상위 폴더가 없기 때문. | Java 프로세스에 쓰기 권한이 있는지, 기본 경로가 존재하는지 확인하세요. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: [here](https://releases.aspose.com/words/java/)에서 Aspose.Words for Java를 다운로드하고 제공된 설치 안내를 따르세요.

**Q: What document formats are supported for detection?**  
A: Aspose.Words는 DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, 그리고 97 이전 형식 등 다양한 포맷을 감지할 수 있습니다.

**Q: Can this code handle password‑protected documents?**  
A: 예. `FileFormatInfo.isEncrypted()` 플래그가 암호화된 파일을 식별하므로, 열지 않고도 안전한 폴더로 이동할 수 있습니다.

**Q: Is there a performance impact when scanning large folders?**  
A: 감지는 파일 헤더만 읽기 때문에 수천 개 파일도 빠르게 처리됩니다. 매우 큰 배치의 경우 병렬 스트림을 고려해 보세요.

**Q: How can I extend the script to convert unsupported formats?**  
A: 감지 후 `Document.save`를 사용해 원하는 출력 형식으로 저장하면 지원되는 모든 소스 타입을 변환할 수 있습니다.

## Conclusion

Aspose.Words와 함께 **detect document format java**를 사용하면 워드 관련 파일을 자동으로 정렬·격리·변환할 수 있는 신뢰성 높은 방법을 얻을 수 있습니다. 샘플 코드는 깔끔한 폴더 계층을 만들고, 각 파일 형식을 식별한 뒤, 해당 폴더로 이동하는 과정을 보여주어 시간 절약과 수작업 오류 감소에 크게 기여합니다.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}