---
date: '2026-01-14'
description: Aspose.Words Java でページ番号の再設定方法を学び、LayoutCollector を使用してページネーションデータを抽出し、ページレイアウトを更新し、ページを画像としてレンダリングします。
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Aspose.Words Javaでページ番号の再開始 – LayoutCollector と LayoutEnumerator
url: /ja/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Javaでページ番号の再開 – LayoutCollector & LayoutEnumerator

## はじめに

大規模な Java ベースのドキュメントで **ページ番号の再開** に苦労しながら、ページネーションの分析やページを画像としてレンダリングする必要がありますか？ **Aspose.Words for Java** を使用すれば、`LayoutCollector` と `LayoutEnumerator` を活用して、ページ番号の再開だけでなく **ページネーションデータの抽出**、**ページレイアウトの更新**、**画像としてページをレンダリング**（プレビューや PDF 用）も行えます。このガイドでは、ライブラリの設定からコールバックの実装まで、ドキュメントのレンダリングを完全に制御する手順をすべて解説します。

**学べること**
- `LayoutCollector` を使用してページネーションデータを抽出し、ページスパンを判定する方法。
- `LayoutEnumerator` でドキュメントレイアウトを走査する方法。
- ページレイアウトコールバックを実装して **ページを画像としてレンダリング** する方法。
- レイアウトオプションを使用して連続セクションで **ページ番号を再開** する方法。
- **ページレイアウトを効率的に更新** するためのヒント。

## クイック回答

- **Java ドキュメントでページ番号を再開するには？** `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` を使用し、`doc.updatePageLayout()` を呼び出します。
- **ページネーションデータを抽出するクラスは？** 任意のノードの開始/終了ページインデックスを提供するのは `LayoutCollector` です。
- **各ページを画像としてレンダリングできますか？** はい。`IPageLayoutCallback` を実装し、`ImageSaveOptions` を使用します。
- **ページレイアウトの更新は手動で呼び出す必要がありますか？** レイアウトオプションを変更した後は、必ず `doc.updatePageLayout()` を呼び出してください。
- **必要な Aspose.Words のバージョンは？** 例は Aspose.Words for Java 25.3（以降）で動作します。

## ページ番号の再開とは？

ページ番号の再開は、ドキュメントの特定セクションで新しい番号付けシーケンスを開始できる機能で、章や付録ごとに別々の番号付けが必要なレポート、書籍、契約書などで重要です。Aspose.Words は、手動で改ページを挿入するようなトリックなしでこの動作を制御できるレイアウトオプションを提供します。

## なぜ LayoutCollector と LayoutEnumerator を使用するのか？

- **LayoutCollector** はページネーションの詳細にプログラムからアクセスでき、任意のノードの最初と最後のページなど **ページネーションデータの抽出** を可能にします。
- **LayoutEnumerator** はビジュアルレイアウトツリーを歩くことができ、カスタムレンダリングや分析のためにページ、段落、行を簡単に特定できます。
- これらを組み合わせることで、従来は高コストな PDF 変換や手動計算が必要だった複雑なレイアウト作業を簡素化します。

## 前提条件

### 必要なライブラリとバージョン

Aspose.Words for Java バージョン 25.3（以降）がインストールされていることを確認してください。

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 環境設定要件

- Java Development Kit (JDK) がインストールされていること。
- IntelliJ IDEA、Eclipse、または任意の Java IDE が使用できること。
- 有効な Aspose.Words ライセンス（評価用の無料トライアルでも可）。

### 知識の前提条件

基本的な Java プログラミングの知識があれば十分です。

## Aspose.Words の設定

まず、プロジェクトに Aspose.Words ライブラリを統合します。無料トライアルライセンスは [here](https://releases.aspose.com/words/java/) から取得でき、テスト用に一時ライセンスを使用することも可能です。

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

ライブラリの準備ができたら、コア機能に進みます。

## 実装ガイド

### 機能 1: LayoutCollector を使用したページスパン分析

`LayoutCollector` 機能を使用すると、ノードがページにまたがる方法を判定でき、これは **ページネーションデータの抽出** の基礎となります。

#### 概要

`LayoutCollector` を活用することで、任意のノードの開始ページインデックスと終了ページインデックスを取得し、占有する総ページ数を計算できます。

#### 実装手順

**1. Initialize Document and LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Populate the Document**
Here, we'll add content that spans multiple pages:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Update Layout and Retrieve Metrics**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### 解説

- **`DocumentBuilder`** はテキストとページ/セクション区切りを挿入します。
- **`updatePageLayout()`** はレイアウト情報を再計算し、ページネーションデータを正確にします。

### 機能 2: LayoutEnumerator を使用した走査

`LayoutEnumerator` はビジュアルレイアウトツリーを効率的にナビゲートできます。

#### 概要

ページ、段落、行、その他のレイアウトエンティティを歩くことができ、カスタムレンダリングや診断に役立ちます。

#### 実装手順

**1. Initialize Document and LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Traversing Forward and Backward**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### 解説

- **`moveParent()`** は列挙子を親エンティティ（この場合はページレベル）に移動させます。
- 再帰的な走査メソッドにより、レイアウト階層全体を探索できます。

### 機能 3: ページレイアウトコールバック

レイアウトイベントを監視し、必要に応じて **ページを画像としてレンダリング** するコールバックを実装します。

#### 概要

`IPageLayoutCallback` インターフェイスは、ドキュメントの一部が再フローを完了したときや変換が完了したときに通知します。

#### 実装手順

**1. Set Callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Implement Callback Methods**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### 解説

- **`notify()`** はレイアウトイベントに反応します。
- **`ImageSaveOptions`** と `PageSet` を組み合わせることで、**ページを画像としてレンダリング**（この例では PNG）できます。

### 機能 4: 連続セクションでのページ番号再開

複数のセクションが連続して流れる場合のページ番号を制御します。

#### 概要

`ContinuousSectionRestart` オプションを設定することで、ページ番号を新しいページで再開するか、シームレスに継続するかを決定できます。

#### 実装手順

**1. Load Document**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Configure Page Numbering Options**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### 解説

- **`setContinuousSectionPageNumberingRestart()`** は、連続セクションでの番号付け方法を Aspose.Words に指示します。
- オプションを変更した後、**ページレイアウトを更新** して変更を適用します。

## 実用的な応用例

1. **ドキュメントのページネーション分析** – `LayoutCollector` を使用して、コンテンツがページにどのように広がっているかを監査し、余白や改ページを調整します。
2. **PDF レンダリング** – `LayoutEnumerator` とコールバックを組み合わせ、PDF 変換前に高精細なページ画像を生成します。
3. **動的ドキュメント更新** – レイアウトイベント（例: テーブルが拡張された後）に応答し、影響を受けたページを自動的に再レンダリングします。
4. **マルチセクションレポート** – **ページ番号の再開** を適用して、各章に独自の番号付けスキームを持たせつつ、連続したフローを維持します。

## パフォーマンス上の考慮点

- `updatePageLayout()` を呼び出す前に未使用のセクションや非表示コンテンツを削除して、処理を高速化します。
- 大規模ドキュメントにはストリーミング API を使用し、ファイル全体をメモリに読み込むのを回避します。
- ページレベルの情報だけが必要な場合は、`LayoutEnumerator` の再帰走査の深さを制限します。

## よくある問題と解決策

| 問題 | 原因 | 対策 |
|-------|-------|-----|
| `layoutCollector.getNumPagesSpanned()` returns 0 | Layout not updated | Call `doc.updatePageLayout()` before querying |
| Images not generated in callback | Missing `ImageSaveOptions` configuration | Ensure `saveOptions.setPageSet(new PageSet(pageIndex))` is set |
| Page numbers don’t restart | Wrong `ContinuousSectionRestart` value | Use `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` for true restart |

## よくある質問

**Q: 特定の段落の正確なページ番号を抽出できますか？**  
A: はい。`LayoutCollector` を使用して段落ノードの開始ページを取得し、`doc.updatePageLayout()` を呼び出してデータが最新であることを確認します。

**Q: `update page layout` はドキュメントの内容に影響しますか？**  
A: いいえ。レイアウト情報を再計算するだけで、実際のテキストや書式設定は変更されません。

**Q: 大規模ドキュメントのすべてのページを効率的に画像としてレンダリングするには？**  
A: `IPageLayoutCallback` を実装し、各ページを順次処理します。I/O バウンドの保存にはマルチスレッドを使用することも検討してください。

**Q: 特定のセクションだけで番号付けを再開できますか？**  
A: はい。`updatePageLayout()` を呼び出す前に、対象セクションのレイアウトオプションに `setContinuousSectionPageNumberingRestart` を適用します。

**Q: `LayoutCollector` はどのバージョンの Aspose.Words で導入されましたか？**  
A: `LayoutCollector` は 2020 年初期のリリースから利用可能で、例はバージョン 25.3 を使用しています。

## 結論

**ページ番号の再開**、`LayoutCollector`、`LayoutEnumerator` をマスターすることで、Aspose.Words for Java における高度なテキスト処理のための強力なツールキットが手に入ります。**ページネーションデータの抽出**、**ページを画像としてレンダリング**、またはセクション間のページ番号制御が必要な場合でも、これらの API は高精度かつプログラム的な制御を提供し、パフォーマンスを高く保ちます。

---

**最終更新日:** 2026-01-14  
**テスト環境:** Aspose.Words for Java 25.3  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}