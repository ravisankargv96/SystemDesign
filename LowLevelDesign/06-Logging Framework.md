```java
public enum LogLevel {
	DEBUG,
	INFO,
	WARNING,
	ERROR,
	FATAL
}
```

```java
@Getter
@ToString
public class LogMessage {
	private final LogLevel level;
	private final String message;
	private final long timestamp;

	public LogMessage(LogLevel level, String message){
		this.level = level;
		this.message = message;
		this.timestamp = System.currentTimeMillis();
	}
}
```

```java
public interface LogAppender {
	void append(LogMessage logMessage);
}
```

```java
public class ConsoleAppender implements LogAppender {
	@Override
	public void append(LogMessage logMessage) {
		println(logMessage)
	}
}
```

```java
public class DatabaseAppender implements LogAppender {
	private final String jdbcUrl;
	private final String username;
	private final String password;

	public DatabaseAppender(String jdbcUrl, String username, String password){
		this.jdbcUrl = jdbcUrl;
		this.username = username;
		this.password = password;
	}

	@Override
	public void append(LogMessage logMessage){
		
		try (
			Connection connection = DriverManager.getConnection(jdbcUrl, username, password);
			PreparedStatement statement = connection.prepareStatement("INSERT INTO logs (level, message, timestamp) VALUES (?, ?, ?)");)
			statement.setString(1, logMessage.getLevel().toString());
			statement.setString(2, logMessage.getMessage());
			statement.setString(3, logMessage.getTimestamp());
			statement.executeUpdate();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}
}
```

```java
public class FileAppender implements LogAppender {
	private final String filePath;

	public FileAppender(String filePath){
		this.filePath = filePath;
	}

	@Override
	public void append(LogMessage logMessage){
		try (FileWriter writer = new FileWriter(filePath, true)) {
			writer.write(logMessage.toString() + "\n");
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```

```java
public class LoggerConfig {
	private LogLevel logLevel;
	private LogAppender logAppender;

	public LoggerConfig(LogLevel logLevel, LogAppender logAppender){
		this.logLevel = logLevel;
		this.logAppender = logAppender;
	}

	public LogLevel getLogLevel(){
		return logLevel;
	}

	public void setLogLevel(LogLevel logLevel){
		this.logLevel = logLevel;
	}

	public LogAppender getLogAppender(){
		return logAppender;
	}

	public void setLogAppender(LogAppender logAppender){
		this.logAppender = logAppender;
	}
}
```


```java
public class Logger {
	private static final Logger instance;
	private LoggerConfig config;

	private Logger() {
		// private constructor to enforce singleton pattern
		config = new LoggerConfig(LogLevel.INFO, new ConsoleAppender());
	}

	public static Logger getInstance() {
		if(instance == null){
			instance = new Logger();
		}
		return instance;
 	}

	public void setConfig(LoggerConfig config) {
		this.config = config;
	}

	public void log(LogLevel level, String message){
		if(level.ordinal() >= config.getLogLevel().ordinal()) {
			LogMessage logMessage = new LogMessage(level, message);
			config.getLogAppender().append(logMessage);
		}
	}

	public void debug(String message){
		log(LogLevel.DEBUG, message);
	}

	public void info(String message) {
		log(LogLevel.INFO, message);
	}

	public void warning(String message){
		log(LogLevel.WARNING, message);
	}

	public void error(String message){
		log(LogLevel.ERROR, message);
	}

	public void fatal(String message){
		log(LogLevel.FATAL, message);
	}
}
```

Client Code

```java
public class LoggingFrameworkDemo {
	public static void run(){
		Logger logger = Logger.getInstance();

		// Logging with default configuration
		logger.info("This is an information message");
		logger.warning("This is a warning message");
		logger.error("This is an error message");

		// Changing log level & appender
		LoggerConfig config = new LoggerConfig(LogLevel.DEBUG, new FileAppender("app.log"));
		logger.setConfig(config);

		logger.debug("This is a debug message");
		logger.info("This is an information message");
	}
}
```