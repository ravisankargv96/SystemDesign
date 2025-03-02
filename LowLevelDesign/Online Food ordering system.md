taken from keerthi purswani youtube video & chatgpt.

```java
// Class: DeliveryMetaData
public class DeliveryMetaData {
    private Location userLoc;
    private Location restaurantLoc;
    private String orderId;

    public DeliveryMetaData(String orderId, Location userLoc, Location restaurantLoc) {
        this.orderId = orderId;
        this.userLoc = userLoc;
        this.restaurantLoc = restaurantLoc;
    }

    public Location getUserLoc() {
        return userLoc;
    }

    public Location getRestaurantLoc() {
        return restaurantLoc;
    }
}

// Class: DeliveryMgr
public class DeliveryMgr {
    private static DeliveryMgr instance;
    private static final Object mutex = new Object();

    private DeliveryMgr() {}

    public static DeliveryMgr getDeliveryMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new DeliveryMgr();
            }
        }
        return instance;
    }

    public void manageDelivery(String orderId, DeliveryMetaData deliveryMetaData) {
        // Implementation
    }
}

// Class: OrderMgr
public class OrderMgr {
    private static OrderMgr instance;
    private static final Object mutex = new Object();
    private Map<String, Order> ordersMap = new HashMap<>();

    private OrderMgr() {}

    public static OrderMgr getOrderMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new OrderMgr();
            }
        }
        return instance;
    }

    public void manageOrder(String orderId, Order order) {
        ordersMap.put(orderId, order);
    }

    public Order getOrder(String orderId) {
        return ordersMap.get(orderId);
    }
}

// Class: StrategyMgr
public class StrategyMgr {
    private static StrategyMgr instance;
    private static final Object mutex = new Object();

    private StrategyMgr() {}

    public static StrategyMgr getStrategyMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new StrategyMgr();
            }
        }
        return instance;
    }

    public IDeliveryPartnerMatchingStrategy determineDeliveryPartnerMatchingStrategy(DeliveryMetaData metaData) {
        // Implementation
        return new LocBasedDeliveryPartnerMatchingStrategy();
    }
}

// Interface: IDeliveryPartnerMatchingStrategy
public interface IDeliveryPartnerMatchingStrategy {
    List<DeliveryPartner> matchDeliveryPartners(DeliveryMetaData deliveryMetaData);
}

// Class: LocBasedDeliveryPartnerMatchingStrategy
public class LocBasedDeliveryPartnerMatchingStrategy implements IDeliveryPartnerMatchingStrategy {
    @Override
    public List<DeliveryPartner> matchDeliveryPartners(DeliveryMetaData deliveryMetaData) {
        // Implementation
        return new ArrayList<>();
    }
}

// Class: DeliveryPartner
public class DeliveryPartner {
    private String name;

    public DeliveryPartner(String name) {
        this.name = name;
    }

    public void performDelivery(String orderId, DeliveryMetaData deliveryMetaData) {
        // Implementation
    }
}

// Class: FoodMgr
public class FoodMgr {
    private static FoodMgr instance;
    private static final Object mutex = new Object();

    private FoodMgr() {}

    public static FoodMgr getFoodMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new FoodMgr();
            }
        }
        return instance;
    }

    public void prepareFood(String orderId, String restaurantId, Map<Dish, Integer> dishes) {
        // Implementation
    }
}

// Class: RestaurantMgr
public class RestaurantMgr {
    private static RestaurantMgr instance;
    private static final Object mutex = new Object();
    private Map<String, Restaurant> restaurantsMap = new HashMap<>();

    private RestaurantMgr() {}

    public static RestaurantMgr getRestaurantMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new RestaurantMgr();
            }
        }
        return instance;
    }

    public Restaurant getRestaurant(String restaurantName) {
        return restaurantsMap.get(restaurantName);
    }

    public void addRestaurant(String restaurantName, Restaurant restaurant) {
        restaurantsMap.put(restaurantName, restaurant);
    }
}

// Class: Restaurant
public class Restaurant {
    private String name;
    private boolean isAvailable;
    private Menu menu;
    private Location location;
    private RestaurantOwner owner;

    public Restaurant(String name, RestaurantOwner owner, Location location) {
        this.name = name;
        this.owner = owner;
        this.location = location;
        this.isAvailable = true;
    }

    public void prepareFood(String orderId, Map<Dish, Integer> dishes) {
        // Implementation
    }
}

// Class: Dish
public class Dish {
    private String name;
    private String description;
    private String cuisine;
    private double price;

    public Dish(String name, String cuisine, double price) {
        this.name = name;
        this.cuisine = cuisine;
        this.price = price;
    }
}

// Class: NotificationMgr
public class NotificationMgr {
    private static NotificationMgr instance;
    private static final Object mutex = new Object();
    private Map<String, List<INotificationSender>> notificationSendersMap = new HashMap<>();

    private NotificationMgr() {}

    public static NotificationMgr getNotificationMgr() {
        synchronized (mutex) {
            if (instance == null) {
                instance = new NotificationMgr();
            }
        }
        return instance;
    }

    public void notifyUser(String userId, String msg, INotificationSender sender) {
        sender.sendNotification(userId, msg);
    }
}

// Interface: INotificationSender
public interface INotificationSender {
    void sendNotification(String userId, String msg);
}

// Class: PushNotificationSender
public class PushNotificationSender implements INotificationSender {
    @Override
    public void sendNotification(String userId, String msg) {
        // Implementation
    }
}

// Class: SMSNotificationSender
public class SMSNotificationSender implements INotificationSender {
    @Override
    public void sendNotification(String userId, String msg) {
        // Implementation
    }
}

// Supporting Classes
class Location {
    private double latitude;
    private double longitude;
}

class Menu {
    private List<Dish> dishes;
}

class Order {
    // Attributes and methods for Order
}

class RestaurantOwner {
    // Attributes and methods for RestaurantOwner
}

```