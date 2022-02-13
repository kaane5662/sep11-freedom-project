# Entry 3
The Import Journey 2/11/22


## About

After tinkering around with Firestore and Firebase itself, as well as making a few document collections in my Firestore database, it was finally time for me to start getting the necessary ingredients I need to import Firebase to my actual ide. Below I will talk about all the steps I have done in order to get where I am now. Right now I am on the process of learning Firestore and how to import and use Firestore for my project.


## Files Setup

Firstly in order to do any of the below, I need to setup my files in proper orientation. I followed a [tutorial](https://www.youtube.com/watch?v=9zdvmgGsww0&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=1) in order to help me. First I made 2 directories, ```src``` and ```dist```. In ```src``` I made an ```index.js``` file and in ```dist``` I made an ```index.html``` file and put the basic template of HTML on there. The point of these files is to ensure that when adding webpack, the ```bundle.js``` file ends up in ```dist```or destination. Finally the files set up was finished and I was ready to move onto the next step.


## Getting Started with a Webpack

One of the biggest mistakes I have made was skipping instructions and jumping straight into importing firebase because that's where most videos and official documentations start instruction. After viewing a bunch of videos, I finally stumbled across one that finally says my mistake and is up to date, which was I needed a webpack installed. As a result I chose this [video](https://www.youtube.com/watch?v=9zdvmgGsww0&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb) in order to ACTUALLY start my procedure. First I installed Node.js on my computer in order to get npm working onto my ide. Next I did ```npm init -y``` in order to add a package.json file into my ide. Then I used ```npm install webpack webpack-cli -D``` in order to get a packagelock.json file as well as developer tools. Next I made a new file ```webpack.config.js```. Then in that file I added this line of code 
```js 
const path = require("path");
module.exports = {
    mode: "development",
    devtool: "eval-source-map",
    entry: "./src/index.js",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    },
    watch: true
}
``` 
because I had to use an development source. Later, I had to edit the code of package.json in order to include ```"build": webpack``` in the scripts section, however there was a tiny error I made and didn't realize until I opened a [stack overflow](https://stackoverflow.com/questions/40439277/package-json-actually-in-json-not-just-javascript) tab. My problem was I entered
```js 
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
    "build": "webpack"
  },
```
I kept getting the error, ```package.JSON must be a JSON file, not javascript```, the simple problem to my solution was adding a comma  ```"exit 1",``` in order to seperate the ```"test"``` from ```build```, then everything went fine, it took some research because I am not experienced at all with javascript objects. Finally, a new file called ```bundle.js``` was made and in the ```index.html``` file, I used a ```script src``` in order to connect ```bundle.js``` to ```index.html```

## Importing Firebase

My next step was to import firebase to my ide. I followed a simple [tutorial](https://www.youtube.com/watch?v=13eja_RYimU&list=PL4cUxeGkcC9jERUGvbudErNCeSZHWUVlb&index=3) to help give some direction. First I used ```npm install firebase``` in order to install firebase to by ```bundle.js```. Next in my ```index.js``` folder, I added the following codes 
```js
import { initializeApp } from 'firebase/app'

const firebaseConfig = {
  apiKey: "AIzaSyBjhE6EvE4Z_87veOHTiqpTMsDWD3Dbtps",
  authDomain: "freedom-project-858bd.firebaseapp.com",
  projectId: "freedom-project-858bd",
  storageBucket: "freedom-project-858bd.appspot.com",
  messagingSenderId: "286303704031",
  appId: "1:286303704031:web:d49b8f432d3d7123d12a6a",
  measurementId: "G-DNV9WRHR16"
};

// init firebase
initializeApp(firebaseConfig)

```
I first went into my project settings and grabbed my ```firebaseConfig``` object in order to delclare which project I should be getting and saving data from. Next I used ```import``` in order to import the ```firebase/app```. Then I called ```initializeApp``` with the arguement ```firebaseConfig``` in order to properly connect to my firebase database. Firebase was now officially set up. 


## EDP

I am currently in stage 4 of the engineering design process: plan the most promising solution. Basically right now I have set up Firebase and now I am wondering what tools can I use that would help with my current idea. I am trying to make a schedule site that lets you add data, save data, as well as fetch data. I decided that Firestore is an absolute necesity to what I am working on because I can use a series of documents in order to do exactly what was mentioned before. However, I have not created prototypes yet nor planned the necessary docs I need to store data yet, so I am definitley not at stage 5 of the EDP yet.

## Skills

Regarding skills, I think I’m growing in "attention to detail". Watching all the videos, I noticed that a lot of this code requires experience with javascript object oriented programming. I am not experienced AT ALL in object oriented programming so I had to pay VERY close attention. When writing code snippets, I made sure to include every comma, every bracket, and make sure the camel-case responded correctly to the elements of the code. I also think I'm growing in "how to google". Remember the npm run error I had earlier, I wrote the error word for word in google, and looked across every trusted document, until I finally found my solution, a comma was missing. I am glad I made this mistake, because I know how to fix it if I ever encounter another error like this one.

## Future Plans

Currently since I have Firebase setup, and I absolutley will be importing Firestore to my project IDE. Firestore is a necessity since it helps fetch, save, delete, and add documents, according to this [documentation](https://firebase.google.com/docs/firestore). My freedom project is a schedule website, in which users can load, save, or add to their schedules. So, in the future I will slowly start adding docs and deleting docs and implement the basics of DOM in order to broadcast the information from front end to the back end for my project. Furthermore, I am thinking of starting to make the front-end of the website, think of a style and layout ui that would look aesthetically pleasing, but can access the back end in order for the user to customize.

[Previous](entry02.md) | [Next](entry04.md)

[Home](../README.md)
