# QA-Tools
Guides for using JIRA, Selenium, and Postman.
# JIRA Basics for Testers

## Key Features:
- **Create and Manage Issues:** Log and track bugs or tasks.
- **Sprint Planning:** Collaborate with developers on Agile projects.
- **Defect Reporting:** Assign defects with priority and severity.

## Steps to Log a Bug:
1. Navigate to the "Create Issue" screen.
2. Fill in the required fields:
   - **Summary:** Short description of the bug.
   - **Description:** Detailed steps to reproduce.
   - **Priority:** Critical, High, Medium, Low.
   - **Attachments:** Add screenshots if available.
3. Assign the issue to the appropriate team member.
4. Click "Create."

# Postman Basics for Testers

## Key Features:
- **API Testing:** Send requests and validate responses.
- **Collections:** Group and organize related requests.
- **Environments:** Manage environment-specific variables (e.g., QA, Production).
- **Assertions:** Write test scripts to validate API responses.

## Steps to Test an API:
1. **Launch Postman.**
2. **Create a Request:**
   - Select the HTTP method (e.g., GET, POST, PUT, DELETE).
   - Enter the API endpoint URL.
   - Add required headers (e.g., `Content-Type: application/json`).
   - For POST/PUT, provide the request body (JSON format).
3. **Send the Request:**
   - Click on the **Send** button.
   - View the response status (e.g., 200 OK, 404 Not Found) and the response body.
4. **Write Assertions:**
   - Go to the **Tests** tab.
   - Add scripts like:
     ```javascript
     pm.test("Status code is 200", function () {
         pm.response.to.have.status(200);
     });
     pm.test("Response time is less than 500ms", function () {
         pm.expect(pm.response.responseTime).to.be.below(500);
     });
     ```

## Bonus Tips:
- Use **Pre-request scripts** to set up authentication tokens dynamically.
- Export and share **Collections** with team members.
- Integrate Postman with CI/CD tools for automated testing.

# Selenium Basics for Testers

## What is Selenium?
Selenium is an open-source framework for automating web application testing across different browsers and platforms.

## Key Features:
- **Cross-Browser Testing:** Works on Chrome, Firefox, Safari, and more.
- **Scripted Automation:** Automate UI interactions with a web application.
- **Supports Multiple Languages:** Java, Python, C#, etc.
- **Integration:** Works with CI/CD tools like Jenkins.

## Getting Started:
1. **Install Selenium:**
   - Install Selenium WebDriver for your preferred programming language (e.g., `pip install selenium` for Python).
   - Download the appropriate browser driver (e.g., ChromeDriver for Chrome).

2. **Write Your First Selenium Script:**
   Example in Python:
   ```python
   from selenium import webdriver
   from selenium.webdriver.common.keys import Keys

   # Set up the driver
   driver = webdriver.Chrome(executable_path="path_to_chromedriver")
   
   # Open a website
   driver.get("https://example.com")
   
   # Perform actions
   search_box = driver.find_element("name", "q")
   search_box.send_keys("Selenium WebDriver")
   search_box.send_keys(Keys.RETURN)

   # Verify the page title
   assert "Selenium" in driver.title

   # Close the browser
   driver.quit()

