1-Lets assume you have a list of ideas called @ideas, then in the div you need to place the stream in will be like this:
<% @ideas.each do |your_idea|%>
<%= render partial: "ideas/stream_component", locals: {idea: your_idea}%>
<% end %>
2-Then I assume you need to hook the infinite scrolling function to your stream, then you need to follow these steps:
There are two cases:
Case 1:If you are applying the infinite scroll in actions that don't include the id of this instance e.g the index action
Case 2:If you are applying the infinite scroll in actions that include the id of this instance e.g the show action

Case 1:
a-you need to make a partial that will include the part where you render the stream_component e.g _index.html.erb and write in it the ruby part above.
b-You need to make a index.js.erb file where you append the next ideas to the div it will be as follows $('yourdiv').append("<%= escape_javascript(render(:partial => "your_partial"))%>");
c-then in your .js file you will call the method in the $(window).scroll() function
d- in your action you should place the respond_to format.js statement in order to render the .js.erb file
e- when calling the function you give it params as follows (controller_name,action_name,page,"",[])
f- this function will return an int that will be setted to a var in your .js file called page where you will call the function with every scroll.

Case 2:
Same as case 1, however when calling the function you will call it as follows (controller_name,"",page,id,[]) where the id is the id of the object you are showing.

for further explanation: there will be a meeting to settle it for every body.
