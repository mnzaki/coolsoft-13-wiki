# RSpec gems installing
1. Make sure you [merge](https://github.com/DevYah/coolsoft-13/wiki/Git-CheatSheet#merging) the latest master as it contains the gems needed for RSpec.
3. Now you need to type "rails generate rspec:install" in the terminal. This generates the .rspec file and spec folder, where all your test files be placed.
4. Now you're ready to follow these guides, **especially the last one**, in order to write your test files successfully
  * [RSpec-core](http://rubydoc.info/gems/rspec-core/frames)
  * [RSpec-expectations](http://rubydoc.info/gems/rspec-expectations/frames)
  * [RSpec-mocks](http://rubydoc.info/gems/rspec-mocks/frames)
  * [RSpec-rails](http://rubydoc.info/gems/rspec-rails/frames)

## Here's a simple demo
This demo doesn't mean you ignore the links! ;)
If you want to test for example deleting something from table "Table":
```ruby
    describe TableController do
      describe 'DELETE destroy' do
        it "redirects to root" do
          @instance = Table.create
          
          delete :destroy, id: @instance
          response.should redirect_to '/'
        end
      end
    end
```

### Here are more links to understand how RSpec Tests may be setup to your working directories and how you could start to deal with it
  * [Testing intro](http://everydayrails.com/2012/03/12/testing-series-intro.html)
  * [IMPORTANT! Setting up](http://everydayrails.com/2012/03/12/testing-series-rspec-setup.html)
  * [Model Specs](http://everydayrails.com/2012/03/19/testing-series-rspec-models-factory-girl.html)
  * [Controller Specs](http://everydayrails.com/2012/04/07/testing-series-rspec-controllers.html)