---
title: Χρήση ιδιοτήτων εγγράφου στο Aspose.Words για Java
linktitle: Χρήση ιδιοτήτων εγγράφου
second_title: Aspose.Words Java Document Processing API
description: Βελτιστοποιήστε τη διαχείριση εγγράφων με το Aspose.Words για Java. Μάθετε να εργάζεστε με ιδιότητες εγγράφων, να προσθέτετε προσαρμοσμένα μεταδεδομένα και πολλά άλλα σε αυτό το περιεκτικό σεμινάριο.
weight: 32
url: /el/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση ιδιοτήτων εγγράφου στο Aspose.Words για Java


## Εισαγωγή στις ιδιότητες του εγγράφου

Οι ιδιότητες εγγράφων αποτελούν ζωτικό μέρος οποιουδήποτε εγγράφου. Παρέχουν πρόσθετες πληροφορίες σχετικά με το ίδιο το έγγραφο, όπως τίτλο, συγγραφέα, θέμα, λέξεις-κλειδιά και άλλα. Στο Aspose.Words για Java, μπορείτε να χειριστείτε τόσο τις ενσωματωμένες όσο και τις προσαρμοσμένες ιδιότητες εγγράφου.

## Απαρίθμηση ιδιοτήτων εγγράφου

### Ενσωματωμένες ιδιότητες

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

Αυτός ο κώδικας θα εμφανίζει το όνομα του εγγράφου και τις ενσωματωμένες ιδιότητες, συμπεριλαμβανομένων ιδιοτήτων όπως "Τίτλος", "Συγγραφέας" και "Λέξεις-κλειδιά".

### Προσαρμοσμένες ιδιότητες

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

Αυτό το απόσπασμα κώδικα δείχνει πώς μπορείτε να προσθέσετε προσαρμοσμένες ιδιότητες εγγράφου, συμπεριλαμβανομένης μιας boolean τιμής, μιας συμβολοσειράς, μιας ημερομηνίας, ενός αριθμού αναθεώρησης και μιας αριθμητικής τιμής.

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

Αυτός ο κωδικός αφαιρεί την προσαρμοσμένη ιδιότητα "Authorized Date" από το έγγραφο.

## Διαμόρφωση συνδέσμου προς περιεχόμενο

Σε ορισμένες περιπτώσεις, μπορεί να θέλετε να δημιουργήσετε συνδέσμους μέσα στο έγγραφό σας. Δείτε πώς μπορείτε να το κάνετε:

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

    // Προσθήκη συνδεδεμένου με την ιδιοκτησία περιεχομένου.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Αυτό το απόσπασμα κώδικα δείχνει πώς να δημιουργήσετε έναν σελιδοδείκτη στο έγγραφό σας και να προσθέσετε μια προσαρμοσμένη ιδιότητα εγγράφου που συνδέεται με αυτόν τον σελιδοδείκτη.

## Μετατροπή μεταξύ μονάδων μέτρησης

Στο Aspose.Words για Java, μπορείτε εύκολα να μετατρέψετε μονάδες μέτρησης. Ακολουθεί ένα παράδειγμα για το πώς να το κάνετε:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Ορίστε τα περιθώρια σε ίντσες.
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

Οι χαρακτήρες ελέγχου μπορεί να είναι χρήσιμοι όταν ασχολείστε με κείμενο. Δείτε πώς μπορείτε να αντικαταστήσετε έναν χαρακτήρα ελέγχου στο κείμενό σας:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Αντικαταστήστε τον χαρακτήρα ελέγχου "\r" με "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Σε αυτό το παράδειγμα, αντικαθιστούμε την επιστροφή μεταφοράς (`\r`) με επιστροφή μεταφοράς ακολουθούμενη από τροφοδοσία γραμμής (`\r\n`).

## Σύναψη

Οι ιδιότητες εγγράφων διαδραματίζουν σημαντικό ρόλο στη διαχείριση και την αποτελεσματική οργάνωση των εγγράφων σας στο Aspose.Words για Java. Είτε λειτουργεί με ενσωματωμένες ιδιότητες, προσαρμοσμένες ιδιότητες ή χρησιμοποιώντας χαρακτήρες ελέγχου, έχετε στη διάθεσή σας μια σειρά εργαλείων για να βελτιώσετε τις δυνατότητες διαχείρισης εγγράφων σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να αποκτήσω πρόσβαση στις ενσωματωμένες ιδιότητες εγγράφου;

 Για πρόσβαση στις ενσωματωμένες ιδιότητες εγγράφου στο Aspose.Words για Java, μπορείτε να χρησιμοποιήσετε το`getBuiltInDocumentProperties` μέθοδος στο`Document` αντικείμενο. Αυτή η μέθοδος επιστρέφει μια συλλογή από ενσωματωμένες ιδιότητες που μπορείτε να επαναλάβετε.

### Μπορώ να προσθέσω προσαρμοσμένες ιδιότητες εγγράφου σε ένα έγγραφο;

 Ναι, μπορείτε να προσθέσετε προσαρμοσμένες ιδιότητες εγγράφου σε ένα έγγραφο χρησιμοποιώντας το`CustomDocumentProperties` συλλογή. Μπορείτε να ορίσετε προσαρμοσμένες ιδιότητες με διάφορους τύπους δεδομένων, συμπεριλαμβανομένων συμβολοσειρών, booleans, ημερομηνιών και αριθμητικών τιμών.

### Πώς μπορώ να καταργήσω μια συγκεκριμένη ιδιότητα προσαρμοσμένου εγγράφου;

 Για να καταργήσετε μια συγκεκριμένη ιδιότητα προσαρμοσμένου εγγράφου, μπορείτε να χρησιμοποιήσετε το`remove` μέθοδος στο`CustomDocumentProperties`συλλογή, μεταβιβάζοντας ως παράμετρο το όνομα της ιδιότητας που θέλετε να καταργήσετε.

### Ποιος είναι ο σκοπός της σύνδεσης με περιεχόμενο εντός ενός εγγράφου;

Η σύνδεση με το περιεχόμενο ενός εγγράφου σάς επιτρέπει να δημιουργείτε δυναμικές αναφορές σε συγκεκριμένα μέρη του εγγράφου. Αυτό μπορεί να είναι χρήσιμο για τη δημιουργία διαδραστικών εγγράφων ή παραπομπών μεταξύ των ενοτήτων.

### Πώς μπορώ να κάνω μετατροπή μεταξύ διαφορετικών μονάδων μέτρησης στο Aspose.Words για Java;

 Μπορείτε να κάνετε μετατροπή μεταξύ διαφορετικών μονάδων μέτρησης στο Aspose.Words για Java χρησιμοποιώντας το`ConvertUtil` τάξη. Παρέχει μεθόδους μετατροπής μονάδων όπως ίντσες σε σημεία, σημεία σε εκατοστά και πολλά άλλα.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
