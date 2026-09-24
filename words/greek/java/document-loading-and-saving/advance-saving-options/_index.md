---
date: 2026-02-22
description: Μάθετε πώς να αποθηκεύετε έγγραφα Word με κωδικό πρόσβασης και να χρησιμοποιείτε
  προχωρημένες επιλογές αποθήκευσης, όπως η διαχείριση μετααρχείων και ο έλεγχος εικόνων‑κουκίδων,
  με το Aspose.Words for Java.
linktitle: Saving Documents in Various Formats with
second_title: Aspose.Words Java Document Processing API
title: Αποθήκευση Word με κωδικό πρόσβασης και προχωρημένες επιλογές – Aspose.Words
  για Java
url: /el/java/document-loading-and-saving/advance-saving-options/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word με Κωδικό Πρόσβασης και Προηγμένες Επιλογές – Aspose.Words for Java

Σε σύγχρονες εφαρμογές Java, η **αποθήκευση Word με κωδικό πρόσβασης** είναι συχνή απαίτηση για την προστασία ευαίσθητου περιεχομένου. Το Aspose.Words for Java όχι μόνο επιτρέπει την κρυπτογράφηση εγγράφων, αλλά προσφέρει επίσης λεπτομερή έλεγχο της συμπίεσης μετααρχείων, των εικόνων‑κουκίδων και πολλών άλλων λειτουργιών αποθήκευσης. Σε αυτό το βήμα‑βήμα tutorial θα εξετάσουμε τις πιο χρήσιμες *προηγμένες επιλογές αποθήκευσης* που μπορείτε να εφαρμόσετε με το Aspose.Words Java API.

## Γρήγορες Απαντήσεις
- **Πώς προσθέτω κωδικό πρόσβασης σε αρχείο Word;** Χρησιμοποιήστε `DocSaveOptions.setPassword("yourPassword")` πριν καλέσετε `doc.save()`.  
- **Μπορώ να αποτρέψω τη συμπίεση μετααρχείων;** Ορίστε `saveOptions.setAlwaysCompressMetafiles(false)`.  
- **Είναι δυνατόν να εξαιρέσω τις εικόνες‑κουκίδες;** Ναι, καλέστε `saveOptions.setSavePictureBullet(false)`.  
- **Χρειάζεται άδεια για αυτές τις λειτουργίες;** Μια δοκιμαστική έκδοση λειτουργεί για αξιολόγηση· απαιτείται εμπορική άδεια για παραγωγή.  
- **Ποιο προϊόν Aspose καλύπτει αυτό;** Aspose.Words for Java — η κορυφαία βιβλιοθήκη για **aspose words document saving** εργασίες.

## Τι είναι η “αποθήκευση Word με κωδικό πρόσβασης”;
Η αποθήκευση ενός εγγράφου Word με κωδικό πρόσβασης σημαίνει κρυπτογράφηση του αρχείου ώστε μόνο οι χρήστες που γνωρίζουν τον κωδικό να μπορούν να το ανοίξουν, να το επεξεργαστούν ή να το εκτυπώσουν. Αυτό το επίπεδο ασφαλείας είναι απαραίτητο για εμπιστευτικές αναφορές, συμβάσεις ή οποιαδήποτε δεδομένα πρέπει να παραμείνουν ιδιωτικά.

## Γιατί να χρησιμοποιήσετε τις δυνατότητες αποθήκευσης του Aspose.Words;
Το Aspose.Words παρέχει ένα πλούσιο σύνολο **aspose words document saving** επιλογών που υπερβαίνουν την απλή εξαγωγή αρχείου. Μπορείτε να ελέγχετε τη συμπίεση, τη διαχείριση εικόνων και ακόμη να αποφασίσετε αν θα ενσωματώσετε εικόνες‑κουκίδες—όλα χωρίς να αφήσετε τον κώδικα Java.

## Προαπαιτούμενα
- Εγκατεστημένο Java 8 ή νεότερο.  
- Βιβλιοθήκη Aspose.Words for Java προστεθειμένη στο έργο σας (Maven/Gradle ή χειροκίνητο JAR).  
- Βασική εξοικείωση με IDE Java (IntelliJ, Eclipse κ.λπ.).

## Οδηγός Βήμα‑Βήμα

### Βήμα 1: Δημιουργία απλού εγγράφου
Πρώτα, δημιουργούμε ένα νέο `Document` και προσθέτουμε κάποιο κείμενο. Αυτό θα είναι το βασικό αρχείο που θα προστατεύσουμε αργότερα με κωδικό.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Hello world!");
```

### Βήμα 2: Αποθήκευση Word με κωδικό πρόσβασης
Τώρα κρυπτογραφούμε το έγγραφο. Το αντικείμενο `DocSaveOptions` μας επιτρέπει να ορίσουμε τον κωδικό και άλλες προτιμήσεις αποθήκευσης.

```java
DocSaveOptions saveOptions = new DocSaveOptions();
{
    saveOptions.setPassword("password");
}
doc.save("Your Directory Path" + "EncryptedDocument.docx", saveOptions);
```

> **Συμβουλή επαγγελματία:** Αποθηκεύετε τους κωδικούς με ασφάλεια (π.χ., σε θυρίδα) και ποτέ μην τους κωδικοποιείτε σκληρά στον κώδικα παραγωγής.

### Βήμα 3: Μη συμπίεση μικρών μετααρχείων
Αν το έγγραφό σας περιέχει διανυσματικά γραφικά (π.χ., αντικείμενα εξισώσεων), μπορεί να προτιμάτε να τα αφήσετε ασυμπίεστα για καλύτερη ποιότητα. Το παρακάτω παράδειγμα απενεργοποιεί την αυτόματη συμπίεση.

```java
@Test
public void doNotCompressSmallMetafiles() throws Exception {
    Document doc = new Document("Your Directory Path" + "Microsoft equation object.docx");
    DocSaveOptions saveOptions = new DocSaveOptions();
    {
        saveOptions.setAlwaysCompressMetafiles(false);
    }
    doc.save("Your Directory Path" + "NotCompressedMetafiles.docx", saveOptions);
}
```

### Βήμα 4: Εξαίρεση εικόνων‑κουκίδων από το αποθηκευμένο αρχείο
Οι εικόνες‑κουκίδες μπορούν να αυξήσουν το μέγεθος του αρχείου. Αν δεν τις χρειάζεστε, απενεργοποιήστε τες με `setSavePictureBullet(false)`.

```java
@Test
public void doNotSavePictureBullet() throws Exception {
    Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
    DocSaveOptions saveOptions = new DocSaveOptions();
    {
        saveOptions.setSavePictureBullet(false);
    }
    doc.save("Your Directory Path" + "NoPictureBullet.docx", saveOptions);
}
```

### Βήμα 5: Πλήρης κώδικας για αναφορά
Παρακάτω βρίσκεται ο πλήρης, εκτελέσιμος κώδικας που δείχνει όλες τις τρεις προχωρημένες επιλογές αποθήκευσης μαζί.

```java
public void encryptDocumentWithPassword() throws Exception {
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.write("Hello world!");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setPassword("password");
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.EncryptDocumentWithPassword.docx", saveOptions);
}
@Test
public void doNotCompressSmallMetafiles() throws Exception {
	Document doc = new Document("Your Directory Path" + "Microsoft equation object.docx");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setAlwaysCompressMetafiles(false);
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.NotCompressSmallMetafiles.docx", saveOptions);
}
@Test
public void doNotSavePictureBullet() throws Exception {
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	DocSaveOptions saveOptions = new DocSaveOptions();
	{
		saveOptions.setSavePictureBullet(false);
	}
	doc.save("Your Directory Path" + "WorkingWithDocSaveOptions.DoNotSavePictureBullet.docx", saveOptions);
}
```

## Συνηθισμένα Προβλήματα και Συμβουλές
| Πρόβλημα | Αιτία | Λύση |
|----------|-------|------|
| **Το έγγραφο ανοίγει αλλά ο κωδικός αγνοείται** | Χρήση `saveOptions` με διαφορετικό `SaveFormat` | Βεβαιωθείτε ότι περνάτε το ίδιο αντικείμενο `DocSaveOptions` στο `doc.save()` και ότι η επέκταση αρχείου ταιριάζει με τη μορφή (π.χ., `.docx`). |
| **Τα μετααρχεία παραμένουν συμπιεσμένα** | `setAlwaysCompressMetafiles` επηρεάζει μόνο *μικρά* μετααρχεία | Ελέγξτε το μέγεθος του μετααρχείου· τα μεγάλα συμπιέζονται πάντα σύμφωνα με το πρότυπο DOCX. |
| **Οι εικόνες‑κουκίδες εξακολουθούν να εμφανίζονται** | Το έγγραφο περιέχει ενσωματωμένες εικόνες που χρησιμοποιούνται ως κουκίδες | Μετατρέψτε αυτές τις κουκίδες σε τυπικά στυλ λίστας πριν την αποθήκευση ή αφαιρέστε τες χειροκίνητα μέσω του API. |

## Συχνές Ερωτήσεις

**Ε: Είναι το Aspose.Words for Java δωρεάν;**  
Α: Όχι, το Aspose.Words for Java είναι εμπορική βιβλιοθήκη. Μπορείτε να βρείτε λεπτομέρειες αδειοδότησης [εδώ](https://purchase.aspose.com/buy).

**Ε: Πώς μπορώ να αποκτήσω δωρεάν δοκιμή του Aspose.Words for Java;**  
Α: Μπορείτε να λάβετε δωρεάν δοκιμή του Aspose.Words for Java [εδώ](https://releases.aspose.com/).

**Ε: Πού μπορώ να βρω υποστήριξη για το Aspose.Words for Java;**  
Α: Για υποστήριξη και συζητήσεις κοινότητας, επισκεφθείτε το [φόρουμ Aspose.Words for Java](https://forum.aspose.com/).

**Ε: Μπορώ να χρησιμοποιήσω το Aspose.Words for Java με άλλες βιβλιοθήκες Java;**  
Α: Ναι, το Aspose.Words for Java είναι συμβατό με διάφορες βιβλιοθήκες και πλαίσια Java.

**Ε: Υπάρχει διαθέσιμη προσωρινή άδεια;**  
Α: Ναι, μπορείτε να αποκτήσετε προσωρινή άδεια [εδώ](https://purchase.aspose.com/temporary-license/).

## Πρόσθετες Συχνές Ερωτήσεις

**Ε: Επηρεάζει η προστασία με κωδικό το μέγεθος του εγγράφου;**  
Α: Το κρυπτογραφημένο αρχείο είναι ελαφρώς μεγαλύτερο λόγω του φορτίου κρυπτογράφησης, αλλά η αύξηση είναι συνήθως αμελητέα.

**Ε: Μπορώ να ορίσω διαφορετικούς κωδικούς για ανάγνωση‑μόνο και επεξεργασία;**  
Α: Το Aspose.Words υποστηρίζει έναν μόνο κωδικό για το άνοιγμα του εγγράφου. Για πιο λεπτομερή δικαιώματα, σκεφτείτε τη μετατροπή σε PDF με ξεχωριστές ρυθμίσεις προστασίας.

**Ε: Διατίθενται αυτές οι επιλογές αποθήκευσης για όλες τις μορφές Word (DOC, DOCX, RTF);**  
Α: Ναι, το `DocSaveOptions` λειτουργεί με όλες τις μορφές που υποστηρίζει το Aspose.Words, αν και ορισμένες επιλογές είναι ειδικές για μορφές (π.χ., οι εικόνες‑κουκίδες αφορούν μόνο DOCX).

---

**Τελευταία ενημέρωση:** 2026-02-22  
**Δοκιμασμένο με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}