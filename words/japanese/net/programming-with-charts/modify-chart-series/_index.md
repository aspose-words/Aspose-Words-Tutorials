---
title: Aspose.Words for .NET を使用して Word ドキュメントのチャートシリーズ データを更新する
weight: 610
limit:
description: Aspose.Words for .NET を使用して、Word ドキュメント内のチャートシリーズ データポイントを変更し、チャートを更新する方法を学びます。
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して、Word ドキュメント内のチャートシリーズ データポイントを変更し、チャートを更新する方法を学びます。
  headline: Aspose.Words for .NET を使用して Word ドキュメントのチャートシリーズ データを更新する
  type: TechArticle
- description: Aspose.Words for .NET を使用して、Word ドキュメント内のチャートシリーズ データポイントを変更し、チャートを更新する方法を学びます。
  name: Aspose.Words for .NET を使用して Word ドキュメントのチャートシリーズ データを更新する
  steps:
  - name: 新しい Document を作成し、DocumentBuilder で列グラフを挿入し、初期ファイルとして保存します。
    text: 新しい Document を作成し、DocumentBuilder で列グラフを挿入し、初期ファイルとして保存します。
  - name: 保存したファイルを開き、チャート シェイプを見つけて既存の Chart オブジェクトを取得します。
    text: 保存したファイルを開き、チャート シェイプを見つけて既存の Chart オブジェクトを取得します。
  - name: 最初のシリーズの値をクリアして新しいポイントを追加し、次に2番目のシリーズの最初のポイントを削除して新しいポイントを追加して調整します。
    text: 最初のシリーズの値をクリアして新しいポイントを追加し、次に2番目のシリーズの最初のポイントを削除して新しいポイントを追加して調整します。
  - name: 変更されたドキュメントを新しいファイルに保存し、更新されたチャートを含めます。
    text: 変更されたドキュメントを新しいファイルに保存し、更新されたチャートを含めます。
  type: HowTo
- questions:
  - answer: '`document.GetChildNodes(NodeType.Shape, true)` を使用してすべてのシェイプを取得し、`s.HasChart`
      でフィルタリングして最初のもの（または必要なもの）を選択します。これにより、無関係な画像やテキスト ボックスを選んでしまうことを防げます。'
    question: 他のシェイプが含まれる可能性のあるドキュメントで、チャート シェイプを確実に見つけるにはどうすればよいですか？
  - answer: '`ClearValues()` は既存のデータポイントを削除します。これを実行しないと新しいポイントが古いものに追加され、カテゴリが重複したり合計が正しくなくなったりします。'
    question: '`ClearValues()` を呼び出す前にシリーズに新しいポイントを追加する必要があるのはなぜですか？'
  - answer: 'チャートの X 軸カテゴリがテキスト（例: "Group A"）の場合は `FromString` を使用し、日付や測定値など数値を期待する場合は
      `FromDouble` を使用します。'
    question: X 軸の値に対して `ChartXValue.FromString` と `ChartXValue.FromDouble` のどちらを使用すべきかは、いつですか？
  - answer: 存在しないシリーズにアクセスしようとすると `ArgumentOutOfRangeException` がスローされます。特定のインデックスを参照する前に必ず
      `existingChart.Series.Count` を確認してください。
    question: チャートにシリーズが1つしかなく、`existingChart.Series[1]` にアクセスしようとするとどうなりますか？
  - answer: '`openedDoc` を保存すれば十分です。なぜなら、変更されたチャートを含むドキュメント インスタンスは `openedDoc` であり、元の
      `document` は初期ファイルを作成するためだけに使用されたからです。'
    question: チャートを変更した後、元の `document` を再保存する必要がありますか？それとも `openedDoc` を保存すれば十分ですか？
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Word でチャートシリーズ データを編集する
og_description: Aspose.Words for .NET を使用して、Word ファイル内のチャートシリーズの値を変更するステップバイステップ ガイドです。
og_image_alt: Aspose.Words for .NET を使用してシリーズ データを更新する前後の、列グラフを含む Word ドキュメントを示すガイドです。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word ドキュメントのチャートシリーズ データを更新する
このチュートリアルでは、列グラフを含む Word ドキュメントの作成方法、ファイルの再オープン、既存のチャートシリーズの取得、データポイントの変更、そしてチャートに新しい値が表示されるようにドキュメントを保存する手順を示します。ステップバイステップのコードに従って、Aspose.Words for .NET でプログラム的にチャート データを調整するのがいかに簡単かをご確認ください。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 他のシェイプが含まれる可能性のあるドキュメントで、チャート シェイプを確実に見つけるにはどうすればよいですか？**  
A: `document.GetChildNodes(NodeType.Shape, true)` を使用してすべてのシェイプを取得し、`s.HasChart` でフィルタリングして最初のもの（または必要なもの）を選択します。これにより、無関係な画像やテキスト ボックスを選んでしまうことを防げます。

**Q: `ClearValues()` を呼び出す前にシリーズに新しいポイントを追加する必要があるのはなぜですか？**  
A: `ClearValues()` は既存のデータポイントを削除します。これを実行しないと新しいポイントが古いものに追加され、カテゴリが重複したり合計が正しくなくなったりします。

**Q: X 軸の値に対して `ChartXValue.FromString` と `ChartXValue.FromDouble` のどちらを使用すべきかは、いつですか？**  
A: チャートの X 軸カテゴリがテキスト（例: "Group A"）の場合は `FromString` を使用し、日付や測定値など数値を期待する場合は `FromDouble` を使用します。

**Q: チャートにシリーズが1つしかなく、`existingChart.Series[1]` にアクセスしようとするとどうなりますか？**  
A: 存在しないシリーズにアクセスしようとすると `ArgumentOutOfRangeException` がスローされます。特定のインデックスを参照する前に必ず `existingChart.Series.Count` を確認してください。

**Q: チャートを変更した後、元の `document` を再保存する必要がありますか？それとも `openedDoc` を保存すれば十分ですか？**  
A: `openedDoc` を保存すれば十分です。なぜなら、変更されたチャートを含むドキュメント インスタンスは `openedDoc` であり、元の `document` は初期ファイルを作成するためだけに使用されたからです。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}