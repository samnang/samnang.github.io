---
title: Use View Helper Methods in Rails 3 Controller
date: 2011/09/09
tags: Rails
description: view_context lets you call view helper methods in your controllers.
layout: post
---

Sometimes people use [`helper_method`](http://apidock.com/rails/ActionController/Helpers/ClassMethods/helper_method) to turn their controller methods to be able to use in their views. Rails provides a lot of [view helpers](http://apidock.com/rails/ActionView/Helpers), and sometimes we would like to use some helper methods that have in helper modules in our controllers instead, for example `link_to`, `mail_to`, `pluralize`, etc. One way to archive this in Rails 3 is to call [`view_context`](http://apidock.com/rails/AbstractController/Rendering/view_context) inside the controller to create a new ActionView instance for a controller, then all helper methods will be available through this instance in the controller.

<script src="https://gist.github.com/1205781.js?file=gistfile1.rb"></script>
<noscript>
	# app/controllers/posts_controller.rb
	class PostsController < ActionController::Base
	  def show
	    # ...
	    tags = view_context.generate_tags(@post)
	    email_link = view_context.mail_to(@user.email)
	    # ...
	  end 
	end

	# app/helpers/posts_helper.rb
	module PostsHelper
	  def generate_tags(post)
	    "Generate Tags"
	  end
	end
</noscript>
