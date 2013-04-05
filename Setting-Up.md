Some things need a bit of setup before they can work properly:
* [Paperclip](Setting-Up#paperclip)
* [Solr](Setting-Up#solr)
* [Database Seeds] (Setting-Up#database_seeds)

## Paperclip
FIXME

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