```java
// Step 1:
// Here is the definition of parking slot & all it's children classes
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction TB	
	class ParkingSlot {
	    - number : String
	    - free : boolean
	    - vehicle : Vehicle
	    - final type : ParkingSlotType 
	    + ParkingSlot(ParkingSlotType type)
	    + IsFree() boolean
	    + assignVehicle(Vehicle vehicle) boolean 
	    + removeVehicle() boolean
	}
	
	class HandicappedSlot {
	    + HandicappedSlot()
	}
	
	class CompactSlot {
	    + CompactSlot()
	}
	
	class LargeSlot {
	    + LargeSlot()
	}
	
	class MotorbikeSlot {
	    + MotorbikeSlot()
	}
	
	class ElectricSlot {
	    + ElectricSlot()
	}

	class ParkingSlotType {
        <<enumeration>>
        HANDICAPPED
        COMPACT
        LARGE
        MOTORBIKE
        ELECTRIC
    }
		
	ParkingSlot <|-- HandicappedSlot
	ParkingSlot <|-- CompactSlot
	ParkingSlot <|-- LargeSlot
	ParkingSlot <|-- MotorbikeSlot
	ParkingSlot <|-- ElectricSlot
	%% ParkingSlot o-- ParkingSlotType %%
```

```java
// step1a:
// Here is the definition for vehicle and all of it's child classes
// ParkingSlot --> Vehicle
```

```mermaid
classDiagram

class Vehicle {
    - licenseNumber : String 
    - final type : VehicleType
    - ticket : ParkingTicket
    + Vehicle(VehicleType type)
    + assignTicket(ParkingTicket ticket) void
}

class Car {
    + Car()
}

class Van {
    + Van()
}

class Truck {
    + Truck()
}

class VehicleType {
	<<enumeration>>
	CAR
	TRUCK
	ELECTRIC
	VAN
	MOTORBIKE
}

Vehicle <|-- Car
Vehicle <|-- Van
Vehicle <|-- Truck
```

```java
// step2:
// ParkingFloor *-- ParkingSlot
```
```mermaid
classDiagram
direction LR

class ParkingFloor {
    - name : String
    - handicappedSlots : HashMap~String, HandicappedSlot~
    - compactSlots : HashMap~String, CompactSlot~
    - largeSlots : HashMap~String, LargeSlot~
    - motorbikeSlots : HashMap~String, MotorbikeSlot~
    - electricSlots : HashMap~String, ElectricSlot~
    - infoPortals : HashMap~String, CustomerInfoPortal~
    - displayBoard : ParkingDisplayBoard
    + ParkingFloor(String name)
    + addParkingSlot(ParkingSlot slot) void 
    + assignVehicleToSlot(Vehicle vehicle, ParkingSlot slot) void 
    - updateDisplayBoardForHandicapped(ParkingSlot slot) void 
    - updateDisplayBoardForCompact(ParkingSlot slot) void
    + freeSlot(ParkingSlot slot) void 
}
```
```java
// step 3:
// ParkingFloor *-- ParkingDisplayBoard
```

```mermaid
classDiagram

class ParkingDisplayBoard {
    - id : String
    - handicappedFreeSlot : HandicappedSlot 
    - compactFreeSlot : CompactSlot 
    - largeFreeSlot : LargeSlot 
    - motorbikeFreeSlot : MotorBikeSlot 
    - electricFreeSlot : ElectricSlot 
    + showEmptySlotNumber() void
}
```
```java
// step4:
// ParkingLot *-- ParkingFloor
```

```mermaid
classDiagram
direction LR

class ParkingLot {
    - name : String 
    - address : Location 
    - parkingRate : ParkingRate 
    - compactSlotCount : int 
    - largeSlotCount : int 
    - motorbikeSlotCount : int 
    - electricSlotCount : int 
    - final maxCompactCount : int 
    - final maxLargeCount : int 
    - final maxMotorbikeCount : int 
    - final maxElectricCount : int 
    - entrancePanels : HashMap~String, EntrancePanel~
    - exitPanels : HashMap~String, ExitPanel~ 
    - parkingFloors : HashMap~String, ParkingFloor~ 
    - activeTickets : HashMap~String, ParkingTicket~ 
    - ParkingLot() // Singleton constructor
    + getInstance() ParkingLot$
    + sync getNewParkingTicket(Vehicle vehicle) ParkingTicket
    + isFull(VehicleType type) boolean
    - incrementSlotCount(VehicleType type) boolean
    + isFull() boolean 
    + addParkingFloor(ParkingFloor floor) void 
    + addEntrancePanel(EntrancePanel entrancePanel) void 
    + addExitPanel(ExitPanel exitPanel) void 
}
```


```mermaid
classDiagram
    class ParkingTicketStatus {
        <<enumeration>>
        ACTIVE
        PAID
        LOST
    }
```

```java
//For simplicity, we are not defining getter & setter functions. The reader can assume that all class attributes are private & accessed through their respective public getter method & modified through public setter.
```

```mermaid
classDiagram
    class Account {
        <<abstract>>
        - userName : String
        - password : String
        - status : AccountStatus
        - person : Person
        + resetPassword() boolean
    }

    class AccountStatus {
        <<enumeration>>
        ACTIVE
        BLOCKED
        BANNED
        COMPROMIZED
        ARCHIEVED
        UNKNOWN
    }

    class Person {
        - name : String
        - address : Address
        - email : String
        - phone : String
    }

    class Address {
        - streetAddress : String
        - city : String
        - state : String
        - zipCode : String
        - country : String
    }

    Account --> AccountStatus : uses
    Account --> Person : uses
    Person --> Address : has-a
```
```java
// Admin --|> Account 
// ParkingAttendant --|> Account 
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '12px'}}}%%
classDiagram
direction LR
class Admin {
    + addParkingFloor(ParkingFloor floor) boolean 
    + addParkingSlot(String floorName, ParkingSlot slot) boolean 
    + addParkingDisplayBoard(String floorName, ParkingDisplayBoard displayBoard) boolean 
    + addCustomerInfoPanel(String floorName, CustomerInfoPanel infoPanel) boolean
    + addEntrancePanel(EntrancePanel entrancePanel) boolean
    + addExitPanel(ExitPanel exitPanel) boolean
}

class ParkingAttendant {
    + processTicket(String TicketNumber) boolean
}

Admin --|> Account
ParkingAttendant --|> Account
```


