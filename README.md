# Selenium Grid Setup

This repository contains instructions and scripts to set up and use Selenium Grid for parallel test execution across different browsers and operating systems.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running Selenium Grid](#running-selenium-grid)
- [Creating Nodes](#creating-nodes)
- [Running Tests](#running-tests)
- [License](#license)

## Introduction

Selenium Grid is a tool that allows you to run your tests on different machines against different browsers in parallel. This can significantly speed up your testing process.

## Prerequisites

- Java 8 or higher
- Maven (optional, if using Maven for your project)
- Browsers installed (e.g., Chrome, Firefox)

## Installation

1. Download the latest Selenium Server from the [Selenium Releases](https://www.selenium.dev/downloads/) page.
2. Make sure to have the appropriate WebDriver binaries (e.g., ChromeDriver, GeckoDriver) in your system's PATH or specify their locations.

## Running Selenium Grid

To start the Selenium Grid Hub:

```bash
java -jar selenium-server-<version>.jar hub
```

To start a Selenium Node:

```bash
java -Dwebdriver.chrome.driver="path/to/chromedriver" -jar selenium-server-<version>.jar node
```

### Notes
- Replace `<version>` with the actual version number of the Selenium Server you downloaded.
- Ensure the path to the WebDriver executable is correct.

## Creating Nodes

You can add multiple nodes by specifying the necessary capabilities. Hereâ€™s a sample command:

```bash
java -Dwebdriver.gecko.driver="path/to/geckodriver" -jar selenium-server-<version>.jar node --detect-drivers true
```

## Running Tests

Run your Selenium tests against the Grid using the following code snippet:

```java
DesiredCapabilities caps = new DesiredCapabilities();
caps.setBrowserName("chrome"); // or "firefox", etc.

WebDriver driver = new RemoteWebDriver(new URL("http://<hub-ip>:4444"), caps);
driver.get("http://example.com");
```

Replace `<hub-ip>` with the IP address of your Selenium Grid hub.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

