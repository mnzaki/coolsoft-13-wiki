### Here is how you can retrieve the count of facebook comments of a specific idea:-

You should just place this piece of HTML wherever you want to retrieve the count, for an idea = @idea:
`<div class="fb-comments-count" data-href="http://apps.facebook.com/idearator/ideas/<%= @idea.id %>">0</div>`

Notice the tag has "0" inside the div, that's totally "USELESS!" It'll be overridden by the actual count of comments! So, if you try to place any text inside this div, i.e beside the count, they will be overridden!

If you need to place any text beside the count, you should consider placing the div element above inside another "whatever" element, eg. link, paragraph, div, etc..

WARNING: If you do so, add a surrounding tag around the comments count div to place some text beside it, please be careful to add to the fb comments div a `class='inline'`