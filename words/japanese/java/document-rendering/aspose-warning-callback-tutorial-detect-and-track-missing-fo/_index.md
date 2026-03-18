---
category: general
date: 2026-03-17
description: 完全な実行可能サンプルを用いて、Java ドキュメントでフォントの欠落を検出し追跡するための Aspose 警告コールバックチュートリアルを学びましょう。
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: ja
og_description: Asposeの警告コールバックチュートリアルを習得し、Javaのワード処理ワークフローで欠落フォントを検出・追跡しましょう。
og_title: Aspose 警告コールバックチュートリアル – 欠落フォントの検出
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Aspose 警告コールバックチュートリアル – 欠落フォントの検出と追跡
url: /ja/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

original shortcodes.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – 欠損フォントの検出と追跡

Aspose.WordsでWordファイルを変換または編集する際に、**欠損フォントを検出**する方法を考えたことはありませんか？ あなたは一人ではありません。実際のプロジェクトでは、余計なフォントがレイアウトの乱れを引き起こすことがあり、後で問題になる前に**欠損フォントを追跡**する信頼できる方法が必要です。

良いニュースです。**aspose warning callback tutorial**は、フォント置換警告が発生したときに正確に出力するクリーンなプログラムフックを提供します。このガイドでは、コールバックの設定、ドキュメントの読み込み、警告の実際の表示までをJavaで順に解説します。

この記事の最後までに、欠損フォントを自動的に検出し、ログに記録し、置換フォントを埋め込むかソースファイルを調整するかを判断できるようになります。外部ツールは不要です。

## 前提条件

- **Java 8+**（コードは最新のJDKでコンパイル可能）
- **Aspose.Words for Java** バージョン 23.10以降 – Asposeポータルからダウンロードするか、Maven依存関係を追加してください。
- インストールされていないフォントを意図的に参照しているサンプルDOCX（例: Linux環境での “Comic Sans MS”）

以上です。追加のライブラリや複雑なビルド手順は不要です。

## Step 1: 警告コールバックの登録 – aspose warning callback tutorial のコア

チュートリアルで最初に教えるのは、警告リスナーをアタッチする方法です。Aspose.Wordsは検出した各問題について `WarningInfo` オブジェクトを発生させ、`WarningSource.FONT_SUBSTITUTION` フラグはフォントが置換される正確なタイミングを示します。

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Why this matters:** コールバックがなければ、Asposeは欠損フォントを黙って置換し、どの文字が崩れるか分かりません。警告をログに記録することで、**欠損フォントを早期に検出**し、正しいフォントを埋め込むかどうか判断できます。

> **Pro tip:** 後でレポートするために警告を収集する必要がある場合は、直接出力する代わりに `List<WarningInfo>` に保存してください。

## Step 2: ドキュメントの読み込み – 欠損フォントが潜む場所

ここで、マシンに存在しないフォントを参照している可能性のあるDOCXを読み込みます。読み込み時にフォントが欠損していれば、警告コールバックがトリガーされます。

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**What’s happening behind the scenes?** Asposeはドキュメントのスタイル定義を解析し、テキストの各ランを走査してシステムのフォントリポジトリをチェックします。完全一致が見つからない場合、代替フォントにフォールバックし、先ほど設定した警告を発生させます。

## Step 3: ドキュメントの保存 – 警告のフラッシュ

最後に、ドキュメントを保存します。保存処理でもフォントが再評価されるため、ロード時に出力されなかった警告もここで表示されます。

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

プログラムを実行すると、以下のようなコンソール出力が表示されます。

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

この出力により、**aspose warning callback tutorial** が機能し、**欠損フォントを検出**し、ログで**欠損フォントを追跡**できていることが確認できます。

## Wordドキュメントで欠損フォントを検出する方法 – 基本を超えて

コールバック方式は単発の実行には最適ですが、再利用可能なユーティリティが必要な場合もあります。以下は任意のプロジェクトに組み込める簡易ラッパーです。

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

以下のように呼び出します。

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

これで、CIパイプラインやUIに渡せるリストを返す、再利用可能な **detect missing fonts** メソッドが手に入ります。

## Aspose.Wordsで欠損フォントを追跡 – チーム向けレポート

大規模なチームでは、複数のドキュメントにわたるすべての欠損フォントのCSVレポートを作成したい場合があります。前述のユーティリティとシンプルなファイル反復処理を組み合わせます。

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

このスクリプトを実行すると、**track missing fonts** のCSVが生成され、開発者はドキュメントを本番にコミットする前に確認できます。

## よくある落とし穴と回避策

| 落とし穴 | 発生理由 | 対策 |
|---------|----------------|-----|
| **コールバックが発火しない** | ドキュメントをロードする前にコールバックを設定するのを忘れました。 | `Document.setWarningCallback` を `main` の最上部に配置してください。 |
| **最初の警告しか表示されない** | Asposeは `Document` インスタンスごとに警告をキャッシュします。 | 各ファイルごとに新しい `Document` オブジェクトを使用するか、実行間でコールバックをリセットしてください。 |
| **ログに誤ったフォント名が出る** | 説明文に余分なテキスト（“Font … not found”）が含まれています。 | CSV例のように正規表現で除去してください。 |
| **大量バッチでのパフォーマンス低下** | コールバックはすべてのテキストランで実行され、コストがかかります。 | チェックを事前検査ステップに限定し、検出だけが必要な場合は保存をスキップしてください。 |

## 期待結果と検証

1. **コンソール出力** – 欠損フォントごとに少なくとも1行の “Font substitution warning” が表示されるはずです。  
2. **CSVレポート** – バルクスクリプトが完了したら `missing-fonts-report.csv` を開き、各行にドキュメント名と正確な欠損フォントが記載されていることを確認してください。  
3. **保存されたドキュメント** – 出力されたDOCXは代替フォントでレンダリングされますが、見た目のレイアウトは元と異なる場合があります。

これらの手順のいずれかが期待通りに動作しない場合は、Aspose.WordsのJARがクラスパスに含まれているか、`input.docx` が本当にOSに存在しないフォントを参照しているかを再確認してください。

## 結論

これで **aspose warning callback tutorial** を完了し、Javaアプリケーションで **欠損フォントを検出**し **欠損フォントを追跡**する方法が分かりました。警告リスナーを登録し、ドキュメントを読み込み、必要に応じて結果をエクスポートすることで、プロダクションで問題が表面化する前にフォント関連の課題を完全に把握できます。

次に検討できること:

- `LoadOptions.setFontSubstitution` を使用して欠損フォントを直接埋め込む。
- `FontSettings` クラスを使用して欠損フォントを特定の代替フォントにマッピングする。
- CSVレポートをCI/CDパイプラインに統合し、未記載フォントが出現した際にビルドを失敗させる。

実際に試してみて、コールバックを自分のロギングフレームワークに合わせて調整すれば、ドキュメントワークフローが格段に堅牢になります。コーディングを楽しんでください！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}