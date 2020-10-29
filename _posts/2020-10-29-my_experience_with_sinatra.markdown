---
layout: post
title:      "My Experience with Sinatra"
date:       2020-10-29 16:44:58 +0000
permalink:  my_experience_with_sinatra
---

​
![alt_text](https://media.giphy.com/media/4hnQDVKVARZ6w/giphy.gif)

​
For my second Project I to make a Sinatra based web page. This project needed to have two models, with a has_many and belongs to relationship, user authentication as well as implementing CRUD.  I choose to base my project on Pokemon.
​
# Getting Started
To help with the file structure setup I used the gem [Corneal](HTTPS://github.com/thebrianemory/cornealttp://). This made the process that much easier. To get started all you need to do is use these commands. 
“`
gem install corneal new MY-NEW-APP-NAME
bundle
“`
​
After you run these commands you get this 
“`
└─app
 ├── controllers
 │ ├──application_controller.rb
 │ └──new_model_controller.rb
 ├── models
 │ └──new_model.rb
 └── views
 ├──new_models
 │ ├──index.html.rb.erb
 │ ├──show.html.rb.erb
 │ ├──new.html.rb.erb
 │ └──edit.html.rb.erb
 ├── layout.erb
 └── welcome.erb
“`
​
Not only did this save a lot of time for me but it was very convent too.
​
# Using ActiveRecord 
Two of my best friends became ` rake db:rollback` & `rake db:migrate`.  These two parts of code helped me start fresh whenever I made the error of adding bad data to my database. I caught on quickly when I started to notice errors coming from bad data. This was defiantly a tough process but it showed me how important user input validations are.
​
​
# Models
My two models were easy to set up and consisted of a trainer model and a Pokemon model. A Trainer has_many Pokemon and a Pokemon belongs_to a Trainer. In my model I was able to add password validations so when a Trainer logged in they had to meet a specific set of rules.

​
![alt_text](https://media.giphy.com/media/uLnPIWsqIz2aA/giphy.gif)
# Controllers
The next step was to set up my controllers. This taught me a lot about the RESTful routes. I needed to make sure that a Trainer(User) could make a team and edit his own team but not edit another trainers team. This was where I hit a bump in the road and found out how having one extra 's' at the end of sessions cans reck havoc on my whole user experience.
(Quick shoutout to Brock, Dasha, Leah and Nancy for helping me get through this).
​
# Views
This was probably my favorite part. I enjoyed styling with css and trying to make the page look as nice as I could. I defiantly could have done more but this project was mentally taxing. I used bootstrap to make a navigation bar which made it, so I didn't have to have random buttons on every page.

​
​
In conclusion this was a challenging project but I enjoyed the challenge but I'm ready to move onto Rails.
