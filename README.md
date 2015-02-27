# JQuery/Ajax Quiz

Write your answer below each question.

### Question 1
(a) What is a click handler?

A click handler is an event listener that will fire off a function once the target has been clicked.

(b) Where in your JS file should you put it, and WHY?

You should put in the document ready. You need to make sure the target element exists before you attach anything to it.

### Question 2
If you get the error `$ is undefined`, what does that mean and what could you do to fix it?

It means that $ is undefined. idk, probably means JQuery isn't being loaded in.

### Question 3
What should go in the `$(document).ready()` part of your JS file?

Anything that needs to reference a specific DOM element.

### Question 4
In an AJAX GET request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent?

It represents the data returned from the GET request. In our case that has been a JSON object.

```
$.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
```
### Question 5
In an AJAX POST request, what does the argument of the `.done()` callback - in the example below, that would be `data` - represent? (Hint: it's not the same as in Question 4.)

It represents the object that you just created with the POST request (just the one, not all of the object in existence.)

```
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'POST',
    dataType: 'JSON',
    data: { user: { name: "Anna", about: "instructor", email: "hi@gmail.com" } },
  })
  .done(function(data) {
    console.log("success!");
  });
```
### Question 6
Suppose you had the following form in your HTML file. Use jQuery to write a single line of code that takes whatever the user entered in the textbox and saves it to the variable `user_input`.

Assuming event handler already exists exists:
var user_input = $('#color').val();

Code for event handler as well:
$('form').submit(function(event){
  event.preventDefault();
  var user_input =$('#color').val();
  });


```
  <form>
    <p>The dress is:</p><input type="text" id="color">
    <input type="submit" value="Submit" id="submit">
  </form>
```

### Question 7
This code looks like it works, but when you run it, you see that the `UserApp.add_all_users()` function executes but `console.log` displays `undefined`. What's wrong with the code?

```UserApp.add_all_users(data);``` This line cannot access the data. In the done function data is being passed from the GET request. If you wanted the code to work this way you could put the call to UserApp.add_all_users(data) to inside the function in the done action.

```
UserApp.get_all_users = function() {
  $.ajax({
    url: 'http://ig-hacker-news.herokuapp.com/users',
    type: 'GET',
  })
  .done(function(data) {
    console.log("success!")
  });
  UserApp.add_all_users(data);
};

UserApp.add_all_users = function(data) {
  console.log(data);
};
```



