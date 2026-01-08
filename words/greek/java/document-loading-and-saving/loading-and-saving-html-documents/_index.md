---
date: 2025-12-20
description: Μάθετε πώς να φορτώνετε HTML και να μετατρέπετε HTML σε DOCX με το Aspose.Words
  for Java. Ο οδηγός βήμα‑προς‑βήμα δείχνει πώς να αποθηκεύετε αρχεία DOCX και να
  χρησιμοποιείτε δομημένες ετικέτες εγγράφου.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Πώς να φορτώσετε HTML και να το αποθηκεύσετε ως DOCX χρησιμοποιώντας το Aspose.Words
  για Java
url: /el/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε HTML και να το αποθηκεύσετε ως DOCX χρησιμοποιώντας το Aspose.Words για Java

## Εισαγωγή στη Φόρτωση και Αποθήκευση Εγγράφων HTML με το Aspose.Words για Java

Σε αυτό το άρθρο, θα εξερευνήσουμε **πώς να φορτώσετε html** και να το αποθηκεύσετε ως αρχείο DOCX χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Το Aspose.Words είναι ένα ισχυρό API που σας επιτρέπει να χειρίζεστε έγγραφα Word προγραμματιστικά, και περιλαμβάνει εκτενή υποστήριξη για εισαγωγή/εξαγωγή HTML. Θα περάσουμε από όλη τη διαδικασία, από τη ρύθμιση των επιλογών φόρτωσης μέχρι την αποθήκευση του αποτελέσματος ως έγγραφο Word.

## Γρήγορες Απαντήσεις
- **Ποια είναι η κύρια κλάση για τη φόρτωση HTML;** `Document` μαζί με `HtmlLoadOptions`.
- **Ποια επιλογή ενεργοποιεί τις Structured Document Tags;** `HtmlLoadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG)`.
- **Μπορώ να μετατρέψω HTML σε DOCX σε ένα βήμα;** Ναι – φορτώστε το HTML και καλέστε `doc.save(...".docx")`.
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμαστική έκδοση λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.
- **Ποια έκδοση της Java απαιτείται;** Υποστηρίζεται η Java 8 ή νεότερη.

## Τι σημαίνει “πώς να φορτώσετε html” στο πλαίσιο του Aspose.Words;
Η φόρτωση HTML σημαίνει ανάγνωση μιας συμβολοσειράς ή αρχείου HTML και μετατροπή του σε αντικείμενο `Document` του Aspose.Words. Αυτό το αντικείμενο μπορεί στη συνέχεια να επεξεργαστεί, να μορφοποιηθεί ή να αποθηκευτεί σε οποιαδήποτε μορφή υποστηρίζεται από το API, όπως DOCX, PDF ή RTF.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για μετατροπή HTML‑σε‑DOCX;
- **Διατηρεί τη διάταξη** – πίνακες, λίστες και εικόνες παραμένουν αμετάβλητες.
- **Υποστηρίζει Structured Document Tags** – ιδανικό για δημιουργία ελέγχων περιεχομένου στο Word.
- **Δεν απαιτείται Microsoft Office** – λειτουργεί σε οποιονδήποτε διακομιστή ή περιβάλλον cloud.
- **Υψηλή απόδοση** – επεξεργάζεται μεγάλα αρχεία HTML γρήγορα.

## Προαπαιτούμενα

1. **Βιβλιοθήκη Aspose.Words για Java** – κατεβάστε την από [εδώ](https://releases.aspose.com/words/java/).
2. **Περιβάλλον Ανάπτυξης Java** – εγκατεστημένο και ρυθμισμένο JDK 8+.
3. **Βασική εξοικείωση με Java I/O** – θα χρησιμοποιήσουμε `ByteArrayInputStream` για την παροχή της συμβολοσειράς HTML.

## Πώς να Φορτώσετε Έγγραφα HTML

Παρακάτω υπάρχει ένα σύντομο παράδειγμα που δείχνει τη φόρτωση ενός αποσπάσματος HTML ενώ ενεργοποιεί τη δυνατότητα **structured document tag**.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
    loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}

Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
```

**Επεξήγηση**

- Δημιουργούμε μια συμβολοσειρά `HTML` που περιέχει έναν απλό έλεγχο `<select>`.
- Το `HtmlLoadOptions` μας επιτρέπει να καθορίσουμε πώς θα ερμηνευτεί το HTML. Ορίζοντας τον προτιμώμενο τύπο ελέγχου σε `STRUCTURED_DOCUMENT_TAG` λέμε στο Aspose.Words να μετατρέπει τα HTML form controls σε ελέγχους περιεχομένου του Word.
- Ο κατασκευαστής `Document` διαβάζει το HTML από ένα `ByteArrayInputStream` χρησιμοποιώντας κωδικοποίηση UTF‑8.

## Πώς να Αποθηκεύσετε ως DOCX (Μετατροπή HTML σε DOCX)

Μόλις το HTML φορτωθεί σε ένα `Document`, η αποθήκευσή του ως αρχείο DOCX είναι απλή:

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Αντικαταστήστε το `"Your Directory Path"` με τον πραγματικό φάκελο όπου θέλετε να εμφανιστεί το αρχείο εξόδου.

## Πλήρης Πηγαίος Κώδικας για Φόρτωση και Αποθήκευση Εγγράφων HTML

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που συνδυάζει τα βήματα φόρτωσης και αποθήκευσης. Μπορείτε να το αντιγράψετε‑και‑επικολλήσετε στο IDE σας.

```java
final String HTML = "\r\n
					<html>\r\n
					<select name='ComboBox' size='1'>\r\n
					<option value='val1'>item1</option>\r\n
					<option value='val2'></option>\r\n
					</select>\r\n
					</html>\r\n";
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
{
	loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);
}
Document doc = new Document(new ByteArrayInputStream(HTML.getBytes(StandardCharsets.UTF_8)), loadOptions);
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

## Συνηθισμένα Προβλήματα & Συμβουλές

| Πρόβλημα | Γιατί συμβαίνει | Πώς να το διορθώσετε |
|----------|----------------|----------------------|
| **Λείπουν γραμματοσειρές** | Το HTML αναφέρει γραμματοσειρές που δεν είναι εγκατεστημένες στον διακομιστή. | Ενσωματώστε γραμματοσειρές στο DOCX χρησιμοποιώντας `FontSettings` ή βεβαιωθείτε ότι οι απαιτούμενες γραμματοσειρές είναι διαθέσιμες. |
| **Οι εικόνες δεν εμφανίζονται** | Οι σχετικές διαδρομές εικόνων δεν μπορούν να επιλυθούν. | Χρησιμοποιήστε απόλυτες URL ή φορτώστε εικόνες σε ένα `MemoryStream` και ορίστε `HtmlLoadOptions.setImageSavingCallback`. |
| **Ο τύπος ελέγχου δεν μετατράπηκε** | Δεν έχει οριστεί `setPreferredControlType` ή έχει οριστεί το λάθος enum. | Επαληθεύστε ότι χρησιμοποιείτε `HtmlControlType.STRUCTURED_DOCUMENT_TAG`. |
| **Προβλήματα κωδικοποίησης** | Η συμβολοσειρά HTML κωδικοποιείται με διαφορετικό charset. | Χρησιμοποιείτε πάντα `StandardCharsets.UTF_8` όταν μετατρέπετε τη συμβολοσειρά σε bytes. |

## Συχνές Ερωτήσεις

### Πώς εγκαθιστώ το Aspose.Words για Java;
Το Aspose.Words για Java μπορεί να ληφθεί από [εδώ](https://releases.aspose.com/words/java/). Ακολουθήστε τον οδηγό εγκατάστασης στη σελίδα λήψης για να προσθέσετε τα αρχεία JAR στην classpath του έργου σας.

### Μπορώ να φορτώσω πολύπλοκα έγγραφα HTML χρησιμοποιώντας το Aspose.Words;
Ναι, το Aspose.Words για Java μπορεί να διαχειριστεί πολύπλοκο HTML, συμπεριλαμβανομένων ενσωματωμένων πινάκων, CSS styling και διαδραστικών στοιχείων χωρίς JavaScript. Προσαρμόστε τις `HtmlLoadOptions` (π.χ., `setLoadImages` ή `setCssStyleSheetFileName`) για να βελτιστοποιήσετε την εισαγωγή.

### Ποιες άλλες μορφές εγγράφων υποστηρίζει το Aspose.Words;
Το Aspose.Words υποστηρίζει DOC, DOCX, RTF, HTML, PDF, EPUB, XPS και πολλές άλλες. Το API παρέχει αποθήκευση με μία γραμμή κώδικα σε οποιαδήποτε από αυτές τις μορφές.

### Είναι το Aspose.Words κατάλληλο για αυτοματοποίηση εγγράφων σε επίπεδο επιχείρησης;
Απολύτως. Χρησιμοποιείται από μεγάλες επιχειρήσεις για αυτόματη δημιουργία αναφορών, μαζική μετατροπή εγγράφων και επεξεργασία εγγράφων στο διακομιστή χωρίς εξαρτήσεις από το Microsoft Office.

### Πού μπορώ να βρω περισσότερη τεκμηρίωση και παραδείγματα για το Aspose.Words για Java;
Μπορείτε να εξερευνήσετε την πλήρη αναφορά API και επιπλέον tutorials στην ιστοσελίδα τεκμηρίωσης του Aspose.Words για Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Τελευταία ενημέρωση:** 2025-12-20  
**Δοκιμασμένο με:** Aspose.Words for Java 24.12 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}