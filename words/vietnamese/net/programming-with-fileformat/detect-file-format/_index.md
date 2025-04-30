---
"description": "Tìm hiểu cách phát hiện định dạng tệp tài liệu bằng Aspose.Words cho .NET với hướng dẫn toàn diện, từng bước này."
"linktitle": "Phát hiện định dạng tệp tài liệu"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Phát hiện định dạng tệp tài liệu"
"url": "/vi/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Phát hiện định dạng tệp tài liệu

## Giới thiệu

Trong thế giới kỹ thuật số ngày nay, việc quản lý các định dạng tài liệu khác nhau một cách hiệu quả là rất quan trọng. Cho dù bạn đang xử lý Word, PDF, HTML hay các định dạng khác, việc có thể phát hiện và xử lý các tệp này một cách chính xác có thể giúp bạn tiết kiệm rất nhiều thời gian và công sức. Trong hướng dẫn này, chúng ta sẽ khám phá cách phát hiện các định dạng tệp tài liệu bằng Aspose.Words cho .NET. Hướng dẫn này sẽ hướng dẫn bạn mọi thứ bạn cần biết, từ các điều kiện tiên quyết đến hướng dẫn từng bước chi tiết.

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

- Aspose.Words cho .NET: Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/). Hãy đảm bảo bạn có giấy phép hợp lệ. Nếu không, bạn có thể xin cấp [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Bất kỳ phiên bản nào gần đây đều hoạt động tốt.
- .NET Framework: Đảm bảo bạn đã cài đặt đúng phiên bản.

## Nhập không gian tên

Để bắt đầu, bạn sẽ cần nhập các không gian tên cần thiết vào dự án của mình:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Chúng ta hãy chia nhỏ ví dụ thành nhiều bước để dễ hiểu hơn.

## Bước 1: Thiết lập thư mục

Đầu tiên, chúng ta cần thiết lập các thư mục nơi các tập tin sẽ được sắp xếp dựa trên định dạng của chúng.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Tạo thư mục nếu chúng chưa tồn tại.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Bước 2: Lấy danh sách các tập tin

Tiếp theo, chúng ta sẽ nhận được danh sách các tập tin từ thư mục, loại trừ bất kỳ tài liệu nào bị hỏng.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Bước 3: Phát hiện định dạng tệp

Bây giờ, chúng ta lặp lại từng tệp và phát hiện định dạng của tệp đó bằng Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Hiển thị loại tài liệu
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Phần kết luận

Phát hiện định dạng tệp tài liệu bằng Aspose.Words cho .NET là một quá trình đơn giản. Bằng cách thiết lập thư mục, lấy danh sách tệp và sử dụng Aspose.Words để phát hiện định dạng tệp, bạn có thể sắp xếp và quản lý tài liệu của mình một cách hiệu quả. Cách tiếp cận này không chỉ tiết kiệm thời gian mà còn đảm bảo rằng bạn xử lý đúng nhiều định dạng tài liệu khác nhau.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ để làm việc với các tài liệu Word theo chương trình. Nó cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi tài liệu ở nhiều định dạng khác nhau.

### Aspose.Words có thể phát hiện tài liệu được mã hóa không?
Có, Aspose.Words có thể phát hiện xem tài liệu có được mã hóa hay không và bạn có thể xử lý các tài liệu đó cho phù hợp.

### Aspose.Words có thể phát hiện những định dạng nào?
Aspose.Words có thể phát hiện nhiều định dạng khác nhau bao gồm DOC, DOCX, RTF, HTML, MHTML, ODT và nhiều định dạng khác nữa.

### Làm thế nào tôi có thể nhận được giấy phép tạm thời cho Aspose.Words?
Bạn có thể nhận được giấy phép tạm thời từ [Mua Aspose](https://purchase.aspose.com/temporary-license/) trang.

### Tôi có thể tìm tài liệu về Aspose.Words ở đâu?
Tài liệu về Aspose.Words có thể được tìm thấy [đây](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}