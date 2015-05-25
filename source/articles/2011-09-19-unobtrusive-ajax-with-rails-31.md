---
title: Unobtrusive AJAX with Rails 3.1
date: 2011/09/19
tags: Rails, AJAX
description: AJAX with Rails, if you have some experiences with RJS in previous versions of Rails, then you will not see many differences when you implement AJAX in Rails 3.1.
layout: post
---

Since Rails 3.0 release, Unobtrusive Javascript has introduced in building Rails application. It's a technique for separating the behavior of a web application from its content. It helps us to implement a web application that works for clients with and without enabled javascript. If users don't have enabled javascript, then it works just traditional web application.

AJAX with Rails, if you have some experiences with RJS in previous versions of Rails, then you will not see many differences when you implement AJAX in Rails 3.1. One different is you create template in javascript or coffee-script instead of RJS. Let's see how we implement application below:

![Unobtrusive AJAX with Rails 3.1](https://img.skitch.com/20110918-rga8gjep56nrs24kq5c1d8esc8.png)

Add js respond format to comments controller `app/controllers/comments_controller.rb`
<script src="https://gist.github.com/1225377.js?file=comments_controller.rb"></script>
<noscript>
	# app/controllers/comments_controller.rb    
	class CommentsController < ApplicationController
	  respond_to :html, :js

	  def index
	    @comments = Comment.all
	  end

	  def create
	    @comment = Comment.new(params[:comment])

	    @comment.save

	    respond_with @comment, :location => comments_url
	  end
	end
</noscript>	

Implement views `app/views/comments/index.html.erb` with remote form
<script src="https://gist.github.com/1225377.js?file=index.html.erb"></script>
<noscript>
	# app/views/comments/index.html.erb
	<% title "Comments for Ajax in Rails 3.1" %>

	<div id="comments_count"><%= comments_count %></div>

	<div id="comments">
	  <%= render @comments %>
	</div>

	<h3>Add your comment:</h3>

	<%= form_for Comment.new, :remote => true do |f| %>
	  <%= f.error_messages %>
	  <p>
	    <%= f.label :name %><br />
	    <%= f.text_field :name %>
	  </p>
	  <p>
	    <%= f.label :content, "Comment" %><br />
	    <%= f.text_area :content, :rows => '12', :cols => 35 %>
	  </p>
	  <p><%= f.submit %></p>
	<% end %>
</noscript>
<script src="https://gist.github.com/1225377.js?file=_comment.html.erb"></script>
<noscript>
	# app/views/comments/_comment.html.erb
	<div class="comment">
	  <strong><%= comment.name %></strong>
	  <em>on <%= comment.created_at.strftime('%b %d, %Y at %I:%M %p') %></em>
	  <%= simple_format comment.content %>
	</div>
</noscript>

Add javascript or coffeescript template, I prefer (`app/views/comments/create.js.coffee`) to handle ajax request
<script src="https://gist.github.com/1225377.js?file=create.js.coffee"></script>
<noscript>
	# app/views/comments/create.js.coffee	
	$('<%= escape_javascript(render(:partial => @comment))%>')
	  .appendTo('#comments')
	  .hide()
	  .fadeIn()

	$('#new_comment')[0].reset()

	$('#comments_count').html '<%= comments_count %>'
</noscript>
The complete source is on [Github](https://github.com/samnang/ajax_rails31_demo). So feel free to checkout and run it to see in action.
