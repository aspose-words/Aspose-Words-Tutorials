---
date: 2025-12-19
description: Μάθετε πώς να αποθηκεύετε το Word με κωδικό πρόσβασης, να ελέγχετε τη
  συμπίεση των μετααρχείων και να διαχειρίζεστε τις εικόνες κουκίδες χρησιμοποιώντας
  το Aspose.Words for Java.
linktitle: Saving Documents in Various Formats with
second_title: Aspose.Words Java Document Processing API
title: Αποθήκευση Word με κωδικό πρόσβασης χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-loading-and-saving/advance-saving-options/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word με κωδικό πρόσβασης και προχωρημένες επιλογές χρησιμοποιώντας το Aspose.Words για Java

## Οδηγός βήμα‑βήμα: Αποθήκευση Word με κωδικό πρόσβασης και άλλες προχωρημένες επιλογές αποθήκευσης

Στον σημερινό ψηφιακό κόσμο, οι προγραμματιστές συχνά χρειάζονται να προστατεύσουν αρχεία Word, να ελέγξουν πώς αποθηκεύονται τα ενσωματωμένα αντικείμενα ή να αφαιρέσουν ανεπιθύμητες εικόνες-κουκίδες. **Η αποθήκευση ενός εγγράφου Word με κωδικό πρόσβασης** είναι ένας απλός αλλά ισχυρός τρόπος για την ασφάλεια ευαίσθητων δεδομένων, και το Aspose.Words για Java το καθιστά αβίαστο. Σε αυτόν τον οδηγό θα περάσουμε από την κρυπτογράφηση ενός εγγράφου, την αποτροπή συμπίεσης μικρών μετααρχείων και την απενεργοποίηση picture bullets—ώστε να μπορείτε να ρυθμίσετε ακριβώς πώς αποθηκεύονται τα αρχεία Word σας.

## Γρήγορες Απαντήσεις
- **Πώς αποθηκεύω ένα έγγραφο Word με κωδικό πρόσβασης;** Χρησιμοποιήστε `DocSaveOptions.setPassword()` πριν καλέσετε `doc.save()`.  
- **Μπορώ να αποτρέψω τη συμπίεση μικρών μετααρχείων;** Ναι, ορίστε `saveOptions.setAlwaysCompressMetafiles(false)`.  
- **Μπορεί να εξαλειφθούν τα picture bullets από το αποθηκευμένο αρχείο;** Απόλυτα—χρησιμοποιήστε `saveOptions.setSavePictureBullet(false)`.  
- **Χρειάζομαι άδεια για τη χρήση αυτών των λειτουργιών;** Απαιτείται έγκυρη άδεια Aspose.Words για Java για παραγωγική χρήση.  
- **Ποια έκδοση της Java υποστηρίζεται;** Το Aspose.Words λειτουργεί με Java 8 και νεότερες.

## Τι είναι η «αποθήκευση Word με κωδικό πρόσβασης»;
Η αποθήκευση ενός εγγράφου Word με κωδικό πρόσβασης κρυπτογραφεί το περιεχόμενο του αρχείου, απαιτώντας τον σωστό κωδικό για το άνοιγμά του στο Microsoft Word ή σε οποιονδήποτε συμβατό προβολέα. Αυτή η δυνατότητα είναι ουσιώδης για την προστασία εμπιστευτικών αναφορών, συμβάσεων ή οποιουδήποτε δεδομένου που πρέπει να παραμείνει ιδιωτικό.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για Java για αυτήν την εργασία;
- **Πλήρης έλεγχος** – Μπορείτε να ορίσετε κωδικούς πρόσβασης, επιλογές συμπίεσης και διαχείριση bullets όλα σε μία κλήση API.  
- **Δεν απαιτείται Microsoft Office** – Λειτουργεί σε οποιαδήποτε πλατφόρμα που υποστηρίζει Java.  
- **Υψηλή απόδοση** – Βελτιστοποιημένο για μεγάλα έγγραφα και επεξεργασία παρτίδων.

## Προαπαιτούμενα
- Εγκατεστημένη Java 8 ή νεότερη.  
- Προσθήκη της βιβλιοθήκης Aspose.Words για Java στο έργο σας (Maven/Gradle ή χειροκίνητο JAR).  
- Έγκυρη άδεια Aspose.Words για παραγωγική χρήση (διατίθεται δωρεάν δοκιμή).

## Οδηγός βήμα‑βήμα

### 1. Δημιουργία απλού εγγράφου
Πρώτα, δημιουργήστε ένα νέο `Document` και προσθέστε κάποιο κείμενο. Αυτό θα είναι το αρχείο που θα προστατεύσουμε αργότερα με κωδικό πρόσβασης.

```java
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.write("Hello world!");
```

### 2. Κρυπτογράφηση του εγγράφου – **αποθήκευση Word με κωδικό πρόσβασης**
Τώρα ρυθμίζουμε το `DocSaveOptions` ώστε να ενσωματώνει έναν κωδικό πρόσβασης. Όταν το αρχείο ανοιχθεί, το Word θα ζητήσει αυτόν τον κωδικό.

```java
DocSaveOptions saveOptions = new DocSaveOptions();
{
    saveOptions.setPassword("password");
}
doc.save("Your Directory Path" + "EncryptedDocument.docx", saveOptions);
```

### 3. Να μην συμπιεστούν μικρά μετααρχεία
Τα μετααρχεία (όπως EMF/WMF) συχνά συμπιέζονται αυτόματα. Αν χρειάζεστε την αρχική ποιότητα, απενεργοποιήστε τη συμπίεση:

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

### 4. Εξαίρεση picture bullets από το αποθηκευμένο αρχείο
Τα picture bullets μπορούν να αυξήσουν το μέγεθος του αρχείου. Χρησιμοποιήστε την παρακάτω επιλογή για να τα παραλείψετε κατά την αποθήκευση:

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

### 5. Πλήρης κώδικας πηγής για αναφορά
Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει και τις τρεις προχωρημένες επιλογές αποθήκευσης μαζί.

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
```

## Συχνά Προβλήματα & Επίλυση
- **Ο κωδικός πρόσβασης δεν εφαρμόζεται** – Βεβαιωθείτε ότι χρησιμοποιείτε `DocSaveOptions` *αντί για* `PdfSaveOptions` ή άλλες επιλογές ειδικές για μορφές.  
- **Τα μετααρχεία εξακολουθούν να συμπιέζονται** – Ελέγξτε ότι το αρχείο προέλευσης περιέχει πράγματι μικρά μετααρχεία· η επιλογή επηρεάζει μόνο εκείνα κάτω από ένα συγκεκριμένο όριο μεγέθους.  
- **Τα picture bullets εξακολουθούν να εμφανίζονται** – Ορισμένες παλαιότερες εκδόσεις του Word αγνοούν τη σημαία· σκεφτείτε να μετατρέψετε τα bullets σε τυπικά στυλ λίστας πριν την αποθήκευση.

## Συχνές Ερωτήσεις

**Q: Είναι το Aspose.Words για Java δωρεάν βιβλιοθήκη;**  
A: Όχι, το Aspose.Words για Java είναι εμπορική βιβλιοθήκη. Μπορείτε να βρείτε λεπτομέρειες αδειοδότησης [εδώ](https://purchase.aspose.com/buy).

**Q: Πώς μπορώ να αποκτήσω δωρεάν δοκιμή του Aspose.Words για Java;**  
A: Μπορείτε να λάβετε δωρεάν δοκιμή [εδώ](https://releases.aspose.com/).

**Q: Πού μπορώ να βρω υποστήριξη για το Aspose.Words για Java;**  
A: Για υποστήριξη και συζητήσεις κοινότητας, επισκεφθείτε το [φόρουμ Aspose.Words για Java](https://forum.aspose.com/).

**Q: Μπορώ να χρησιμοποιήσω το Aspose.Words για Java με άλλα πλαίσια Java;**  
A: Ναι, ενσωματώνεται άψογα με Spring, Hibernate, Android και τα περισσότερα containers Java EE.

**Q: Υπάρχει προσωρινή άδεια για αξιολόγηση;**  
A: Ναι, μια προσωρινή άδεια είναι διαθέσιμη [εδώ](https://purchase.aspose.com/temporary-license/).

## Συμπέρασμα
Τώρα γνωρίζετε πώς να **αποθηκεύσετε Word με κωδικό πρόσβασης**, να ελέγξετε τη συμπίεση μετααρχείων και να εξαιρέσετε picture bullets χρησιμοποιώντας το Aspose.Words για Java. Αυτές οι προχωρημένες επιλογές αποθήκευσης σας δίνουν ακριβή έλεγχο του τελικού μεγέθους αρχείου, της ασφάλειας και της εμφάνισης—ιδανικό για επιχειρηματική αναφορά, αρχειοθέτηση εγγράφων ή οποιοδήποτε σενάριο όπου η ακεραιότητα του εγγράφου είναι κρίσιμη.

---

**Τελευταία ενημέρωση:** 2025-12-19  
**Δοκιμή με:** Aspose.Words για Java 24.12 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}