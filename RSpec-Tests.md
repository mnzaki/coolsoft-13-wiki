# RSpec gems installing
1. First merge the latest master to your branch, as it contains, in the Gemfile and Gemfile.lock, the gems needed for RSpec.
2. When you pull the master and merge it, you'll probably need to bundle install.
3. Now you need to type "rails generate rspec:install" in the terminal. This generates the .rspec file and spec folder, where all your test files be placed.
4. Now you're ready to follow these guides, "ESPECIALLY LAST TWO," in order to write your test files successfully =D
  * [RSpec-core](http://rubydoc.info/gems/rspec-core/frames)
  * [RSpec-expectations](http://rubydoc.info/gems/rspec-expectations/frames)
  * [RSpec-mocks](http://rubydoc.info/gems/rspec-mocks/frames)
  * [RSpec-rails](http://rubydoc.info/gems/rspec-rails/frames)
  * [RSpec Controller Specs](http://everydayrails.com/2012/04/07/testing-series-rspec-controllers.html)

## Here's a simple demo
This demo doesn't mean you ignore the links! ;)
If you want to test for example deleting something from table "Table":

    describe TableController do
      describe 'DELETE destroy' do
        it "redirects to root" do
          @instance = Table.create
          
          delete :destroy, id: @instance
          response.should redirect_to '/'
        end
      end
    end