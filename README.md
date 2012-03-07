## Sample Rails 3 application showing the use of the [dust_assets](https://github.com/hasmanydevelopers/dust_assets) gem

# There we go!

* I've just created a vanilla Rails (in my case a 3.2.2)
* Added the ´dust_assets´ gem to the Gemfile like this:

```
  group :assets do
    gem 'handlebars_assets'
  end
```

* Required dust.js in my application.js file adding somethin like this to it:

```
  //= require dust
```

* Created a dust.js template in 'templates/' (you can user any dir structure) dir and   
  named it to `hello.jst.dust``. Note template file *extension* *.jst.dust if you don't  
  use that extension Sprockets will not be able to identify and compile the file, neither  
  put the compiled template into the ´JST´ object.
* After that created a simple controller 'main' with a basic 'index' action
* Droped some div in the 'app/views/index.html.erb'
* The important stuff goes into 'app/assets/javascripts/application.js'. Something like this:

  ```
    $(function() {
      JST["templates/hello"]({ name : "World" }, function(err, out) {
        $('#dust').html(out);
      });
    });
  ```
* When you visit '/main/index' you will see ;)