# Price Drop Alert - Amazon Price Tracker

## Overview
This Python application monitors the price of a product on Amazon. It tracks a specific product's price and notifies the user via email when the price drops below a specified threshold. The application uses **PyQt5** for the graphical user interface (GUI) and **Selenium** for web scraping to fetch the product price. **BeautifulSoup** is used for HTML parsing to extract relevant data, and **smtplib** is used to send email alerts.

## Features:
- **Price Monitoring**: Monitors the price of a product on Amazon and compares it to a user-defined threshold.
- **Email Notification**: Sends an email alert to the user when the price drops below the set threshold.
- **Price Validation**: Ensures that the product URL, price, and email are valid before proceeding.
- **Amazon Product Scraping**: Uses **Selenium** and **BeautifulSoup** to fetch product details from Amazon.
- **User-Friendly GUI**: The application features a simple and intuitive GUI built with **PyQt5**.

## Requirements
- Python 3.x
- Libraries:
  - **PyQt5** for the graphical user interface
  - **Selenium** for web scraping
  - **BeautifulSoup4** for HTML parsing
  - **requests** for HTTP requests
  - **lxml** for handling XML and HTML parsing
  - **webdriver_manager** for managing the Chrome WebDriver automatically
  - **smtplib** for sending email alerts
  
Install the required dependencies with:
```bash
pip install PyQt5 selenium webdriver-manager requests beautifulsoup4 lxml
```

## Installation
1. Clone the repository or download the files.
   ```bash
   git clone https://github.com/yourusername/amazon-price-tracker.git
   cd amazon-price-tracker
   ```

2. Make sure you have the required libraries installed (see above).

3. Run the application:
   ```bash
   python main.py
   ```

4. The GUI will open, where you can input:
   - Amazon product URL
   - Desired price threshold
   - Your email address to receive notifications

## Code Structure

### **MainWindow Class (GUI)**
The main GUI class inherits from `QMainWindow` and `Ui_MainWindow`. It manages the user interface, including:
- Accepting the Amazon product URL.
- Allowing the user to set a price threshold.
- Allowing the user to input their email address.
- Performing validations on the inputs.
- Fetching the price of the product using **Selenium** and **BeautifulSoup**.
- Sending email alerts when the price drops below the specified threshold.

### **Validator Function**
The `validator` function ensures:
- The Amazon URL is correctly formatted (`amazon.in`).
- The price input is a valid number.
- The email address is in a proper format.

### **Scraping and Emailing Logic**
- The application uses **Selenium** to open the Amazon product page and extract the title and price.
- If the price is lower than the threshold, an email is sent using **smtplib**.
- The email contains the Amazon product link and notifies the user of the price drop.

### **smail Function**
The `smail` function is responsible for sending the email alert using the Gmail SMTP server. The function logs into a Gmail account (`amazon.price.drop1@gmail.com`) and sends a message to the user’s provided email address when the price falls below the set threshold.

### **MessageBox Function**
The `msgbox` function is used to show different types of messages to the user, such as:
- Alerts for wrong inputs
- Information about price drops
- Warnings for errors
- Success messages for sending the email

## Example Workflow:
1. **User Input**: The user enters the Amazon product URL, a target price, and their email address in the GUI.
2. **Product Scraping**: When the user clicks the "Submit" button, the application scrapes the Amazon product page to fetch the current price.
3. **Price Comparison**: If the product price is below the specified target price, an email is sent to the user.
4. **Email Notification**: The user receives an email alerting them that the price has dropped.

## Example Conversation:
- **User**: Enters the URL for an Amazon product, such as "https://www.amazon.in/Test-Exclusive-550/dp/B077Q7GW9V".
- **User**: Sets a price threshold, such as ₹2000.
- **User**: Enters their email address, e.g., "user@example.com".
- **App**: Scrapes the product price and checks if it’s below ₹2000. If so, it sends an email notification to the user with the subject "Price fell down" and a link to the product.

## Screenshots
![Amazon Price Tracker GUI](screenshots/gui.png)

## Troubleshooting
- **Invalid Email**: Make sure your email address is correctly formatted.
- **Price Parsing Issue**: Ensure that the Amazon product page is accessible and contains the price details.
- **No Email Sent**: Check your internet connection and confirm that the Gmail account used for sending emails is properly configured.
