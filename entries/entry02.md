# Entry 2
The Journey 12/17/21


## About

After locking in all the components I need for my freedom project, it was time to start learning at least one of my tools. I started off personally with Firebase. Firebase is a Google Firebase is a Google-backed application development software that enables developers to develop iOS, Android and Web apps. Firebase provides tools for tracking analytics, reporting and fixing app crashes, creating marketing and product experiment. Below I will briefly mention my progress so far and what I have done after tinkering around with Firebase.


## Getting Started

Firstly, I read the [introduction](https://firebase.google.com/docs/firestore?authuser=0) to know what Firebase is about. I read about the key capabilities and I also read about the implementation path. Now it was time to start, I clicked the [Get Started](https://firebase.google.com/docs/firestore/quickstart?authuser=0) tab and started to look over procedure. Firstly, I went over to the Firebase console and clicked "add project". I named my project ```freedom-project```. The console later then asked if I want it on test mode or locked mode. I chose test mode because I am new to programming and was just getting introduced with mobile and web client libraries. Finally, I set up my [development environment](https://firebase.google.com/docs/firestore/quickstart?authuser=0#set_up_your_development_environment), which was the code for Web Version 8 for my ide.

## Understanding Cloud Firestore

My next steps, were considering the data I need to store and them adding them to Cloud Firestore. I had no idea how to implement datea to clud firestore so I watched a helpful [tutorial](https://www.youtube.com/watch?v=BjtxPj6jRM8). I went over to the "Cloud Firestore" tab and clicked "Create Database". The prompt asked me to choose whether if I wanted to stay in "Test Mode" or "Production Mode". Production mode was where data was private by default in which client's viewing or editig access are determined by your security rules. In test mode, your data is open by default to enable a quick setup, however security rules must be updated within 30 days for the long-term. So, I chose test mode. Then I was greeted with a prompt that asked where the location of where my cloud firestore data will be stored. From the dropdown menu, I chose ```us-east``` because I live in the US and I live in New York which is to the east coast of the US. My data base was now set up and ready for collections.

## Starting a Collection

After careful consideration of what I want to be stored for my freedom project, I considered starting a collection of ```names``` because for my site I wanted to store each clients individual schedule with their own name. I had no idea where to start, so I opened up a helpful [video](https://www.youtube.com/watch?v=T-h5Oiyihjo) to follow along. I first clicked ```start collection``` and then wrote ```names``` for my document parent path. Then a prompt came up asking me for my document id. Since, I had no clue what to put I let the prompt autogenerate an id for me. Next I was instructed to add a field, in which I created 4. I decided to write in camelcase format since the instructor was also doing the same, I wrote for field 1: ```firstName```, field 2: ```lastName```, field 3: ```dateOfBirth```. I wanted all this infor to be stored as string values since these were names and not numbers, so for "type", from the dropdown menu, I chose ```string```. The first values I put in were some of my own just to test, ```firstName string value: Kaan```, ```lastName string value: Eren```, ```dateOfBirth string value: 2005```. 

## EDP

I am currently in stages 1 and 2 of the engineering design process: defining and researching the problem. Basically right now I am still researching the problem and visualizing what data I'm gonna store and what data I'm gonna fetch. In addition I am asking questions to my self about how will this impact the client based side along with how will this visually preload to the user when i fetch the data. Up next, I will be brainstorming possible javascript I can use to make the ability to store the data come to life. This will require thinking inside and outside the box about how to tackle this issue in a way that has been done before, but improving it and making sure the site loads in the fetches the data in a correct visually matter. So far in class, we’ve learned about the basics of Javascript, and I’m slowly realizing that the possibilities are endless with what I can create with Javacript.

## Skills

Regarding skills, I think I’m growing in learning “being creative of solving the problem” specifically toggling the issues of the client as well as giving the user an immersive experience. There is plenty of sources out there and I learned that the tools I use are beneficial to me as they can be published with Javascript. I also noticed that I can implement other backup tools since Javascript is one of the most popular programming languages out there. Basically, the more I get the hang of Javascript, the better I will be able to understand the function of these tools and implement them too my product. 

## Over the Break

During the break, I initially want to start planning out how the website will look CSS/HTML wise, and how the backhand/JS will run when the client enters my website. Also I want to figure out how to link all my stuff on Cloud Firestore to my ide as well as set up security measures. To test, I will be writing random lines of code for each ```client``` and see if cloud firestore will save it's info. I was initially thinking of a login page, but I feel that's far outside my learning zone, and actually in my panic zone, but I might still try.


[Previous](entry01.md) | [Next](entry03.md)

[Home](../README.md)
