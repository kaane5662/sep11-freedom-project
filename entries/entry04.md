# Entry 3
The Firestore Journey 3/18


## About

Over the past few months, I have been tinkering around and getting to know my javascript tool, Firebase, better and better. In this entry I will talk about my use and application of Firestore as well how I set up firestore in my ```index.js``` file.


## Firestore Setup

Before I use Firestore, I need to set it up in my ```index.js```. In order to set up, I used this [video](https://www.youtube.com/watch?v=rQvOAnNvcNQ&t=244s), that thoroughy explained the process. First I used an import function using a browser module in order to link to the firestore servers. In the import function I added, ```getFirestore```, which initializes the firestore services. So far it looks like this.
```js
import { getFirestore } from 'https://www.gstatic.com/firebasejs/9.6.9/firebase-firestore.js';


```
Finally I added a constant which was named ```db```, where it called a function ```getFirestore()```, in which it had an arguement in the parenthesis ```(app)```. 
```js

const db = getFirestore(app);


```
This was in order to configure firestore and to make sure that data was coming from the Firebase Firestore database. Firestore was now officially set up for my IDE.



## Reading and Getting Docs

Now I had to learn how to fetch and read data from Firestore Database. In order to do so, I followed along with this [video](https://www.youtube.com/watch?v=2yNyiW_41H8&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=4). The first step was to add new arguements to my import function. For adding and reading, I added ```getDocs``` and ```collection```to my firebase import function.
```js
import { getFirestore, collection, getDocs} from 'https://www.gstatic.com/firebasejs/9.6.9/firebase-firestore.js';

```
Next the video instructed me to store a collection reference using the syntax ```const colRef = collection(db, "path")```, where db was the database and the path was any directory in my firestore database. In order to experiment, I created a new collection known as userInfo on Firestore. Next I added a doc named as password and a doc named as username. In the name query, I used a ```string``` called ```kaanthepro``` and in the password query, I used a ```string``` called ```testPass``` Then I used getDocs(colRef) in order to call my collection reference, where in the bottom I wrote:
```js

getDocs(colRef)
  .then(snapshot => {
    // console.log(snapshot.docs)
    let userInfo = []
    snapshot.docs.forEach(doc => {
      userInfo.push({ ...doc.data(), id: doc.id })
    })
    console.log(userInfo)
  })
  .catch(err => {
    console.log(err.message)
  })


```
This code was useful as it pushed each and every doc from my Firestore ```userInfo``` collection and returned the collection as an array with a parent being the collection name. Basically:
```js
Array(7)
    0:
    id: "CW88yekRO8ykULltjd1u"
    password: "testPass"
    username: "kaanthepro"
    [[Prototype]]: Object


```
Which allowed me to get the children of my userInfo parent collection, aka the password and username value.



## Add Docs

My next add docs to my firestore database from my ide. I followed a simple [tutorial](https://www.youtube.com/watch?v=s1frrNxq4js&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=5) to help guide me. First I imported ```addDoc``` to my firestore import function in order to set up the ability and syntax to be able to add documents.
```js
import { getFirestore, collection, getDocs, addDoc} from 'https://www.gstatic.com/firebasejs/9.6.9/firebase-firestore.js';
```
Before I test adding document, I made a signup page in which the user can input their username and password, in order to see if it would store in the database.
```html
<form class = "signingUp">
         <input type="text" placeholder="Create Username" name="newUser" class ="textbox" required><br>
         <input type="text" placeholder="Create Password" name="newPass"class = "textbox" required><br>
         <button>Sign Up</button><br>
         <a href = "login.html">Login</a>
</form>


```
In ```index.js``` I selected the form using ```document.querySelector(".signingUp")```and I used an ```eventListener``` with the value of ```submit``` in order to make it so if the user clicks the ```Sign Up``` button, the data they entered goes straight into Firebase.
```js

const addAccount = document.querySelector('.signingUp')


addAccount.addEventListener('submit', (e) => {
  e.preventDefault()

  
})


```
In the event listener I used the syntax ```addDoc('colRef') {} ``` in order to be able to tell Firestore I am trying to add a document with the following data in the parenthesis. I used: 
```js

addAccount.addEventListener('submit', (e) => {
  e.preventDefault()

  addDoc(colAccount, {
    password: addAccount.newPass.value,  //notice its newPass, name of the textbox
    username: addAccount.newUser.value,  //notice its newUser, name of the text
  })
  .then(() => {
    addAccount.reset()
  })
})



```
In my javascript object, I made sure to specify my collection reference was ```colAccount``` and that I was adding docs to that specific collect. The ```password``` and ```username``` objects are there becuause I want to add the person's password and username to the document, which comes from the VALUE of the student textboxes. I made a huge mistake beforehand, after addAccount I would usually give classes or ids of the certain value, however in this cause you have to use the ```NAME``` property value of an object. After executing the code and clicking sign up, I was able to get my docs into the collection.

## EDP

I am currently in stage 4 of the engineering design process: plan the most promising solution. Basically right now I have set up Firestore and now I am wondering what datastructure I should use for my current idea. I am trying to make a schedule site that lets you add data, save data, as well as fetch data, but its for each user. I have not tested, but prototyped in my head what a basic datastructure can look like, basically the parent being the usernames and passwords, and the children being the schedules they uploaded. However, I have not created an actual prototypes yet nor planned the necessary docs I need to store data yet, so I am definitley not at stage 5 of the EDP yet.

## Skills

Regarding skills, I think I’m growing in "attention to detail". Watching all the videos, I noticed that a lot of this code requires experience with javascript object oriented programming. I am not experienced AT ALL in object oriented programming so I had to pay VERY close attention. Remember that error I faced of not using a ```name``` property, well I realized that the name property was indeed the only thing the instructor used. Also forgot to mention, but the textboxes had to be within a form and they had to be labeled reuqired in order to submit the data to Firestore.
## Future Plans

Currently since I have Firestore setup, and I absolutley will start making a datastructure on my database. A datastructure is absolutley necessary for my freedome -project.. My freedom project is a schedule website, in which users can load, save, or add to their schedules. So, in the future I will slowly start adding docs and deleting docs and subcollections in order to broadcast the information from front end to the back end for my project. Furthermore, I am thinking of starting to design the front-end of the website, think of a style and layout ui that would look aesthetically pleasing, but can access the back end in order for the user to customize. I made a beta version of my schedule, but so far the customization is with prompts, instead of pop-ups, so learning further HTML and CSS, would also be helpful.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)
