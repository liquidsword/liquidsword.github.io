---
layout: post
title:      "has_secure_password"
date:       2018-08-21 22:22:44 +0000
permalink:  has_secure_password
---


   So I found myself a little confused about using has_secure_password in my code so this post is about password, password confirmation, and password_digest  and how it relates to has_secure_password. First and foremost to include the has_secure_password method you must include it in your gemfile: gem 'bcrypt' . This will give you access to the has_secure_password method. In your migration you are now capable of including password_digest. Here's how it should look:
	 
	 `class User < ActiveRecord::Base
         has_secure_password
    end`

   Also note that password and password_confirmation are not columns in the database only password_digest is, which is stored as a hash for security purposes :). Has_secure_password adds the before_save hooks to the model which then compares password and password_confirmation to make certain that they are the same. If they are then the password_digest column is updated.
