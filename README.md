# Qiita Rails Post with Ajax in JS

JavaScript内のAjax通信でモデルオブジェクトをPOSTするサンプル

## Qiita


## Model

```
$ rails g scaffold user name:string
```

## Ajax

```
#Gemfile

gem 'jquery-rails'
```

```
# app/assets/javascripts/application.js

//= require jquery3
//= require jquery_ujs
```

```
# app/views/static_pages/home.html.erb

<input type="text" id="name">
<button id="create">post</button>

<script>

  $("#create").click(function () {

    var data = {
      "user":
        {
          name: $("#name").val()
        }
    };

    $.ajax({
      type: "post",
      url: "<%= users_path %>",
      data: JSON.stringify(data),
      contentType: 'application/json',
      dataType: "json",

      success: function (data) {
        console.log("success");
        console.log(data);
        $("#name").val("");
      },

      error: function (data) {
        console.log("error");
        console.log(data);
      }
    });
  });

</script>
```