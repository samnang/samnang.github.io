---
title: .NET Coders should give Ruby a try
date: 2009/01/20
slug: dotnet-coders-should-give-ruby-a-try
tags: .Net, Ruby
layout: post
---

Last weekend, I gave [Ruby](http://www.ruby-lang.org/ "Ruby programming language") a try. 
Ruby is a dynamic, open source programming language with focusing on simplicity and 
productivity. It has elegant syntax that is natural to read and easy to write. 
I’m a .NET coder, everyday I use C# for developing projects in my company. There are few
reasons that bring me to try Ruby because I see a lot programmers have mentioned 
Ruby is a very powerful and flexible programming language, is it true? And the main 
reason, I would like to try something new because almost my programming skills are 
just in static typed language and a bit dynamic typed language with Javascript.

After I played with Ruby about a few hours, I start loving it. Ruby is a fun toy. 
Like the differences between spoken languages, Ruby differs from most other programming 
languages not only by syntax, but by culture, grammar, and customs. And some programmers 
consider Ruby is English for computers. Ruby brings a new way of thinking about 
programming and software development. I would like to show you very basic examples, 
let’s go to see snippets of code comparation between C# and Ruby.

```cs
// === Examples in C# ===

//Swap value between two variables
int a = 5, b = 10;
int temp = a;
a = b;
b = temp;

//Output message 3 times
for(int i = 0; i <= 3; i++)
    Console.WriteLine("Hello");

//Output message if condition is true string
str = string.Empty;
if(str == string.Empty)
    Console.WriteLine("str is empty");
```

```ruby
# === Examples in Ruby ===

#Swap value between two variables
a, b = 5, 10
a, b = b, a

#Output message 3 times
3.times { puts "Hello" }

#Output message if condition is true
str = ''
puts "str is empty" if str.empty?
```

Code comparisons above are not to show which language is bad and another is good, 
but I just want to show how I feel about new language. Ruby code is short and readable 
like in English. There are lots of more powerful features in Ruby that I haven’t mentioned here.

If you haven’t touched something new recently, why don’t you give Ruby a try?

