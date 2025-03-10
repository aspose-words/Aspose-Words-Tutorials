---
title: Chèn tài liệu vào Mail Merge
linktitle: Chèn tài liệu vào Mail Merge
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách chèn tài liệu vào trường trộn thư bằng Aspose.Words cho .NET trong hướng dẫn toàn diện, từng bước này.
weight: 10
url: /vi/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn tài liệu vào Mail Merge

## Giới thiệu

Chào mừng đến với thế giới tự động hóa tài liệu với Aspose.Words cho .NET! Bạn đã bao giờ tự hỏi làm thế nào để chèn tài liệu động vào các trường cụ thể trong một tài liệu chính trong quá trình trộn thư chưa? Vâng, bạn đã đến đúng nơi rồi. Hướng dẫn này sẽ hướng dẫn bạn từng bước trong quá trình chèn tài liệu tại các trường trộn thư bằng Aspose.Words cho .NET. Giống như việc ghép một câu đố, trong đó từng mảnh ghép đều khớp hoàn hảo với nhau. Vậy, hãy cùng bắt đầu nào!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

1.  Aspose.Words cho .NET: Bạn có thể[tải phiên bản mới nhất tại đây](https://releases.aspose.com/words/net/) . Nếu bạn cần mua giấy phép, bạn có thể làm như vậy[đây](https://purchase.aspose.com/buy) . Ngoài ra, bạn có thể nhận được một[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) hoặc thử nó với một[dùng thử miễn phí](https://releases.aspose.com/).
2. Môi trường phát triển: Visual Studio hoặc bất kỳ IDE C# nào khác.
3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn thực hiện hướng dẫn này dễ dàng.

## Nhập không gian tên

Trước tiên, bạn cần phải nhập các không gian tên cần thiết. Chúng giống như các khối xây dựng của dự án của bạn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Hãy chia nhỏ quy trình thành các bước dễ quản lý. Mỗi bước sẽ dựa trên bước trước đó, đưa bạn đến một giải pháp hoàn chỉnh.

## Bước 1: Thiết lập thư mục của bạn

Trước khi bạn có thể bắt đầu chèn tài liệu, bạn cần xác định đường dẫn đến thư mục tài liệu của mình. Đây là nơi lưu trữ tài liệu của bạn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tải tài liệu chính

Tiếp theo, bạn sẽ tải tài liệu chính. Tài liệu này chứa các trường hợp nhập nơi các tài liệu khác sẽ được chèn vào.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Bước 3: Thiết lập lệnh gọi lại hợp nhất trường

Để xử lý quá trình hợp nhất, bạn sẽ cần thiết lập một hàm gọi lại. Hàm này sẽ chịu trách nhiệm chèn tài liệu vào các trường hợp hợp nhất đã chỉ định.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Bước 4: Thực hiện trộn thư

Bây giờ là lúc thực hiện trộn thư. Đây là nơi phép thuật xảy ra. Bạn sẽ chỉ định trường trộn thư và tài liệu cần chèn vào trường này.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Bước 5: Lưu tài liệu

Sau khi quá trình trộn thư hoàn tất, bạn sẽ lưu tài liệu đã sửa đổi. Tài liệu mới này sẽ có nội dung được chèn vào đúng nơi bạn muốn.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Bước 6: Tạo Trình xử lý gọi lại

Trình xử lý gọi lại là một lớp thực hiện xử lý đặc biệt cho trường hợp hợp nhất. Nó tải tài liệu được chỉ định trong giá trị trường và chèn vào trường hợp hợp nhất hiện tại.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Bước 7: Chèn tài liệu

Phương pháp này chèn tài liệu được chỉ định vào đoạn văn hoặc ô bảng hiện tại.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Phần kết luận

Và bạn đã có nó! Bạn đã chèn thành công các tài liệu vào các trường cụ thể trong quá trình trộn thư bằng Aspose.Words cho .NET. Tính năng mạnh mẽ này có thể giúp bạn tiết kiệm rất nhiều thời gian và công sức, đặc biệt là khi xử lý khối lượng lớn tài liệu. Hãy nghĩ về nó như có một trợ lý cá nhân lo liệu mọi công việc nặng nhọc cho bạn. Vì vậy, hãy thử xem. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể chèn nhiều tài liệu vào các trường hợp nhập khác nhau không?
Có, bạn có thể. Chỉ cần chỉ định các trường hợp nhập thích hợp và các đường dẫn tài liệu tương ứng trong`MailMerge.Execute` phương pháp.

### Có thể định dạng tài liệu được chèn khác với tài liệu chính không?
 Chắc chắn rồi! Bạn có thể sử dụng`ImportFormatMode` tham số trong`NodeImporter` để kiểm soát định dạng.

### Nếu tên trường hợp nhập là động thì sao?
Bạn có thể xử lý tên trường hợp nhập động bằng cách truyền chúng dưới dạng tham số cho trình xử lý gọi lại.

### Tôi có thể sử dụng phương pháp này với các định dạng tệp khác không?
Có, Aspose.Words hỗ trợ nhiều định dạng tệp khác nhau bao gồm DOCX, PDF, v.v.

### Tôi phải xử lý lỗi như thế nào trong quá trình chèn tài liệu?
Triển khai xử lý lỗi trong trình xử lý gọi lại để quản lý mọi trường hợp ngoại lệ có thể xảy ra.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
