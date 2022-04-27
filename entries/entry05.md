# Entry 5
The MVP 4/25


## About

At long last I have fully completed my MVP project and learned the necessar components I need from Firebase in order to make my project come to life. My MVP is a schedule website in which users can create or login/logout of accounts and they can save their schedules and reload them as soon as the relogin.


## Authenication Import Statement Setup

Originally I wasn't planning to do Authenication, but slowly after getting through more steps done in my project, I thought it would be absolutley necessary, so I watched this [video](https://www.youtube.com/watch?v=n-kUZw97-lA&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=11) for guidance. First I made a SignUp page. For the signup page I created four files ```signup.html```, ```signup.js```, ```login.html```, and ```login.js```. I wrote some basic HTML in order to make a basic signup page. Next I copied and pasted my Firebase constants to the js file, but added a new import statement with ```auth```
```js

import { getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut, onAuthStateChanged } from 'https://www.gstatic.com/firebasejs/9.6.9/firebase-auth.js';

```
These arguements in the import statements will be neccessary for the next procedures.

## SignUp Page

It was time to begin the javascript process of the Javascript page. First I went to the Auth page and enabled ```Create Account with Username and Password```, so user emails can be stored in auth and later used. Then I added these lines of code based on this [video](https://www.youtube.com/watch?v=-zHAVEoLkG0&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=12):
```js
document.querySelector(".signUpButton").addEventListener("click", function(){




  signupForm.addEventListener('submit', (e) => {
    e.preventDefault()

    const email = signupForm.newUser.value
    const password = signupForm.newPass.value

    createUserWithEmailAndPassword(auth, email, password)
      .then(cred => {
        console.log('user created:', cred.user)

        //later

        const colAccount = doc(db, 'accounts', cred.user.uid)





            setDoc(colAccount, {globalData: ["white", "white", "black", "0px"], Column1: column1, Column2: column2, Column3: column3, Column4: column4, Column5: column5 })

        //



        signupForm.reset();






      })
      .catch(err => {
        console.log(err.message)
      })


  })



```
Basically here is what the code means. First I add an event listener to my ```signUp``` button on my HTML page, then I make another event listener specifically with submit being the event because we want to submit a form when adding data to Firebase Authenication. Next I defined the values of my ```Create Email``` and ```Create Password``` textbox values by the name property(signupForm.newUser.value and signupFrom.newPass.value), then I use the ```cred``` to output the user token as soon as the info is generated. That's pretty much it for creating an account, the information goes straight into the Firebase Authenication.


## Login/Logout Page

Now it was time to make the login/logout page of the portion that way the user isn't always stuck on the same ```uid```. First I added some basic HTML in ```login.html``` Then I added these lines of code based on this the [video](https://www.youtube.com/watch?v=ZUJlSAYvPf0&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=13):
```js

//selecting the login form
const loginForm = document.querySelector(".logIn")

//selecting the logOut button
const loggingOut = document.querySelector(".logout")



//loging the user in


loginForm.addEventListener('submit', (e) => {
  e.preventDefault()

  const email = loginForm.userAccount.value
  const password = loginForm.userPass.value

  signInWithEmailAndPassword(auth, email, password)
    .then(cred => {
      console.log('user logged in:', cred.user)
      loginForm.reset()
    })
    .catch(err => {
      console.log(err.message)
    })
})




//loging the user out

loggingOut.addEventListener('click', () => {
  signOut(auth)
    .then(() => {
      console.log('user signed out')
    })
    .catch(err => {
      console.log(err.message)
    })
})


//detecting auth changes

onAuthStateChanged(auth, (user) => {
  console.log('user status changed:', user)
})





```
Loos like the same process, but we now have two different arguements ```signInWithEmailandUsername``` and ```signOut```. Before I show what does two things do, I need to mention that I selected the name property values for my two textboxes ```Username```, ```Password```(loginForm.userAccount.value and loginForm.userPass.value). I also then added two seperate event listeners for my ```Login``` button and ```Logout``` button, however each with the event ```submit```. Anyways for Login, I call the ```signInWithEmailandUsername(auth, email, password)```, which basically does exactly that. The two parameters, email and password are basically the name properties of my textboxes. Moving on to the signIn button, I just call ```signOut(auth)```, which basically signs out the user auth token, making it null.

## Editions to the signUp using Firestore Arguements

Remember than comment on my signUp code and I wrote ```later```, well now I am going to talk about the significance of those lines of code. The ```const colAccount = doc(db, 'accounts', cred.user.uid)``` basically means to select the accounts collection in my Firebase Database account along with the the specific document being the user auth token. However, user.uid(user auth token) is not defined yet because there is no current doc for the user named this ```auth token```. Then the next set of lines come into play which were based of this [video](): ```setDoc(colAccount, {globalData: ["white", "white", "black", "0px"], Column1: column1, Column2: column2, Column3: column3, Column4: column4, Column5: column5 })```. Ignore the arrays those will come in a later time, but focus on two things ```setDoc``` and ```colAccount```. Since we previously defined the collection as ```colAccount```, but the doc ```user.uid``` does not exist, Firebase Firestore will automatically make up the document, making the user auth the token the exact document name as the doc in the ```accounts``` collection, which is really proefficient for the next steps. For example let's say the user auth token is ```nfRgvGb``` when the user generates an accounts, Firestore will automatically make a doc in the collection ```accounts``` called ```nfRgvGb```


## The Schedule Set Up

Now it is time to set up the page for the schedule. I created 4 new files, ```scheduleInput.html```, ```scheduleOutput.html```, ```scheduleInput.js```, and ```scheduleOutput.js```. In both JS files, I added the following code based on this [video](https://www.youtube.com/watch?v=SFJsgSPzsYI):
```js

onAuthStateChanged(auth, (user) => {


  // var discriminant = prompt("Did you already have a schedule made?")



  console.log('user status changed:', user.email)


    //get the user document based on the current user id object
    const docRef = doc(db, 'accounts', user.uid)



    onSnapshot(docRef, (doc) => {
      console.log(doc.data().globalData, doc.id)

       //the globalData array
       var collectionInfo = doc.data().globalData





       var column1Load = doc.data().Column1
       var column2Load = doc.data().Column2
       var column3Load = doc.data().Column3
       var column4Load = doc.data().Column4
       var column5Load = doc.data().Column5
       var column6Load = doc.data().Column6

      // console.log(column1Load.c1r1[0])








  //global variables









    document.querySelector(".addSchedule").addEventListener('submit', (e) => {
                  e.preventDefault()


        // const inputs = document.querySelectorAll('.testing')
        // const inputsArr = Array.from(inputs);





        setDoc(docRef, {Column1: column1Load, Column2: column2Load, Column3: column3Load, Column4: column4Load, Column5: column5Load, globalData: collectionInfo })



        // const colAccount = doc(db, 'accounts', user.uid)




        .then(() => {

          console.log('user added data')

        })
        .catch(err => {
          console.log(err.message)
        })

        })





    })




})
```
There are 2 new arguements here, doc.id() and onSnaphot and doc. First, I want to load the document reference in realtime which is what ```onSnaphot()``` does and the doc arguement bascially is the doc of the collection. Originally I defined colDoc as ```const docRef = doc(db, 'accounts', user.uid)```, which is basically the user auth token of the user when they log in that way we can immediatley get the document as soon as the user logs in, as the auth token changes with each account, that way everyone's data is local to them personally. Next you can see I set a bunch of variables such as ```column6!Load``` which all seem to use the arguement ```doc.data()```, which basically gets all the documents based on a certain element in the object. For example, ```doc.data().Column1``` specifically gets the Column 1 array in the object of the user's auth document. Furthermore, ```setDoc()``` is used again with parameters that look like objects such as ```Column1: column1Load``` which basically overwrites my original Column1 element with new values, which in my case are arrays.


## The Schedule Page1

Since the code is way too long to copy and paste and since there are 2 pages, I'm gonna only briefly go through the most important javascript codes. First off ```inputSchedule.js```. I inserted the following code:

```js

       var column1Load = doc.data().Column1
       var column2Load = doc.data().Column2
       var column3Load = doc.data().Column3
       var column4Load = doc.data().Column4
       var column5Load = doc.data().Column5
       var column6Load = doc.data().Column6


var newlyAdded
var newColor
var newTextColor
var newBorders
var parent
var newImage
var linebreak
var convertClassToString



  function local(column) {

        newlyAdded = prompt("What would you like to add.")
        newColor = prompt("What background color would you like to add")
        newTextColor = prompt("What text color would you like to add")

        // console.log(newStuff)
        // // newStuff.push(newlyAdded, newColor, newTextColor)
        // console.log(newStuff)



    //     parent = image.parentElement
    //   console.log(parent)





       parent = column.parentElement
       console.log(parent)

       linebreak = document.createElement("br");
       newImage = document.createElement("img");



       newImage.src = "https://cdn-icons-png.flaticon.com/512/84/84380.png"
       newImage.classList.add("newIcon")
       newImage.style.marginTop = "50px";

        parent.innerText = newlyAdded
        parent.style.backgroundColor = newColor
        parent.style.color = newTextColor
        // parent.style.borderRadius = newBorders

       parent.appendChild(linebreak)
       parent.appendChild(newImage)








  }














    var globalBackground
    var globalColumns
    var globalText
    var globalBorders



     globalBackground = collectionInfo[0]
     globalColumns = collectionInfo[1]
     globalText = collectionInfo[2]
     globalBorders = collectionInfo[3]


    global()




  document.querySelector("#global").addEventListener("click", function(){







     globalBackground = prompt("What would you like the background color to be")
     collectionInfo[0] = globalBackground
     globalColumns = prompt("What would you like your column colors to be")
     collectionInfo[1] = globalColumns
     globalText = prompt("What would you like your text color to be")
     collectionInfo[2] = globalText
     globalBorders = prompt("What would you like your borders to be")
     collectionInfo[3] = globalBorders


   global()



})




}

```
Basically what these lines of code set up two things, the customization for each column in the schedule and the customization globally such as background color and column padding. The prompts are run after a button event listen(not shown) called ```Global Settings``` and basically the prompts run and overwrite the ```globalSettings``` element with new array values. Next the ```function local()```, basically there are event listeners(not shown) in the columns, in which if the user clicks, the parent element of the item they selected gets changed with the prompts and then overwritten in ```setDoc()``` (check original paragraph for the arrays)

## The Schedule Page2

This page allows the user to view an uneditable live preview of their document with everything they have stored. Here is what the code of ```output.js``` looks like:
```js

function load(columnRow, columnRowLoad) {



       parent = columnRow.parentElement
      // console.log(columnRowLoad)

       linebreak = document.createElement("br");
       newImage = document.createElement("img");



       newImage.src = "https://cdn-icons-png.flaticon.com/512/84/84380.png"
       newImage.classList.add("newIcon")
       newImage.style.marginTop = "50px";

       var testThing = {
         name: columnRow
       }


        var stringClass = Object.toString(testThing)
        console.log(stringClass)


        // console.log(column.row)
        parent.innerHTML = columnRowLoad[0]
        parent.style.backgroundColor = columnRowLoad[1]
        parent.style.color = columnRowLoad[2]
        // newImage.setAttribute("id",columnRow)
        // parent.style.borderRadius = newBorders

      parent.appendChild(linebreak)
      parent.appendChild(newImage)




  }


```
Basically the ```function load()``` makes it so multiple parent elements of each column can be updated instantly by using the parameters of one of the elements```columnRowLoad``` in the document and the ```columnRow``` which is querySelected on ```outputStie.html```(not shown). There is also a global function that does the same thing, but instead updates the background color and the paddings of the column rows using a ```global``` arguement instead.






## EDP

I am currently in stage 7 of the engineering design process: improve as needed. Basically right now currently have no errors in my code, but it is very messy and needs to somehow be refactored. I am trying my best in order to efficently use the database, while not having too many reads, and trying to keep the client side also not messy. I feel like I can use for loops in order to go through each element along with each array in an object.
## Skills

Regarding skills, I think I’m growing in "attention to detail". Watching all the videos, I noticed that a lot of this code requires experience with javascript object oriented programming. I am not experienced AT ALL in object oriented programming so I had to pay VERY close attention. Remember that error I faced of not using a ```name``` property, well I realized that the name property was indeed the only thing the instructor used. Also forgot to mention, but the textboxes had to be within a form and they had to be labeled reuqired in order to submit the data to Firestore.
## Future Plans

Currently I am finished with my MVP, and after major refactoring, I think I will try and design a good CSS style to my site in order to make it look professional. I am currently using prompts to be able to add user info, which is not seen at all normally, instead I want to turn it into a pop-up. Further, in the future I will slowly start redesiging all of the pages in order to make sure they can redirect to one another as well as the ability to press a button and view the live preview.

[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)
