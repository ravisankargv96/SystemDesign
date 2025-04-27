```java
// coin.java

// this enum has fields, constructor in enum
public enum Coin{
	PENNY(0.01),
	NICKET(0.05),
	DIME(0.1),
	QUARTER(0.25);

	private final double value;

	Coin(double value){
		this.value = value;
	}

	public double getValue(){
		return value;
	}
}
```

```java
public enum Note {
	ONE(1),
	FIVE(5),
	TEN(10),
	TWENTY(20);

	private final int value;

	Note(int value) {
		this.value = value;
	}

	public int getValue() {
		return value;
	}
}
```

```java
public class Product {
	private final String name;
	private final double price;

	public Product(String name, double price) {
		this.name = name;
		this.price = price;
	}

	public String getName() {
		return name;
	}

	public double getPrice() {
		return price;
	}
}
```

```java
// Inventory.java
public class Inventory {
	private final Map<Product, Integer> products;

	public Inventory() {
		products = new ConcurrentHashMap<>();
	}

	public void addProduct(Product product, int quantity) {
		products.put(product, quantity);
	}

	public void removeProduct(Product product) {
		products.remove(product);
	}

	public void updateQuantity(Product product, int quantity) {
		products.put(product, quantity);
	}

	public int getQuantity(Product product) {
		return products.getOrDefault(product, 0);
	}

	public boolean isAvailable(Product product) {
		return products.containsKey(product) && products.get(product) > 0;
	}
}
```

```java

public class VendingMachine {
	private static VendingMachine instance;
	Inventory inventory;
	private final VendingMachineState idleState;
	private final VendingMachineState readyState;
	private final VendingMachineState dispenseState;
	private final VendingMachineState returnChangeState;

	private VendingMachineState currentState;
	private Product selectedProduct;
	private double totalPayment;

	private VendingMachine() {
		inventory = new Inventory();
		idleState = new IdleState(this);
		readyState = new ReadyState(this);
		dispenseState = new DispenseState(this);
		returnChangeState = new ReturnChangeState(this);
		currentState = idleState;
		selectedProduct = null;
		totalPayment = 0.0;
	}

	public static synchronized VendingMachine getInstance() {
		if(instance == null) {
			instance = new VendingMachine();
		}
	}

	public void selectProduct(Product product){
		currentState.selectProduct(product);
	}

	public void insertCoin(Coin coin){
		currentState.insertCoin(coin);
	}

	public void insertNote(Note note) {
		currentState.insertNote(note);
	}

	public void dispenseProduct() {
		currentState.dispenseProduct();
	}

	public void returnChange() {
		currentState.returnChange();
	}

	void setState(VendingMachineState state) {
		currentState = state;
	}

	VendingMachineState getIdleState() {
		return idleState;
	}

	VendingMachineState getReadyState() {
		return readyState;
	}

	VendingMachineState getDispenseState() {
		return dispenseState;
	}

	VendingMachineState getReturnChangeState() {
		return returnChangeState;
	}

	Product getSelectedProduct() {
		return selectedProduct;
	}

	void setSelectedProduct(Product product) {
		selectedProduct = product;
	}

	void resetSelectedProduct() {
		selectedProduct = null;
	}

	double getTotalPayment() {
		return totalPayment;
	}

	void addCoin(Coin coin) {
		totalPayment += coin.getValue();
	}

	void addNote(Note note) {
		totalPayment += note.getValue();
	}

	void resetPayment() {
		totalPayment = 0.0;
	}
}
```

```java
//VendingMachineState.java
public interface VendingMachineState {
	void selectProduct(Product product);
	void insertCoin(Coin coin);
	void insertNote(Note note);
	void dispenseProduct();
	void returnChange();
}
```

```java
// DispenseState.java
public class DispenseState implements VendingMachineState {
	private final VendingMachine vendingMachine;

	public DispenseState(VendingMachine vendingMachine){
		this.vendingMachine = vendingMachine;
	}

	@Override
	public void selectProduct(Product product){
		println("Product already selected. Please collect the dispensed product");
	}

	@Override
	public void insertCoin(Coin coin){
		println("Payment already made. Please collect the dispensed product");
	}

	@Override
	public void insertNote(Note note){
		println("Payment already made. Please collect the dispensed product.");
	}

	@Override
	public void dispenseProduct() {
		vendingMachine.setState(vendingMachine.getReadyState());

		Product product = vendingMachine.getSelectedProduct();

		vendingMachine.inventory.updateQuantity(product, vendingMachine.inventory.getQuantity(product) - 1);

		println("Product dispensed: " + product.getName());
		vendingMachine.setState(vendingMachine.getReturnChangeState());
	}

	@Override
	public void returnChange(){
		println("Please collect the dispensed product first");
	}
}
```

```java
//IdleState.java
class IdleState implements VendingMachineState {
	private final VendingMachine vendingMachine;

	public IdleState(VendingMachine vendingMachine) {
		this.vendingMachine = vendingMachine;
	}

	@Override
	public void selectProduct(Product product) {
		if(vendingMachine.inventory.isAvailable(product)) {
			vendingMachine.setSelectedProduct(product);
			vendingMachine.setState(vendingMachine.getReadyState());
			println("Product selected: " + product.getName());
		} else {
			println("Product not available " + product.getName());
		}
	}

	@Override
	public void insertCoin(Coin coin) {
		println("Please select a product first");
	}

	@Override
	public void insertNote(Note note) {
		println("Please select a product first.");
	}

	@Override
	public void dispenseProduct() {
		println("Please select a product and make payment.");
	}

	@Override
	public void returnChange() {
		println("No change to return.");
	}
}
```

```java
public class ReadyState implements VendingMachineState {
	private final VendingMachine vendingMachine;

	public ReadyState(VendingMachine vendingMachine) {
		this.vendingMachine = vendingMachine;
	}

	@Override
	public void selectProduct(Product product) {
		println("Product already selected. Please make payment");
	}

	@Override
	public void insertCoin(Coin coin) {
		vendingMachine.addCoin(coin);
		println("Coin inserted: " + coin);
		checkPaymentStatus();
	}

	@Override
	public void insertNote(Note note) {
		vendingMachine.addNote(note);
		println("Note inserted: " + note);
		checkPaymentStatus();
	}

	@Override
	public void dispenseProduct() {
		println("Please make payment first.");
	}

	@Override
	public void returnChange() {
		println("Please make paymnet first.");
	}

	private void checkPaymentStatus() {
		if(vendingMachine.getTotalPayment() >= vendingMachine.getSelectedProduct().getPrice()) {
			vendingMachine.setState(vendingMachine.getDispenseState());
		}
	}
}
```

```java
public class ReturnChangeState implements VendingMachineState {
	private final VendingMachine vendingMachine;

	public ReturnChangeState(VendingMachine vendingMachine) {
		this.vendingMachine = vendingMachine;
	}

	@Override
	public void selectProduct(Product product) {
		println("Please collect the change first.");
	}

	@Override
	public void insertCoin(Coin coin) {
		println("Please collect the change first.");
	}

	@Override
	public void inserNote(Note note) {
		println("Please collect the change first.");
	}

	@Override
	public void dispenseProduct() {
		println("Product already dispensed. Please collect the change.");
	}

	@Override
	public void returnChange() {
		double change = vendingMachine.getTotalPayment() - vendingMachine.getSelectedProduct().getPrice();
		if (change > 0) {
			println("Change returned: $" + change);
		} else {
			println("No change to return.");
		}

		vendingMachine.resetPayment();
		vendingMachine.resetSelectedProduct();
		vendingMachine.setState(vendingMachine.getIdleState());
	}
}
```


```java

public class VendingMachineDemo {
	public static void run() {
		VendingMachine vendingMachine = VendingMachine.getInstance();

		// Add products to inventory
		Product coke = new Product("Coke", 1.5);
		Product pepsi = new Product("Pepsi", 1.5);
		Product water = new Product("Water", 1.0);

		vendingMachine.inventory.addProduct(coke, 5);
		vendingMachine.inventory.addProduct(pepsi, 3);
		vendingMachine.inventory.addProduct(water, 2);

		// Select a product
		vendingMachine.selectProduct(coke);

		// Insert coins
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);

		// Insert a note
		vendingMachine.insertNote(Note.FIVE);

		// Dispense the product
		vendingMachine.dispenseProduct();

		// Return change
		vendingMachine.returnChange();

		// Select another product
		vendingMachine.selectProduct(pepsi);

		// Insert insufficient payment
		vendingMachine.insertCoin(Coin.QUARTER);

		// Try to dispense the product
		vendingMachine.dispenseProduct();

		// Insert more coins
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);
		vendingMachine.insertCoin(Coin.QUARTER);

		// Dispense the product
		vendingMachine.dispenseProduct();

		// Return change
		vendingMachine.returnChange();
		
	}
}

```