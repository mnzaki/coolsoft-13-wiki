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

## Code Style
* No tabs! Set your editor to replace tabs with spaces.
* Each tab/indent is 2 spaces.
* snake_case_like_this for methods and variables
* CamelCaseLikeThis for classes and modules

### Common Rubocop Errors
Rubocop is the style checker that we use. Sometimes its error messages are not very clear.

* Prefer single-quoted strings when you don't need string interpolation or special symbols.  
  This means use single quotes `'like this'` if you don't use any escapes (like `\n`) or inline code (using `#{}`) or other things inside your string. If you need those, then you should use double quotes `"like this"`

* Trailing whitespace detected.  
  This means there is whitespace at the end of your line. For example: `"end         "`
  Remove the unnecessary whitespace.

* Tab detected.  
  Don't use tabs! Set your editor to change tabs to 2 spaces.

* Use def with parentheses when there are arguments.  
  Pretty clear. If you have arguments for your method, then use parentheses() when defining it with `def`

* Avoid using {...} for multi-line blocks  
  If you are passing a block to something and it spans multiple lines, then use the `do |args| ... end` syntax instead of the `{ |args| ... }` sytax

## Text formating
* No spaces before punctuation (dots, commas, semicolon)
* Don't overuse exclamation marks!!!!!!!!

## Documentation
```
# This is what the method does, it's a very brief description of the action
# Params:
# +parameter1+:: the parameter is an instance of +Entity+ passed through ....
# +parameter2+:: etc,...
# Author: Your Name
```

## Reviewing/Evaluation
### Code
FIXME
### Scenario
[Checkout](Git-CheatSheet#pull-other-branches) the branch you want to review. Open the Backlog. Try each success and failure scenario. If something is missing not functioning as outlined in the backlog, tell the developer.
### Tests
FIXME
### Documentation
FIXME
### UML
FIXME