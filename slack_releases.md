# Instacar Releases Log
*Extracted from Slack #releases channel*

---

### Ilias Samartzis
* **Instafleet > My Tasks:** Προστέθηκε και το Mailbox! Μπορείτε να βλέπετε τις επικοινωνίες που είναι assigned σε εσας απευθείας από τον πίνακα “My Tasks”, στο tab “Mailbox”, καθώς και να φιλτράρετε ανάλογα, όπως στο Unified View.
* **Unified View / My Tasks > Mailbox:** Αλλαγές σε Team/Assignee/Status πλέον εφαρμόζονται συνολικά στο εκάστοτε Thread ώστε να ενημερώνονται σωστά οι Agents αλλά και το “My Tasks” board. Διορθώθηκε ένα bug στο οποίο λανθασμένα καταγράφονταν κινήσεις σε “Done” Tickets.
* **WWW > Leasing:** Προστέθηκε φίλτρο “Τύπος συνδρομής” (Contract Period).
* **Predel Candidates:** Νέο Tab στο Availability Table (“Predel”) που φέρνει τα καλύτερα υποψήφια οχήματα για προπαράδοση βάσει χιλιομέτρων.
* **Changelog:** Καταγράφονται πλέον οι χρήστες (Agents) που κάνουν αλλαγές στο Changelog των οχημάτων αντί για “System”.
* **Reset Delivery/Return Plan:** Δυνατότητα εκκαθάρισης ενός Delivery ή Return Plan (από Admins) μέσω του overflow menu στο Subscription.
* **Global Search - Subscription Results Redesign:** Τα αποτελέσματα συνδρομών εμφανίζουν πλέον: User Name, Brand, Model, Plate ID, Sub ID, Subscription Type, Subscription Status.
* **Predel/Temp via 1 Button:** Προστέθηκε το πεδίο “Promised Delivery Date”.
* **My Tasks / Generic Ticket:** Οι Agents μπορούν να προσαρμόσουν τις θέσεις των στηλών.
* **ERFUDD Alerts:** Προστέθηκε φίλτρο και σήμανση (πορτοκαλί χρώμα) για περιπτώσεις όπου το ERFUDD ενός οχήματος είναι μικρότερο των 10 ημερών από το Promised Delivery Date (στα Subscriptions και Reservations).
* **SKU’s - Category Class:** Νέο πεδίο στο Properties > Miscellaneous, Vehicle Page > Information, και ως στήλη/φίλτρο στο Fleet/Catalog.
* **Sell Requests:** Προστέθηκαν στήλες Vehicle Ownership + Financing Provider.
* **Βεβαίωση Λιανικής Τιμής Προ Φόρων:** Διαθέσιμο στο MY/App (μόνο για Owner/Admin).
* **Team Signatures:** Δυνατότητα επιλογής Team Signature όταν στέλνετε e-mail μέσω του Unified View.
* **Booking Agent στα Subscriptions:** Προστέθηκε ο Booking Agent (Pipedrive Deal Owner).
* **Campaign Duration field:** Προστέθηκε πεδίο “Duration” (μήνες) κατα τη δημιουργία καμπάνιας.
* **Send Email via Booking/Subscription:** Δυνατότητα αποστολής Email απευθείας από Booking/Subscription με pre-filled παραλήπτη τον User/Owner.
* **Logistics Table - Date Of Completion:** Καταγράφεται η ημερομηνία/ώρα (Completed At) όταν το task περνάει σε Status = Done.
* **Export Subscriptions (Bundles):** Νέο Export option που περιλαμβάνει και τα Bundles (σε extra rows).
* **TIN at Subscriptions:** Στήλη ΑΦΜ (TIN) προστέθηκε στο Subscriptions Table και στα exports.
* **User's Media:** Δυνατότητα ανεβάσματος αρχείων τύπου "Other".
* **Generic Tickets:** Προσθήκη επιλογής "Extra Documents" στο Ticket Reason.
* **Car History - AR&M:** Προστέθηκε πεδίο "Reason" των ARM Tickets στο preview. Βελτιώθηκε η μορφή του ID (π.χ. [PlateID]_[ReasonPrefix][5-digit Number]).
* **Unified View - Connect Mail to Booking/Subscription:** Νέο πεδίο σύνδεσης email με συγκεκριμένο Booking ή Subscription του User (ή Unrelated/Other).
* **Monthly Fee Campaign:** Νέο Product που προσαρμόζεται βάσει καμπάνιας. Μπαίνει αυτόματα από το Booking Creation, δημιουργείται στο Pipedrive, και το offer.pdf δείχνει τη μειωμένη τιμή με disclaimer.
* **Bookings - Car ID Validation:** Το πεδίο αναζητά το Car ID στο Availability Table για αποφυγή λαθών.
* **Bookings - 2 new Stages:** Προστέθηκαν τα "Sales Pending" και "Credit Pending" μετά το Docs Received για άμεση επικοινωνία Sales & Credit. 

---

### Alexandros Galanis
* **Predel/Temp Creation via 1 Button:** Δυνατότητα δημιουργίας συνδρομής (Temp/Predel) μέσω του User Page. Συμπληρώνοντας το Sub ID, Car ID, Pipedrive Stage, και Fee, δημιουργείται αυτόματα Booking, Deal, και Subscription.
* **Assignees in Subscriptions:** Το πεδίο “Assignee” προστέθηκε στις συνδρομές (General Tab, Column, Filter).
* **Car History:** Προστέθηκε Changelog, Tasks, και Notes. Στη συνέχεια προστέθηκε πλήρης υποστήριξη στα Notes (CRUD) και φίλτρα στο Changelog (erfudd, reservation type, availability status).
* **Email Templates στο Unified View Reply:** Προστέθηκε κουμπί “Templates” για εισαγωγή προκαθορισμένων απαντήσεων (με επιλογή γλώσσας).
* **Search V2:** Νέα έκδοση αναζήτησης στο Instafleet (ως switch option αρχικά).
* **Credit Mailbox:** Προστέθηκε το credit@instacar.gr mailbox στο Unified View.
* **Promised Delivery Date:** Νέο πεδίο σε Reservations και Bookings με αυτόματο συγχρονισμό.
* **Labels στο Booking Creation:** Νέες επιλογές στο modal (Renewal, Change Contract, Car Swap, Predel, Temp, RAC).
* **Post-payment emails merge:** Ενοποιήθηκαν τα emails Select Delivery Method και Invite Additional Drivers σε ένα ενιαίο flow.
* **Νέα φίλτρα στο Subscriptions:** Προστέθηκαν τα Procurement Stage, Vehicle Reservation Type, Vehicle Availability Status (ως Quick Filters), Planned Downpayment Date, ERFUDD, Created at (στο Custom Modal).
* **No Answer Automation:** Το automation για "No Answer" μεταφέρθηκε στο Instafleet (αποστέλλει αυτόματα email και SMS, βάσει της γλώσσας του πελάτη, με προστασία από διπλές αποστολές).

---

### Dimitris Galanis
* **Generic ticket:** Απλό task στο sidebar όπου μπορεί κανείς να σημειώσει αιτήματα πελατών. Περιλαμβάνει User Search, Sub Search, Assignee (default current user), Ticket type & description. Εμφανίζεται στο My Tasks.
* **ARM ticket in side bar:** Δυνατότητα δημιουργίας ARM Maintenance ticket.
* **Tires data (Fragoulopoulos):** Όλα τα data για ελαστικά είναι διαθέσιμα στο Marketplace -> Tires. Update κάθε 10 λεπτά, δυναμικές στήλες και φίλτρα.
* **Generic ticket (Updates):** Προσθήκη Team και Due Date. Αργότερα προστέθηκαν πεδία Priority και Reason. Μεγάλωσε το πεδίο Description για ευκολότερο scroll.
* **Instacar Premium:** Κυκλοφόρησε το MVP του Instacar Premium στο Instafleet (αρχικά για την ομάδα πωλήσεων).
* **Unified view - Compose email:** Δυνατότητα Compose (Νέου email) απευθείας από το Unified View -> Mailboxes (με πολλαπλούς παραλήπτες, Cc/Bcc, και signatures).
* **Generic ticket - Export:** Δυνατότητα export data (φιλτραρισμένων ή μη) από τη σελίδα των generic tickets.
* **Booking Creation Modal:** Προστέθηκαν "12ος" και "24ος" στο πεδίο Extra months. Consent buttons έγιναν default TRUE.
* **Total Initial Costs banner:** Προστέθηκε banner συνολικού αρχικού κόστους στο Booking και Booking creation modal.
* **Linked Items:** Στα Subscriptions, το "Linked Subscriptions" μετονομάστηκε σε "Linked Items" (Περιλαμβάνει Predel/Temp, αρχικό Booking, ARM tickets, και Generic tickets).
* **Referral Coupon MVP:** Σε νέα bookings/offers προστίθεται κουπόνι (βάσει του booking ID) όπου τρίτος λαμβάνει 500€ έκπτωση, και αν ολοκληρωθεί αγορά, ο πελάτης κερδίζει αφαίρεση 1 μήνα.
* **Create new labels in Bookings:** Δυνατότητα δημιουργίας custom labels μέσω του UI στα bookings.

---

### Dimosthenis Avgeris
* **DriveHome Pricing:** Ενημερώθηκαν οι τιμές για όλες τις κατηγορίες (διαθέσιμες στο site).
* **SEO Μεταχειρισμένων:** Νέες κατηγορίες σελίδων (14 σύνολο) και ενημερωμένα metadata (Landing, Listing, Brand, Product pages).
* **VAT Finder tool:** Νέα πεδία (Ενεργός/Ανενεργός ΑΦΜ, Φυσικό/Μη Φυσικό Πρόσωπο, Αναλυτική διεύθυνση).
* **Billing Boards Export:** Ολοκληρώθηκε το Export στα 5 boards (Billing-instacar, instaride, Refunds, Damages, Other).
* **Lost Flow στο Instafleet:** Νέο κουμπί "Lost" στο booking detail page. Όλα τα πεδία γίνονται read-only. Δυνατότητα "Reopen".

---

### Kanella Dionysopoulou
* **Bookings Kanban Redesign:** Νέο compact design (τα ονόματα κόβονται σε 1 γραμμή), πάνελ "Choose Card Infos" (απόκρυψη/εμφάνιση πεδίων), "Choose Stages", και χρωματικά chips ανά τύπο (Fixed, Open, Predel, Temp, RAC). 

---

### Vangelis Papangelis
* **iOS Release 3.4.2:** Ανανεωμένο Checkout (sticky bottom CTA), UI Polish (Sale details), επίλυση προβλημάτων πλοήγησης και flickering, διόρθωση λίστας deliverables στις συνδρομές, και συμβατότητα με iOS 26.
* **iOS Release 3.5.1:**
  * **Private Vehicles:** Πλήρης υλοποίηση του flow για τα ιδιωτικά οχήματα! Πλέον οι χρήστες μπορούν να προσθέσουν το δικό τους όχημα (Private Vehicle creation), να συμπληρώσουν επιπλέον στοιχεία (π.χ. VIN, έγγραφα), και να διαχειριστούν το όχημά τους μέσα από τη νέα σελίδα λεπτομερειών (Vehicle Details Page).
  * **Login & Account Management:** Προσθήκη λειτουργικότητας Login και υλοποίηση της δυνατότητας διαγραφής λογαριασμού (Delete request).
  * **UI/UX Βελτιώσεις:**
    * Αντικατάσταση των alerts με snackbars/toasts και προσθήκη bottom action banners στη ροή των private vehicles.
    * Διόρθωση του UI στο vehicles tab bar για μη συνδεδεμένους χρήστες (σωστή εμφάνιση της λίστας leasing πίσω από το tab bar).
    * Ανανέωση των εικονιδίων για τα verticals στην αρχική σελίδα μαζί με ενημέρωση του αντίστοιχου φωτογραφικού υλικού στο App Store.
