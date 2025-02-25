#### Actors
1. **Librarian (Admin)**
2. **Member (User)**
3. **System**


#### Top Use Cases:
1. **Register new account/cancel membership:**
	1. Every system provides Users/Admin to register to access their services
	2. Deactivate account, if no longer needed.
2. **Add/Remove/Edit book (Inventory)**: 
	Usually Admin will perform CRUD on Inventory (**books**)
3. **Search Catalog:** 
	Anyone can search books by { **title**, **author**, **subject** or **publication date** }
4. **Outcome scenarios:**
	1. **Check-out book:**
		User can check-out necessary book
	2. **Reserve book:**
		User can reserve book, which isn't currently available
	3. **Renew book:**
		User can renew book, which have already borrowed after expiry date (here we are considering 10 days)
	4. **Return book:**
		User will return the book

### Outcome Flows
#### 1. Check-out book:
1. Member scans their library card through barcode reader (User details needed)
2. Member scans the barcode of the book (Book details needed)
3. **Check:** if the book can be issued and that the book is not `reference only`
	1. **Check:** No of books issued to the Member `<=` **limit**
		1. **Check:** if book has been reserved by anyone
			1. System creates book checkout transaction
			2. System updates the status of the book to `Loaned`
			3. System increments number of books issued to the member
			4. System marks any reservation `Completed` that the member had made against the book (Extra feature added, since we are providing reservation for a book)
4. Any other scenario `show error: Book can't be issued`

#### 2. Return a book:
1. Member scans barcode of the book (Book Details)
2. System fetches book's details
3. **check:** if the book is being not returned within the due date
	1. Calculate fine
	2. Create transaction for fine collection
	3. Collect fine
4. system decrements the number of books issued to the member
5. **check:** If book reserved by any member
	1. Update book status `reserved`
6. if not: 
	1. System updates the status to `Available`
7. System sends notification to the member who has reserved the book about the availability of the book.

### 3. Renew a book:
1. Member scans their library card through barcode reader
2. Member scans barcode of the book and selects to renew the book
3. System fetches book's details
4. **Check:** if the book **hasn't been returned** within the due date
	1. Calculate fine
	2. Create transaction
	3. Collect fine
5. **Check:** if the book has been **reserved** by any other member
	1. `Show error message` that the book can't be issued
	2. Update the status of the book to `Reserved`
	3. Send notification to the member who has reserved the book that the book has become available
6. **if not Reserved:**
	1. Create book checkout transaction with new due date

### Pseudo Code
```java
// check-out book
public void checkOutBook(User user, Book book){
	
	checkOut = false; // written for better code refactoring
	if(!book.isReferenceOnly){
		if(user.booksIssued <= limit){
			if(book.status != 'reserved'){
				// calls book checkout transaction
				book.status = 'loaned';
				user.booksIssued++;
				bookReservation.status(user,book,'completed');
				checkOut = true;
			}
		}
	}

	if(!checkOut){
		println('Show Error')
	}
}

//Return a book
public void returnBook(User user, Book book){
	if(Datetime.Date() > book.dueDate()){  // book retured lately
		//Calculate fine
		int fine = calculateFine(Datetime.Date(), book.dueDate());
		int transactionId = payment(fine);
		println('Collected fine')
	}
	user.booksIssued--;
	if(bookReservation.getDetails(book) != null){
		book.status = 'reserved';
		notificationServer(bookReservation.getDetails(book), book);
	} else {
		book.status = 'available';
	}
}


//Renew a book
public void renewBook(User user, Book book){
	if(Datetime.Date() > book.dueDate()){  // book retured lately
		//Calculate fine
		int fine = calculateFine(Datetime.Date(), book.dueDate());
		int transactionId = payment(fine);
		println('Collected fine')
	}
	if(bookReservation.getDetails(book) != null){
		println('Show Error msg');
		book.status = 'reserved';
		notificationServer(bookReservation.getDetails(book), book);
	} else {
		// calls book checkout transaction
		book.status = 'loaned';
		user.booksIssued++;
		bookReservation.status(user,book,'completed');
	}
}
```
#### Skeleton of the system
```java

```