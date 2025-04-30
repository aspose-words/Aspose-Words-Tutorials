---
"description": "Naučte se v tomto podrobném návodu, jak převést DOCX do MHTML a odesílat e-maily pomocí Aspose.Words pro .NET. Zvyšte svou produktivitu pomocí snadné automatizace."
"linktitle": "Převod Docx do Mhtml a odesílání e-mailů"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Převod Docx do Mhtml a odesílání e-mailů"
"url": "/cs/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Převod Docx do Mhtml a odesílání e-mailů

## Zavedení

dnešní digitální době je převod dokumentů z jednoho formátu do druhého a jejich odesílání e-mailem běžným úkolem. Tento článek vás provede procesem převodu souboru DOCX do formátu MHTML a jeho následným odesláním e-mailem pomocí Aspose.Words pro .NET. Každý krok rozebereme v podrobném a srozumitelném návodu, abyste celému procesu porozuměli od začátku do konce. Pojďme se na to pustit!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Aspose.Words pro .NET: Stáhněte a nainstalujte knihovnu Aspose.Words pro .NET z [Stránka s vydáním Aspose](https://releases.aspose.com/words/net/).
2. Aspose.Email pro .NET: Stáhněte a nainstalujte knihovnu Aspose.Email pro .NET z [Stránka s vydáním Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
4. SMTP server: Pro odesílání e-mailů potřebujete přístup k SMTP serveru.

## Importovat jmenné prostory

Chcete-li ve svém projektu použít Aspose.Words a Aspose.Email, je třeba importovat potřebné jmenné prostory. Na začátek souboru C# přidejte následující direktivy using:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Rozdělme si proces do několika kroků, abyste každé části jasně porozuměli.

## Krok 1: Načtěte dokument DOCX

Nejprve je třeba načíst dokument DOCX, který chcete převést. Použijte `Document` třída z Aspose.Words pro načtení souboru DOCX.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 2: Uložte dokument jako MHTML

Dále uložte načtený dokument jako soubor MHTML. To se provádí pomocí `Save` metoda `Document` třída.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Přetočte stream na začátek, aby si ho Aspose.Email mohl přečíst.
stream.Position = 0;
```

## Krok 3: Vytvořte e-mailovou zprávu

Nyní vytvořte e-mailovou zprávu z MHTML streamu pomocí Aspose.Email. Použijete `MailMessage` třídu pro tento účel.

```csharp
// Vytvořte e-mailovou zprávu Aspose.Email MIME ze streamu.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Krok 4: Odeslání e-mailu

Nakonec odešlete e-mail pomocí SMTP klienta. Nakonfigurujte SMTP klienta s údaji o vašem SMTP serveru a použijte `Send` způsob odeslání zprávy.

```csharp
// Odešlete zprávu pomocí Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Závěr

Gratulujeme! Úspěšně jste převedli dokument DOCX do formátu MHTML a odeslali jej e-mailem pomocí Aspose.Words pro .NET. Tento proces zahrnuje načtení dokumentu, jeho převod do formátu MHTML, vytvoření e-mailové zprávy a její odeslání pomocí SMTP klienta. Pomocí těchto kroků můžete snadno automatizovat převod a odesílání dokumentů e-mailem ve vašich aplikacích.

## Často kladené otázky

### Mohu tuto metodu použít k převodu jiných formátů dokumentů?
Ano, Aspose.Words podporuje různé formáty a můžete převádět dokumenty jako DOC, DOCX, RTF a další do MHTML.

### Jak mohu k e-mailu přidat přílohy?
Můžete použít `Attachments` majetek `MailMessage` třída pro přidání příloh k e-mailu.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words je kompatibilní s .NET Core. Můžete ho použít i v aplikacích .NET Core.

### Potřebuji licenci pro Aspose.Words a Aspose.Email?
Ano, obě knihovny vyžadují licence. Dočasnou licenci můžete získat od [Nákupní stránka Aspose](https://purchase.aspose.com/temporary-license/) pro účely hodnocení.

### Kde najdu další dokumentaci?
Podrobnou dokumentaci k Aspose.Words naleznete zde. [zde](https://reference.aspose.com/words/net/) a pro Aspose.Email [zde](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}