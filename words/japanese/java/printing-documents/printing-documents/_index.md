---
"description": "Aspose.Words for Javaを使用してドキュメントを印刷する方法を学びましょう。Javaアプリケーションでシームレスに印刷するためのステップバイステップガイドです。"
"linktitle": "文書の印刷"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でドキュメントを印刷する"
"url": "/ja/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントを印刷する


Aspose.Words for Java を使ってドキュメントを印刷したいとお考えなら、ここが最適な場所です。このステップバイステップガイドでは、提供されているソースコードを使って、Aspose.Words for Java でドキュメントを印刷する手順を詳しく説明します。

## 導入

文書の印刷は多くのアプリケーションで一般的なタスクです。Aspose.Words for Javaは、Word文書の印刷機能を含む、Word文書を操作するための強力なAPIを提供します。このチュートリアルでは、Word文書の印刷手順をステップバイステップで解説します。

## 環境の設定

コードに進む前に、次の前提条件が満たされていることを確認してください。

- Java開発キット（JDK）がインストールされている
- Aspose.Words for Java ライブラリがダウンロードされ、プロジェクトに追加されました

## ドキュメントの読み込み

まず、印刷したいWord文書を読み込む必要があります。 `"Your Document Directory"` ドキュメントへのパスと `"Your Output Directory"` 希望する出力ディレクトリを指定します。

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 印刷ジョブの作成

次に、読み込んだドキュメントを印刷するための印刷ジョブを作成します。以下のコードスニペットは、印刷ジョブを初期化し、必要なプリンター設定を設定します。

```java
// ドキュメントを印刷するための印刷ジョブを作成します。
PrinterJob pj = PrinterJob.getPrinterJob();
// ドキュメント内のページ数で属性セットを初期化します。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// プリンターの設定を他のパラメーターとともに印刷ドキュメントに渡します。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## 文書の印刷

印刷ジョブの設定が完了したら、ドキュメントを印刷します。以下のコードスニペットは、ドキュメントと印刷ジョブを関連付け、印刷プロセスを開始します。

```java
// 印刷ジョブを使用して印刷するドキュメントを渡します。
pj.setPrintable(awPrintDoc);
pj.print();
```
## 完全なソースコード
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// ドキュメントを印刷するための印刷ジョブを作成します。
PrinterJob pj = PrinterJob.getPrinterJob();
// ドキュメント内のページ数で属性セットを初期化します。
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// プリンターの設定を他のパラメーターとともに印刷ドキュメントに渡します。
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// 印刷ジョブを使用して印刷するドキュメントを渡します。
pj.setPrintable(awPrintDoc);
pj.print();
```
MultipagePrintDocument のソースコード
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <要約>
    /// カスタム PrintDocument クラスのコンストラクター。
    /// </サマリー> 
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        // 属性セットで定義されたページの開始インデックスと終了インデックス。
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // 次にレンダリングされるページインデックスを計算します。
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // ページインデックスがページ範囲全体より大きい場合は何も起こりません
        // レンダリングするものがさらにあります。
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // 各サムネイル プレースホルダーのサイズをポイント単位で計算します。
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // この紙に印刷される最初のページ番号を計算します。
        int startPage = pagesOnCurrentSheet + fromPage;
        // この用紙に印刷する最後のページ番号を選択します。
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // 保存された現在のページから計算されたページまで選択したページをループします
        // 最後のページ。
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // 列と行のインデックスを計算します。
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // サムネイルの位置をワールド座標 (この場合はポイント) で定義します。
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // 左と上の開始位置を計算します。
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // 計算された座標を使用してドキュメントページをグラフィックスオブジェクトにレンダリングします
                // およびサムネイル プレースホルダーのサイズ。
                // 便利な戻り値は、ページがレンダリングされたスケールです。
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // ページの境界線を描画します（ページのサムネイルはサムネイルより小さくなる場合があります）
                // プレースホルダーのサイズ)。
                if (mPrintPageBorders) {
                    // ページの実際の 100% サイズをポイント単位で取得します。
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // 既知のスケール係数を使用して、拡大縮小されたページの周囲に境界線を描画します。
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // サムネイル プレースホルダーの周囲に境界線を描画します。
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // レンダリング中にエラーが発生した場合は何も行いません。
                // レンダリング中にエラーが発生した場合、空白のページが描画されます。
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // シート上の列と行の数を定義します。
        // 横長の用紙です。
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // 用紙が縦向きの場合は、幅と高さを入れ替えます。
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## 結論

おめでとうございます！Aspose.Words for Java を使用して Word 文書を印刷できました。このステップバイステップガイドは、ドキュメント印刷機能を Java アプリケーションにシームレスに統合するのに役立ちます。

## よくある質問

### Q1: Aspose.Words for Java を使用してドキュメントの特定のページを印刷できますか?

はい、文書を印刷する際にページ範囲を指定できます。コード例では、 `attributes.add(new PageRanges(1, doc.getPageCount()))` すべてのページを印刷します。必要に応じてページ範囲を調整できます。

### Q2: Aspose.Words for Java はバッチ印刷に適していますか?

はい、もちろんです！Aspose.Words for Javaはバッチ印刷タスクに最適です。ドキュメントのリストを反復処理し、同様のコードを使用して1つずつ印刷できます。

### Q3: 印刷エラーや例外をどのように処理すればよいですか?

印刷プロセス中に発生する可能性のある例外をすべて処理する必要があります。例外処理の詳細については、Aspose.Words for Java のドキュメントをご覧ください。

### Q4: 印刷設定をさらにカスタマイズできますか?

はい、特定の要件に合わせて印刷設定をカスタマイズできます。利用可能な印刷オプションの詳細については、Aspose.Words for Java のドキュメントをご覧ください。

### Q5: Aspose.Words for Java に関する詳細なヘルプやサポートはどこで受けられますか?

追加のサポートと支援については、 [Aspose.Words for Java フォーラム](https://forum。aspose.com/).

---

Aspose.Words for Java を使ってドキュメントを印刷する方法を習得しました。この機能を Java アプリケーションに実装してみましょう。コーディングを楽しみましょう！


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}