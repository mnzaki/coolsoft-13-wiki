Some things need a bit of setup before they can work properly:
* [Paperclip](Setting-Up#paperclip)
* [Solr](Setting-Up#solr)
* [Database Seeds] (Setting-Up#database-seeds)
* [Faker](Setting-Up#faker)

## Paperclip
1. `bundle install` if you haven't after your last merge
2. Install Imagemagick.  

**For Windows**
   1. Go to <http://rubydoc.info/gems/paperclip/3.4.1/frames> and install imagemagick.
   2. In `Idearator/config/environments/development.rb`  
       `Paperclip.options[:command_path] = "C:\Program Files (x86)\ImageMagick-6.8.4-Q16"`
 
**For Linux**
   1. Install through synaptic the packages `imagemagick-common` and `imagemagick`
   2. In `Idearator/config/environments/development.rb`  
       `Paperclip.options[:command_path] = "/usr/local/bin/"`

**Common error**

Check that the migration is there UploadImage.
Check that the migration occured by finding in the schema some attributes for the `photopath`,`size`
***
Check in Model :- `has_attached_file :photo, :styles => { :small => '60x60>', :medium => "300x300>",:thumb => '10x10!' },:default_url =>'/images/:style/missing.png' `
You have list of styles `small`,`medium` and `thumb`
Make sure that you have a style that exists in your view `<%= image_tag @idea.photo.url(:medium) %`

## Sunspot with solr
**1st Step:**                                                                                                                       
`bundle install`
***
**2nd Step:**                                                                                                             
`rake db:migrate`
***

**3rd Step:**                                            
`rake sunspot:solr:run`
***
 
**4th Step:(wait till you see the command stating that a connection has been achieved then In another terminal tab)**                                                                                   
`rails s`
***

Now you're done !!!

## Database Seeds
###What is the seeds.rb file?

Seeds.rb file is simply a file that contains data to fill your database 
tables. This file contains "seeds" that each fill a record/s in the 
database. 
To run the seeds.rb file, type:
`rake db:seed`

#####Note:
It is advisable that you `rake db:drop` and then `rake db:migrate`
to start with an empty database.

###User Records in the seeds file:
####User:
```sh
email : hishamelkbeer@gmail.com
password : 123123123
```
####Admin:
```sh
email : hishameladmin@gmail.com
password : 123123123
```
####Committee
```sh
email : marwaelcommittee@gmail.com
password : 123123123
```

##Faker
1. Bundle install after merging with master to install Faker gem.
2. run "rake db:populate" and you are done.

###What is Faker?
Faker is a gem that helps generate fake names,emails, addresses, etc.

###What does populate.rake do exactly?
Populate.rake is a task that inserts records into Users,Ideas and IdeasTags. It inserts 50 users with the password "123123123" and randomly generated emails. It also inserts 50 ideas with 3 tags each and a random number of votes(1 to 500). 