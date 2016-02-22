---
title: "Ruby Debugging"
slug: 0-ruby-debugging
---

"The most effective debugging tool is still careful thought, coupled with judiciously placed print statements." - Brian Kernighan

Here are a number of tips and tricks for effective Ruby debugging. 

# Undefined method for nil:NilClass

One of the common errors new ruby developers run into is NoMethodError. Imagine you have a class AuthorFromParams:

```
class AuthorFromParams
  
  def initialize(params)
    @params = params
  end

  def author_name
    @params['author']['name']
  end

end
```

Here we have a simple class that takes the params as an argument, and returns the author's name. You would expect params to be 

`{ post_id: 1, post_title: "First!", author: { name: “joe”, id: 3 }}`

Now, what happens if you do not receive the author key?

```
my_class = MyClass.new({post_id: 1, post_title: "First!"})

author_from_params.rb:7:in `author_name': undefined method `[]' for nil:NilClass (NoMethodError)
  from author_from_params.rb:12:in `<main>'
```

Oh, that is somewhat surprising. what this error is telling us is nil class does not implement square brackets. It is true that square brackets are not implemented on nil, but that is not what I want. I never asked if square brackets are defined on nil. or did I?

Let’s take a closer look at the author_name method.

```
def author_name
  @params['author']['name']
end
```

if we call @params[‘author’], ruby will return `nil` since it is not present in the hash. Ruby considers that perfectly normal, so it continues on and asks the return value from `@params[‘author’]` (`nil`) what `[‘name’]` returns. Boom! this is where we explode. Since we are now effectively calling `nil[‘name’]`, we get this error.

Now that we understand what is going on, we can more easily fix it and there are several ways to fix it.

**Task: Try fixing this error using a conditional.**

**Task: Try fixing this error using ruby’s ****[#dig method](http://ruby-doc.org/core-2.3.0/Hash.html#method-i-dig)**.**

This is a very common error for new and experienced developers alike. Now you should be able to identify it more quickly and fix it appropriately.

# Finding the problem

In the previous example, we knew where our error was coming from, it was present in the stack trace and easy to identify. Now what do we do when we don’t actually know where the error is? Consider this example[1].

```
def show
  render params[:id]
end
```

We are calling the render method, but we don’t know where it goes. We can use a method called `source_location` to find where it is defined. we can call `method(:render).source_location`.

**Task: Try out using source location to find where framework methods are defined. Open the file where it is defined and peek at the implementation.**

# Modifying your dependencies

Sometimes a library you are using (including Rails) while hide some useful piece of debugging information. Thankfully, in Ruby we can add debugging information directly into our dependencies!

For example, if I am debugging actionmailer (the email sender used in rails) I can `bundle open` that dependency and edit it directly. My new modified action mailer will be used when I restart my rails app. 

`bundle open actionmailer`

open the `inline_preview_interceptor.rb` file

look at the #transform! method

```
   def transform! #:nodoc:                                                                                              
      return message if html_part.blank?                                                                                 
                                                                                                                        
      html_source.gsub!(PATTERN) do |match|                                                                              
        if part **=** find_part(match[9..-2])                                                                                
          **%**[src="#{data_url(part)}"]                                                                                     
        else                                                                                                             
          match                                                                                                          
        end                                                                                                              
      end                                                                                                                
                                                                                                                         
      message                                                                                                            
    end   
```

Depending on which part of this method I am debugging, I can add `#puts` throughout the method or anywhere in the file to inspect the current state. For example, I could add `puts data_url(part)` to see what asset path ActionMailer is generating.

When you are done, you can restore the gem to its original state with `gem pristine actionmailer`

# What methods do I have?

To see what is defined, you can look at what methods a class implements with `MyClass.methods`. This output is often very long and contains a lot of methods that are inherited from Ruby’s `Object` class. You can remove these by doing `MyClass.methods - Object.methods`. The same thing works for instance methods using `MyClass.new.methods - Object.new.methods`.

There are a ton of other tricks like these to more easily debug Ruby programs. Please follow the links in further reading.

**Task: Read about Pry, a popular Ruby debugging tool: **[http://pryrepl.org**/](http://pryrepl.org/)

Further reading:

[1] [http://tenderlovemaking.com/2016/02/05/i-am-a-puts-debuggerer.html](http://tenderlovemaking.com/2016/02/05/i-am-a-puts-debuggerer.html)

[2][http://www.schneems.com/2016/01/25/ruby-debugging-magic-cheat-sheet.html](http://www.schneems.com/2016/01/25/ruby-debugging-magic-cheat-sheet.html)

