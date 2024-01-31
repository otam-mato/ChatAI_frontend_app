## Front-end ChatAI

### Final result:

<br>

<img width="1000" alt="image" src="https://github.com/otam-mato/ChatAI_frontend_app/assets/113034133/7072215a-ce77-4a5e-9318-162bf21fcfbb">

<br>

**[link to the source code](https://github.com/otam-mato/ChatAI_frontend_app/blob/main/index.html)**

**[link to the deployed app on github pages]()**

---

### User stories

1. **Capture Form Data and Display on Page**: As a front-end developer, I want to start by writing a JavaScript function that captures the text from the textarea and displays it in a designated section on my web page when I press the submit button, using an **`onclick`** event handler and DOM manipulation methods like **`document.getElementById`** and **`textContent`**.
2. **API Key Entry**: As a front-end developer, I want to create a secure input field for entering my API key and storing it in a local variable, which I understand will only be for the learning process and not for a production environment.
3. **Store API Key Temporarily**: As a front-end developer, I want to temporarily store my entered API key in a JavaScript variable upon form submission and then remove the input field from the UI for subsequent chats.
4. **Send API Requests**: As a front-end developer, I want to write a JavaScript function that sends the captured text to the OpenAI API, using the **`https://api.openai.com/v1/chat/completions`** endpoint with the API key in the header, and to get a response, using **`fetch()`** and **`.then()`** (and probably not using `async`/`await`, unless you are confident using it).
5. **Handle API Responses**: As a front-end developer, I want to take the response from the OpenAI API and display it in the designated section, using methods like **`JSON.parse()`** and `**JSON.stringify**` and updating the DOM to display the response.
6. **Enhance User Interaction**: As a front-end developer, I want to add CSS to make the interaction with my bot more visually appealing.

### Stretch stories

1. **Send Chat History with API Requests**: As a front-end developer, I want to include the chat history in each API request to OpenAI. This will involve appending previous chat messages and responses to the request payload, ensuring the AI can contextualise new messages based on the ongoing conversation.
2. **Create a separate config file for Environment Variables**: As a front-end developer, I aim to create my own config file for storing sensitive information like the OpenAI API key and exclude it from GitHub using a `.gitignore` file. I plan to manually load these variables at the start of my application, understanding this approach doesn't offer real security in a front-end only environment but is valuable for learning about environment variables.


---

### Implementation

We created an HTML file for a web page that implements a simple chat interface using the OpenAI GPT-3.5 model. Here's a brief overview of the structure and functionality:

1. **HTML Structure:**
   - The HTML document starts with the usual structure, including the `<!DOCTYPE html>` declaration and the opening `<html>` tag.
   - The `<head>` section includes meta tags for character set and viewport settings, as well as a title for the web page.
   - CSS styles are embedded within the `<style>` tag in the `<head>` section.

2. **CSS Styles:**
   - Styles define the appearance of various elements on the page.
   - The overall layout uses flexbox for centering and responsiveness.
   - Different styles are applied to the form, buttons, input fields, and other elements to create a clean and modern design.
   - Media queries are used to adjust styles for screens with a maximum width of 768 pixels (e.g., for mobile devices).

3. **JavaScript:**
   - JavaScript code is included in the `<script>` tag at the end of the document.
   - The script manages the interaction with the OpenAI GPT-3.5 API, handles API key storage/retrieval, and updates the UI dynamically.
   - Functions like `addApiKey`, `deleteApiKey`, `searchQuestion`, and `clearHistory` handle user input and API interactions.
   - The script fetches user questions and displays responses, maintaining a history of Q&A interactions.

4. **API Interaction:**
   - The OpenAI GPT-3.5 API is used to generate responses to user questions.
   - The `makeChatGPTApiCall` function constructs the API request, **including messages from the conversation history**.
   - The conversation history is stored in the `questionHistory` variable, which is updated as users interact with the chat.

5. **LocalStorage Usage:**
   - LocalStorage is used to persist the API key and question history even if the user refreshes the page.

6. **Initialization:**
   - The `checkApiKeyStatus` function is called immediately to check if an API key is present and adjust the display accordingly.
   - The `displayQuestionHistory` function is called to populate the UI with the existing question history.

7. **Event Listeners:**
   - Event listeners are attached to form submissions, button clicks, and the "Clear History" button to trigger corresponding functions.

8. **Responsiveness:**
   - The page layout is designed to be responsive, adjusting its appearance for smaller screens using media queries.
  
---

### More details on key parts of the JavaScript:

The JavaScript code handles the main functionality of your chat interface, including API interactions, updating the UI, and managing the question history.

- **Global Variables:** `apiKeyValue` and `questionHistory` are global variables to store the API key and question history. They are initialized based on the values stored in LocalStorage.

- **Functions:**
  - `hideApiForm`: Hides the API form.
  - `addApiKey`: Adds the API key to LocalStorage and hides the API form.
  - `deleteApiKey`: Deletes the API key from LocalStorage and shows the API form.
  - `searchQuestion`: Initiates the search for a user's question, makes an API call, and updates the question history.
  - `updateQuestionHistory`: Updates the question history and displays it on the UI.
  - `makeChatGPTApiCall`: Constructs and sends the API call to OpenAI GPT-3.5.
  - `clearHistory`: Clears the question history from LocalStorage and the UI.
  - `checkApiKeyStatus`: Checks the status of the API key and adjusts the display accordingly.
  - `displayQuestionHistory`: Displays the existing question history on the UI.

- **Page Initialization:**
  - `(function () {...})();`: Immediately invoked function expression (IIFE) to run functions on page load. Calls `checkApiKeyStatus()` and `displayQuestionHistory()`.

- **Event Listener:**
  - Attaches an event listener to the "Clear History" button to trigger the `clearHistory` function.


> [!NOTE]
> Keep in mind that the actual API endpoint and key handling should be implemented securely in a production environment.
