# Ruby on Rails API with Vue.js

What are we building exactly?
This app at its core is simple. It will be an archive of vinyl records for sale and categorized by artist. We won't be implementing a ton of foreign logic but rather just getting the foundations of an API-based application in order. We'll touch on authentication (not using Devise 😉) and basic CRUD.

There will be two apps.

* A Ruby on Rails backend - This will handle our data, sessions, and authentication.
* A Vue.js frontend - This will be the view layer but also the one responsible for sending and receiving data to our rails-based backend. The front-end will run on a different instance using the [Vue-CLI](https://cli.vuejs.org/) to help us set up an app.

[Read and watch the whole tutorial series](https://web-crunch.com/posts/ruby-on-rails-api-vue-js)

* Versions

```
ruby 2.6.3p62
Rails 6.1.3.1
@vue/cli 4.5.12
```

* Configuration
```
bundle
```

* Database creation
```
rails db:create db:migrate
```

* Gems
```
Gem bcrypt 3.1.7
Gem rack-cors
Gem redis 4.1.0
Gem jwt-sessions
```
