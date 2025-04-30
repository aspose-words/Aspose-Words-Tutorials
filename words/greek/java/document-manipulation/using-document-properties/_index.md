---
"description": "Βελτιστοποιήστε τη διαχείριση εγγράφων με το Aspose.Words για Java. Μάθετε να εργάζεστε με ιδιότητες εγγράφων, να προσθέτετε προσαρμοσμένα μεταδεδομένα και πολλά άλλα σε αυτό το ολοκληρωμένο σεμινάριο."
"linktitle": "Χρήση ιδιοτήτων εγγράφου"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Χρήση ιδιοτήτων εγγράφου στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση ιδιοτήτων εγγράφου στο Aspose.Words για Java


## Εισαγωγή στις Ιδιότητες Εγγράφου

Οι ιδιότητες εγγράφου αποτελούν ζωτικό μέρος κάθε εγγράφου. Παρέχουν πρόσθετες πληροφορίες σχετικά με το ίδιο το έγγραφο, όπως τον τίτλο, τον συγγραφέα, το θέμα, τις λέξεις-κλειδιά και άλλα. Στο Aspose.Words για Java, μπορείτε να χειριστείτε τόσο τις ενσωματωμένες όσο και τις προσαρμοσμένες ιδιότητες του εγγράφου.

## Απαρίθμηση ιδιοτήτων εγγράφου

### Ενσωματωμένες Ιδιότητες

Για να ανακτήσετε και να εργαστείτε με ενσωματωμένες ιδιότητες εγγράφου, μπορείτε να χρησιμοποιήσετε το ακόλουθο απόσπασμα κώδικα:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Αυτός ο κώδικας θα εμφανίσει το όνομα του εγγράφου και τις ενσωματωμένες ιδιότητες, συμπεριλαμβανομένων ιδιοτήτων όπως "Τίτλος", "Συγγραφέας" και "Λέξεις-κλειδιά".

### Προσαρμοσμένες Ιδιότητες

Για να εργαστείτε με προσαρμοσμένες ιδιότητες εγγράφου, μπορείτε να χρησιμοποιήσετε το ακόλουθο απόσπασμα κώδικα:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Αυτό το απόσπασμα κώδικα δείχνει πώς να προσθέσετε προσαρμοσμένες ιδιότητες εγγράφου, όπως μια λογική τιμή, μια συμβολοσειρά, μια ημερομηνία, έναν αριθμό αναθεώρησης και μια αριθμητική τιμή.

## Αφαίρεση ιδιοτήτων εγγράφου

Για να καταργήσετε συγκεκριμένες ιδιότητες εγγράφου, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Αυτός ο κώδικας καταργεί την προσαρμοσμένη ιδιότητα "Εξουσιοδοτημένη Ημερομηνία" από το έγγραφο.

## Ρύθμιση παραμέτρων σύνδεσης προς περιεχόμενο

Σε ορισμένες περιπτώσεις, ίσως θελήσετε να δημιουργήσετε συνδέσμους μέσα στο έγγραφό σας. Δείτε πώς μπορείτε να το κάνετε:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Προσθήκη ιδιότητας που συνδέεται με το περιεχόμενο.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Αυτό το απόσπασμα κώδικα δείχνει πώς να δημιουργήσετε έναν σελιδοδείκτη στο έγγραφό σας και να προσθέσετε μια προσαρμοσμένη ιδιότητα εγγράφου που συνδέεται με αυτόν τον σελιδοδείκτη.

## Μετατροπή μεταξύ μονάδων μέτρησης

Στο Aspose.Words για Java, μπορείτε να μετατρέψετε εύκολα μονάδες μέτρησης. Ακολουθεί ένα παράδειγμα για το πώς να το κάνετε:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Ορίστε περιθώρια σε ίντσες.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Αυτό το απόσπασμα κώδικα ορίζει διάφορα περιθώρια και αποστάσεις σε ίντσες μετατρέποντάς τα σε σημεία.

## Χρήση χαρακτήρων ελέγχου

Οι χαρακτήρες ελέγχου μπορούν να είναι χρήσιμοι κατά την επεξεργασία κειμένου. Δείτε πώς μπορείτε να αντικαταστήσετε έναν χαρακτήρα ελέγχου στο κείμενό σας:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Αντικαταστήστε τον χαρακτήρα ελέγχου "\r" με "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Σε αυτό το παράδειγμα, αντικαθιστούμε την επαναφορά χαρακτήρα (`\r`) με επαναφορά χαρακτήρα ακολουθούμενη από αλλαγή γραμμής (`\r\n`).

## Σύναψη

Οι ιδιότητες εγγράφων παίζουν σημαντικό ρόλο στην αποτελεσματική διαχείριση και οργάνωση των εγγράφων σας στο Aspose.Words για Java. Είτε πρόκειται για εργασία με ενσωματωμένες ιδιότητες, προσαρμοσμένες ιδιότητες είτε για χρήση χαρακτήρων ελέγχου, έχετε στη διάθεσή σας μια σειρά από εργαλεία για να βελτιώσετε τις δυνατότητες διαχείρισης εγγράφων σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να αποκτήσω πρόσβαση στις ενσωματωμένες ιδιότητες εγγράφου;

Για να αποκτήσετε πρόσβαση στις ενσωματωμένες ιδιότητες εγγράφου στο Aspose.Words για Java, μπορείτε να χρησιμοποιήσετε το `getBuiltInDocumentProperties` μέθοδος στο `Document` αντικείμενο. Αυτή η μέθοδος επιστρέφει μια συλλογή από ενσωματωμένες ιδιότητες τις οποίες μπορείτε να επαναλάβετε.

### Μπορώ να προσθέσω προσαρμοσμένες ιδιότητες εγγράφου σε ένα έγγραφο;

Ναι, μπορείτε να προσθέσετε προσαρμοσμένες ιδιότητες εγγράφου σε ένα έγγραφο χρησιμοποιώντας το `CustomDocumentProperties` συλλογή. Μπορείτε να ορίσετε προσαρμοσμένες ιδιότητες με διάφορους τύπους δεδομένων, όπως συμβολοσειρές, λογικές τιμές, ημερομηνίες και αριθμητικές τιμές.

### Πώς μπορώ να καταργήσω μια συγκεκριμένη ιδιότητα προσαρμοσμένου εγγράφου;

Για να καταργήσετε μια συγκεκριμένη ιδιότητα προσαρμοσμένου εγγράφου, μπορείτε να χρησιμοποιήσετε την `remove` μέθοδος στο `CustomDocumentProperties` συλλογή, μεταβιβάζοντας το όνομα της ιδιότητας που θέλετε να καταργήσετε ως παράμετρο.

### Ποιος είναι ο σκοπός της σύνδεσης με περιεχόμενο εντός ενός εγγράφου;

Η σύνδεση με περιεχόμενο εντός ενός εγγράφου σάς επιτρέπει να δημιουργείτε δυναμικές αναφορές σε συγκεκριμένα μέρη του εγγράφου. Αυτό μπορεί να είναι χρήσιμο για τη δημιουργία διαδραστικών εγγράφων ή διασταυρούμενων αναφορών μεταξύ ενοτήτων.

### Πώς μπορώ να μετατρέψω διαφορετικές μονάδες μέτρησης στο Aspose.Words για Java;

Μπορείτε να μετατρέψετε μεταξύ διαφορετικών μονάδων μέτρησης στο Aspose.Words για Java χρησιμοποιώντας το `ConvertUtil` κλάση. Παρέχει μεθόδους για τη μετατροπή μονάδων όπως ίντσες σε σημεία, σημεία σε εκατοστά και άλλα.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}