---
title: Μετατροπή Docx σε Mhtml και αποστολή email
linktitle: Μετατροπή Docx σε Mhtml και αποστολή email
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς να μετατρέπετε το DOCX σε MHTML και να στέλνετε μηνύματα ηλεκτρονικού ταχυδρομείου χρησιμοποιώντας το Aspose.Words για .NET σε αυτόν τον οδηγό βήμα προς βήμα. Αυξήστε την παραγωγικότητά σας με τον εύκολο αυτοματισμό.
weight: 10
url: /el/net/basic-conversions/docx-to-mhtml-and-sending-email/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Docx σε Mhtml και αποστολή email

## Εισαγωγή

Στη σημερινή ψηφιακή εποχή, η μετατροπή εγγράφων από μια μορφή σε άλλη και η αποστολή τους μέσω email είναι μια κοινή εργασία. Αυτό το άρθρο θα σας καθοδηγήσει στη διαδικασία μετατροπής ενός αρχείου DOCX σε μορφή MHTML και στη συνέχεια αποστολής του ως email χρησιμοποιώντας το Aspose.Words για .NET. Θα αναλύσουμε κάθε βήμα σε έναν λεπτομερή, εύκολο στην παρακολούθηση οδηγό, διασφαλίζοντας ότι κατανοείτε τη διαδικασία από την αρχή μέχρι το τέλος. Ας βουτήξουμε!

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

1.  Aspose.Words για .NET: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.Words για .NET από το[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email για .NET: Λήψη και εγκατάσταση της βιβλιοθήκης Aspose.Email για .NET από τη[Σελίδα εκδόσεων Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στον υπολογιστή σας.
4. Διακομιστής SMTP: Χρειάζεστε πρόσβαση σε διακομιστή SMTP για να στείλετε μηνύματα ηλεκτρονικού ταχυδρομείου.

## Εισαγωγή χώρων ονομάτων

Για να χρησιμοποιήσετε το Aspose.Words και το Aspose.Email στο έργο σας, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων. Προσθέστε τα ακόλουθα χρησιμοποιώντας οδηγίες στην κορυφή του αρχείου C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Ας αναλύσουμε τη διαδικασία σε πολλαπλά βήματα για να διασφαλίσουμε ότι κατανοείτε καθαρά κάθε μέρος.

## Βήμα 1: Φορτώστε το έγγραφο DOCX

 Πρώτα, πρέπει να φορτώσετε το έγγραφο DOCX που θέλετε να μετατρέψετε. Χρησιμοποιήστε το`Document` τάξη από το Aspose.Words για να φορτώσετε το αρχείο DOCX.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Βήμα 2: Αποθηκεύστε το Έγγραφο ως MHTML

 Στη συνέχεια, αποθηκεύστε το φορτωμένο έγγραφο ως αρχείο MHTML. Αυτό γίνεται χρησιμοποιώντας το`Save` μέθοδος του`Document` τάξη.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Κάντε επαναφορά της ροής στην αρχή, ώστε το Aspose.Email να μπορεί να το διαβάσει.
stream.Position = 0;
```

## Βήμα 3: Δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου

 Τώρα, δημιουργήστε ένα μήνυμα email από τη ροή MHTML χρησιμοποιώντας το Aspose.Email. Θα χρησιμοποιήσετε το`MailMessage` τάξη για το σκοπό αυτό.

```csharp
// Δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου Aspose.Email MIME από τη ροή.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Βήμα 4: Στείλτε το email

 Τέλος, στείλτε το email χρησιμοποιώντας έναν πελάτη SMTP. Διαμορφώστε τον πελάτη SMTP με τα στοιχεία του διακομιστή SMTP και χρησιμοποιήστε το`Send` τρόπο αποστολής του μηνύματος.

```csharp
// Στείλτε το μήνυμα χρησιμοποιώντας το Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Σύναψη

Συγχαρητήρια! Μετατρέψατε επιτυχώς ένα έγγραφο DOCX σε MHTML και το στείλατε μέσω email χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η διαδικασία περιλαμβάνει τη φόρτωση του εγγράφου, τη μετατροπή του σε MHTML, τη δημιουργία ενός μηνύματος email και την αποστολή του χρησιμοποιώντας έναν πελάτη SMTP. Με αυτά τα βήματα, μπορείτε εύκολα να αυτοματοποιήσετε τη μετατροπή και την αποστολή μέσω email των εγγράφων στις εφαρμογές σας.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω αυτήν τη μέθοδο για να μετατρέψω άλλες μορφές εγγράφων;
Ναι, το Aspose.Words υποστηρίζει διάφορες μορφές και μπορείτε να μετατρέψετε έγγραφα όπως DOC, DOCX, RTF και άλλα σε MHTML.

### Πώς μπορώ να προσθέσω συνημμένα στο email;
 Μπορείτε να χρησιμοποιήσετε το`Attachments` ιδιοκτησία του`MailMessage` τάξη για να προσθέσετε συνημμένα στο email σας.

### Είναι το Aspose.Words συμβατό με .NET Core;
Ναι, το Aspose.Words είναι συμβατό με .NET Core. Μπορείτε να το χρησιμοποιήσετε και σε εφαρμογές .NET Core.

### Χρειάζομαι άδεια για το Aspose.Words και το Aspose.Email;
 Ναι, και οι δύο βιβλιοθήκες απαιτούν άδειες. Μπορείτε να πάρετε μια προσωρινή άδεια από το[Σελίδα αγοράς Aspose](https://purchase.aspose.com/temporary-license/) για σκοπούς αξιολόγησης.

### Πού μπορώ να βρω περισσότερα έγγραφα;
 Μπορείτε να βρείτε αναλυτική τεκμηρίωση για το Aspose.Words[εδώ](https://reference.aspose.com/words/net/) και για το Aspose.Email[εδώ](https://reference.aspose.com/email/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
