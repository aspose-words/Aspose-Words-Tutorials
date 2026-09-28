---
date: 2026-02-24
description: Μάθετε πώς να φορτώνετε HTML και πώς να αποθηκεύετε DOCX χρησιμοποιώντας
  το Aspose.Words for Java – ένας οδηγός βήμα‑προς‑βήμα για τη μετατροπή HTML σε DOCX.
linktitle: Loading and Saving HTML Documents
second_title: Aspose.Words Java Document Processing API
title: Πώς να φορτώσετε HTML και να το αποθηκεύσετε ως DOCX με το Aspose.Words for
  Java
url: /el/java/document-loading-and-saving/loading-and-saving-html-documents/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε HTML και να το αποθηκεύσετε ως DOCX με Aspose.Words for Java

## Γρήγορες Απαντήσεις
- **Τι κάνει ο κώδικας;** Φορτώνει μια συμβολοσειρά HTML, τη θεωρεί ως ετικέτα δομημένου εγγράφου και την αποθηκεύει ως αρχείο DOCX.  
- **Ποια βιβλιοθήκη απαιτείται;** Aspose.Words for Java (το SDK “aspose words java”).  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.  
- **Μπορώ να προσαρμόσω τις επιλογές φόρτωσης HTML;** Ναι – μπορείτε να ορίσετε το `PreferredControlType` σε `STRUCTURED_DOCUMENT_TAG`.  
- **Είναι κατάλληλο για εταιρικά έργα;** Απόλυτα· το API έχει σχεδιαστεί για επεξεργασία εγγράφων υψηλού όγκου σε επιχειρησιακό επίπεδο.

## Τι είναι **πώς να φορτώσετε html** με Aspose.Words for Java;
Η φόρτωση HTML σημαίνει ότι παρέχετε μια συμβολοσειρά ή αρχείο HTML στον κατασκευαστή `Document`, ώστε το Aspose.Words να αναλύσει το markup και να δημιουργήσει ένα εσωτερικό μοντέλο εγγράφου Word. Αυτό το μοντέλο μπορεί στη συνέχεια να τροποποιηθεί ή να αποθηκευτεί σε οποιαδήποτε υποστηριζόμενη μορφή, όπως DOCX.

## Γιατί να χρησιμοποιήσετε **Aspose.Words for Java** για μετατροπή HTML‑σε‑DOCX;
- **Πλήρης υποστήριξη μορφών** – από απλό HTML έως σύνθετες σελίδες με CSS, εικόνες και στοιχεία φόρμας.  
- **Ετικέτα Δομημένου Εγγράφου** – διατηρεί τα στοιχεία φόρμας ως επαναχρησιμοποιήσιμες ετικέτες, ιδανικό για μετέπειτα επεξεργασία.  
- **Χωρίς εξάρτηση από το Microsoft Office** – λειτουργεί σε οποιαδήποτε πλατφόρμα που εκτελεί Java.  
- **Επίδοση επιπέδου επιχειρήσεων** – διαχειρίζεται μεγάλα έγγραφα αποδοτικά.

## Προαπαιτούμενα
1. **Aspose.Words for Java Library** – κατεβάστε την από [εδώ](https://releases.aspose.com/words/java/).  
2. **Περιβάλλον Ανάπτυξης Java** – εγκατεστημένο και ρυθμισμένο JDK 8 ή νεότερο.

## Πώς να Φορτώσετε Έγγραφα HTML
Παρακάτω βρίσκεται το βασικό απόσπασμα κώδικα που δείχνει **πώς να φορτώσετε html** σε ένα `Document`. Δημιουργούμε ένα μικρό απόσπασμα HTML, ρυθμίζουμε το `HtmlLoadOptions` ώστε να χρησιμοποιεί **structured document tag**, και στη συνέχεια δημιουργούμε το `Document`.

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

*Συμβουλή:* Η επιλογή `STRUCTURED_DOCUMENT_TAG` διατηρεί τα στοιχεία φόρμας (όπως το στοιχείο `<select>`) ως επεξεργάσιμες ετικέτες στο τελικό έγγραφο Word, κάτι που είναι χρήσιμο για μετέπειτα εισαγωγή δεδομένων.

## Πώς να Αποθηκεύσετε DOCX από HTML
Αφού φορτωθεί το HTML, η αποθήκευσή του ως αρχείο DOCX είναι απλή. Αυτό το παράδειγμα δείχνει **πώς να αποθηκεύσετε docx** χρησιμοποιώντας το ίδιο αντικείμενο `Document`.

```java
doc.save("Your Directory Path" + "WorkingWithHtmlLoadOptions.PreferredControlType.docx");
```

Αντικαταστήστε το `"Your Directory Path"` με το φάκελο όπου θέλετε να εμφανιστεί το αρχείο εξόδου. Το παραγόμενο DOCX μπορεί να ανοιχθεί στο Microsoft Word, LibreOffice ή οποιονδήποτε άλλο προβολέα συμβατό με DOCX.

## Πλήρης Πηγαίος Κώδικας για Φόρτωση και Αποθήκευση Εγγράφων HTML
Για ευκολία, εδώ είναι το πλήρες, εκτελέσιμο παράδειγμα που συνδυάζει τα βήματα φόρτωσης και αποθήκευσης. Μπορείτε να το αντιγράψετε‑και‑επικολλήσετε στο IDE σας και να το εκτελέσετε όπως είναι.

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

Η εκτέλεση του κώδικα θα δημιουργήσει ένα έγγραφο Word με όνομα `WorkingWithHtmlLoadOptions.PreferredControlType.docx` που περιέχει το HTML dropdown ως ετικέτα δομημένου εγγράφου.

## Συχνά Προβλήματα & Επίλυση
| Συμπτωμα | Πιθανή Αιτία | Διόρθωση |
|---|---|---|
| Το αναπτυσσόμενο μενού εξαφανίζεται μετά την αποθήκευση | `PreferredControlType` δεν έχει οριστεί | Βεβαιωθείτε ότι η κλήση `loadOptions.setPreferredControlType(HtmlControlType.STRUCTURED_DOCUMENT_TAG);` γίνεται πριν τη φόρτωση. |
| Οι εικόνες δεν εμφανίζονται | Τα URLs των εικόνων είναι σχετικά ή μη προσβάσιμα | Χρησιμοποιήστε απόλυτα URLs ή ενσωματώστε τις εικόνες ως Base64 μέσα στη συμβολοσειρά HTML. |
| Απρόσμενη μορφοποίηση | Το CSS δεν υποστηρίζεται πλήρως | Απλοποιήστε το CSS ή χρησιμοποιήστε ενσωματωμένα στυλ· το Aspose.Words υποστηρίζει ένα υποσύνολο του CSS. |

## Συχνές Ερωτήσεις

**Ε: Πώς εγκαθιστώ το Aspose.Words for Java;**  
Α: Κατεβάστε τη βιβλιοθήκη από [εδώ](https://releases.aspose.com/words/java/) και προσθέστε τα αρχεία JAR στην classpath του έργου σας.

**Ε: Μπορώ να φορτώσω σύνθετα έγγραφα HTML (με CSS, scripts, images);**  
Α: Ναι. Το Aspose.Words μπορεί να διαχειριστεί σύνθετο HTML. Για καλύτερα αποτελέσματα, παρέχετε καλά δομημένο markup και χρησιμοποιήστε `HtmlLoadOptions` για να ρυθμίσετε τη μετατροπή.

**Ε: Ποιες άλλες μορφές μπορώ να μετατρέψω προς/από;**  
Α: Το API υποστηρίζει DOC, DOCX, RTF, PDF, HTML, EPUB, ODT και πολλές άλλες.

**Ε: Είναι το Aspose.Words κατάλληλο για μεγάλης κλίμακας, εταιρικές εγκαταστάσεις;**  
Α: Απόλυτα. Χρησιμοποιείται από επιχειρήσεις παγκοσμίως για παραγωγή εγγράφων υψηλού όγκου, αναφορές και έργα μετεγκατάστασης.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα και αναφορά API;**  
Α: Επισκεφθείτε την επίσημη τεκμηρίωση στο [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

## Συμπέρασμα
Τώρα έχετε έναν σαφή, ολοκληρωμένο οδηγό για **πώς να φορτώσετε html** σε ένα `Document` και **πώς να αποθηκεύσετε docx** χρησιμοποιώντας το Aspose.Words for Java. Αυτή η τεχνική **μετατροπής html σε docx** είναι αξιόπιστη τόσο για απλά αποσπάσματα όσο και για πλήρεις ιστοσελίδες, και η χρήση **structured document tag** εξασφαλίζει ότι τα στοιχεία φόρμας παραμένουν επεξεργάσιμα στο τελικό αρχείο Word.

---

**Τελευταία ενημέρωση:** 2026-02-24  
**Δοκιμή με:** Aspose.Words for Java 24.12 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}