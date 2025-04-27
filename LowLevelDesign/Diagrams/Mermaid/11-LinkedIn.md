```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction BT
    class Connection {
        - USER : User
        - CONNECTIONDATE : Timestamp
        + Connection(User user, Timestamp connectionDate)
        + getUser() User
        + getConnectionDate() Timestamp
    }

    class User {
        - ID : String
        - NAME : String
        - EMAIL : String
        - PASSWORD : String
        - profile : Profile
        - CONNECTIONS : List~Connection~
        - INBOX : List~Message~
        - SENTMESSAGES : List~Message~

        + User(String id, String name, String email, String password, Profile profile, List<Connection> connections, List<Message> inbox, List<Message> sentMessages)
        + setProfile(Profile profile) void
        + getId() String
        + getName() String
        + getEmail() String
        + getPassword() String
        + getProfile() Profile
        + getConnections() List~Connection~
        + getInbox() List~Message~
        + getSentMessages() List~Message~
    }

    Connection *--> User
    User o--> "1..*" Connection
    User o--> "0..*" Message
    User o--> Profile

    class Education {
        - school : String
        - degree : String
        - fieldOfStudy : String
        - startDate : String
        - endDate : String
    }

    class Experience {
        - title : String
        - company : String
        - startDate : String
        - endDate : String
        - description : String
    }

    class JobPosting {
        - ID : String
        - TITLE : String
        - DESCRIPTION : String
        - REQUIREMENTS : List~String~
        - LOCATION : String
        - POSTDATE : Timestamp
        + JobPosting(String id, String title, String description, List~String~ requirements, String location, Timestamp postDate)
        + getId() String
        + getTitle() String
        + getDescription() String
        + getRequirement() List~String~
        + getLocation() String
        + getPostDate() Timestamp
    }

    class LinkedInService {
        - instance : LinkedInService$
        - USERS : Map~String, User~
        - JOBPOSTINGS : Map~String, JobPosting~
        - NOTIFICATIONS : Map~String, List~Notification~~
        - LinkedInService()
        + getInstance() LinkedInService sync$
        + registerUser(User user) void
        + loginUser(String email, String password) User
        + updateUserProfile(User user) void
        + sendConnectionRequest(User sender, User receiver) void
        + acceptConnectionRequest(User user, User connectionUser) void
        + searchUsers(String keyword) List~User~
        + postJobListing(JobPosting jobPosting) void
        + searchJobPostings(String keyword) List~JobPosting~
        + sendMessage(User sender, User receiver, String content) void
        + addNotification(String userId, Notification notification) void
        + getNotifications(String userId) List~Notification~
        + generateNotificationId() String
        + generateMessageId() String
    }

    LinkedInService *--> "1..*" User
    LinkedInService o--> "0..*" JobPosting
    LinkedInService o--> "0..*" Notification

    class Message{
        - ID : String
        - SENDER : User
        - RECEIVER : User
        - CONTENT : String
        - TIMESTAMP : Timestamp
        + Message(String id, User sender, User receiver, String content, Timestamp timestamp)
    }

    Message *--> User

    class Notification {
        - ID : String
        - USER : User
        - TYPE : NotificationType
        - CONTENT : String
        - TIMESTAMP : Timestamp
        + Notification(String id, User user, NotificationType type, String content, Timestamp timestamp)
        + getId() String
        + getUser() String
        + getType() NotificationType
        + getContent() String
        + getTimestamp() Timestamp 
    }

    Notification *--> User
    Notification --> NotificationType

    class Profile {
        - profilePicture : String
        - headline : String
        - summary : String
        - experiences : List~Experience~
        - educations : List~Education~
        - skills : List~Skill~
        + setSummary(String summary) void
        + setHeadline(String headline) void
        + getProfilePicture() String
        + getHeadline() String
        + getSummary() String
        + getExperiences() List~Experience~
        + getEducations() List~Education~
        + getSkills() List~Skill~
    }

    Profile o--> Experience
    Profile o--> Education
    Profile o--> Skill

    class Skill {
        - name : String
    }

    class NotificationType {
        CONNECTION_REQUEST
        MESSAGE
        JOB_POSTING
    }
```

```java
public class LinkedInDemo {
	public static void run() {
		LinkedInService linkedInSrvc = LinkedInService.getInstance();

		// User registration
		User user1 = new User("1", "John Doe", "john@example.com", "password", new Profile(), new ArrayList<>(), new ArrayList<>(), new ArrayList<>());
		User user2 = new User("2", "Jane Smith", "jane@example.com", "password", new Profile(), new ArrayList<>(), new ArrayList<>(), new ArrayList<>());
		linkedInSrvc.registerUser(user1);
		linkedInSrvc.registerUser(user2);

		// User login
		User loggedInUser = linkedInSrvc.loginUser("john@example.com", "password");
		if (loggedInUser != null){
			println("User Logged in: " + loggedInUser.getName());
		} else {
			println("Invalid email or password")
		}

		// Update user profile
		Profile profile = new Profile();
		profile.setHeadline("Software Engineer");
		profile.setSummary("Passionate about coding & problem-solving");
		loggedInUser.setProfile(profile);
		linkedInSrvc.updateUserProfile(loggedInUser);

		// Send connection request
		linkedInSrvc.sendConnectionRequest(user1, user2);

		// Accept connection request
		linkedInSrvc.acceptConnectionRequest(user2, user1);

		// Post a job listing
		JobPosting jobPosting = new JobPosting("1", "Software Developer", "We are hiring!", Arrays.asList("Java", "Python"), "San Francisco", new Timestamp( System.currentTimeMillis() ));
		linkedInSrvc.postJobListing(jobPosting);

		// Search for users
		List<User> searchResults = linkedInSrvc.searchUsers("John");
		println("Search Results:");
		for(User user : searchResults){
			println("Name: " + user.getName());
			println("Headline: "+ user.getProfile().getHeadline());
			println();
		}

		// Search for job postings
		List<JobPosting> jobPostingResults = linkedInSrvc.searchJobPosting("Software");
		println("Job Posting Results:");
		for(JobPosting posting : jobPostingResults){
			println("Title: " + posting.getTitle());
			println("Description: " + posting.getDescription());
			println();
		}

		// Send a message
		linkedInSrvc.sendMessage(user1, user2, "Hi Jane, hope you're doing well!");

		// Get notifications
		List<Notification> notifications = linkedInSrvc.getNotifications(user2.getId());
		println("Notifications :");
		for(Notification notification : notifications){
			println("Type: " + notification.getType());
			println("Content: "+ notification.getContent());
			println();
		}
	}
}
```