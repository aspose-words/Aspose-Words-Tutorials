---
title: Aspose.Words for .NET を使用して Word の折れ線グラフでセカンダリ X 軸をフォーマットし、表示単位を千単位に設定する
weight: 710
limit:
description: Aspose.Words for .NET を使用して Word の折れ線グラフを作成し、セカンダリ X 軸を追加、表示単位を千単位に設定し、カスタム数値書式を適用します。
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET を使用して Word の折れ線グラフを作成し、セカンダリ X 軸を追加、表示単位を千単位に設定し、カスタム数値書式を適用します。
  headline: Aspose.Words for .NET を使用して Word の折れ線グラフでセカンダリ X 軸をフォーマットし、表示単位を千単位に設定する
  type: TechArticle
- description: Aspose.Words for .NET を使用して Word の折れ線グラフを作成し、セカンダリ X 軸を追加、表示単位を千単位に設定し、カスタム数値書式を適用します。
  name: Aspose.Words for .NET を使用して Word の折れ線グラフでセカンダリ X 軸をフォーマットし、表示単位を千単位に設定する
  steps:
  - name: 新しい Document と DocumentBuilder を作成し、Word ファイルの作成を開始します。
    text: 新しい Document と DocumentBuilder を作成し、Word ファイルの作成を開始します。
  - name: サイズ 500×300 の折れ線グラフを文書に挿入し、Chart オブジェクトを取得します。
    text: サイズ 500×300 の折れ線グラフを文書に挿入し、Chart オブジェクトを取得します。
  - name: Aspose.Words が自動的に追加するデフォルトのデモシリーズを削除します。
    text: Aspose.Words が自動的に追加するデフォルトのデモシリーズを削除します。
  - name: X 軸に使用するカテゴリラベルの配列を定義します。
    text: X 軸に使用するカテゴリラベルの配列を定義します。
  - name: ラベルと値を使用して、"Main Data" という名前のプライマリ データシリーズを追加します。
    text: ラベルと値を使用して、"Main Data" という名前のプライマリ データシリーズを追加します。
  - name: Line タイプのセカンダリ シリーズ グループを作成し、セカンダリ 軸グループに割り当てます。
    text: Line タイプのセカンダリ シリーズ グループを作成し、セカンダリ 軸グループに割り当てます。
  - name: セカンダリ X 軸の表示単位を千単位に設定し、値が K で表示されるようにします。
    text: セカンダリ X 軸の表示単位を千単位に設定し、値が K で表示されるようにします。
  - name: カスタム数値書式 "#,##0.0" をセカンダリ X 軸の目盛ラベルに適用します。
    text: カスタム数値書式 "#,##0.0" をセカンダリ X 軸の目盛ラベルに適用します。
  - name: 必要に応じて、補助データシリーズをセカンダリ グループに追加します。
    text: 必要に応じて、補助データシリーズをセカンダリ グループに追加します。
  - name: 文書を .docx ファイルとして保存します。
    text: 文書を .docx ファイルとして保存します。
  type: HowTo
- questions:
  - answer: いいえ – `AxisX` の設定は `ChartSeriesGroup` に属するため、シリーズを追加する前でも後でも `secondaryGroup.AxisX.DisplayUnit.Unit`
      と `secondaryGroup.AxisX.NumberFormat.FormatCode` を設定できます。設定はどちらの場合でもグループの軸に適用されます。
    question: セカンダリ X 軸の表示単位と数値書式を設定する前に、セカンダリシリーズを追加する必要がありますか？
  - answer: はい – 任意の `AxisBuiltInUnit` 値を割り当てれば可能です。例えば `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` とすれば、軸の値が千単位ではなく百万単位で表示されます。
    question: セカンダリ X 軸に、千単位ではなく百万単位などの別の組み込み単位を使用できますか？
  - answer: いいえ – 書式コードは変更した軸（`secondaryGroup.AxisX.NumberFormat.FormatCode`）にのみ適用されるため、プライマリ
      X 軸はデフォルトの書式のままです。
    question: カスタム書式 "#,##0.0" はプライマリ X 軸のラベルに影響しますか？
  - answer: チャートには追加したシリーズに加えてデフォルトのデモシリーズも含まれ、余分な線やカテゴリの不一致が発生します。コレクションをクリアすれば、意図したデータだけが表示されます。
    question: '`lineChart.Series.Clear();` でデモシリーズのクリアを忘れるとどうなりますか？'
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: セカンダリ X 軸をフォーマットし、単位を千に設定する
og_description: Word の折れ線グラフにセカンダリ X 軸を追加し、カスタムパターンでラベルを千単位にフォーマットします。
og_image_alt: Aspose.Words for .NET を使用して、Word の折れ線グラフにセカンダリ X 軸を追加し、ラベルを千単位で表示するようにフォーマットする方法を示すガイド
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET を使用して Word の折れ線グラフでセカンダリ X 軸をフォーマットし、表示単位を千単位に設定する
このチュートリアルでは、折れ線グラフを含む Word 文書の作成、セカンダリ X 軸の追加、およびその軸を千単位で表示するように設定する手順を説明します。また、セカンダリ軸ラベルにカスタム数値書式を適用してデータの表示を細かく制御する方法も学べます。手順に従って、Word レポートのマルチ軸チャートの可読性を向上させましょう。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: セカンダリ X 軸の表示単位と数値書式を設定する前に、セカンダリシリーズを追加する必要がありますか？**  
A: いいえ – `AxisX` の設定は `ChartSeriesGroup` に属するため、シリーズを追加する前でも後でも `secondaryGroup.AxisX.DisplayUnit.Unit` と `secondaryGroup.AxisX.NumberFormat.FormatCode` を設定できます。設定はどちらの場合でもグループの軸に適用されます。

**Q: セカンダリ X 軸に、千単位ではなく百万単位などの別の組み込み単位を使用できますか？**  
A: はい – 任意の `AxisBuiltInUnit` 値を割り当てれば可能です。例えば `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` とすれば、軸の値が千単位ではなく百万単位で表示されます。

**Q: カスタム書式 "#,##0.0" はプライマリ X 軸のラベルに影響しますか？**  
A: いいえ – 書式コードは変更した軸（`secondaryGroup.AxisX.NumberFormat.FormatCode`）にのみ適用されるため、プライマリ X 軸はデフォルトの書式のままです。

**Q: `lineChart.Series.Clear();` でデモシリーズのクリアを忘れるとどうなりますか？**  
A: チャートには追加したシリーズに加えてデフォルトのデモシリーズも含まれ、余分な線やカテゴリの不一致が発生します。コレクションをクリアすれば、意図したデータだけが表示されます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}