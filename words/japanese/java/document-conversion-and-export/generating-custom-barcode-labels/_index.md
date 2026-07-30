---
date: 2026-02-09
description: Aspose.Words for Java で Aspose Barcode Java を使用してカスタムバーコードラベルを生成します。Word
  文書にバーコードを埋め込む方法と、QR コードの Java サンプルの生成方法を学びましょう。
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Aspose Barcode Javaでカスタムバーコードラベルを生成する
url: /ja/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Barcode Javaでカスタムバーコードラベルを生成する

## Aspose.Words for Javaでカスタムバーコードラベルを生成する概要

バーコードは現代のアプリケーションに欠かせない要素で、**Aspose Barcode Java** を使用すれば、Word 文書内で直接簡単に作成できます。Word に **バーコードを埋め込む** 方法や、URL 用の QR コードを生成する方法、測定単位の変換まで、本チュートリアルで必要なすべてを解説します。さあ、始めましょう！

## よくある質問
- **Javaでバーコードを作成するライブラリはどれですか？** Aspose Barcode JavaとAspose.Words for Javaを組み合わせて使用​​します。
- **どのバーコードタイプがデモされていますか？** QRコード（JavaでQRコードを生成する）です。
- **twipsをピクセルに変換するにはどうすればよいですか？** 提供されているユーティリティメソッド`twipsToPixels`を使用します。
- **既存のWordファイルにバーコードを追加できますか？** はい、`DocumentBuilder.insertImage`メソッドを使用するだけです。
- **ライセンスは必要ですか？** 一時ライセンスを使用すると、評価版の制限が解除されます。

## Aspose Barcode Java とは？

Aspose Barcode Java は、開発者がプログラムから幅広い 1D および 2D バーコード（QR コードを含む）を生成できる強力な API です。Aspose.Words for Java と組み合わせることで、**バーコードを Word** 文書に **埋め込む** ことが、Java 環境を離れることなく実現できます。

## Aspose Barcode Java と Aspose.Words を組み合わせて使用するメリット
- **フルコントロール**：バーコードの色、サイズ、フォーマットを自由に設定可能。  
- **シームレス統合**：バーコード画像を直接 Word 文書に挿入できる。  
- **クロスプラットフォーム**：任意の Java 対応プラットフォームで動作。  
- **拡張性**：ユーティリティクラスを作成して、プロジェクト間でバーコードロジックを再利用できる。

## 前提条件

コードを書く前に、以下を準備してください。

- Java Development Kit (JDK)：バージョン 8 以上。  
- Aspose.Words for Java ライブラリ： [Download here](https://releases.aspose.com/words/java/)  
- Aspose.BarCode for Java ライブラリ： [Download here](https://releases.aspose.com/)  
- 統合開発環境 (IDE)：IntelliJ IDEA、Eclipse、またはお好みの IDE。  
- 一時ライセンス：制限のない利用のために [temporary license](https://purchase.aspose.com/temporary-license/) を取得。

## パッケージのインポート

Aspose.Words と Aspose.BarCode ライブラリを使用します。プロジェクトに以下のパッケージをインポートしてください。

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

これらのインポートにより、バーコード生成機能と Word 文書への統合が利用可能になります。

タスクを管理しやすいステップに分割していきましょう。

## 手順 1: バーコード操作用ユーティリティクラスの作成

バーコード関連の処理を簡素化するため、色変換や **twips からピクセルへの変換** などの共通タスクを提供するユーティリティクラスを作成します。

### コード

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**解説**

- `twipsToPixels` は Word が使用する測定単位 (twips) を画面ピクセルに変換します。正確なサイズ指定が必要なときに便利です。  
- `convertColor` は 16 進カラー文字列（例: “FF0000”）を Java の `Color` オブジェクトに変換し、バーコードの前景色・背景色をカスタマイズできます。

## 手順 2: カスタムバーコードジェネレータの実装

`IBarcodeGenerator` インターフェイスを実装し、Aspose.Words がバーコード フィールドに遭遇したときに画像を取得できるようにします。

### コード

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**解説**

- `getBarcodeImage` は、指定した **generate qr code java** タイプ（本例では QR）で `BarcodeGenerator` を構築します。  
- ユーティリティメソッドで前景色・背景色を設定し、生成した画像を返します。  
- バーコード生成に失敗した場合でもプログラムが継続できるよう、フォールバック画像を返します。

## 手順 3: バーコードを生成し Word 文書に追加する

ここまでの要素を組み合わせ、ドキュメントを作成し、バーコードを生成して **Word ファイルにバーコードを追加する** 方法を示します。

### コード

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**解説**

1. **Document の初期化** – 新規 `Document` を作成（既存の .docx をロードすることも可能）。  
2. **バーコードパラメータ** – タイプ (`QR`)、値、色を定義し、**generate qr code java** の使用例を示す。  
3. **画像挿入** – `builder.insertImage` で必要な位置にバーコードを配置し、**Word ファイルにバーコードを追加する** 方法を実演。  
4. **保存** – 完成した文書 (`CustomBarcodeLabels.docx`) には埋め込まれたバーコードが含まれ、印刷や配布が可能です。

## よくある問題と対策

| 問題 | 原因 | 解決策 |

|-------|-------|-----|
| バーコードが空白になる | 無効なカラー文字列またはサポートされていないバーコードタイプ | 16進数カラー形式を確認し、サポートされているタイプ（例：QR、Code128）を使用してください。 |
| 画像サイズが間違っている | ピクセル変換が正しくない | Wordのレイアウトに基づいて正確な寸法を計算するには、`twipsToPixels`を使用してください。 |
| ライセンス例外 | 有効なAsposeライセンスがありません | コードを実行する前に、一時ライセンスまたは購入済みのライセンスを適用してください。 |

## よくある質問

**Q: Aspose.Words for Javaはライセンスなしで使用できますか？** A: はい、使用できますが、評価版の機能制限が適用されます。すべての機能を使用するには、[一時ライセンス](https://purchase.aspose.com/temporary-license/) を取得してください。


**Q: どのような種類のバーコードを生成できますか？** A: Aspose.BarCodeは、QRコード、Code128、EAN-13など、多くの種類のバーコードをサポートしています。完全なリストについては、公式ドキュメント（https://reference.aspose.com/words/java/） をご覧ください。

**Q: バーコードのサイズを変更するにはどうすればよいですか？** 
A: `builder.insertImage` の幅/高さパラメータを調整するか、`BarcodeGenerator` オブジェクトの `XDimension` および `BarHeight` プロパティを変更してください。

**Q: バーコードの人間が読み取れる部分にカスタムフォントを使用できますか？** 
A: はい、可能です。`CodeTextParameters` プロパティを使用して、フォントファミリー、サイズ、スタイルを設定してください。

**Q: Aspose.Words に関するヘルプはどこで入手できますか？** 
A: コミュニティによるサポートや公式サポートについては、[サポートフォーラム](https://forum.aspose.com/c/words/8/) をご覧ください。

---

**Last Updated:** 2026-02-09  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}