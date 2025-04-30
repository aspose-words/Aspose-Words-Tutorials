---
"description": "Μάθετε πώς να βρίσκετε και να αντικαθιστάτε κείμενο σε έγγραφα Word με το Aspose.Words για Java. Οδηγός βήμα προς βήμα με παραδείγματα κώδικα. Βελτιώστε τις δεξιότητές σας στον χειρισμό εγγράφων Java."
"linktitle": "Εύρεση και αντικατάσταση κειμένου"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/finding-and-replacing-text/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java


## Εισαγωγή στην εύρεση και αντικατάσταση κειμένου στο Aspose.Words για Java

Το Aspose.Words για Java είναι ένα ισχυρό API Java που σας επιτρέπει να εργάζεστε με έγγραφα του Word μέσω προγραμματισμού. Μία από τις συνηθισμένες εργασίες κατά την επεξεργασία εγγράφων του Word είναι η εύρεση και η αντικατάσταση κειμένου. Είτε χρειάζεται να ενημερώσετε δεσμευτικά θέσης σε πρότυπα είτε να εκτελέσετε πιο σύνθετους χειρισμούς κειμένου, το Aspose.Words για Java μπορεί να σας βοηθήσει να επιτύχετε τους στόχους σας αποτελεσματικά.

## Προαπαιτούμενα

Πριν εμβαθύνουμε στις λεπτομέρειες της εύρεσης και αντικατάστασης κειμένου, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Περιβάλλον Ανάπτυξης Java
- Aspose.Words για βιβλιοθήκη Java
- Ένα δείγμα εγγράφου του Word για εργασία

Μπορείτε να κατεβάσετε τη βιβλιοθήκη Aspose.Words για Java από [εδώ](https://releases.aspose.com/words/java/).

## Εύρεση και αντικατάσταση απλού κειμένου

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργία ενός DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Εύρεση και αντικατάσταση κειμένου
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, φορτώνουμε ένα έγγραφο του Word, δημιουργούμε ένα `DocumentBuilder`, και χρησιμοποιήστε το `replace` μέθοδος για την εύρεση και αντικατάσταση του "παλιού κειμένου" με "νέο κείμενο" μέσα στο έγγραφο.

## Χρήση κανονικών εκφράσεων

Οι κανονικές εκφράσεις παρέχουν ισχυρές δυνατότητες αντιστοίχισης μοτίβων για αναζήτηση και αντικατάσταση κειμένου. Το Aspose.Words για Java υποστηρίζει κανονικές εκφράσεις για πιο προηγμένες λειτουργίες εύρεσης και αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργία ενός DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Χρήση κανονικών εκφράσεων για εύρεση και αντικατάσταση κειμένου
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε ένα μοτίβο κανονικής έκφρασης για να βρούμε και να αντικαταστήσουμε κείμενο μέσα στο έγγραφο.

## Αγνόηση κειμένου εντός πεδίων

Μπορείτε να ρυθμίσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα στα πεδία κατά την εκτέλεση λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε την τιμή IgnoreFields σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό είναι χρήσιμο όταν θέλετε να εξαιρέσετε το κείμενο μέσα σε πεδία, όπως τα πεδία συγχώνευσης, από την αντικατάσταση.

## Αγνόηση κειμένου μέσα σε διαγραφή αναθεωρήσεων

Μπορείτε να ρυθμίσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα σε αναθεωρήσεις διαγραφής κατά τη διάρκεια των λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε την τιμή IgnoreDeleted σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εξαιρέσετε κείμενο που έχει επισημανθεί για διαγραφή στις εντοπισμένες αλλαγές από την αντικατάσταση.

## Αγνόηση κειμένου μέσα σε εισαγωγικές αναθεωρήσεις

Μπορείτε να ρυθμίσετε το Aspose.Words ώστε να αγνοεί το κείμενο μέσα σε αναθεωρήσεις εισαγωγής κατά τη διάρκεια των λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε την τιμή IgnoreInserted σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-text", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εξαιρέσετε κείμενο που έχει επισημανθεί ως εισαγόμενο στις εντοπισμένες αλλαγές από την αντικατάσταση.

## Αντικατάσταση κειμένου με HTML

Μπορείτε να χρησιμοποιήσετε το Aspose.Words για Java για να αντικαταστήσετε κείμενο με περιεχόμενο HTML.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions με μια προσαρμοσμένη επιστροφή κλήσης αντικατάστασης
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε μια προσαρμοσμένη `ReplaceWithHtmlEvaluator` για να αντικαταστήσετε κείμενο με περιεχόμενο HTML.

## Αντικατάσταση κειμένου σε κεφαλίδες και υποσέλιδα

Μπορείτε να βρείτε και να αντικαταστήσετε κείμενο μέσα σε κεφαλίδες και υποσέλιδα του εγγράφου του Word.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Αποκτήστε τη συλλογή κεφαλίδων και υποσέλιδων
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Επιλέξτε τον τύπο κεφαλίδας ή υποσέλιδου στον οποίο θέλετε να αντικαταστήσετε το κείμενο (π.χ., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Δημιουργήστε μια παρουσία FindReplaceOptions και εφαρμόστε την στην περιοχή του υποσέλιδου
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εκτελείτε αντικαταστάσεις κειμένου ειδικά σε κεφαλίδες και υποσέλιδα.

## Εμφάνιση αλλαγών για τις παραγγελίες κεφαλίδας και υποσέλιδου

Μπορείτε να χρησιμοποιήσετε το Aspose.Words για να εμφανίσετε αλλαγές στις τάξεις κεφαλίδας και υποσέλιδου στο έγγραφό σας.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Αποκτήστε το πρώτο τμήμα
Section firstPageSection = doc.getFirstSection();

// Δημιουργήστε μια παρουσία FindReplaceOptions και εφαρμόστε την στην περιοχή του εγγράφου
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Αντικατάσταση κειμένου που επηρεάζει τις σειρές κεφαλίδων και υποσέλιδων
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να οπτικοποιήσετε αλλαγές που σχετίζονται με τις σειρές κεφαλίδων και υποσέλιδων στο έγγραφό σας.

## Αντικατάσταση κειμένου με πεδία

Μπορείτε να αντικαταστήσετε κείμενο με πεδία χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε μια προσαρμοσμένη επιστροφή κλήσης αντικατάστασης για πεδία
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, αντικαθιστούμε το κείμενο με πεδία και καθορίζουμε τον τύπο πεδίου (π.χ., `FieldType.FIELD_MERGE_FIELD`).

## Αντικατάσταση με έναν αξιολογητή

Μπορείτε να χρησιμοποιήσετε έναν προσαρμοσμένο αξιολογητή για να προσδιορίσετε δυναμικά το κείμενο αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε μια προσαρμοσμένη επιστροφή κλήσης αντικατάστασης
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε έναν προσαρμοσμένο αξιολογητή (`MyReplaceEvaluator`) για αντικατάσταση κειμένου.

## Αντικατάσταση με Regex

Το Aspose.Words για Java σάς επιτρέπει να αντικαθιστάτε κείμενο χρησιμοποιώντας κανονικές εκφράσεις.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Χρήση κανονικών εκφράσεων για εύρεση και αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε ένα μοτίβο κανονικής έκφρασης για να βρούμε και να αντικαταστήσουμε κείμενο μέσα στο έγγραφο.

## Αναγνώριση και Αντικαταστάσεις εντός Προτύπων Αντικατάστασης

Μπορείτε να αναγνωρίσετε και να κάνετε αντικαταστάσεις μέσα σε μοτίβα αντικατάστασης χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions με την τιμή UseSubstitutions σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Χρήση επιλογών κατά την αντικατάσταση κειμένου με μοτίβο
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εκτελείτε αντικαταστάσεις εντός των μοτίβων αντικατάστασης για πιο προηγμένες αντικαταστάσεις.

## Αντικατάσταση με συμβολοσειρά

Μπορείτε να αντικαταστήσετε κείμενο με μια απλή συμβολοσειρά χρησιμοποιώντας το Aspose.Words για Java.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Αντικατάσταση κειμένου με μια συμβολοσειρά
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Σε αυτό το παράδειγμα, αντικαθιστούμε το "text-to-replace" με το "new-string" μέσα στο έγγραφο.

## Χρήση παλαιάς παραγγελίας

Μπορείτε να χρησιμοποιήσετε την παλαιότερη σειρά κατά την εκτέλεση λειτουργιών εύρεσης και αντικατάστασης.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Δημιουργήστε μια παρουσία FindReplaceOptions και ορίστε την τιμή UseLegacyOrder σε true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Χρήση επιλογών κατά την αντικατάσταση κειμένου
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να χρησιμοποιείτε την παλαιότερη σειρά για λειτουργίες εύρεσης και αντικατάστασης.

## Αντικατάσταση κειμένου σε πίνακα

Μπορείτε να βρείτε και να αντικαταστήσετε κείμενο μέσα σε πίνακες στο έγγραφο του Word.

```java
// Φόρτωση του εγγράφου
Document doc = new Document("your-document.docx");

// Αποκτήστε ένα συγκεκριμένο τραπέζι (π.χ., το πρώτο τραπέζι)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Χρησιμοποιήστε το FindReplaceOptions για την αντικατάσταση κειμένου στον πίνακα
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Αποθήκευση του τροποποιημένου εγγράφου
doc.save("modified-document.docx");
```

Αυτό σας επιτρέπει να εκτελείτε αντικαταστάσεις κειμένου ειδικά μέσα σε πίνακες.

## Σύναψη

Το Aspose.Words για Java παρέχει ολοκληρωμένες δυνατότητες για την εύρεση και αντικατάσταση κειμένου σε έγγραφα του Word. Είτε χρειάζεται να εκτελέσετε απλές αντικαταστάσεις κειμένου είτε πιο προηγμένες λειτουργίες χρησιμοποιώντας κανονικές εκφράσεις, χειρισμούς πεδίων ή προσαρμοσμένους αξιολογητές, το Aspose.Words για Java σας καλύπτει. Φροντίστε να εξερευνήσετε την εκτενή τεκμηρίωση και τα παραδείγματα που παρέχονται από το Aspose για να αξιοποιήσετε πλήρως τις δυνατότητες αυτής της ισχυρής βιβλιοθήκης Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να κατεβάσω το Aspose.Words για Java;

Μπορείτε να κατεβάσετε το Aspose.Words για Java από τον ιστότοπο, μεταβαίνοντας στη διεύθυνση [αυτός ο σύνδεσμος](https://releases.aspose.com/words/java/).

### Μπορώ να χρησιμοποιήσω κανονικές εκφράσεις για αντικατάσταση κειμένου;

Ναι, μπορείτε να χρησιμοποιήσετε κανονικές εκφράσεις για την αντικατάσταση κειμένου στο Aspose.Words για Java. Αυτό σας επιτρέπει να εκτελείτε πιο προηγμένες και ευέλικτες λειτουργίες εύρεσης και αντικατάστασης.

### Πώς μπορώ να αγνοήσω κείμενο μέσα σε πεδία κατά την αντικατάσταση;

Για να αγνοήσετε το κείμενο μέσα στα πεδία κατά την αντικατάσταση, μπορείτε να ορίσετε το `IgnoreFields` ιδιοκτησία του `FindReplaceOptions` να `true`Αυτό διασφαλίζει ότι το κείμενο εντός πεδίων, όπως τα πεδία συγχώνευσης, εξαιρείται από την αντικατάσταση.

### Μπορώ να αντικαταστήσω κείμενο μέσα σε κεφαλίδες και υποσέλιδα;

Ναι, μπορείτε να αντικαταστήσετε κείμενο μέσα σε κεφαλίδες και υποσέλιδα του εγγράφου του Word. Απλώς αποκτήστε πρόσβαση στην κατάλληλη κεφαλίδα ή υποσέλιδο και χρησιμοποιήστε το `replace` μέθοδος με την επιθυμητή `FindReplaceOptions`.

### Σε τι χρησιμεύει η επιλογή UseLegacyOrder;

Ο `UseLegacyOrder` επιλογή σε `FindReplaceOptions` σας επιτρέπει να χρησιμοποιείτε παλαιά σειρά κατά την εκτέλεση λειτουργιών εύρεσης και αντικατάστασης. Αυτό μπορεί να είναι χρήσιμο σε ορισμένα σενάρια όπου επιθυμείτε συμπεριφορά παλαιάς σειράς.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}