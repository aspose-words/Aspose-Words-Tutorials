---
category: general
date: 2026-03-19
description: Aspose.Words for Java で警告を取得し、欠落フォントを検出する方法を学びます。このステップバイステップガイドでは、欠落フォントを上手に処理する方法も示しています。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: ja
og_description: Aspose.Words for Javaで警告を取得し、欠落フォントを検出し、欠落フォントを処理する完全なコード例。
og_title: 警告をキャプチャする方法 – Aspose.Wordsで欠落フォントを検出
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: 警告の取得方法 – Aspose.Wordsで欠落フォントを検出する
url: /ja/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 警告の取得方法 – Aspose.Words で欠落フォントを検出する

Word 文書を読み込む際に、一部のフォントがマシンに存在しない場合の **警告の取得方法** を疑問に思ったことはありませんか？ あなただけではありません。実際のプロジェクトでは、欠落フォントが原因でレイアウトが静かにずれることが多く、何が起きたかを知る唯一の方法は Aspose.Words が出す警告ストリームをリッスンすることです。

このチュートリアルでは、**欠落フォントを検出** する完全な実行可能サンプルを順に解説し、プログラムから **欠落フォントを検出する方法** を示すとともに、出力を予測可能に保つための **欠落フォントの処理** に関する簡単なヒントも提供します。

> **クイックノート:** このコードは Aspose.Words 23.9（以降）で動作し、Java 8 以上が必要です。

---

## 必要なもの

- **Aspose.Words for Java** (Maven/Gradle 依存関係またはクラスパス上の JAR)  
- システムにインストールされていないフォント（例: “Comic Sans MS”）を参照している Word ファイル（`input.docx`）  
- Java IDE またはシンプルな `javac`/`java` コマンドライン環境  

他のライブラリは不要です—すべて Aspose.Words パッケージ内に収められています。

---

## ステップ 1 – 警告を取得するための LoadOptions の設定  

警告のリッスンを開始するには、`LoadOptions` インスタンスを作成する必要があります。このオブジェクトは、欠落フォントなどの問題を追跡するようローダーに指示します。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**なぜ重要か:** `LoadOptions` がないと、ローダーは欠落フォントをデフォルトのシステムフォントに静かに置き換えてしまい、置換が行われたことに気付くことはありません。警告を有効にすることで、完全な可視性が得られます。

---

## ステップ 2 – LoadOptions を使用してドキュメントを読み込む  

実際にドキュメントを読み込みます。先ほど作成した `LoadOptions` をコンストラクタに渡すことで、解析中に生成された警告がすべて取得されます。

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**プロティップ:** バッチで多数のファイルを処理する場合、不要なオブジェクト生成を避けるために同じ `LoadOptions` インスタンスを再利用してください。

---

## ステップ 3 – 取得した警告を反復処理する  

Aspose.Words は各警告を `WarningInfo` オブジェクトとして保存します。フォント関連の警告だけに関心があるので、`FontSubstitutionWarningInfo` でフィルタリングします。

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**説明:**  
- `document.getWarnings()` は読み込み中に発生したすべての警告のリストを返します。  
- `FontSubstitutionWarningInfo` には、**要求されたフォント**（DOCX が求めたフォント）と、Aspose.Words がフォールバックした **実際のフォント** の 2 つの重要なデータが含まれます。  
- 両方を出力すれば、どのフォントが欠落していてどのように置換されたかを即座に把握できます。

---

## ステップ 4 – （オプション）欠落フォントをプログラムで処理する  

警告を取得するだけでは不十分です。フォントが欠落していることが分かったら、カスタム置換を提供したり、後でレビューできるように問題をログに記録したりして **欠落フォントを処理** したい場合があります。

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**なぜこれを行うのか:**  
- マシン間で一貫したレンダリングを保証します。  
- 後で生成される PDF や画像で予期しないレイアウト変更が起こるのを防ぎます。  

警告の詳細をデータベースに保存したり、コンテンツチームへメールで通知したり、重要なフォントが欠落している場合は処理自体を中止することも可能です。

---

## 完全な動作例  

以下は完成した実行可能プログラムです。`YOUR_DIRECTORY/input.docx` をテストファイルのパスに置き換え、Aspose.Words JAR をクラスパスに追加して実行してください。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**期待される出力**（“Comic Sans MS” が欠落している場合）:

```
Requested: Comic Sans MS → Substituted: Arial
```

オプションのフォールバックコードが実行された後、保存された `output.docx` は “Comic Sans MS” が参照されていた箇所すべてで **Arial** を使用してレンダリングされます。

---

## よくある質問とエッジケース  

| 質問 | 回答 |
|----------|--------|
| *文書に複数の欠落フォントがある場合はどうなりますか？* | ループはそれぞれのフォントについて警告を出します。`Map<String, String>` に収集してバッチ処理することができます。 |
| *文書から生成した PDF でも機能しますか？* | はい。フォント置換はロード段階で行われるため、後続のエクスポート（PDF、HTML、画像）では解決済みのフォントが使用されます。 |
| *警告を取得せずに抑制することはできますか？* | できます — `loadOptions.setWarningCallback(null);` と設定すれば警告は出ませんが、欠落フォントの可視性は失われます。 |
| *保存後に警告リストはクリアされますか？* | 警告コレクションは `Document` インスタンスに属しています。`document.save()` を呼び出した後もリストは変わりません（新しい `Document` を作成しない限り）。 |
| *DOCX に埋め込まれたカスタムフォントはどう扱われますか？* | 埋め込みフォントは利用可能とみなされます。ホストシステムにインストールされていなくても Aspose.Words はそれらを使用します。 |

---

## 本番環境でのプロティップス  

- **Cache FontSettings:** 数百ファイルを処理する場合、好みのフォールバックを設定した単一の `FontSettings` を作成し、再利用してオーバーヘッドを削減します。  
- **Log Structured Data:** 単なる `System.out` の代わりに警告を JSON ログに書き出すと、下流の分析（例: “最も欠落しているフォント”）が容易になります。  
- **Validate Early:** 重い処理を始める前に `LoadOptions` で軽い “ドライロード” を実行し、重要なフォントが欠落している場合は早期に中止します。  
- **Thread Safety:** `Document` オブジェクトはスレッドセーフではありません。各ファイルの処理は個別のスレッドで行うか、スレッドローカルな `LoadOptions` を使用してください。  

---

## 結論  

これで **Aspose.Words for Java で警告を取得する方法**、**欠落フォントを検出する方法**、そして **欠落フォントをクリーンなフォールバック戦略で処理する方法** が分かりました。`LoadOptions` と `document.getWarnings()` のイテレーションを活用すれば、フォント置換イベントを完全に把握でき、生成されたドキュメントがすべての環境で意図した通りに表示されることを保証できます。

次のステップに進みませんか？このパターンを拡張して **欠落画像の検出**、**未対応機能の追跡**、あるいは **欠落フォントの自動埋め込み** へと応用してみてください。同じ警告取得アプローチは他の多くの文書処理シナリオでも有効で、コードを堅牢かつ将来にわたって保守しやすくします。

コーディングを楽しんで、あなたの文書が常に美しくレンダリングされますように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}