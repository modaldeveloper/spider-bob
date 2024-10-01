# spider-bob
### A script to send multiple emails at once using a google sheets database
-----
##### Getting Started

1. Login to Google Sheets
2. Open a Blank Sheet
3. Add a list of Emails to a Row of Cells
4. Click on `Extensions` > `Apps Script`
5. Open your `Editor`
6. Import code

```    function myFunction() {
  emailEveryone(); // Call the emailEveryone function correctly here
}

function emailEveryone() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var emailRange = sheet.getRange('A1:A'); // Adjust this to match the exact range of emails
  var emailValues = emailRange.getValues();
  
  var subject = "Seed Funding Investment Opportunity"; // Your subject line
  var plainMessage = "Hello,\n\nBest regards,\n[Your Name]"; // Plain-text fallback message
  
  var htmlMessage = `
    <h2>Hello World!</h2> // Introduction
        <p>Abracadabra</p> // Paragraph
        <p>Neater format</p>// Paragraph 2
            <footer>
                <p>Sincerely Bob</p>
            </footer>
  `;

  // Loop through each email in the range and send the email
  for (var i = 0; i < emailValues.length; i++) {
    var emailAddress = emailValues[i][0];
    if (emailAddress) { // Check if email is not empty
      MailApp.sendEmail({
        to: "Youremail@youremail.com", // your email or list of emails goes here
        subject: subject,
        body: plainMessage, // Plain text fallback
        htmlBody: htmlMessage // HTML formatted message
      });
    }
  }
}
```
7. Run `debug` tool to check for errors
8. Click `Deploy`



