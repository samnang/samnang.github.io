---
title: Convert nested JSON to object in Ruby
date: 2015-05-26 19:15 UTC
tags: Ruby
layout: post
---

In the past, every time I tried to convert a complex nested JSON to an object, 
I used to depend on some third party gems like [Hashie](https://github.com/intridea/hashie)
or [recursive-open-struct](https://github.com/aetherknight/recursive-open-struct).
Recently I found a very simple way to solve my problem which depend on `json` which is included in standard lib of Ruby itself.

```ruby
require 'json'
require 'ostruct'

result = JSON.parse(
  "{\"foo\":{\"bar\":[1,2,3]}}",
  object_class: OpenStruct
)
result.foo.bar  # => [1, 2, 3]
```

You also can learn more about other options that available to pass when you call [`JSON.parse`](http://ruby-doc.org/stdlib-2.2.2/libdoc/json/rdoc/JSON.html#method-i-parse)
