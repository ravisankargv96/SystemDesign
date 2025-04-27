```java
public class Account {
	private String userName;
	private String password;
	private AccountStatus status;
	private String name;
	private Address shippingAddress;
	private String email;
	private String phone;

	private List<CreditCard> creditCards;
	private List<ElectronicBankTransfer> bankAccounts;

	public boolean addProduct(Product product);
	public boolean addProductReview(ProductReview review);
	public boolean resetPassword();
}

public class Address {
	private String streetAddress;
	private String city;
	private String state;
	private String zipcode;
	private String country;
}

public enum AccountStatus {
	ACTIVE,
	BLOCKED,
	BANNED,
	COMPROMIZED,
	ARCHIVED,
	UNKNOWN
}

public enum PaymentStatus {
	UNPAID,
	PENDING,
	COMPLETED,
	FILLED,
	DECLINED,
	CANCELLED,
	ABONDENED,
	SETTLING,
	SETTLED,
	REFUNDED
}
```

```java
// Account, Customer, Admin & Guest: These classes represent different people that interact with our system
public abstract class Customer {
	private ShoppingCart cart;
	private Order order;

	public ShoppingCart getShoppingCart();
	public boolean addItemToCart(Item item);
	public boolean removeItemFromCart(Item item);
}

public class Guest extends Customer {
	public boolean register Account();
}

public class Member extends Customer {
	private Account account;
	public OrderStatus placeOrder(Order order);
}
```

```java
//ProductCategory, Product & Product Review: Here are the classes related to a product
public class ProductCategory {
	private String name;
	private String description;
}

public class ProductReview {
	private int rating;
	private String review;

	private Member reviewer;
}

public class Product {
	private String name;
	private String description;
	private double price;
	private ProductCategory category;
	private int availableItemCount;

	private Account seller;

	public int getAvailableCount();
	public boolean updatePrice(double newPrice);
}
```

```java
//ShoppingCart, Item, Order & OrderLog: Users will put items in shopping cart and place order to buy all items in the cart.

public class Item {
	private int quantity;
	private double price;

	public boolean updateQuantity(int quantity);
}

public class ShoppingCart {
	private List<Items> items;

	public boolean addItem(Item item);
	public boolean removeItem(Item item);
	public boolean updateItemQuantity(Item item, int quantity);
	public List<Item> getItems();
	public boolean checkout();
}

public class OrderLog {
	private String orderNumber;
	private Date creationDate;
	private OrderStatus status;
}

public class Order {
	private String orderNumber;
	private OrderStatus status;
	private Date orderDate;
	private List<OrderLog> orderLog;

	public boolean sendForShipment();
	public boolean makePayment(Payment payment);
	public boolean addOrderLog(OrderLog orderLog);
}

public enum OrderStatus {
	UNSHIPPED,
	PENDING,
	SHIPPED,
	COMPLETED,
	CANCELED,
	REFUND_APPLIED
}

```

```java
//Shipment, ShipmentLog & Notification: After successfully placing an order, a shipment record will be created:

public enum ShipmentStatus {
	PENDING,
	SHIPPED,
	DELIVERED,
	ON_HOLD
}

public class ShipmentLog {
	private String shipmentNumber;
	private ShipmentStatus status;
	private Date creationDate;
}

public class Shipment {
	private String shipmentNumber;
	private Date shipmentDate;
	private Date estimatedArrival;
	private String shipmentMethod;

	public boolean addShipmentLog(ShipmentLog shipmentLog);
}

public abstract class Notification{
	private int notificationId;
	private Date createdOn;
	private String content;

	public boolean sendNotification(Account account);
}
```

```java
// Search interface & Catalog: Catalog will implement Search to facilitate searching of products
public interface Search {
	public List<Product> searchProductsByName(String name);
	public List<Product> searchProductsByCategory(String category);
}

public class Catalog implements Search {
	HashMap<String, List<Product>> productNames;
	HashMap<String, List<Product>> productCategories;

	public List<Product> searchProductsByName(String name) {
		return productNames.get(name);
	}

	public List<Product> searchProductsByCategory(String category) {
		return productCategories.get(category);
	}
}
```
