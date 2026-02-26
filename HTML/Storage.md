# Storage

The Storage is a Web Storage API that provides access to a particular domain's i.e. session or local storage. It allows you to store key-value pairs in a web browser.

## 1) Local Storage

 - Local storage is a web storage API provided by browser that allows you to store data with no expiration date.
   
 - The data will not be deleted when the browser is closed and will be available the next day, week, or year.

 => Local Storage is accessed via 

```javascript
window.localStorage
```
 => Syntax 
    localStorage.setItem(key,value)


```javascript

localStorage.setItem
localStorage.getItem
localStorage.removeItem
localStorage.clear
```

ex:

```javascript
// Storing data in local storage
localStorage.setItem('name', 'John Doe');
// Retrieving data from local storage
const name = localStorage.getItem('name');
// Removing data from local storage
localStorage.removeItem('name');

```
=> Key Features
- Data is stored as key-value pairs.
- Data is stored in the browser and is accessible across sessions.
- Local storage has a larger storage capacity compared to cookies (typically around 5MB).
- Size limit 5-10 MB Depending on the browser.

## 2) Session Storage

- Session storage is a web storage API provided by browser that allows you to store data for the duration of the page session.

- The data is deleted when the browser tab is closed.

=> Session Storage is accessed via 

```javascript 
window.sessionStorage
```
=> Syntax 
    sessionStorage.setItem(key,value)

```javascript
sessionStorage.setItem
sessionStorage.getItem
sessionStorage.removeItem
sessionStorage.clear
```
ex:

```javascript
// Storing data in session storage
sessionStorage.setItem('name', 'John Doe');
// Retrieving data from session storage
const name = sessionStorage.getItem('name');
// Removing data from session storage
sessionStorage.removeItem('name');

```
=> Key Features

- Data is stored as key-value pairs.
- Data is stored in the browser and is only accessible within the same session.
- Session storage has a smaller storage capacity compared to local storage (typically around 5MB).
- Size limit 5-10 MB Depending on the browser.

## Real Example Analogy

- Local Storage can be compared to a filing cabinet where you can store important documents that you want to keep for a long time. You can access these documents whenever you need them, and they will remain safe even if you close the cabinet (browser).

- Session Storage can be compared to a whiteboard where you can jot down temporary notes during a meeting. Once the meeting is over and you erase the whiteboard (close the browser tab), all the notes are gone.

## Conclusion
The Web Storage API provides a way to store data on the client side, allowing for faster access and improved performance compared to server-side storage.
Local storage is ideal for storing data that needs to persist across sessions, while
Session storage is suitable for temporary data that should only be available during a single session.


### Cookies
- Cookies are small pieces of data stored on the client side that are sent to the server with each HTTP request.

- Size limit 4kb

- Mostly used for Authentication, Session & Tracking Purpose

