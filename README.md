## Link Extractor - Documentation

### Motivation
During the development of my project, I needed a tool to extract links from a webpage and save them in a structured format. This helped me streamline the process of gathering relevant links and storing them for further analysis or reference.

### Overview
The Link Extractor is a JavaScript tool designed to extract links from a webpage based on a user-defined matching pattern. It then saves the extracted links in JSON format, which can be easily stored, manipulated, or used in other parts of a web application.

### How to Use
1. **Access the Tool**: To use the Link Extractor, you need to integrate the provided JavaScript code into your web application or use it in the browser's developer console while browsing a webpage.

2. **Enter Matching Pattern**: Upon execution, the tool prompts the user to enter a matching pattern. This pattern helps filter out the links that match a specific criterion. For example, you might enter `https://example.com/` to extract all links that start with this URL.

3. **Enter File Name**: After specifying the matching pattern, the tool prompts the user to enter a name for the JSON file where the extracted links will be saved. The file name should be provided without the `.json` extension.

4. **Extraction Process**: The tool then scans the webpage for anchor tags (`<a>` elements) and checks if their `href` attributes match the specified pattern. It collects all matching links and stores them in a JSON object.

5. **Save JSON File**: Once the extraction process is complete, the tool converts the JSON object into a formatted JSON string. It then creates a downloadable JSON file containing the extracted links.

6. **Access Saved Links**: The saved JSON file can be accessed and utilized according to the requirements of your project. You can load the JSON file into your application, store it locally, or perform any further processing as needed.

```js
var matchingPattern = prompt("Enter the matching pattern (e.g., https://leetcode.com/problems/):");
var fileName = prompt("Enter the name of the JSON file to be saved (without the .json extension):");
var links = document.getElementsByTagName('a');
var matchedLinks = [];

for (var i = 0; i < links.length; i++) {
    var href = links[i].href;
    if (href && href.indexOf(matchingPattern) !== -1) {
        matchedLinks.push(href);
    }
}

var jsonOutput = {
    "matchedLinks": matchedLinks
};

var jsonString = JSON.stringify(jsonOutput, null, 2);

console.log(jsonString);

var blob = new Blob([jsonString], { type: 'application/json' });
var url = URL.createObjectURL(blob);
var a = document.createElement('a');
a.href = url;
a.download = fileName + '.json';
document.body.appendChild(a);
a.click();
a.remove();

```

### Example Use Case
Suppose you are building a web application that aggregates links related to specific topics, such as educational resources or news articles. The Link Extractor can help automate the process of gathering relevant links from various webpages and organizing them in a structured format. This saves time and effort while ensuring consistency and accuracy in link collection.

### Conclusion
The Link Extractor is a handy tool for extracting links from webpages and saving them in JSON format. Its simplicity and flexibility make it suitable for a wide range of web development projects where link extraction and organization are essential tasks. Whether you're building a content aggregator, a research tool, or a data analysis platform, the Link Extractor can enhance your workflow and streamline the process of gathering valuable information from the web.
