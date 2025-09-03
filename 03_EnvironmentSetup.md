- [Objective](#objective)
- [Choosing a Code Editor](#choosing-a-code-editor)
- [Setting Up Visual Studio Code](#setting-up-visual-studio-code)
- [Setting Up a Web Browser for Development](#setting-up-a-web-browser-for-development)
- [Using Chrome Developer Tools (DevTools)](#using-chrome-developer-tools-devtools)
- [Using Online Playgrounds](#using-online-playgrounds)

---

Reference [^1]

---

# Objective

Starting a journey in JavaScript programming requires a properly configured environment. Having the right tools can make a significant difference in learning efficiency and ease, especially for beginners.

---

# Choosing a Code Editor

A code editor is where you’ll spend a lot of time writing and debugging your JavaScript code. Many editors are available, each offering unique features to suit different programming needs. Here are a few popular ones that are particularly beginner-friendly:

- **`Visual Studio Code` (VS Code)**: A free, open source editor developed by Microsoft, VS Code is a favorite among developers due to its extensive library of extensions, ease of use, and efficient debugging tools. VS Code also integrates seamlessly with AI tools like GitHub Copilot, which offers real-time code suggestions and can significantly speed up development. Copilot is free for personal use in VS Code, making it a great choice for beginners and professionals alike.

- **Sublime Text**: Known for its speed and responsiveness, Sublime Text offers a straightforward interface that is well-suited for beginners, though it lacks some of the built-in tools available in VS Code.

- **Atom**: Originally developed by GitHub, is another free and open source editor with a strong community. It’s highly customizable, although it may not perform as well with larger codebases compared with VS Code.

- **WebStorm**: A premium Integrated Development Environment (IDE) developed by JetBrains, WebStorm is tailored for JavaScript, TypeScript, and front-end development. It offers advanced features like intelligent code completion, integrated version control, and seamless debugging tools.

---

# Setting Up Visual Studio Code

1. [Download](https://code.visualstudio.com/Download) and Install VS Code
2. Install Extensions - For WEBDEVT, here are the recommended extensions:
  - **Prettier** for consistent formatting
  - **ESLint** to check for syntax and style issues
  - **JavaScript (ES6) code snippets** to simplify coding with predefined snippets

> [!TIP]
> To install extensions, you may use the keyboard shortcut `ctrl+shift+x`, then search for the extension name (from the list above, the extension name is higlighted in **bold font**)

> [!IMPORTANT]
> Configure autosave in VS Code by using the keyboard shortcut `ctrl+,`, then search for "autosave". The default is set to "off", and I recommend that you change it to "onFocusChange"


# Setting Up a Web Browser for Development

JavaScript primarily runs within web browsers, so having a developer-friendly browser is essential. Here are a few commonly used browsers with strong developer support:

- **Google Chrome**: Known for its powerfol developer tools (DevTools), Chrome is often the first choice for JavaScript development.
  
- **Firefox**: Firefox also provides an extensive set of developer tools and is a strong choice, especially if you’re interested in cross-browser compatibility testing.

- **Microsoft Edge**: Edge shares many features with Chrome, as both are built on the Chromium engine. It includes a comprehensive set of tools for debugging.

- **Brave**: may be known as Google Chrome's privacy-focused cousin.

---

# Using Chrome Developer Tools (DevTools)

DevTools is an integrated suite of tools within Chrome that allows you to inspect and debug JavaScript code directly in the browser. Here’s how to access and use DevTools for JavaScript:

1. **Open DevTools**: Right-click any web page, select Inspect, or press F12. This will open the DevTools panel.

 
2. **Use the Console Tab**: The Console tab is a critical area for JavaScript development. You can enter JavaScript commands here to test code or debug errors in real time.

 
3. **Sources Tab**: This tab is useful for viewing and setting breakpoints within your code, helping you step through JavaScript line by line.

 
4. **Network Tab**: The Network tab displays all network activity, which is particularly helpful for monitoring API calls and performance.

 
5. **Use Lighthouse for Performance Audits**: The Lighthouse tab in DevTools allows you to run performance audits on your web page. It provides insights on performance, accessibility, search engine optimization (SEO), and best practices. You can generate a report by clicking the “Generate report” button, which will give you a detailed analysis and suggestions for improving the performance and user experience of your website.
   
---

# Using Online Playgrounds

For quick JavaScript testing, online playgrounds are a fantastic option. These platforms let you write and run JavaScript code without the need for a full environment setup. They are particularly useful for experimentation, prototyping, and sharing code snippets. Here are some popular choices:

- **JSFiddle**: A long-standing favorite for testing and sharing code that combines HTML, CSS, and JavaScript. It’s simple to use and allows you to quickly experiment with different ideas.

- **CodePen**: Ideal for front-end development and widely used by designers and developers to create and share interactive code snippets. CodePen supports live previews and offers a vibrant community where you can explore examples and learn from others’ work.

- **Replit**: A collaborative online IDE that supports JavaScript and many other languages. It allows real-time collaboration, making it great for pair programming or working on small projects with others.

- **StackBlitz**: A powerful option tailored for modern web development. It provides an online environment for JavaScript, TypeScript, and even full Angular, React, or Vue projects. StackBlitz mimics a local development setup, supports npm packages, and integrates well with GitHub, making it a great tool for more advanced testing and prototyping.

---

[^1] Kapoor, S. (2025). Beginning JavaScript syntax : understanding syntactical rules and structures for better JavaScript programming. Apress. https://doi.org/10.1007/979-8-8688-1460-0