```mermaid
classDiagram
    class PaymentStatus {
        <<enumeration>>
        UNPAID
        PENDING
        COMPLETED
        FILLED
        DECLINED
        CANCELLED
        ABONDENED
        SETTLING
        SETTLED
        REFUNDED
    }

	class Account {
        - userName : String
        - password : String
        - status : AccountStatus
        - name : String
        - shippingAddress : Address
        - email : String
        - phone : String
        - creditCards : List<CreditCard>
        - bankAccounts : List<ElectronicBankTransfer>
        + addProduct(Product product) boolean
        + addProductReview(ProductReview review) boolean
        + resetPassword() boolean
    }

    class Address {
        - streetAddress : String
        - city : String
        - state : String
        - zipcode : String
        - country : String
    }

    class AccountStatus {
        <<enumeration>>
        ACTIVE
        BLOCKED
        BANNED
        COMPROMIZED
        ARCHIVED
        UNKNOWN
    }
	
	Account --> Address
    Account --> AccountStatus
```
```java
// Account, Customer, Admin & Guest: These classes represent different people that interact with our system
```

```mermaid
classDiagram
    class Customer {
        <<abstract>>
        - cart : ShoppingCart
        - order : Order
        + getShoppingCart() ShoppingCart
        + addItemToCart(Item item) boolean
        + removeItemFromCart(Item item) boolean
    }

    class Guest {
        + register() Account
    }

    class Member {
        - account : Account
        + placeOrder(Order order) OrderStatus
    }

    Customer <|-- Guest
    Customer <|-- Member
```
```java
//ProductCategory, Product & Product Review: Here are the classes related to a product
```

```mermaid
classDiagram
	class ProductCategory {
        - name : String
        - description : String
    }

    class ProductReview {
        - rating : int
        - review : String
        - reviewer : Member
    }

    class Product {
        - name : String
        - description : String
        - price : double
        - category : ProductCategory
        - availableItemCount : int
        - seller : Account
        + getAvailableCount() int
        + updatePrice(double newPrice) boolean
    }

    Product --> ProductCategory
    Product --> Account
    ProductReview --> Member

```

```java
//ShoppingCart, Item, Order & OrderLog: Users will put items in shopping cart and place order to buy all items in the cart.
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
    class Item {
        - quantity : int
        - price : double
        + updateQuantity(int quantity) boolean
    }

    class ShoppingCart {
        - items : List<Item>
        + addItem(Item item) boolean
        + removeItem(Item item) boolean
        + updateItemQuantity(Item item, int quantity) boolean
        + getItems() List<Item>
        + checkout() boolean
    }

    class OrderLog {
        - orderNumber : String
        - creationDate : Date
        - status : OrderStatus
    }

    class Order {
        - orderNumber : String
        - status : OrderStatus
        - orderDate : Date
        - orderLog : List<OrderLog
        + sendForShipment() boolean
        + makePayment(Payment payment) boolean
        + addOrderLog(OrderLog orderLog) boolean
    }

    class OrderStatus {
        <<enumeration>>
        UNSHIPPED
        PENDING
        SHIPPED
        COMPLETED
        CANCELED
        REFUND_APPLIED
    }

    ShoppingCart --> Item
    Order --> OrderLog
    Order --> OrderStatus
```

```java
//Shipment, ShipmentLog & Notification: After successfully placing an order, a shipment record will be created:
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '13px'}}}%%
classDiagram
    class ShipmentStatus {
        <<enumeration>>
        PENDING
        SHIPPED
        DELIVERED
        ON_HOLD
    }

    class ShipmentLog {
        - shipmentNumber : String
        - status : ShipmentStatus
        - creationDate : Date
    }

    class Shipment {
        - shipmentNumber : String
        - shipmentDate : Date
        - estimatedArrival : Date
        - shipmentMethod : String
        + addShipmentLog(ShipmentLog shipmentLog) boolean
    }

    class Notification {
        <<abstract>>
        - notificationId : int
        - createdOn : Date
        - content : String
        + sendNotification(Account account) boolean
    }

    Shipment --> ShipmentLog
    ShipmentLog --> ShipmentStatus
```

```java
// Search interface & Catalog: Catalog will implement Search to facilitate searching of products
```

```mermaid
classDiagram
    class Search {
        <<interface>>
        + searchProductsByName(String name) List<Product>
        + searchProductsByCategory(String category) List<Product>
    }

    class Catalog {
        - productNames : HashMap<String, List<Product>>
        - productCategories : HashMap<String, List<Product>>
        + searchProductsByName(String name) List<Product>
        + searchProductsByCategory(String category) List<Product>
    }

    Search <|.. Catalog
```
