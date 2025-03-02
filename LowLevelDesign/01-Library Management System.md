```java
True -> Wrong
true -> right representation in java, change later
```
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

#### 3. Renew a book:
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
### 1. Skeleton of the system
##### 1. Managing Users & Performed Actions on System
```java
public class Account{
	String userId;
	String password;
	String accountStatus;
	User user; //Enhace all the User related Details here.

	//methods
	+ boolean resetPassword();
}

// Admin
public class Librarian extends Account{
	// 1. managing inventory
	+ boolean addBook(Book book);

	// 2. managing Users
	+ boolean blockUser(User user);
	+ boolean unBlockUser(User user);
}

// User
public class Member extends Account{
	int totalBooksCheckedOut; //booksIssued

	// Actions: Outcomes
	+ boolean checkOutBook(Book book);
	+ boolean reserveBook(Book book);
	+ boolean returnBook(Book book);
	+ boolean renewBook(Book book);
}
```

##### 2. Managing Inventory of System
```java
public class Book {
	+ String id;
	+ String title;

	// checks to checkout that book
	+ boolean checkOut(String userId);
}

public class Search {
	// 1. method on Book
	+ List<Book> searchByTitle(String title);
}
```
##### 3. Functionalities of System
```java
//operations on the Book
public class BookReservation {
	String reservationStatus;
	Book book;
	User user;

	//Got Association of 2 class
	+ BookReservation fetchReservationDetails(Book book, User user);
}

public class BookLending {
	Date dueDate;
	Book book;
	User user;

	//Got Association of 2 objects
	+ void lendBook(Book book, User user);
	+ BookLending fetchLendingDetails(Book book, User user);
}

public class Fine {
	+ Date today;
	+ Book book;
	+ User user;

	+ int void collectFine(Book book, User user)
}
```


### 2. Extending Above Code

##### 2a. Inventory
```java
/*
	Inventory: Books & Searching books
	Books: Inventory Item, so focus more about (features) to this item.
	Search: Focuses functionalities 
*/
```

```java
// Each Book can have many copies, so each copy is denoted as BookItem
public abstract class Book {
	private String ISBN;  // Unique for a Book
	private String title; // mandatory
	
	//requirement
	private String subject;
	private String publisher;
	private List<Author> authors; // association, enhancing

	private String language;  
	private int numberOfPages;
}

public class Author {
	public String name;
	public String description;
}

public class BookItem extends Book {
	private String barcode; // Unique for copy
	private boolean isReferenceOnly; // Can't issue this kind of book

	private Date dateOfPurchase; //other metadata
	private Date publicationDate;
	private double price;

	// used for business Logic
	private Date borrowed;
	private Date dueDate;

	private BookFormat format; // hardcover, paperback, .. (primitive -> enum)
	private BookStatus status; // available, reserved, ..  (primitive -> enum)
		
	private Rack placedAt;   // {num:1, loc: "bottom"} ie. association enhance

	public boolean checkout(String memberId); //complete this method
}

public class Rack {
	private int number;
	private String locationIdentifier;
}

public enum BookFormat {
	HARDCOVER,
	PAPERBACK,
	AUDIO_BOOK,
	EBOOK,
	NEWSPAPER,
	MAGAZINE,
	JOURNAL
}

public enum BookStatus {
	AVAILABLE,
	RESERVED,
	LOANED,
	LOST
}
```

```java
// Search interface & catalog
public interface Search {
	
	// Based on requirements
	public List<Book> searchByTitle(String title);
	public List<Book> searchByAuthor(String author);
	public List<Book> searchBySubject(String subject);
	public List<Book> searchByPubDate(String publishDate);
}

// Catalog implements Search
public Catalog implements Search {

	//Assume DB Records, with Key as search Item
	private HashMap<String, List<Book>> bookTitles;
	private HashMap<String, List<Book>> bookAuthors;
	private HashMap<String, List<Book>> bookSubjects;
	private HashMap<String, List<Book>> bookPublicationDates;
	
	public List<Book> searchByTitle(String title){
		// return all the books containing the string query in their title
		return bookTitles.get(query)
	}

	// similarly rest 3 methods.
}
```

##### 2b. Functionalities
```java
/* Actions:
	1. fetchReservationDetails(String barcode)
	2. lendBook(String barcode, String memberId)
	3. fetchLendingDetails(String barcode);
	4. collectFine(String memberId, long days)
*/

public class BookReservation {
	
	private String bookBarcode;
	private String memberId;

	//Date
	private Date creationDate;
	private ReservationStatus status; // waiting, pending, canceled, none

	public static BookReservervation fetchReservationDetails(String barcode);
	public void updateStatus(ReservationStatus resStatus); 
}

public enum ReservationStatus {
	WAITING,
	PENDING,
	CANCELED,
	NONE
}

public class BookLending {

	private String bookBarcode;
	private String memberId;

	// lending details
	private Date creationDate;
	private Date dueDate;
	private Date returnDate;
	
	public static void lendBook(String barcode, String memberId);
	public static BookLending fetchLendingDetails(String barcode);
}

public class Fine {

	private double bookBarcode;
	private String memberId;

	private Date creationDate;

	public static void collectFine(String memberId, long days);
}
```

##### 1. Managing Users & Performed Actions on System
```java
// Account: Member & Librarian - These classes represent different people that interact with our system


/* 
7. For simplicity, we are not defining getter & setter functions.
8. The readers can assume that all class attributes are private & accessed through their respective public getter method & modified only through public setter method.
*/
```

```java
public abstract class Account{
	private String id;
	private String password;
	private AccountStatus status; //fixed Values, so extending primitive to Enum
	private Person person; //Lots details, so extending primitive to Class

	public boolean resetPassword();
}

// Associations of above class: 
// 1. AccountStatus:Enum
public enum AccountStatus {
	ACTIVE,
	CLOSED,
	CANCELLED,
	BLACKLISTED,
	NONE
}

// 2. Person: Class
public class Person {
	private String name;
	private String email;
	private String phone;
	private Address address; //Lots of details, so extending primitive to Class
}
// 2a. Address: Class
public class Address {
	private String streetAddress;
	private String city;
	private String state;
	private String zipCode;
	private String country;
}
```

```java
public class Librarian extends Account{
	public boolean addBookItem(BookItem bookItem);
	public boolean blockMember(Member member);
	public boolean unBlockMember(Member member);
}
```

```java
public class Member extends Account{
	private Date dateOfMembership;
	private int totalBooksCheckedout;

	public void incrementTotalBooksCheckedout(); // feels optional, can use setter
	public int getTotalBooksCheckedout();// Actually we'll use this;

	//Actions: (uses BookReservation, BookLending & Fine)
	public boolean checkoutBookItem(BookItem bookItem);
	public boolean reserveBookItem(BookItem bookItem);

	public boolean returnBookItem(BookItem bookItem);
	public boolean renewBookItem(BookItem bookItem);

	// 1. checkout:
	public boolean checkoutBookItem(BookItem bookItem){
		
		if( this.getTotalBooksCheckedOut() >= Constants.MAX_BOOKS_ISSUED){
			println('Show Error');
		}
		
		//has member details, if reserved.
		BookReservation bookRes = BookReservation.fetchReserDetails(bookItem);
		if(bookRes != null && bookRes.getMemberId() != this.getId()){
			println("Show Error: It's reserved by another person");
			return False;
		} else if(bookRes != null){
			// this.person, reserved the book
			bookRes.updateStatus(ReservationStatus.COMPLETED);
		}

		if(!bookItem.checkout( this.getId() )) {
			return False;
		}

		this.totalBooksCheckedout++; // we can use getters & setters for this
		return True;
	}

	// Collecting Fine :-> returnBookItem
	private void checkForFine(String bookBarcode){
		BookLending bookLending = BookLending.fetchLendingDetails(bookBarcode);
		Date dueDate = bookLending.getDueDate();
		Date today = new Date();

		// check if book has returned within due date
		if(today.compareTo(dueDate) > 0){
			long diff = todayDate.getTime() - dueDate.getTime();
			long diffDays = diff / (24 * 60 * 60 * 1000);
			Fine.collectFine(memberId, diffDays);
		}
	}

	// 2. returning BookItem
	public void returnBookItem(BookItem bookItem){
		this.checkForFine(bookItem.getBookBarcode());
		BookReservation bookRes = BookReservation.fetchReservationDetails(bookItem.getBarcode());
		
		if(bookReservation != null){
			bookItem.updateBookItemStatus(BookStatus.RESERVED);
			bookReservation.sendBookAvailableNotification();
		} else{
			bookItem.updateBookItemStatus(BookStatus.AVAILABLE);
		}
	}

	// 3. renew BookItem
	public boolean renewBookItem(BookItem bookItem) {
		this.checkForFine();
		BookReservation bookReservation = 
			BookReservation.fetchReservationDetails(bookItem.getBarcode());

		if( bookReservation != null 
			&& bookReservation.getMemberId() != member.getMemberId()) {
			ShowError("This book is reserved by another member");
			member.decrementTotalBooksCheckedout(); // need to implement
			bookItem.updateBookItemState(BookStatus.RESESRVED);
			bookReservation.sendBookAvailableNotification();
			return False;
		} else if (bookReservation != null) {
			bookReservation.updateStatus(ReservationStatus.COMPLETED);
		}
		BookLending.lendBook(bookItem.getBarCode(), this.getMemberId());
		bookItem.updateDueDate(LocalDate.now().plusDays(Constants.MAX_LENDING_DAYS));
		return True;
	}
}
```

