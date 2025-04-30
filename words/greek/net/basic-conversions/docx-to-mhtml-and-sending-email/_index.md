---
"description": "Μάθετε πώς να μετατρέπετε DOCX σε MHTML και να στέλνετε email χρησιμοποιώντας το Aspose.Words για .NET σε αυτόν τον οδηγό βήμα προς βήμα. Αυξήστε την παραγωγικότητά σας με εύκολο αυτοματισμό."
"linktitle": "Μετατροπή Docx σε Mhtml και αποστολή email"
"second_title": "API επεξεργασίας εγγράφων Aspose.Words"
"title": "Μετατροπή Docx σε Mhtml και αποστολή email"
"url": "/el/net/basic-conversions/docx-to-mhtml-and-sending-email/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Docx σε Mhtml και αποστολή email

## Εισαγωγή

Στη σημερινή ψηφιακή εποχή, η μετατροπή εγγράφων από τη μία μορφή στην άλλη και η αποστολή τους μέσω email είναι μια συνηθισμένη εργασία. Αυτό το άρθρο θα σας καθοδηγήσει στη διαδικασία μετατροπής ενός αρχείου DOCX σε μορφή MHTML και στη συνέχεια στην αποστολή του ως email χρησιμοποιώντας το Aspose.Words για .NET. Θα αναλύσουμε κάθε βήμα σε έναν λεπτομερή, εύχρηστο οδηγό, διασφαλίζοντας ότι κατανοείτε τη διαδικασία από την αρχή μέχρι το τέλος. Ας ξεκινήσουμε!

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

1. Aspose.Words για .NET: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.Words για .NET από το [Σελίδα κυκλοφοριών Aspose](https://releases.aspose.com/words/net/).
2. Aspose.Email για .NET: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.Email για .NET από το [Σελίδα κυκλοφοριών Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework στον υπολογιστή σας.
4. Διακομιστής SMTP: Χρειάζεστε πρόσβαση σε έναν διακομιστή SMTP για να στείλετε email.

## Εισαγωγή χώρων ονομάτων

Για να χρησιμοποιήσετε το Aspose.Words και το Aspose.Email στο έργο σας, πρέπει να εισαγάγετε τους απαραίτητους χώρους ονομάτων. Προσθέστε τα ακόλουθα χρησιμοποιώντας οδηγίες στο επάνω μέρος του αρχείου C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

Ας χωρίσουμε τη διαδικασία σε πολλά βήματα για να διασφαλίσουμε ότι κατανοείτε πλήρως κάθε μέρος.

## Βήμα 1: Φόρτωση του εγγράφου DOCX

Αρχικά, πρέπει να φορτώσετε το έγγραφο DOCX που θέλετε να μετατρέψετε. Χρησιμοποιήστε το `Document` κλάση από το Aspose.Words για να φορτώσετε το αρχείο DOCX σας.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Βήμα 2: Αποθήκευση του εγγράφου ως MHTML

Στη συνέχεια, αποθηκεύστε το φορτωμένο έγγραφο ως αρχείο MHTML. Αυτό γίνεται χρησιμοποιώντας το `Save` μέθοδος του `Document` τάξη.

```csharp
Stream stream = new MemoryStream();
doc.Save(stream, SaveFormat.Mhtml);

// Επαναφέρετε τη ροή στην αρχή, ώστε το Aspose.Email να μπορεί να τη διαβάσει.
stream.Position = 0;
```

## Βήμα 3: Δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου

Τώρα, δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου από τη ροή MHTML χρησιμοποιώντας το Aspose.Email. Θα χρησιμοποιήσετε το `MailMessage` τάξη για τον σκοπό αυτό.

```csharp
// Δημιουργήστε ένα μήνυμα ηλεκτρονικού ταχυδρομείου Aspose.Email MIME από τη ροή.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Βήμα 4: Στείλτε το email

Τέλος, στείλτε το email χρησιμοποιώντας ένα πρόγραμμα-πελάτη SMTP. Ρυθμίστε το πρόγραμμα-πελάτη SMTP με τα στοιχεία του διακομιστή SMTP σας και χρησιμοποιήστε το `Send` μέθοδος για την αποστολή του μηνύματος.

```csharp
// Στείλτε το μήνυμα χρησιμοποιώντας το Aspose.Email.
SmtpClient client = new SmtpClient();
client.Host = "your_smtp.com";
client.Send(message);
```

## Σύναψη

Συγχαρητήρια! Μετατρέψατε με επιτυχία ένα έγγραφο DOCX σε MHTML και το στείλατε μέσω email χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η διαδικασία περιλαμβάνει τη φόρτωση του εγγράφου, τη μετατροπή του σε MHTML, τη δημιουργία ενός μηνύματος email και την αποστολή του χρησιμοποιώντας ένα πρόγραμμα-πελάτη SMTP. Με αυτά τα βήματα, μπορείτε εύκολα να αυτοματοποιήσετε τη μετατροπή και την αποστολή εγγράφων μέσω email στις εφαρμογές σας.

## Συχνές ερωτήσεις

### Μπορώ να χρησιμοποιήσω αυτήν τη μέθοδο για να μετατρέψω άλλες μορφές εγγράφων;
Ναι, το Aspose.Words υποστηρίζει διάφορες μορφές και μπορείτε να μετατρέψετε έγγραφα όπως DOC, DOCX, RTF και άλλα σε MHTML.

### Πώς μπορώ να προσθέσω συνημμένα στο email;
Μπορείτε να χρησιμοποιήσετε το `Attachments` ιδιοκτησία του `MailMessage` κλάση για να προσθέσετε συνημμένα στο email σας.

### Είναι το Aspose.Words συμβατό με το .NET Core;
Ναι, το Aspose.Words είναι συμβατό με το .NET Core. Μπορείτε να το χρησιμοποιήσετε και σε εφαρμογές .NET Core.

### Χρειάζομαι άδεια χρήσης για τα Aspose.Words και Aspose.Email;
Ναι, και οι δύο βιβλιοθήκες απαιτούν άδειες χρήσης. Μπορείτε να λάβετε μια προσωρινή άδεια χρήσης από το [Σελίδα αγοράς Aspose](https://purchase.aspose.com/temporary-license/) για σκοπούς αξιολόγησης.

### Πού μπορώ να βρω περισσότερη τεκμηρίωση;
Μπορείτε να βρείτε λεπτομερή τεκμηρίωση για το Aspose.Words [εδώ](https://reference.aspose.com/words/net/) και για το Aspose.Email [εδώ](https://reference.aspose.com/email/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}