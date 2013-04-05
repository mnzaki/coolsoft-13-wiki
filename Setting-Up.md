Some things need a bit of setup before they can work properly:
* [Paperclip](Setting-Up#paperclip)
* [Solr](Setting-Up#solr)
* [Database Seeds] (Setting-Up#database-seeds)

## Paperclip
1)Go to this "http://rubydoc.info/gems/paperclip/3.4.1/frames"
and install imagemagick which is compatible with your operating system.
2) write in Idearator/config/environments/development.rb 
   a)For Windows:Paperclip.options[:command_path] = "C:\Program Files (x86)\ImageMagick-6.8.4-Q16"
   b)For Linux:Paperclip.options[:command_path] = "/usr/local/bin/"
3)bundle install

## Solr
FIXME

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