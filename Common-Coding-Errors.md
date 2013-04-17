## HTML
- All tags without a closing tag should be made self closing:  
    `<br>` `<hr>` `<input name=test>` is **BAD**  
    `<br />` `<hr />` `<input name=test />` is **GOOD**  
    NOT doing this WILL break autoindentation.   

- There should be NO spaces around `=` in tag attributes:  
    `<input name = "a_field" />` is **BAD**  
    `<input name="a_field" />` is **GOOD**  
    NOT doing this is against standards and might cause trouble under certain conditions.  

- We do NOT use `<table>` tags for layout. Use only `<div>` tags with the appropriate bootstrap classes.  
    Read [the bootstrap documentation](http://twitter.github.io/bootstrap/scaffolding.html#gridSystem). We are using the fixed grid system and not the fluid system.

## Ruby and ERB
TOEXPAND
## Rails
TOEXPAND