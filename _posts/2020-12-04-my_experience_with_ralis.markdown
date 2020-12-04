---
layout: post
title:      "My Experience With Ralis"
date:       2020-12-04 19:23:41 +0000
permalink:  my_experience_with_ralis
---

​
![alt_text](https://media.giphy.com/media/3otPoEvMyH2X0NTOWk/giphy.gif)

​
For my third project I choose to make a Real Estate web page. One of the features I wanted to include was the ability to upload pictures . This was a big learning experience, I have a new respect for uploading images.
​
# Getting Started
> Once I knew I wanted to upload images I stated to look around for different ways to do so. I came across a gem named shrine which can be found here `https://shrinerb.com/`. This is were the hard part came in. Aside from installing the gem like normal, there was a second step that needed to be done to allow images to be rendered. I needed to install  `https://imagemagick.org/index.php` ImageMagick onto my system. After this I was able to add images.
​
# Using Shrine
There was a slight learning curve to using this gem. There are pages upon pages of doucments on different ways to use this gem. To get started I follwed these steps : "Add Shrine to the Gemfile and write an initializer which sets up the storage and loads integration for your persistence library:"

```
require "shrine"
require "shrine/storage/file_system"
 
Shrine.storages = { 
  cache: Shrine::Storage::FileSystem.new("public", prefix: "uploads/cache"), # temporary 
  store: Shrine::Storage::FileSystem.new("public", prefix: "uploads"),       # permanent 
}
 
Shrine.plugin :sequel # or :activerecord 
Shrine.plugin :cached_attachment_data # for retaining the cached file across form redisplays 
Shrine.plugin :restore_cached_data # re-extract metadata when attaching a cached file 
Shrine.plugin :rack_file # for non-Rails apps 
```
Next 
​`$ rails generate migration add_image_data_to_photos image_data:text`

Now you want to make an uploader class like such

`class Photo < ActiveRecord::Base
  include ImageUploader::Attachment(:image) # adds an `image` virtual attribute 
end`

For the form you need 

`form_for @photo do |f|
  f.hidden_field :image, value: @photo.cached_image_data
  f.file_field :image
  f.submit
end
`
And in your controller you want to require photo and permit image
`class PhotosController < ApplicationController
  def create
    Photo.create(photo_params)
		      end
 
  private
 
  def photo_params
    params.require(:photo).permit(:image)
  end
end`

# Closing
After following these steps you should have a working image uploader. You can check out my project here. [](https://github.com/csdj92/real-estate-project)

