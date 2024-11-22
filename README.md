# Google Apps Script Workshop: Interactive Functions in Google Docs

Welcome to the interactive Google Apps Script workshop! In this workshop, we will create some useful functions to enhance the functionality of Google Docs using Google Apps Script.

## Setup

1. **Create a New Google Document**:
   - Go to [Google Docs](https://docs.google.com) and create a new blank document.
   - Paste **Lorem Ipsum** text (around 100 words) into the document to work with.

2. **Open Google Apps Script**:
   - Click on `Extensions` in the Google Docs menu bar.
   - Select `Apps Script` to open the script editor in a new tab.

3. **Create a Function to Capitalize Sentences**:
   - In the Apps Script editor, paste the following code and save it.
   - This function will capitalize the first letter of each sentence in the document.

   ```javascript
   function capitalizeSentences() {
     var body = DocumentApp.getActiveDocument().getBody();
     var text = body.getText();
     var sentences = text.split(/([.!?]\s*)/);
     var capitalizedText = sentences.map(function(sentence) {
       return sentence.charAt(0).toUpperCase() + sentence.slice(1);
     }).join('');
     body.setText(capitalizedText);
   }
   ```

4. **Create a Custom Menu with a Button:**
- Let's add a dropdown menu with the "Capitalize Sentences" function in it. This menu will appear every time you open your document.

```javascript
function onOpen() {
  var ui = DocumentApp.getUi();
  ui.createMenu('My Custom Menu')
    .addItem('Capitalize Sentences', 'capitalizeSentences')
    .addToUi();
}
```

5. **Save and Close the Script Editor:**
- After writing the functions in the Apps Script editor, save your project.
- Refresh your Google Docs document to see the newly added menu item under My Custom Menu.

## Additional Functions

**1. Count Words in Document:**
- This function will count the number of words in the document and display it in an alert.

```javascript
function wordCount() {
  var body = DocumentApp.getActiveDocument().getBody();
  var text = body.getText();
  var wordCount = text.split(/\s+/).filter(word => word).length;
  DocumentApp.getUi().alert('The document contains ' + wordCount + ' words.');
}
```

**2. Count Sentences and Display Statistics**

- This function counts the number of sentences in the document and shows both word count and sentence count statistics.

```javascript
function documentStats() {
  var body = DocumentApp.getActiveDocument().getBody();
  var text = body.getText();
  var sentences = text.split(/[\.\!\?]+/).filter(Boolean);
  DocumentApp.getUi().alert(
    'Document Statistics:\n' +
    'Word Count: ' + text.split(/\s+/).filter(word => word).length + '\n' +
    'Sentence Count: ' + sentences.length
  );
}
```

# Congratulations!

You've just created several helpful functions that you can use in Google Docs. As you continue exploring Google Apps Script, you'll be able to automate even more tasks to improve your productivity.