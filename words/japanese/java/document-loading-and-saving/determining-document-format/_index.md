---
date: 2025-12-20
description: Aspose.Words を使用して、Java でファイルをタイプ別に整理し、ドキュメント形式を検出する方法を学びましょう。DOC、DOCX、RTF
  などに対応しています。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用してファイルをタイプ別に整理する
url: /ja/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用したタイプ別ファイルの整理

Java アプリケーションで **タイプ別にファイルを整理** する必要がある場合、最初のステップは各ドキュメントの形式を確実に判別することです。Aspose.Words for Java を使用すれば、DOC、DOCX、RTF、HTML、ODT など多数の形式を検出でき、暗号化されたファイルや不明なファイルも対象にできます。本ガイドでは、フォルダーの設定、ファイル形式の検出、そして自動的なファイルの振り分け方法を解説します。

## クイック回答
- **“タイプ別にファイルを整理” とは何ですか？** 検出された形式（例: DOCX、PDF、RTF）に基づいてドキュメントを自動的にフォルダーへ移動することを指します。  
- **Java でファイル形式を検出するのに役立つライブラリはどれですか？** Aspose.Words for Java が `FileFormatUtil.detectFileFormat()` を提供します。  
- **API は不明なファイルタイプを識別できますか？** はい、サポートされていないまたは認識できないファイルには `LoadFormat.UNKNOWN` を返します。  
- **暗号化されたドキュメントの検出はサポートされていますか？** もちろんです。`FileFormatInfo.isEncrypted()` フラグでファイルがパスワード保護されているかどうかが分かります。  
- **本番環境で使用する際にライセンスは必要ですか？** 商用デプロイには有効な Aspose.Words ライセンスが必要です。

## はじめに: Aspose.Words for Java を使用したタイプ別ファイルの整理

Java でドキュメント処理を行う際、取り扱うファイルの形式を判別することは極めて重要です。Aspose.Words for Java は **detect file format java** の強力な機能を提供し、ファイルを効率的に整理する手順をご紹介します。

## 前提条件

開始する前に、以下の前提条件を満たしていることを確認してください。

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) がシステムにインストールされていること
- Java プログラミングの基本的な知識

## ステップ 1: ディレクトリの設定

まず、ファイルを効果的に整理するために必要なディレクトリを設定します。異なるドキュメントタイプ用のディレクトリを作成します。

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

サポート対象、未知、暗号化、そして pre‑97 ドキュメント用のディレクトリを作成しました。

## ステップ 2: ドキュメント形式の検出

次に、ディレクトリ内のドキュメント形式を検出します。Aspose.Words for Java を使用して実現します。

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

このスニペットではファイルを反復処理し、**detect file format java** を実行して、適切なフォルダーに整理します。

## Aspose.Words for Java におけるドキュメント形式判定の完全ソースコード

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

## File Format Java の検出方法

`FileFormatUtil.detectFileFormat()` メソッドはファイルヘッダーを解析し、`FileFormatInfo` オブジェクトを返します。このオブジェクトは **load format**、ファイルが暗号化されているかどうか、その他の有用なメタデータを提供します。この情報を使用して、プログラム上で **identify unknown file types** を行い、各ファイルの処理方法を決定できます。

## 不明なファイルタイプの識別

API が `LoadFormat.UNKNOWN` を返す場合、ファイルは破損しているか、Aspose.Words がサポートしていない形式です。サンプルコードでは、これらのファイルを **Unknown** フォルダーに移動し、後で確認できるようにしています。

## よくある問題と解決策

| 問題 | 原因 | 対策 |
|------|------|------|
| ファイルが常に *Supported* フォルダーに配置される | `FileFormatUtil` がヘッダーを読み取れなかった（例: ファイルが空） | 正しいファイルパスを渡しているか、ファイルがゼロバイトでないことを確認してください。 |
| 暗号化されたファイルで例外がスローされる | 暗号化処理を行わずに読み取ろうとした | コード例のように、さらに処理を行う前に `info.isEncrypted()` チェックを使用してください。 |
| Pre‑97 Word ドキュメントが検出されない | 古い形式は `DOC_PRE_WORD_60` ケースが必要 | `case LoadFormat.DOC_PRE_WORD_60` ブロックを保持し、*Pre97* フォルダーへルーティングしてください。 |

## よくある質問

### Aspose.Words for Java のインストール方法は？

Aspose.Words for Java は [here](https://releases.aspose.com/words/java/) からダウンロードでき、提供されているインストール手順に従ってください。

### サポートされているドキュメント形式は何ですか？

Aspose.Words for Java は DOC、DOCX、RTF、HTML、ODT など多数のドキュメント形式をサポートしています。完全な一覧は公式ドキュメントをご参照ください。

### Aspose.Words for Java を使用して暗号化されたドキュメントを検出するには？

`FileFormatUtil.detectFileFormat()` メソッドを使用します。返される `FileFormatInfo.isEncrypted()` フラグで暗号化の有無が分かります。本ガイドの例をご参照ください。

### 古いドキュメント形式を扱う際の制限はありますか？

MS Word 6 や Word 95 などの古い形式は最新機能が欠如していることがあり、互換性の問題が生じる可能性があります。可能であれば新しい形式に変換することを検討してください。

### Java アプリケーションでドキュメント形式の検出を自動化できますか？

はい、提供したコードをアプリケーションの処理パイプラインに組み込むことで、検出された形式に基づく自動的な振り分けと処理が可能になります。

---

**最終更新日:** 2025-12-20  
**テスト環境:** Aspose.Words for Java 24.12 (latest)  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}