---
title: Δημιουργήστε νέα γραμμή υπογραφής και ορίστε το αναγνωριστικό παρόχου
linktitle: Δημιουργήστε νέα γραμμή υπογραφής και ορίστε το αναγνωριστικό παρόχου
second_title: Aspose.Words Document Processing API
description: Μάθετε πώς μπορείτε να δημιουργήσετε μια νέα γραμμή υπογραφής και να ορίσετε το αναγνωριστικό παρόχου στα έγγραφα του Word χρησιμοποιώντας το Aspose.Words για .NET. Οδηγός βήμα προς βήμα.
weight: 10
url: /el/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε νέα γραμμή υπογραφής και ορίστε το αναγνωριστικό παρόχου

## Εισαγωγή

Γεια σας, λάτρεις της τεχνολογίας! Αναρωτηθήκατε ποτέ πώς να προσθέσετε μια γραμμή υπογραφής στα έγγραφα του Word μέσω προγραμματισμού; Λοιπόν, σήμερα ασχολούμαστε ακριβώς με αυτό χρησιμοποιώντας το Aspose.Words για .NET. Αυτός ο οδηγός θα σας καθοδηγήσει σε κάθε βήμα, καθιστώντας εύκολη τη δημιουργία μιας νέας γραμμής υπογραφής και τον ορισμό του αναγνωριστικού παρόχου στα έγγραφα του Word. Είτε αυτοματοποιείτε την επεξεργασία εγγράφων είτε απλώς θέλετε να βελτιστοποιήσετε τη ροή εργασίας σας, αυτό το σεμινάριο σας καλύπτει.

## Προαπαιτούμενα

Πριν λερώσουμε τα χέρια μας, ας βεβαιωθούμε ότι έχουμε όλα όσα χρειαζόμαστε:

1.  Aspose.Words για .NET: Εάν δεν το έχετε κάνει ήδη, κάντε λήψη του[εδώ](https://releases.aspose.com/words/net/).
2. Περιβάλλον ανάπτυξης: Visual Studio ή οποιοδήποτε άλλο περιβάλλον ανάπτυξης C#.
3. .NET Framework: Βεβαιωθείτε ότι έχετε εγκαταστήσει το .NET Framework.
4. Πιστοποιητικό PFX: Για την υπογραφή εγγράφων, θα χρειαστείτε ένα πιστοποιητικό PFX. Μπορείτε να πάρετε ένα από μια αξιόπιστη αρχή έκδοσης πιστοποιητικών.

## Εισαγωγή χώρων ονομάτων

Πρώτα πράγματα πρώτα, ας εισαγάγουμε τους απαραίτητους χώρους ονομάτων στο έργο σας C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Εντάξει, ας πάμε στο τσακωτικό. Ακολουθεί μια λεπτομερής ανάλυση κάθε βήματος για να δημιουργήσετε μια νέα γραμμή υπογραφής και να ορίσετε το αναγνωριστικό παρόχου.

## Βήμα 1: Δημιουργήστε ένα νέο έγγραφο

Για να ξεκινήσουμε, πρέπει να δημιουργήσουμε ένα νέο έγγραφο του Word. Αυτός θα είναι ο καμβάς για τη γραμμή υπογραφής μας.

```csharp
// Η διαδρομή προς τον κατάλογο εγγράφων.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Σε αυτό το απόσπασμα, προετοιμάζουμε ένα νέο`Document` και α`DocumentBuilder` . Ο`DocumentBuilder` μας βοηθά να προσθέσουμε στοιχεία στο έγγραφό μας.

## Βήμα 2: Ορίστε τις επιλογές γραμμής υπογραφής

Στη συνέχεια, ορίζουμε τις επιλογές για τη γραμμή υπογραφής μας. Αυτό περιλαμβάνει το όνομα, τον τίτλο, το email και άλλα στοιχεία του υπογράφοντος.

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Αυτές οι επιλογές εξατομικεύουν τη γραμμή υπογραφής, καθιστώντας την σαφή και επαγγελματική.

## Βήμα 3: Εισαγάγετε τη γραμμή υπογραφής

Με τις επιλογές μας ορισμένες, μπορούμε τώρα να εισάγουμε τη γραμμή υπογραφής στο έγγραφο.

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Εδώ, το`InsertSignatureLine` μέθοδος προσθέτει τη γραμμή υπογραφής και της εκχωρούμε ένα μοναδικό αναγνωριστικό παρόχου.

## Βήμα 4: Αποθηκεύστε το έγγραφο

Αφού εισαγάγετε τη γραμμή υπογραφής, ας αποθηκεύσουμε το έγγραφο.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Αυτό αποθηκεύει το έγγραφό σας με τη νέα γραμμή υπογραφής που προστέθηκε.

## Βήμα 5: Ρύθμιση επιλογών υπογραφής

Τώρα, πρέπει να ρυθμίσουμε τις επιλογές για την υπογραφή του εγγράφου. Αυτό περιλαμβάνει το αναγνωριστικό γραμμής υπογραφής, το αναγνωριστικό παρόχου, τα σχόλια και την ώρα υπογραφής.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Αυτές οι επιλογές διασφαλίζουν ότι το έγγραφο είναι υπογεγραμμένο με τις σωστές λεπτομέρειες.

## Βήμα 6: Δημιουργία κατόχου πιστοποιητικού

Για να υπογράψουμε το έγγραφο, θα χρησιμοποιήσουμε ένα πιστοποιητικό PFX. Ας δημιουργήσουμε έναν κάτοχο πιστοποιητικού για αυτό.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Φροντίστε να αντικαταστήσετε`"morzal.pfx"` με το πραγματικό αρχείο πιστοποιητικού σας και`"aw"` με τον κωδικό πρόσβασης του πιστοποιητικού σας.

## Βήμα 7: Υπογράψτε το Έγγραφο

Τέλος, υπογράφουμε το έγγραφο χρησιμοποιώντας το βοηθητικό πρόγραμμα ψηφιακής υπογραφής.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Αυτό υπογράφει το έγγραφο και το αποθηκεύει ως νέο αρχείο.

## Σύναψη

Και ορίστε το! Δημιουργήσατε επιτυχώς μια νέα γραμμή υπογραφής και έχετε ορίσει το αναγνωριστικό παρόχου σε ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για .NET. Αυτή η ισχυρή βιβλιοθήκη καθιστά απίστευτα εύκολη τη διαχείριση και την αυτοματοποίηση των εργασιών επεξεργασίας εγγράφων. Δοκιμάστε το και δείτε πώς μπορεί να βελτιώσει τη ροή εργασίας σας.

## Συχνές ερωτήσεις

### Μπορώ να προσαρμόσω την εμφάνιση της γραμμής υπογραφής;
 Απολύτως! Μπορείτε να τροποποιήσετε διάφορες επιλογές στο`SignatureLineOptions`για να ταιριάζει στις ανάγκες σας.

### Τι γίνεται αν δεν έχω πιστοποιητικό PFX;
Θα χρειαστεί να αποκτήσετε ένα από μια αξιόπιστη αρχή έκδοσης πιστοποιητικών. Είναι απαραίτητο για την ψηφιακή υπογραφή εγγράφων.

### Μπορώ να προσθέσω πολλές γραμμές υπογραφής σε ένα έγγραφο;
Ναι, μπορείτε να προσθέσετε όσες γραμμές υπογραφής χρειάζεται επαναλαμβάνοντας τη διαδικασία εισαγωγής με διαφορετικές επιλογές.

### Είναι το Aspose.Words για .NET συμβατό με .NET Core;
Ναι, το Aspose.Words for .NET υποστηρίζει .NET Core, καθιστώντας το ευέλικτο για διαφορετικά περιβάλλοντα ανάπτυξης.

### Πόσο ασφαλείς είναι οι ψηφιακές υπογραφές;
Οι ψηφιακές υπογραφές που δημιουργούνται με το Aspose.Words είναι εξαιρετικά ασφαλείς, υπό την προϋπόθεση ότι χρησιμοποιείτε ένα έγκυρο και αξιόπιστο πιστοποιητικό.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
