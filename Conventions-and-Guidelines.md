## Naming Conventions

<table>
<thead>
<tr><th>What</th><th>How</th></tr>
</thead>
<tbody>
<tr><td>Issue Title</td><td>S4.2: As a user story I must be completed</td></tr>
<tr><td>Branch Names</td><td>C1_username_#42_short_title</td>
<tr><td>UML Files</td><td>Idearator/UML/issue_42_short_title.png</td></tr>
</tbody>
</table>

## Commit Messages
Use infinitives like 'Change', 'Modify', 'Add'  
Don't use 'Changes', 'Changed', 'Adds', 'Added', etc

One line description, then empty line, then long comment if needed. The only way to add a long description is to [set up your git editor.](https://github.com/DevYah/coolsoft-13/wiki/Configuring-Your-Environment#git)

Example commit message:
```
Issue #42, change the argument list of my_cool_method.

There were unused arguments. Notice the empty line after the short description.
This content can be as small or as big as you want. You can even skip it entirely.
But the short description in one line is very important.
```
 
## Code Style and Conventions
### Making your Editor help you
You can setup sublime to show and fix whitespace and indentation errors by following [these](https://github.com/DevYah/coolsoft-13/wiki/Configuring-Your-Environment#configuring-sublime) dead simple instructions.

### Indentation
- Indent as you code, not as an afterthought!
- Two spaces per indent. Absolutely NO tabs.
- Blocks (those pesky things inside `do ... end` and `{|args| }`) need indentation too!  
    Which means indent things inside them inwards and then as necessary!
- DO NOT indent an entire file inwards for no reason!

### Whitespace
Git understands whitespace. An empty line (emphasis on *empty*; no spaces!) signifies the beginning of a new 'block' of text to git. Git can automerge blocks of text no problem. Help Git help You by separating your blocks with empty lines!

- One and only one empty line between method `def`initions.
- One and only one empty line between separate 'blocks' of code inside a method.
- NO useless spaces at the end of the line! [FOLLOW THESE INSTRUCTIONS](https://github.com/DevYah/coolsoft-13/wiki/Configuring-Your-Environment#configuring-sublime)
- NO useless newlines at the end of the file!
- NO spaces before a comma in an argument list  
    `object.bad_call arg1 , arg2` is **BAD**  
    `object.good_call arg1, arg2` is **GOOD**
- Spaces around equal signs, comparisons, hash arrows:  
    `this=that` `this<that` `{this:"that"}` `{:this=>"that"}` is **BAD**  
    `this = that` `this < that` `{ this: "that" }` `{ :this => "that" }` is **GOOD**

### Some Ruby Style Conventions
- snake_case_like_this for methods and variables
- CamelCaseLikeThis for classes and modules
- Use `unless ... end` instead of `if not ... end` except if there is an `else` branch.
- Use `do |k, v| ... end` instead of `{|k, v| }` for multiline blocks
- Avoid extra parentheses when calling methods, but keep them when you assign the return value.  
    `x = Math.sin(y)` but `array.delete e`
- Avoid unnecessary parentheses when calling or defining methods that take no arguments.  
    `def something` instead of `def something()`
- Prefer single-quoted strings when you don't need string interpolation or special symbols.  
    Use single quotes `'like this'` if you don't use any escapes (like `\n`) or inline code (using `#{}`) or other escapes inside your string. If you need those, then you should use double quotes `"like this #{40+2}"` instead.

You can read more here: https://github.com/copycopter/style-guide#ruby

### Some Rails Style Conventions
- Aim for skinny Controllers!
    All business login goes into the Model. The controller should simply `find` or `create` an object, perhaps load some other data or call a Model method, then pass everything to the view.
- Order controller contents: filters, public methods, private methods.
- Order model contents: constants, attributes, associations, nested attributes, named scopes, validations, callbacks, public methods, private methods.

You can read more here: https://github.com/copycopter/style-guide#rails   
And here: https://github.com/bbatsov/rails-style-guide

## Documentation
```
# This is what the method does, it's a very brief description of the action
# Params:
# +parameter1+:: The parameter is an instance of +Entity+ passed through ....
# +parameter2+:: This is another parameter.
#
# Author: Your Name
```
Params (short for parameters) should include all parameters/arguments passed to the method, and also things like `+params['username']+` for example, which is defined locally for the scope of the method but not passed as an actual argument.

If there are no parameters, then your documentation should look like so:
```
# This is what the method does, it's a very brief description of the action
# Params: None
# Author: Your Name
```

## Reviewing Protocol
FIXME FIXME

## Reviewing Guidelines
### Code
Read the [Code Style and Conventions](Conventions-and-Guidelines#code-style-and-conventions) section above and make sure the developer has followed it closely. Your review should not be limited to just those things mentioned above.

### Scenario
[Checkout](Git-CheatSheet#pull-other-branches) the branch you want to review. Open the Backlog. Try each success and failure scenario. If something is missing or not functioning as outlined in the backlog, tell the developer.

### Tests
Make sure developer has followed the test writing best practices.  
Make sure they are actually testing for the return value and effects of the method.  
Make sure they cover all branches of the method they are testing.  
Make sure coverage is at least above 80%.  

Run the tests. Make sure no tests fail, even those that don't belong to the developer you are reviewing. All tests in master should be running successfully.

### Documentation
Read the [Documentation](Conventions-and-Guidelines#documentation) writing section above and make sure the developer has followed it closely; spaces, new lines, tags (`+param+::`), etc

### UML
FIXME FIXME! FIXME? :(