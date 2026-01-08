---
date: 2025-12-10
description: Aspose.Words for Java を使用してカスタムバーコードラベルを生成する方法を学びましょう。このステップバイステップガイドでは、Word
  文書にバーコードを埋め込む方法を示します。
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでカスタムバーコードラベルを生成する
url: /ja/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Javaでカスタムバーコードラベルを生成する

## Aspose.Words for Javaでカスタムバーコードを生成する概要

バーコードは、在庫管理、チケット印刷、IDカード作成など、現代のアプリケーションに不可欠です。このチュートリアルでは、**カスタムバーコード**ラベルを生成し、`IBarcodeGenerator` インターフェイスを使用して Word 文書に直接埋め込みます。環境設定からバーコード画像の挿入まで、すべての手順を順に解説するので、すぐに Java プロジェクトでバーコードを使用できるようになります。

## クイック回答
- **このチュートリアルで学べることは何ですか？** Aspose.Words for Java を使用してカスタムバーコードラベルを生成し、Word ファイルに埋め込む方法。  
- **例で使用されているバーコードタイプは何ですか？** QR コード（任意のサポートされているタイプに置き換え可能）。  
- **ライセンスは必要ですか？** 開発中の無制限アクセスには一時ライセンスが必要です。  
- **必要な Java バージョンは何ですか？** JDK 8 以上。  
- **バーコードのサイズや色を変更できますか？** はい — `BarcodeParameters` と `BarcodeGenerator` の設定を変更してください。

## 前提条件

- Java Development Kit (JDK): バージョン 8 以上。  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/)。  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/)。  
- Integrated Development Environment (IDE): IntelliJ IDEA、Eclipse、またはお好みの IDE。  
- Temporary License: 無制限アクセスのために [temporary license](https://purchase.aspose.com/temporary-license/) を取得してください。

## パッケージのインポート

Aspose.Words と Aspose.BarCode ライブラリを使用します。プロジェクトに以下のパッケージをインポートしてください:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

これらのインポートにより、バーコード生成 API と Word ドキュメントクラスにアクセスできるようになります。

## Step 1: バーコード操作用ユーティリティクラスの作成

メインコードをすっきりさせるため、**twips からピクセルへの変換**や**16 進カラー変換**といった共通ヘルパーをユーティリティクラスにカプセル化します。

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

**説明**

- `twipsToPixels` – Word は寸法を **twips** で測ります。このメソッドはそれを画面ピクセルに変換し、バーコード画像のサイズを正確に指定する際に便利です。  
- `convertColor` – 16 進文字列（例: `"FF0000"` は赤）を `java.awt.Color` オブジェクトに変換し、**how to insert barcode** のように前景色と背景色をカスタマイズできます。

## Step 2: カスタムバーコードジェネレータの実装

次に `IBarcodeGenerator` インターフェイスを実装します。このクラスは Aspose.Words が埋め込める **generate qr code java** スタイルの画像を生成する役割を担います。

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

**説明**

- `getBarcodeImage` は `BarcodeGenerator` のインスタンスを作成し、`BarcodeParameters` で指定された色を適用して最終的に `BufferedImage` を返します。  
- メソッドはエラーが発生した場合にプレースホルダー画像を返すようにし、Word 文書の作成がクラッシュしないようにします。

## Step 3: バーコードを生成し、**Word にバーコードを埋め込む**

ジェネレータの準備ができたら、バーコード画像を生成し、**Word 文書に挿入**します。

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

**説明**

1. **Document Initialization** – 新しい `Document` を作成します（既存のテンプレートをロードしても構いません）。  
2. **Barcode Parameters** – バーコードタイプ (`QR`)、エンコードする値、前景色・背景色を定義します。  
3. **Image Insertion** – `builder.insertImage` が生成したバーコードを希望のサイズ（200 × 200 ピクセル）で配置します。これが **how to insert barcode** の核心です。  
4. **Saving** – 最終的な文書 `CustomBarcodeLabels.docx` には、印刷や配布にすぐ使える埋め込みバーコードが含まれます。

## なぜ Aspose.Words でカスタムバーコードラベルを生成するのか？

- **Full control** over barcode appearance (type, size, colors).  
- **Seamless integration** – 中間画像ファイルは不要です。バーコードはメモリ上で生成され、直接挿入されます。  
- **Cross‑platform** – Java をサポートする任意の OS で動作し、サーバーサイドの文書生成に最適です。  
- **Scalable** – データソースをループして、1 回の実行で数百枚のパーソナライズラベルを作成できます。

## よくある問題とトラブルシューティング

| 症状 | 考えられる原因 | 対策 |
|------|----------------|------|
| Barcode appears blank | `BarcodeParameters` の色が同じ（例: 黒 on 黒） | `foregroundColor` と `backgroundColor` の値を確認してください。 |
| Image is distorted | `insertImage` に渡したピクセル寸法が間違っている | 幅・高さの引数を調整するか、正確なサイズ指定のために `twipsToPixels` 変換を使用してください。 |
| Unsupported barcode type error | `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` が認識しないタイプを使用 | バーコードタイプ文字列がサポートされている `EncodeTypes`（例: `"QR"`、`"CODE128"`）のいずれかと一致していることを確認してください。 |

## よくある質問

**Q: Aspose.Words for Java をライセンスなしで使用できますか？**  
A: はい、可能ですがいくつかの制限があります。完全な機能を利用するには [temporary license](https://purchase.aspose.com/temporary-license/) を取得してください。

**Q: どのような種類のバーコードを生成できますか？**  
A: Aspose.BarCode は QR、Code 128、EAN‑13 など多数のフォーマットをサポートしています。完全な一覧は [documentation](https://reference.aspose.com/words/java/) をご確認ください。

**Q: バーコードのサイズはどう変更しますか？**  
A: `builder.insertImage` の幅・高さ引数を調整するか、Word の測定単位をピクセルに変換する `twipsToPixels` を使用してください。

**Q: バーコードテキストにカスタムフォントを使用できますか？**  
A: はい、`BarcodeGenerator` の `CodeTextParameters` プロパティでテキストフォントをカスタマイズできます。

**Q: 問題が発生した場合、どこでサポートを受けられますか？**  
A: Aspose コミュニティとエンジニアが参加する [support forum](https://forum.aspose.com/c/words/8/) で支援を受けられます。

## 結論

上記の手順に従うことで、Aspose.Words for Java を使用して **カスタムバーコード** 画像を生成し、**Word にバーコードを埋め込む** 方法が習得できました。この手法は在庫タグ、イベントチケット、またはバーコードを文書に組み込む必要があるあらゆるシナリオに柔軟に対応します。さまざまなバーコードタイプやスタイリングオプションを試して、ビジネス要件に最適な形に仕上げてください。

---

**Last Updated:** 2025-12-10  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}