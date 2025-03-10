---
title: ドキュメントの改訂の追跡とレビュー
linktitle: ドキュメントの改訂の追跡とレビュー
second_title: Aspose.Words Python ドキュメント管理 API
description: Aspose.Words for Python を使用してドキュメントの改訂を追跡および確認する方法を学びます。効率的なコラボレーションのためのソース コード付きのステップ バイ ステップ ガイド。今すぐドキュメント管理を強化しましょう。
weight: 23
url: /ja/python-net/document-structure-and-content-manipulation/document-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントの改訂の追跡とレビュー


ドキュメントの改訂と追跡は、共同作業環境の重要な側面です。Aspose.Words for Python は、ドキュメントの改訂の効率的な追跡とレビューを容易にする強力なツールを提供します。この包括的なガイドでは、Aspose.Words for Python を使用してこれを実現する方法を段階的に説明します。このチュートリアルの最後には、改訂追跡機能を Python アプリケーションに統合する方法をしっかりと理解できるようになります。

## ドキュメントの改訂の概要

ドキュメントの改訂には、ドキュメントに加えられた変更を時間の経過とともに追跡することが含まれます。これは、共同執筆、法的文書、規制遵守に不可欠です。Aspose.Words for Python は、ドキュメントの改訂をプログラムで管理するための包括的なツール セットを提供することで、このプロセスを簡素化します。

## Python 用 Aspose.Words の設定

始める前に、Aspose.Words for Pythonがインストールされていることを確認してください。ここからダウンロードできます。[ここ](https://releases.aspose.com/words/python/)インストールが完了したら、Python スクリプトに必要なモジュールをインポートして開始できます。

```python
import aspose.words as aw
```

## ドキュメントの読み込みと表示

ドキュメントを操作するには、まずドキュメントを Python アプリケーションに読み込む必要があります。次のコード スニペットを使用してドキュメントを読み込み、その内容を表示します。

```python
doc = aw.Document("document.docx")
print(doc.get_text())
```

## 変更履歴の有効化

ドキュメントの変更履歴を有効にするには、`TrackRevisions`財産に`True`:

```python
doc.track_revisions = True
```

## ドキュメントにリビジョンを追加する

ドキュメントに変更が加えられると、Aspose.Words はそれをリビジョンとして自動的に追跡します。たとえば、特定の単語を置き換えたい場合、変更を追跡しながら置き換えることができます。

```python
run = doc.get_child_nodes(aw.NodeType.RUN, True)[0]
run.text = "modified content"
```

## 修正内容の確認と承認

ドキュメント内のリビジョンを確認するには、リビジョン コレクションを反復処理して表示します。

```python
revisions = doc.revisions
for revision in revisions:
    print(f"Revision Type: {revision.revision_type}, Text: {revision.parent_node.get_text()}")
```

## 異なるバージョンの比較

Aspose.Words を使用すると、2 つのドキュメントを比較して、それらの違いを視覚化できます。

```python
doc1 = aw.Document("document_v1.docx")
doc2 = aw.Document("document_v2.docx")
comparison = doc1.compare(doc2, "John Doe", datetime.now())
comparison.save("comparison_result.docx")
```

## コメントと注釈の処理

共同作業者はドキュメントにコメントや注釈を追加できます。これらの要素はプログラムで管理できます。

```python
comment = aw.Comment(doc, "John Doe", datetime.now(), "This is a comment.")
paragraph = doc.get_child(aw.NodeType.PARAGRAPH, 0)
paragraph.insert_before(comment, paragraph.runs[0])
```

## リビジョンの外観のカスタマイズ

挿入されたテキストや削除されたテキストの色を変更するなど、ドキュメント内での変更履歴の表示方法をカスタマイズできます。

```python
doc.revision_options.inserted_text_color = aw.layout.RevisionColor.GREEN
doc.revision_options.deleted_text_color = aw.layout.RevisionColor.RED
```

## ドキュメントの保存と共有

修正内容を確認して承認したら、ドキュメントを保存します。

```python
doc.save("final_document.docx")
```

さらなるフィードバックを得るために、最終ドキュメントを共同作業者と共有します。

## 結論

Aspose.Words for Python は、ドキュメントの改訂と追跡を簡素化し、共同作業を強化してドキュメントの整合性を確保します。その強力な機能により、ドキュメントの変更の確認、承認、管理のプロセスを効率化できます。

## よくある質問

### Aspose.Words for Python をインストールするにはどうすればよいですか?

 Aspose.Words for Pythonは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/python/)インストール手順に従って、ご使用の環境に合わせてセットアップしてください。

### ドキュメントの特定の部分の変更履歴の追跡を無効にすることはできますか?

はい、プログラム的に調整することで、文書の特定のセクションの改訂履歴の追跡を選択的に無効にすることができます。`TrackRevisions`それらのセクションのプロパティ。

### 複数の貢献者による変更をマージすることは可能ですか?

もちろんです。Aspose.Words を使用すると、ドキュメントの異なるバージョンを比較し、変更をシームレスにマージできます。

### 異なる形式に変換するときに変更履歴は保持されますか?

はい、Aspose.Words を使用してドキュメントを別の形式に変換すると、変更履歴は保持されます。

### プログラムで修正を承認または拒否するにはどうすればよいですか?

Aspose.Words の API 関数を使用して、リビジョン コレクションを反復処理し、各リビジョンをプログラムで承認または拒否することができます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
