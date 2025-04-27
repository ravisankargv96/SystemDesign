
```java
// Account
```

```mermaid
classDiagram
    class Account {
        - id : String
        - password : String
        - status : AccountStatus
        - name : String
        - address : Address
        - email : String
        - phone : String
        - reputation : int
        + resetPassword() boolean
    }

    class AccountStatus {
        <<enumeration>>
        ACTIVE
        CLOSED
        CANCELLED
        BLACKLISTED
        BLOCKED
    }

    Account --> AccountStatus
    Account --> Address
```
```java
//Member, Admin & Moderator: These classes represent different people that interact with our system:
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '12px'}}}%%
classDiagram
	direction RL
	class Member {
        - account : Account
        - badges : List~Badge~
        + getReputation() int
        + getEmail() String
        + createQuestion(Question question) boolean
        + createTag(Tag tag) boolean
    }

    class Admin {
        + blockMember(Member member) boolean
        + unblockMember(Member member) boolean
    }

    class Moderator {
        + closeQuestion(Question question) boolean
        + undeleteQuestion(Question question) boolean
    }

    Member <|-- Admin
    Member <|-- Moderator
    Member --> Account
    Member --> Badge
```

```java
// Badge, Tag & Notification: Members have badges, questions have tags & notifications:
```

```mermaid
classDiagram
	direction RL
	class Badge {
        - name : String
        - description : String
    }

    class Tag {
        - name : String
        - description : String
        - dailyAskedFrequency : Long
        - weeklyAskedFrequency : Long
    }

    class Notification {
        - notificationId : int
        - createdOn : Date
        - content : String
        + sendNotification() boolean
    }
```

```java
//Photo & Bounty: Members can put bounties on questions. Answers and Questions can have multiple photos
```

```mermaid
classDiagram
    class Photo {
        - photoId : int
        - photoPath : String
        - creationDate : Date
        - creatingMember : Member
        + delete() boolean
    }

    class Bounty {
        - reputation : int
        - expiry : Date
        + modifyReputation(int reputation) boolean
    }

    Photo --> Member
```

```java
// Question, Comment & Answer: Members can ask questions, as well as add an answer to any question. All members can add comments to all open questions or answers:
```

```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction RL
	class QuestionStatus {
        <<enumeration>>
        OPEN
        CLOSED
        ON_HOLD
        DELETED
    }

    class QuestionClosingRemark {
        <<enumeration>>
        DUPLICATE
        OFF_TOPIC
        TOO_BROAD
        NOT_CONSTRUCTIVE
        NOT_A_REAL_QUESTION
        PRIMARILY_OPINION_BASED
    }

    class Search {
        <<interface>>
        + search(String query) List<Question>
    }

    class Question {
        - title : String
        - description : String
        - viewCount : String
        - voteCount : int
        - creationTime : Date
        - updateTime : Date
        - status : QuestionStatus
        - closingRemark : QuestionClosingRemark
        - askingMember : Member
        - bounty : Bounty
        - photos : List<Photo>
        - comments : List<Comment>
        - answers : List<Answer>
        + close() boolean
        + undelete() boolean
        + addComment(Comment comment) boolean
        + addBounty(Bounty bounty) boolean
        + search(String query) List<Question>
    }

    class Comment {
        - text : String
        - creationTime : Date
        - flagCount : int
        - voteCount : int
        - askingMember : Member
        + incrementVoteCount() boolean
    }

    class Answer {
        - answerText : String
        - accepted : boolean
        - voteCount : int
        - flagCount : int
        - creationTime : Date
        - creatingMember : Member
        - photos : List<Photo>
        + incrementVoteCount() boolean
    }

    Question --> QuestionStatus
    Question --> QuestionClosingRemark
    Question --> Member : askingMember
    Question --> Bounty
    Question --> Photo
    Question --> Comment
    Question --> Answer
    Answer --> Photo
    Answer --> Member : creatingMember
    Comment --> Member : askingMember
    Search <|.. Question
```