# The one where you are one of them
### Overview

The idea for this project was to create a chat application where you have your words twisted by a famous TV show character. It would be fun to lose control of how your words get delived to people. 
Have your words twisted and take the group conversation in a completely unanticipated direction.

I started off with basing the chats on a more "friends" show style conversation. Because ofcourse 10 seasons weren't enough.
I scraped the friends transcripts from [here](https://fangj.github.io/friends/) using cheerio. 
And trained a new model on RunwayML on those transcripts. 

Going futher, I do plan to replicate the same experience with other shows too. Where the users can choose which kind of conversation they would like to be a part of.

<img src="https://user-images.githubusercontent.com/12654691/105268597-89186f00-5b60-11eb-8a62-880db25d3096.png" width="600px" height="300px">
<pre>
      Try out the chat <a href="https://goofy-panini-b0b245.netlify.app"> here </a>
</pre>
- Set a topic for the chat and invite your friends by sharing the link

##### It works something like this. 
      Eg: I gave it a prompt of Joey saying "I am not feeling well today."
<img src="https://user-images.githubusercontent.com/12654691/105054311-d94be000-5a3f-11eb-934f-970524f90dea.png"></img>
Once I hosted the model, I could communicate with it via it's REST API. 

### How it works 
- The person initiating the chat sets the topic for the chat eg: "The one where __________"
- The host then invites other friends using the link. 
- They all land on a screen where they are asked to choose the character which would twist their words and also enter their own name. 
- Let the twisted chat begin. 

Behind the scenes 
- If a user called "Mary" has picked "Monica" all her texts will be redone by monica. 
- Before sending the prompt to runway the server replaces all the personal names with the respective character names.
Eg: If another user Tom picked Joey
"Mary: I hate Tom and Tom's cat" becomes "Monica: I hate Joey and Joey's cat" where Tom has picked Joey. 
- The respon