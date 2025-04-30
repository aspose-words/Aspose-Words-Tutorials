---
"description": "Dowiedz się, jak przekonwertować DOCX na MHTML i wysyłać e-maile za pomocą Aspose.Words dla .NET w tym przewodniku krok po kroku. Zwiększ swoją produktywność dzięki łatwej automatyzacji."
"linktitle": "Konwertuj Docx na Mhtml i wysyłaj e-mailem"
"second_title": "Aspose.Words API przetwarzania dokumentów"
"title": "Konwertuj Docx na Mhtml i wysyłaj e-mailem"
"url": "/pl/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Konwertuj Docx na Mhtml i wysyłaj e-mailem

## Wstęp

dzisiejszej erze cyfrowej konwersja dokumentów z jednego formatu na inny i wysyłanie ich pocztą elektroniczną to powszechne zadanie. Ten artykuł przeprowadzi Cię przez proces konwersji pliku DOCX do formatu MHTML, a następnie wysłania go jako wiadomości e-mail przy użyciu Aspose.Words dla .NET. Podzielimy każdy krok na szczegółowe, łatwe do naśladowania przewodniki, zapewniając, że zrozumiesz proces od początku do końca. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że spełnione są następujące wymagania wstępne:

1. Aspose.Words dla .NET: Pobierz i zainstaluj bibliotekę Aspose.Words dla .NET z [Strona wydań Aspose](https://releases.aspose.com/words/net/).
2. Aspose.Email dla .NET: Pobierz i zainstaluj bibliotekę Aspose.Email dla .NET z [Strona wydań Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
4. Serwer SMTP: Aby wysyłać wiadomości e-mail, potrzebny jest dostęp do serwera SMTP.

## Importuj przestrzenie nazw

Aby użyć Aspose.Words i Aspose.Email w swoim projekcie, musisz zaimportować niezbędne przestrzenie nazw. Dodaj następujące dyrektywy using na górze pliku C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Podzielmy ten proces na kilka etapów, aby mieć pewność, że każdy z nich dobrze rozumiesz.

## Krok 1: Załaduj dokument DOCX

Najpierw musisz załadować dokument DOCX, który chcesz przekonwertować. Użyj `Document` klasa z Aspose.Words w celu załadowania pliku DOCX.

```csharp
// Ścieżka do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 2: Zapisz dokument jako MHTML

Następnie zapisz załadowany dokument jako plik MHTML. Można to zrobić za pomocą `Save` metoda `Document` klasa.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Przewiń strumień do początku, aby Aspose.Email mógł go odczytać.
stream.Position = 0;
```

## Krok 3: Utwórz wiadomość e-mail

Teraz utwórz wiadomość e-mail ze strumienia MHTML za pomocą Aspose.Email. Użyjesz `MailMessage` klasę w tym celu.

```csharp
// Utwórz wiadomość e-mail w formacie MIME Aspose.Email ze strumienia.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Krok 4: Wyślij e-mail

Na koniec wyślij wiadomość e-mail za pomocą klienta SMTP. Skonfiguruj klienta SMTP za pomocą danych serwera SMTP i użyj `Send` metoda wysłania wiadomości.

```csharp
// Wyślij wiadomość korzystając z Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować dokument DOCX na MHTML i wysłać go pocztą e-mail za pomocą Aspose.Words dla .NET. Proces ten obejmuje załadowanie dokumentu, przekonwertowanie go na MHTML, utworzenie wiadomości e-mail i wysłanie jej za pomocą klienta SMTP. Dzięki tym krokom możesz łatwo zautomatyzować konwersję i wysyłanie dokumentów pocztą e-mail w swoich aplikacjach.

## Najczęściej zadawane pytania

### Czy mogę użyć tej metody do konwersji innych formatów dokumentów?
Tak, Aspose.Words obsługuje różne formaty, dzięki czemu można konwertować dokumenty w formatach DOC, DOCX, RTF i innych do formatu MHTML.

### Jak mogę dodać załączniki do wiadomości e-mail?
Możesz użyć `Attachments` własność `MailMessage` klasa umożliwiająca dodawanie załączników do wiadomości e-mail.

### Czy Aspose.Words jest kompatybilny z .NET Core?
Tak, Aspose.Words jest kompatybilny z .NET Core. Można go używać również w aplikacjach .NET Core.

### Czy potrzebuję licencji na Aspose.Words i Aspose.Email?
Tak, obie biblioteki wymagają licencji. Możesz uzyskać tymczasową licencję od [Strona zakupu Aspose](https://purchase.aspose.com/temporary-license/) w celach ewaluacyjnych.

### Gdzie mogę znaleźć więcej dokumentacji?
Szczegółową dokumentację Aspose.Words można znaleźć [Tutaj](https://reference.aspose.com/words/net/) i dla Aspose.Email [Tutaj](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}