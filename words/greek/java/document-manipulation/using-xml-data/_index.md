---
date: 2026-01-24
description: Μάθετε πώς να συγχωνεύετε δεδομένα XML με το Aspose.Words for Java, να
  αυτοματοποιείτε τη δημιουργία εγγράφων Java και να χρησιμοποιείτε τη σύνταξη Mustache
  για δυναμικά έγγραφα.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Πώς να συγχωνεύσετε XML στο Aspose.Words για Java
url: /el/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Συγχωνεύσετε XML στο Aspose.Words για Java

Σε αυτόν τον ολοκληρωμένο οδηγό θα ανακαλύψετε **πώς να συγχωνεύετε δεδομένα XML** χρησιμοποιώντας το Aspose.Words για Java. Θα περάσουμε από βασικά και ένθετα σενάρια συγχώνευσης αλληλογραφίας, θα σας δείξουμε πώς να **χρησιμοποιείτε τη σύνταξη Mustache**, και θα εξηγήσουμε πώς να **αυτοματοποιήσετε τη δημιουργία εγγράφων σε έργα Java**. Στο τέλος, θα μπορείτε να δημιουργείτε εξατομικευμένα έγγραφα Word απευθείας από πηγές XML με λίγες μόνο γραμμές κώδικα.

## Γρήγορες Απαντήσεις
- **Ποια είναι η κύρια κλάση για τη συγχώνευση αλληλογραφίας;** `Document` και η ιδιότητα `MailMerge`.  
- **Μπορώ να συγχωνεύσω ένθετους πίνακες XML;** Ναι – χρησιμοποιήστε `executeWithRegions` για ιεραρχικά δεδομένα.  
- **Υποστηρίζεται η σύνταξη Mustache;** Ενεργοποιήστε την με `setUseNonMergeFields(true)`.  
- **Χρει Απαιτείται εμπορική άδεια Aspose.Words.  
- **Ποια έκδοση Java είναιση XML Αλληλογραφίας στο Aspose.Words;
Η συγχώνευση.Words γιαμένων σε XML;
- **Αυτοματοποιήστε τη δημιουργία εγγράφων Java** έργων χωρίς εξαρτήσεις από το Microsoft Office.  
- **Υποστήριξη για σύνθετες ιεραρχίες** – ένθετοι πίνακες, επαναλαμβανόμενες ενότητες και υπό όρους περιεχόμενο.  
ωση.  
- **Διαπλατφορμική** – λειτουργεί σε Windows, Linux και macOS.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τα εξής:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) εγκατεστημένο (την πιο πρόσχεία XML για πελάτες, παραγγελίες και προμηθευτές (το tutorial χρησιμοποιεί `Mail merge data - Customers.xml`, `Orders.xml` και `Vendors.xml`).  
- Πρότυπα εγγράφων Word που περιέχουν πεδία συγχώνευσης (π.χ. `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Πώς να Συγχωνεύσετε XML – Βλέφο.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Συμβουλή:** Κρατήστε τη δομή του XML επίπεδη για απλές συγχωνεύσεις – κάθε πίνακας πρέπει να αντιστοιχεί απευθείας σε ένα σύνολο πεδίων συγχώνευσης.

## Πώς να Συγχωνεύσετε XML – Ένθετη Συγχώνευση Α περιέχει σχέσεις γονέα‑παιδίου (π.χ. παραγγελίες με στοιχεία γραμμής), χρειάζεστε μια ένθετη συγχώνευση. Η μέθοδος `executeWithRegions` επεξεργάζεται κάθε περιοχή αναδρομικά.

1. Φορτώστε το ιεραρχικό XML σε ένα `DataSet`.  
2. Απενεργοποιήστε την αριστείτε όλους τους ένθετους πίνακες.  
4. Αποθηκεύστε το αποτέλεσμα.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Κοινό λάθος:** Η παράσεις{{Customer1. Φορτώστε το XML του προμηθευτή.  
2. Ενεργοποιήστε την υποστήριξη Mustache με `setUseNonMergeFields(true)`.  
3. Εκτελέστε τη συγχώνευση με περιοχές.  
4. Αποθηκεύστε το αποτέλεσμα.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Γιατί να χρησιμοποιήσετε Mustache;** Παρέχει έναν καθαρό, γλωσσικά ανεξάρτητο τρόπο αναφοράς δεδομένων, καθιστώντας τα πρότυπά σας πιο ευανάγνωστα και εύκολα στη συντήρηση, ειδικά όταν **δημιουργείτε έγγραφα με βάση XML**.

## Συνη| Πρόβλημα | Λύση |
|----------|------|
| Οι κόμβοι XML δεν ταιριάζουν με τα πεδία συγχώνευσης | Βεβαιωθείτε ότι τα ονόματα των στοιχείων XML ταιριάζουν ακριβώς με τα ονόματα των πεδίων συγχώνευσης (διάκριση πεζών‑κεφαλαίων). |
| Εμφανίζονται κενά γύρω από τις συγχωνευμένες τιμές | Χρησιμοποιήστε `doc.getMailMerge().setTrimWhitespaces(false η περιοχή του γονικού XML γιαίας;

Βεβαιωθείτε ότι το XML ακολουθεί μια δομή πίνακα όπου κάθε στοιχείο `<TableName>` περιέχει γραμμές (`<Row>`) και στήλες που αντιστοιχούν στα πεδία συγχώνευσης του προτύπου Word.

### Μπορώ να προσαρμόσω τη συμπεριφορά αφαίρε)`λικά κενά όπως εμφανίζονται στο XML.

### Τι είναι η σύνταξη Mustache και πότε πρέπει να τη χρησιμοποιήσω;

Η σύνταξη Mustache (`{{FieldName}}`) επιτρέπει ευέλικτες θέσεις κράτησης που δεν περιορίζονται στα παραδοσιακά πεδία συγχώνευσης. Ενεργοποιήστε τη με `setUseNonMergeFields(true)` όταν χρειάζεστε καθαρότερο πρότυπο ή θέλετε να διαχωρίσετε τη λογική δεδομένων από τους κωδικούς πεδίων του Word.

### Πώς μπορώ να αυτοματοποιήσω τη δημιουργία εγγράφων σε έργα Java με αυτήν την προσέγγιση;

Ενσωματώστε τα παραπάνω αποσπάσματα κώδικα στο επίπεδο υπηρεσίας σας, διαβάστε XML από βάσεις δεδομένων ή API, και καλέστε τη ρουτίνα συγχώνευσης όποτε απαιτείται νέο έγγραφο (π.χ. δημιουργία τιμολογίου, σύναψη σύμβασης).

### Απαιτείται εμπορική άδεια για παραγωγική χρήση;

Ναι, το Aspose.Words απαιτεί έγκυρη άδεια για παραγωγικές εγκαταστάσεις. Διατίθεται δωρεάν προσωρινή άδεια για αξιολόγηση.

---

**Τελευταία ενημέρωση:** 2026-01-24  
**Δοκιμασμένο με:** Aspose.Words for Java (τελευταία έκδοση)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}