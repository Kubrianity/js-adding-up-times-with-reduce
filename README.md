# js-adding-up-times-with-reduce
This is the eighteenth practice of JavaScript30 Challenge. </br></br>
This practice shows how JavaScript Array map and reduce method works to figure out total runtime of given videos in hours, minutes and seconds
## Usage & Features
data-time attributes within li elements show the minutes and seconds as a string format. In order to select list elements with that attribute:
```javascript
  const timeNodes = document.querySelectorAll('[data-time]'); // returns a nodelist
```
Then, we need to convert the nodelist into array with Array.from() method:
```javascript
  const timeNodes = Array.from(document.querySelectorAll('[data-time]'));
```
Now, we extract values of data-time attributes as an array for each li element: 
```javascript
  const seconds = timeNodes.map(node => node.dataset.time);
```  
We convert time in a string format to an array with two numbers as a second and minute with split and parseFloat functions.</br>
Then we return it to seconds: 
```javascript
  const seconds = timeNodes
  .map(node => node.dataset.time)
  .map(timeCode => {
    const [mins, secs] = timeCode.split(":").map(parseFloat);
    return (mins * 60) + secs;
  })
```
Finally, we use reduce method to add all the seconds in the array together:
```javascript
  const seconds = timeNodes
  .map(node => node.dataset.time)
  .map(timeCode => {
    const [mins, secs] = timeCode.split(":").map(parseFloat);
    return (mins * 60) + secs;
  })
  .reduce((total, vidSeconds) => total + vidSeconds);
```
