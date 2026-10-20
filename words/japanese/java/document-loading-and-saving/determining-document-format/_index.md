---
date: 2026-02-22
description: Aspose.Words を使用して Java でドキュメント形式を検出し、形式別にファイルを自動的に移動する方法を学びましょう。DOC、DOCX
  などを識別します。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java を使用して Java でドキュメント形式を検出
url: /ja/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用した **detect document format java** の検出

バッチ処理で **detect document format java** が必要な場合、ファイルを自動的に正しいフォルダーに振り分けることで、手作業の時間を大幅に削減できます。このチュートリアルでは、Aspose.Words for Java を使って Word、RTF、HTML、ODT など多数の形式を簡単に判別し、**move files by format** で整理されたディレクトリに移動する方法を紹介します。

## Quick Answers
- **“detect document format java” とは何ですか？**  
  Java コードでファイルの Word 処理形式（DOC、DOCX、RTF など）をプログラム的に識別するプロセスです。  
- **どのライブラリがこの機能を提供しますか？**  
  Aspose.Words for Java が `FileFormatUtil.detectFileFormat` API を提供します。  
- **暗号化されたファイルも扱えますか？**  
  はい。`FileFormatInfo.isEncrypted()` フラグでパスワード保護されているかどうかを判定できます。  
- **本番環境で使用するにはライセンスが必要ですか？**  
  評価版以外でのデプロイには商用 Aspose.Words ライセンスが必要です。  
- **検出後に自動でファイルを移動できますか？**  
  もちろんです。検出結果と `FileUtils.copyFile` を組み合わせて、カスタムフォルダーへ自動振り分けできます。

## What is detect document format java?
`detect document format java` は、Java コードでファイルのバイナリヘッダーを調べ、どの Word 処理形式（例: DOC、DOCX、ODT）に属するかを判定することを指します。Aspose.Words はドキュメント全体をロードせずにファイルを読み取り、処理を高速かつメモリ効率良く行います。

## Why move files by format?
形式別にドキュメントを整理すると、下流の処理がシンプルになります。

- **バッチ変換** は、すべての DOCX ファイルが同一フォルダーにあるだけで容易に実行できます。  
- **レガシーサポート**：97 年以前の Word ファイルを特別扱いのために分離できます。  
- **セキュリティ**：暗号化された文書を自動的に隔離できます。  

## Prerequisites

開始する前に以下を用意してください。

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)（最新バージョンをダウンロード）  
- Java Development Kit (JDK) 8 以上がインストール済み  
- Java I/O とストリームに関する基本的な知識  

## Step 1: Set up directories for each format

まず、検出されたファイルを移動するためのクリーンなフォルダー構造を作成します。これによりワークフローが整理され、後から新しい形式カテゴリを追加しやすくなります。

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

> **Pro tip:** 絶対パスを使用するか、プロパティファイルでベースディレクトリを設定して、実装コードにハードコーディングしたパスを避けましょう。

## Step 2: Detect the document format and move files

**detect document format java** の核心は以下のループです。各ファイルを走査し、タイプを判定して適切なフォルダーへコピーします。

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

`switch` ブロックは、必要な形式すべてに拡張可能です。各ケースはフレンドリーなメッセージを出力し、該当フォルダーへファイルを移動します。

## Complete source code for detecting document format java

以下はディレクトリ設定と検出ロジックを組み合わせた、すぐに実行できる完全サンプルです。Java クラスに貼り付け、ベースパスを調整して、混在したドキュメントが格納されたフォルダーに対して実行してください。

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
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | ファイルが破損しているか、Word 形式以外のものです。 | ファイル拡張子を確認するか、サンプルにある *Unknown* フォルダーへ移動するフォールバック処理を追加してください。 |
| **Encrypted files throw an exception** | API が暗号化チェック前にコンテンツを読み取ろうとします。 | `info.isEncrypted()` を他の操作の前に必ず呼び出してください。 |
| **Directory creation fails on Linux** | 権限不足または親フォルダーが存在しません。 | Java プロセスに書き込み権限があること、ベースパスが存在することを確認してください。 |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: [here](https://releases.aspose.com/words/java/) から Aspose.Words for Java をダウンロードし、提供されているインストール手順に従ってください。

**Q: What document formats are supported for detection?**  
A: Aspose.Words は DOC、DOCX、DOT、DOTX、DOCM、DOTM、RTF、HTML、MHTML、ODT、OTT、FLAT_OPC、WORD_ML、そして 97 年以前のレガシーフォーマットなど、数多くの形式を検出できます。

**Q: Can this code handle password‑protected documents?**  
A: はい。`FileFormatInfo.isEncrypted()` フラグで暗号化ファイルを特定し、開かずに安全なフォルダーへ移動できます。

**Q: Is there a performance impact when scanning large folders?**  
A: 検出はファイルヘッダーのみを読み取るため、数千件のファイルでも高速に処理できます。非常に大規模なバッチの場合は、並列ストリームの活用を検討してください。

**Q: How can I extend the script to convert unsupported formats?**  
A: 検出後に `Document.save` を使用して、サポート対象の任意の出力形式へ変換できます。

## Conclusion

**detect document format java** を Aspose.Words と組み合わせて使用すれば、Word 系ファイルを自動で分類・隔離・変換する信頼性の高い手段が手に入ります。本サンプルコードは、クリーンなフォルダー階層を作成し、各ファイルの形式を判別して適切に移動する方法を示しており、作業時間の短縮と手動エラーの削減に貢献します。

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}