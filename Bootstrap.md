The documentation covers every thing possible. Start here: http://twitter.github.io/bootstrap/scaffolding.html

We currently use the `bootstrap-sass` gem. Just merge master and `bundle install` and you are good to go.  
If you need to override something in the defined bootstrap classes, do so in the `app/assets/stylesheets/bootstrap_and_overrides.css.scss` file.

## Application Layout
**Navbar**

If you want to display anything in the navigation bar, add it in `_navigation.html.erb` in `views/Layouts`
**Sidebar**

If you want to render your view in sidebar , add before your desired `div` `<% content_for :sidebar do %><div></div><%end%>`  

