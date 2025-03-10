---
title: Převod Docx na Mhtml a odesílání e-mailů
linktitle: Převod Docx na Mhtml a odesílání e-mailů
second_title: Aspose.Words API pro zpracování dokumentů
description: V tomto podrobném průvodci se dozvíte, jak převést DOCX na MHTML a posílat e-maily pomocí Aspose.Words for .NET. Zvyšte svou produktivitu pomocí snadné automatizace.
weight: 10
url: /cs/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Převod Docx na Mhtml a odesílání e-mailů

## Zavedení

dnešní digitální době je převod dokumentů z jednoho formátu do druhého a jejich odesílání e-mailem běžným úkolem. Tento článek vás provede procesem převodu souboru DOCX do formátu MHTML a jeho následného odeslání jako e-mailu pomocí Aspose.Words for .NET. Každý krok rozebereme v podrobném a snadno srozumitelném průvodci, který zajistí, že celý proces pochopíte od začátku do konce. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1.  Aspose.Words for .NET: Stáhněte si a nainstalujte knihovnu Aspose.Words for .NET z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2.  Aspose.Email for .NET: Stáhněte si a nainstalujte knihovnu Aspose.Email for .NET z[Aspose stránku vydání](https://releases.aspose.com/email/net/).
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
4. Server SMTP: K odesílání e-mailů potřebujete přístup k serveru SMTP.

## Importovat jmenné prostory

Chcete-li ve svém projektu používat Aspose.Words a Aspose.Email, musíte importovat potřebné jmenné prostory. Přidejte následující pomocí direktiv v horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Pojďme si tento proces rozdělit do několika kroků, abychom se ujistili, že každé části jasně porozumíte.

## Krok 1: Vložte dokument DOCX

 Nejprve musíte načíst dokument DOCX, který chcete převést. Použijte`Document` třídy z Aspose.Words k načtení souboru DOCX.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 2: Uložte dokument jako MHTML

 Dále uložte načtený dokument jako soubor MHTML. To se provádí pomocí`Save` metoda`Document` třída.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Přetočte stream na začátek, aby jej Aspose.Email mohl přečíst.
stream.Position = 0;
```

## Krok 3: Vytvořte e-mailovou zprávu

 Nyní vytvořte e-mailovou zprávu ze streamu MHTML pomocí Aspose.Email. Budete používat`MailMessage` třídy pro tento účel.

```csharp
// Vytvořte e-mailovou zprávu Aspose.Email MIME ze streamu.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Krok 4: Odešlete e-mail

 Nakonec odešlete e-mail pomocí klienta SMTP. Nakonfigurujte klienta SMTP pomocí podrobností o vašem serveru SMTP a použijte jej`Send` způsob odeslání zprávy.

```csharp
// Odešlete zprávu pomocí Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Závěr

Gratuluji! Úspěšně jste převedli dokument DOCX do MHTML a odeslali jej e-mailem pomocí Aspose.Words for .NET. Tento proces zahrnuje načtení dokumentu, jeho převod do MHTML, vytvoření e-mailové zprávy a její odeslání pomocí klienta SMTP. Pomocí těchto kroků můžete snadno automatizovat převod a zasílání dokumentů ve vašich aplikacích e-mailem.

## FAQ

### Mohu tuto metodu použít k převodu jiných formátů dokumentů?
Ano, Aspose.Words podporuje různé formáty a dokumenty jako DOC, DOCX, RTF a další můžete převádět do MHTML.

### Jak mohu k e-mailu přidat přílohy?
 Můžete použít`Attachments` vlastnictvím`MailMessage` třídy a přidejte přílohy k e-mailu.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words je kompatibilní s .NET Core. Můžete jej použít i v aplikacích .NET Core.

### Potřebuji licenci pro Aspose.Words a Aspose.Email?
 Ano, obě knihovny vyžadují licence. Dočasnou licenci můžete získat od[Aspose nákupní stránku](https://purchase.aspose.com/temporary-license/) pro účely hodnocení.

### Kde najdu další dokumentaci?
 Můžete najít podrobnou dokumentaci k Aspose.Words[zde](https://reference.aspose.com/words/net/) a pro Aspose.Email[zde](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
