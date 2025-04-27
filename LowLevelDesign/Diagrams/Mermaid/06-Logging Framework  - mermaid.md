

```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction TB
	class LogLevel {
        <<enumeration>>
        DEBUG
        INFO
        WARNING
        ERROR
        FATAL
    }
	
	class LoggerConfig {
        - logLevel : LogLevel
        - logAppender : LogAppender
        + LoggerConfig(LogLevel logLevel, LogAppender logAppender)
        + getLogLevel() LogLevel
        + setLogLevel(LogLevel logLevel) void
        + getLogAppender() LogAppender
        + setLogAppender(LogAppender logAppender) void
    }
	
	
	class LogAppender {
        <<interface>>
        + append(LogMessage logMessage) void
    }
	LoggerConfig *--> LogLevel
	LoggerConfig *--> LogAppender
	
	class LogAppender {
        <<interface>>
        + append(LogMessage logMessage) void
    }
    class ConsoleAppender {
        + append(LogMessage logMessage) void
    }
    class DatabaseAppender {
        - JDBC_URL : String
        - USERNAME : String
        - PASSWORD : String
        + DatabaseAppender(String jdbcUrl, String username, String password)
        + append(LogMessage logMessage) void
    }
	class FileAppender {
        - FILE_PATH : String
        + FileAppender(String filePath)
        + append(LogMessage logMessage) void
    }
    LogAppender <|.. ConsoleAppender
	LogAppender <|.. DatabaseAppender
	LogAppender <|.. FileAppender    
```


```mermaid
%%{init: {'themeVariables': {'fontSize': '10px'}}}%%
classDiagram
	direction LR
    class Logger {
        - INSTANCE : Logger$
        - config : LoggerConfig
        - Logger()
        + getInstance() Logger$
        + setConfig(LoggerConfig config) void
        + log(LogLevel level, String message) void
        + debug(String message) void
        + info(String message) void
        + warning(String message) void
        + error(String message) void
        + fatal(String message) void
    }

	class LogMessage {
        - LEVEL : LogLevel
        - MESSAGE : String
        - TIMESTAMP : long
        + LogMessage(LogLevel level, String message)
    }


    Logger *--> LoggerConfig 
	Logger *--> LogMessage 
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