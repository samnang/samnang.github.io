---
title: "Sprinkle: Build remote servers in repeatable way"
date: 2011/08/22
tags: Sprinkle, Automation, Tools
description: Sprinkle uses Ruby's DSL to define packages/steps that are going to execute on remote servers, so that makes it easy to read and write.
layout: post
---

[Cloud Computing](http://en.wikipedia.org/wiki/Cloud_computing) helps us be really easy to scale more servers or relaunch new servers when something went wrong. But setting up a new server to be the same as existing one is not easy because we have to remember all installed packages, custom configurations, and commands that you need to run them in order.

>" [Sprinkle](https://github.com/crafterm/sprinkle/) is a software provisioning tool you can use to build remote servers with, after the base operating system has been installed. For example, to install a Rails or Merb stack on a brand new slice directly after its been created. "

Sprinkle uses Ruby's DSL to define packages/steps that are going to execute on remote servers, so that makes it easy to read and write. Here is an example of package description follows:
<script src="https://gist.github.com/1160876.js?file=ruby_enterprise.rb"></script>
<noscript>	
    package :ruby_enterprise do
	  description 'Ruby Enterprise Edition'
	  version '1.8.7-2011.03'
	  REE_PATH = "/usr/local/ruby-enterprise"
	  binaries = %w(erb gem irb rackup rails rake rdoc ree-version ri ruby testrb)
	  source "http://rubyenterpriseedition.googlecode.com/files/ruby-enterprise-#{version}.tar.gz" do
	    custom_install 'sudo ./installer --auto=/usr/local/ruby-enterprise'
	    binaries.each {|bin| post :install, "ln -s #{REE_PATH}/bin/#{bin} /usr/local/bin/#{bin}" }
	  end

	  verify do
	    has_directory REE_PATH
	    has_executable "#{REE_PATH}/bin/ruby"
	    binaries.each {|bin| has_symlink "/usr/local/bin/#{bin}", "#{REE_PATH}/bin/#{bin}" }
	  end

	  requires :ree_dependencies
	end

	package :ree_dependencies do
	  apt %w(zlib1g-dev libreadline5-dev libssl-dev)
	  requires :build_essential
	end
</noscript>

There are few other tools as well like [Chef](http://www.opscode.com/chef/) and [Puppet](http://www.puppetlabs.com/), and they are popular and really good. But after I spent a few hours to try Chef, then I feel it's not so friendly tool for getting started. So that's why I choose Sprinkle instead.

## Resources
* <https://github.com/crafterm/sprinkle>
* <http://www.vimeo.com/2888665>
* <https://github.com/uhlenbrock/passenger-stack>
* <https://github.com/asanghi/passenger-stack>
* <https://github.com/thoughtbot/continuous_sprinkles>
