---
title: Run only Focus Examples in RSpec like Cucumber
date: 2011/04/09
tags: RSpec, Cucumber, Testing
layout: post
---

While I am coding using Vim as my editor, I don't know an easy way to run only an example or a group examples of [RSpec](https://github.com/rspec/rspec-core) that I am working on until RSpec-2 came out. I know we can run `spec . -e example` to run only match examples in the previous version, but I feel that's not a friendly way to do it. I like Cucumber's `@wip` tag because I can specify on a scenario that I'm working on.

Thank for RSpec team for implementing a cool feature to be able filtering examples that we want to focus on while we are writing with tests.

```ruby
# spec/spec_helper.rb

RSpec.configure do |c|
  c.filter_run :focus => true
  c.run_all_when_everything_filtered = true
end
```

```ruby
require "spec_helper"

describe "group 1" do
  it "group 1 example 1", :focus => true do
  end

  it "group 1 example 2" do
  end
end

describe "group 2" do
  it "group 2 example 1" do
  end
end
```

Run the tests then you will see output:

```
$ rspec .
Run filtered using {:focus=>true}
.

Finished in 0.00026 seconds
1 example, 0 failures
```

After you passed the focus example(s), then you will want to run all examples, you could do it by just removing `:focus => true` from you example(s):

```ruby
require "spec_helper"

describe "group 1" do
  it "group 1 example 1" do
  end

  it "group 1 example 2" do
  end
end

describe "group 2" do
  it "group 2 example 1" do
  end
end
```

Then rerun the tests, you will see the output of all tests:

```
$ rspec .
No examples were matched by {:focus=>true}, running all
...

Finished in 0.00048 seconds
3 examples, 0 failures
```

I would suggest you take a look at [`--tag option`](http://relishapp.com/rspec/rspec-core/v/2-5/dir/command-line/tag-option) as well.
