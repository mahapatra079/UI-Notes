# Fetch 

Getting data from an API & showing it in UI.

## Fetching Steps

1. **Fetch data ( Call api )** from the API using `fetch()`. 
2. **Convert the response** to JSON format using `response.json()`.
3. **Use the data** to update the UI.

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    // Use the data to update the UI
    console.log(data);
  })
  .catch(error => console.error('Error fetching data:', error));
```

## Conclusion
In this we are fetching data from `https://api.example.com/data`, converting the response to JSON, and then logging the data to the console. If there is an error during the fetch process, it will be caught and logged as well.