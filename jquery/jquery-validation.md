
<img src="http://i.imgur.com/xNPu9B7.png" width="200">

`jQuery Validation Plugin`

```
shell> bower install jquery-validation
shell> bower install --save jquery-validation
```

`CDN`

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
<script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.15.0/jquery.validate.min.js"></script>
<script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.15.0/additional-methods.min.js"></script>

<script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.15.0/additional-methods.js"></script>
<script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.15.0/jquery.validate.js"></script>

<script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.15.0/localization/messages_zh_TW.js"></script>
```
---

```html
<form>
    <input required>
</form>
<script src="jquery.js"></script>
<script src="jquery.validate.js"></script>
<script>
$("form").validate();
</script>
```

---

[source code](https://jsfiddle.net/18mgdre5/2/)

```html
<form class="cmxform" id="commentForm" method="get" action="">
  <fieldset>
    <legend>Please provide your name, email address (won't be published) and a comment</legend>
    <p>
      <label for="cname">Name (required, at least 2 characters)</label>
      <input id="cname" name="name" minlength="2" type="text" required>
    </p>
    <p>
      <label for="cemail">E-Mail (required)</label>
      <input id="cemail" type="email" name="email" required>
    </p>
    <p>
      <label for="curl">URL (optional)</label>
      <input id="curl" type="url" name="url">
    </p>
    <p>
      <label for="ccomment">Your comment (required)</label>
      <textarea id="ccomment" name="comment" required></textarea>
    </p>
    <p>
      <input class="submit" type="submit" value="Submit">
    </p>
  </fieldset>
</form>
<script>
  $("#commentForm").validate();
</script>
```

```js
$("#myform").validate({
  rules: {
    field: {
      required: true,
      step: 10
    }
  }
});
```


```js
$("#signupForm").validate({
  rules: {
    firstname: "required",
    lastname: "required",
    username: { required: true, minlength: 2 },
    password: { required: true, minlength: 5 },
    confirm_password: { required: true, minlength: 5, equalTo: "#password" },
    email: { required: true, email: true },
    topic: { required: "#newsletter:checked", minlength: 2 },
    agree: "required"
  },
  messages: {
    firstname: "Please enter your firstname",
    lastname: "Please enter your lastname",
    username: {
      required: "Please enter a username",
      minlength: "Your username must consist of at least 2 characters"
    },
    password: {
      required: "Please provide a password",
      minlength: jQuery.validator.format("Enter at least {0} characters")
      // minlength: "Your password must be at least 5 characters long",
    },
    confirm_password: {
      required: "Repeat your password",
      minlength: jQuery.validator.format("Enter at least {0} characters")
      // minlength: "Your password must be at least 5 characters long",
      equalTo: "Please enter the same password as above"
      // equalTo: "Enter the same password as above"
    },
    email: "Please enter a valid email address",
    agree: "Please accept our policy"
  }
});

```

```js
$(".selector").validate({
  errorClass: "invalid",
  validClass: "success"
});
```

```css
.invalid {
  color: red;
}

.success {
  color: green;
}
```

```js
$(".selector").validate({
  focusInvalid: true
});
```
---

```js
$("#myform").validate({
  rules: {
    email: {
      required: true,
      email: true,
      remote: "/check-email"
    }
  },
  messages: {
    email: {
      required: "Please enter a valid email address",
      minlength: "Please enter a valid email address",
      remote: jQuery.validator.format("{0} is already in use")
    },
  }
});
```

```js
'use strict';

const express = require('express');

// Constants
const PORT = 8080;

app.get('/check-email', (req, res) => {
  var email = req.query.email;

  if () {
    res.send("true");
  } else {
    res.send("false");
  }
});

app.listen(PORT);
console.log('Running on http://localhost:' + PORT);
```

#### :books: 參考網站：
- [jQuery Validation Plugin](https://jqueryvalidation.org/)
- https://jqueryvalidation.org/require_from_group-method/
- https://jqueryvalidation.org/normalizer/
- https://jqueryvalidation.org/step-method/
- https://jqueryvalidation.org/
- https://github.com/jquery-validation/jquery-validation
- https://jqueryvalidation.org/validate/
- https://github.com/jquery-validation/jquery-validation/tree/master/src/localization
- https://jqueryvalidation.org/remote-method/
- https://jqueryvalidation.org/jQuery.validator.addMethod/