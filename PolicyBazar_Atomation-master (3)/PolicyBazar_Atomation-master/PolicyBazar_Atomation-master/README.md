-----

# Policybazaar Automation Suite 🚀

## Project Overview

This project is a robust automated testing suite designed to interact with the **Policybazaar.com** website. It automates key insurance-related scenarios, demonstrating advanced web automation techniques. The suite is built with **Selenium WebDriver** in **Java**, leverages **WebDriverManager** for seamless browser driver management, adopts the **Page Object Model (POM)** design pattern for highly maintainable and scalable tests, and utilizes **Cucumber BDD Framework** with **TestNG** for structured, readable, and executable specifications.

-----

## Problem Statements / Automation Scenarios

This automation suite addresses the following specific scenarios on Policybazaar.com, defined as Gherkin features:

1.  ### Find Travel Insurance Plan for Students ✈️

      * **Objective:** Automate the process of finding international travel insurance plans specifically for students.
      * **Feature File:** `TravelInsurance.feature`
      * **Details:** The automation, driven by `TravelInsuranceSteps.java` and using the `TravelInsurance_Page` object, navigates to the travel insurance section, enters a destination country (e.g., **"France"**), selects specific travel dates (e.g., **August 1, 2025 - August 20, 2025**), and specifies **2 student travelers (aged 21 and 22)** with no pre-existing diseases. It then proceeds to view available plans.
      * **Output:** The script is designed to **display the three lowest-priced international travel insurance plans**, including their respective **amounts and insurance provider companies** (this display logic would be implemented in subsequent steps not yet provided but expected within the same scenario).

2.  ### Get a Car Insurance Quote (Error Handling Validation) 🚗

      * **Objective:** Automate the process of getting a car insurance quote while specifically testing error handling for invalid inputs.
      * **Feature File:** `CarInsurance.feature`
      * **Details:** The script, driven by `CarInsuranceSteps.java`, navigates to the car insurance page. It then simulates a user proceeding without entering a car number, followed by selecting the city, car brand, car model, fuel type, and variant. Finally, it attempts to submit user details with a username ("John Doe") and an **invalid mobile number ("87676788")** obtained from the `config.properties` file.
      * **Output:** The automation captures the error message displayed for the invalid mobile number field and **asserts that it contains the substring "valid"**, demonstrating robust error handling capabilities for invalid data entry.

3.  ### Retrieve Health Insurance Menu Items 🏥

      * **Objective:** Automate the extraction of all health insurance menu items from the Policybazaar website.
      * **Feature File:** `MedicalInsurance.feature`
      * **Details:** The script, driven by `MedicalInsuranceSteps.java` and using the `MedicalInsurancePage` object, navigates to the "View all products" section (which acts as the entry point to list medical options). It then fetches all listed medical insurance options.
      * **Output:** The automation **asserts that more than zero options are found** and then **prints all fetched medical insurance options to the console** for verification.

-----

## Key Automation Scope

The project employs and demonstrates proficiency in the following core web automation techniques:

  * **Behavior-Driven Development (BDD):** Structured tests written in human-readable Gherkin syntax (defined in `.feature` files), executed by Cucumber, enhancing collaboration and understanding between technical and non-technical stakeholders.
  * **Browser Management:** Dynamic initialization and management of Chrome, Firefox, and Edge browsers using **WebDriverManager** (`BaseBrowserSetup`).
  * **Page Object Model (POM):** Extensively implemented for structured, reusable, and highly maintainable test code across `BaseBrowserSetup`, `CarInsurance_Page`, `MedicalInsurancePage`, and `TravelInsurance_Page`.
  * **Cucumber Hooks:** Intelligent utilization of `@Before` and `@After` annotations with **tags** in step definition classes (e.g., `CarInsuranceSteps`, `MedicalInsuranceSteps`, `TravelInsuranceSteps`) for setting up and tearing down browser instances **per scenario or group of scenarios**. This ensures test isolation and efficient resource management.
  * **External Configuration Management:** Reading test data and configuration values (like invalid mobile numbers) from external property files using a `ConfigReader.java` utility, promoting flexibility and easy data management.
  * **Explicit Waits:** Robust use of `WebDriverWait` and `ExpectedConditions` to handle dynamic page loads, asynchronous operations, and ensure elements are present, visible, or clickable before interaction.
  * **JavaScript Executor:** Employed for advanced UI interactions, including scrolling elements into view (`scrollToElement`), visually highlighting elements during execution (`highlightElement` for debugging/demonstration), and performing clicks on elements that might be otherwise intercepted by other elements (`jsClick`).
  * **Actions Class:** Used for performing complex user interactions such as `moveToElement` for hovering or ensuring elements are in the viewport.
  * **Robust Click Handling:** Custom `waitAndClick` methods to handle common Selenium exceptions like `ElementClickInterceptedException` by gracefully falling back to JavaScript clicks, enhancing test reliability.
  * **Form Filling & Interaction:** Automation of filling various web form fields, including text inputs, selecting options from dropdowns, and interacting with date pickers.
  * **Error Message Capture & Validation:** Identifying and extracting warning/error messages displayed on the UI for assertion using TestNG's `Assert.assertTrue`, vital for negative test scenarios.
  * **Data Extraction & Collection:** Retrieving specific data points (e.g., insurance plan details, menu items) from web pages and storing them efficiently in Java collections (`ArrayList`, `List`).
  * **Dynamic Element Interaction:** Handling dynamically loaded or changing UI elements effectively.
  * **Test Tagging:** Strategic usage of Cucumber tags (e.g., `@Smoke`, `@MedicalInsurance`, `@TravelInsurance`, `@CarInsurance`) for selective test execution, enabling flexible regression and sanity testing.
  * **Comprehensive Test Reporting:** Generation of multiple report types including standard HTML, JSON, and rich graphical reports via ExtentReports, providing detailed insights into test execution status.
  * **Rerun Capability:** Configuration to generate a `failed_scenarios.txt` file, enabling efficient re-execution of only failed tests.

-----

## Technologies Used

  * **Programming Language:** Java ☕ (JDK 11)
  * **Web Automation Library:** Selenium WebDriver (v4.21.0)
  * **BDD Framework:** Cucumber (v7.18.0)
  * **Test Runner:** TestNG (v7.8.0)
  * **Browser Driver Management:** WebDriverManager by Boni Garcia (v5.8.0)
  * **Build Tool:** Apache Maven
  * **Logging:** Apache Log4j (v2.23.1) and SLF4j (v2.0.13)
  * **Data Handling:** Apache POI (v5.2.5) for Excel operations (if implemented for data reading/writing)
  * **Reporting:**
      * Cucumber HTML Report
      * Cucumber JSON Report
      * ExtentReports with ExtentCucumberAdapter (v1.14.0)
      * Rerun plugin for failed scenarios
  * **Browsers Supported:** Google Chrome, Mozilla Firefox, Microsoft Edge
  * **Design Pattern:** Page Object Model (POM)

-----

## Setup and Installation

To get this project running on your local machine, follow these steps:

1.  ### Prerequisites

      * **Java Development Kit (JDK):** Ensure you have **JDK 11 or higher** installed. You can download it from [Oracle's website](https://www.oracle.com/java/technologies/downloads/) or use OpenJDK.
      * **Apache Maven:** This project is built with Maven. Download and install Maven from [Apache Maven's official website](https://maven.apache.org/download.cgi).
      * **Internet Connection:** Required for WebDriverManager to automatically download browser drivers the first time they are needed.

2.  ### Clone the Repository

    Open your terminal or command prompt and run:

    ```bash
    git clone 
    cd PolicyBazar_Automation
    ```

3.  ### Install Dependencies

    Navigate to the project's root directory (where your `pom.xml` file is located) and run the Maven command to download all necessary dependencies and compile the project:

    ```bash
    mvn clean install
    ```

    Browser drivers (Chrome, Firefox, Edge) are automatically managed and downloaded by WebDriverManager at runtime when `BaseBrowserSetup.initializeBrowser` is called.

4.  ### Configure Test Data

      * The project utilizes a `ConfigReader` utility to fetch test data and settings from a **`config.properties`** file.
      * This file should be located under `src/test/resources`.
      * Example content for `config.properties`:
        ```properties
        # Car Insurance Test Data
        car.insurance.username=John Doe
        car.insurance.invalid.mobile=87676788
        ```
      * *Ensure the actual values in your `config.properties` match your testing requirements.*

-----

## How to Run

After completing the setup, you can execute the automation tests:

1.  **Ensure all prerequisites and installation steps are complete.**

2.  **Open your IDE** (e.g., IntelliJ IDEA, Eclipse) and import the Maven project.

3.  **Run the tests:**
    The primary way to run tests is via the **`TestRunner.java`** class, which acts as the entry point for Cucumber.

      * **From IDE:**
          * Navigate to `src/test/java/com/policybazaar/runners/TestRunner.java`.
          * Right-click on `TestRunner.java` and select "Run 'TestRunner'".
          * This will execute all scenarios tagged with `@Smoke` (or whatever tag is specified in `TestRunner.java`). Note that `@Before` and `@After` hooks with specific tags (e.g., `@TravelInsurance`) will ensure the correct browser setup and teardown for relevant scenarios.
      * **Via Maven Command Line:**
        ```bash
        mvn test
        ```
        This command will execute all tests defined by the `TestRunner.java` class, respecting its `@CucumberOptions` configuration (e.g., running scenarios tagged `@Smoke`). The `maven-surefire-plugin` is configured to include `**/*Runner.java` for execution.

4.  **Observe the browser automation** as it navigates through Policybazaar.com. You will see elements being **highlighted in red** as the automation interacts with them, providing visual feedback.

5.  **Check the console output** for displayed information such as:

      * Messages indicating successful navigation and interactions.
      * The three lowest travel insurance plan details (if implemented in the Gherkin scenario and step definitions).
      * Captured car insurance error messages (along with assertion results).
      * The list of health insurance menu items.

-----

## Project Structure

This project rigidly follows the industry-standard **Page Object Model (POM)** design pattern combined with the **Cucumber BDD framework** for robust, readable, and highly maintainable test automation.

```
PolicybazaarAutomationSuite/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── policybazaar/
│   │               ├── base/             # Contains core setup and utility classes
│   │               │   └── BaseBrowserSetup.java  # Initializes and manages WebDriver
│   │               ├── pages/            # Page Object classes, encapsulating UI elements and actions for specific pages/sections
│   │               │   ├── CarInsurance_Page.java   # Interactions for Car Insurance flow
│   │               │   ├── MedicalInsurancePage.java  # Interactions for Medical Insurance menu
│   │               │   └── TravelInsurance_Page.java  # Interactions for Travel Insurance plan search
│   │               │   └── [HomePage.java]          # (Optional) For common home page elements or shared header elements
│   │               └── utilities/        # Utility classes (e.g., ConfigReader, custom listeners, common helpers)
│   │                   └── ConfigReader.java # Reads properties from configuration files
│   ├── test/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── policybazaar/
│   │   │           ├── runners/          # Test Runner classes for Cucumber
│   │   │           │   └── TestRunner.java # Configures and runs Cucumber features via TestNG
│   │   │           └── stepdefinitions/  # Step Definition classes, linking Gherkin steps to Java code
│   │   │               ├── CarInsuranceSteps.java     # Step definitions for Car Insurance scenario
│   │   │               ├── MedicalInsuranceSteps.java # Step definitions for Medical Insurance scenario
│   │   │               └── TravelInsuranceSteps.java  # Step definitions for Travel Insurance scenario
│   │   └── resources/
│   │       ├── features/         # Gherkin Feature files defining test scenarios (one per major feature/story)
│   │       │   ├── CarInsurance.feature    # Feature for Car Insurance quote submission
│   │       │   ├── MedicalInsurance.feature # Feature for Medical Insurance options retrieval
│   │       │   └── TravelInsurance.feature  # Feature for Travel Insurance plan search
│   │       └── config.properties # Configuration file for test data and environment settings
├── data/                         # (Future) Directory for external test data files (e.g., .csv, .json, .xlsx)
├── target/                       # Generated by Maven: compiled classes, test results, and reports
│   └── cucumber-reports/         # HTML and JSON Cucumber reports
│   └── extent-reports/           # ExtentReports HTML report
│   └── failed_scenarios.txt      # List of failed scenarios for re-run purposes
├── pom.xml                       # Maven Project Object Model file: manages all dependencies, build plugins, and project metadata
└── README.md                     # This comprehensive documentation file
```

-----

## Reporting

This automation suite generates comprehensive reports to provide insights into test execution:

  * **Cucumber HTML Report:** A basic, human-readable HTML report located at `target/cucumber-reports/cucumber-html-report.html`.
  * **Cucumber JSON Report:** A machine-readable JSON report for integration with other tools, located at `target/cucumber-reports/cucumber.json`.
  * **ExtentReports:** A rich, interactive, and visually appealing HTML report generated by `com.aventstack.extentreports.cucumber.adapter.ExtentCucumberAdapter:`. This report provides detailed test execution summaries, step-by-step logs, and visual feedback. You'll find it typically under `target/ExtentReports/`.
  * **Rerun File:** A `target/failed_scenarios.txt` file is generated, listing any failed Cucumber scenarios. This file can be conveniently used to re-execute only the failed tests, significantly saving time during debugging cycles.

-----

## Contributing

Contributions are welcome to enhance this automation suite\! If you'd like to contribute, please follow these guidelines:

1.  **Fork the repository:** Create your own copy of the project.
2.  **Create a new branch:** For each new feature or bug fix, create a dedicated branch (e.g., `git checkout -b feature/add-new-scenario` or `bugfix/fix-stale-element`).
3.  **Implement your changes:** Ensure your code adheres to the existing **Page Object Model** and coding style.
      * For new features, define your scenarios clearly in a new or existing `.feature` file.
      * Create corresponding Page Objects (if new UI elements are involved) or update existing ones.
      * Implement the step definitions in the appropriate step definition class, linking Gherkin steps to your Java automation code.
4.  **Write/Update Tests:** Add new Cucumber scenarios for new features or update existing ones for bug fixes. Ensure all existing tests pass with your changes.
5.  **Commit your changes:** Use clear, concise, and descriptive commit messages (e.g., `git commit -m 'Feat: Implement flight insurance search functionality'`).
6.  **Push to your branch:** `git push origin feature/your-feature-name`.
7.  **Open a Pull Request (PR):** Submit a PR to the `main` branch with a detailed description of your changes and why they were made. Please link any relevant issues or feature requests.

-----

## License

This project is licensed under the [e.g., MIT License](https://opensource.org/licenses/MIT). You should create a `LICENSE.md` file in the root of your repository with the full text of your chosen license.

-----

## Acknowledgements

  * **Selenium WebDriver:** The industry-standard library that powers robust web browser automation.
  * **WebDriverManager by Boni Garcia:** Greatly simplifies and automates the management of browser drivers, making setup effortless.
  * **Apache Maven:** The powerful build automation tool used for dependency management and project compilation.
  * **Cucumber:** The Behavior-Driven Development (BDD) framework for writing human-readable and executable test specifications.
  * **TestNG:** The popular test runner framework integrated with Cucumber for flexible test execution and comprehensive reporting.
  * **ExtentReports:** For generating rich, interactive, and visually appealing test reports, enhancing test analysis.
  * Special thanks to the open-source community for providing these invaluable tools.

-----
