```mermaid
classDiagram
    direction TB
	class Coin {
        <<enumeration>>
        + PENNY : Coin
        + NICKET : Coin
        + DIME : Coin
        + QUARTER : Coin
        - VALUE : double
        + Coin(double value)
        + getValue() double
    }

	class Note {
        <<enumeration>>
        + ONE : Note
        + FIVE : Note
        + TEN : Note
        + TWENTY : Note
        - VALUE : int
        + Note(int value)
        + getValue() int
    }

```

```mermaid
%%{init: {'themeVariables': {'fontSize': '12px'}}}%%
classDiagram
	direction LR
	class VendingMachine {
        - _INSTANCE_ : VendingMachine
        - INVENTORY : Inventory
        - IDLE_STATE : VendingMachineState
        - READY_STATE : VendingMachineState
        - DISPENSE_STATE : VendingMachineState
        - RETURN_CHANGE_STATE : VendingMachineState
        - CURRENT_STATE : VendingMachineState
        - SELECTED_PRODUCT : Product
        - TOTAL_PAYMENT : double
        - VendingMachine()
        + _getInstance()_ VendingMachine
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + insertNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
        - setState(VendingMachineState state) void
        - getIdleState() VendingMachineState
        - getReadyState() VendingMachineState
        - getDispenseState() VendingMachineState
        - getReturnChangeState() VendingMachineState
        - getSelectedProduct() Product
        - setSelectedProduct(Product product) void
        - resetSelectedProduct() void
        - getTotalPayment() double
        - addCoin(Coin coin) void
        - addNote(Note note) void
        - resetPayment() void
    }
	class Inventory {
        - PRODUCTS : Map<Product, Integer>
        + Inventory()
        + addProduct(Product product, int quantity) void
        + removeProduct(Product product) void
        + updateQuantity(Product product, int quantity) void
        + getQuantity(Product product) int
        + isAvailable(Product product) boolean
    }
	class Product {
        - NAME : String
        - PRICE : double
        + Product(String name, double price)
        + getName() String
        + getPrice() double
    }
	VendingMachine *--> Inventory
	Inventory *--> Product
```

```java
// Dispense State
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
direction TB
	class VendingMachineState {
        <<interface>>
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + insertNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
    }
	class DispenseState {
        - VENDING_MACHINE : VendingMachine
        + DispenseState(VendingMachine vendingMachine)
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + insertNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
    }
	class IdleState {
        - VENDING_MACHINE : VendingMachine
        + IdleState(VendingMachine vendingMachine)
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + insertNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
    }
	class ReadyState {
        - VENDING_MACHINE : VendingMachine
        + ReadyState(VendingMachine vendingMachine)
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + insertNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
        - checkPaymentStatus() void
    }
	class ReturnChangeState {
        - VENDING_MACHINE : VendingMachine
        + ReturnChangeState(VendingMachine vendingMachine)
        + selectProduct(Product product) void
        + insertCoin(Coin coin) void
        + inserNote(Note note) void
        + dispenseProduct() void
        + returnChange() void
    }
    VendingMachineState <|.. DispenseState 
	VendingMachineState <|.. IdleState 
	VendingMachineState <|.. ReadyState
	VendingMachineState <|.. ReturnChangeState  
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