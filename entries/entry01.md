# Entry 1
##### 11/8/21

## About

For my freedom project, I want to create a schedule organizer site/app. The product will contain a variety of local assets(assets given by the site/app), profile customization/statistics, as well as the ability to save schedules, and ability to upload custom assets(assets uploaded by the user). I will be using [Firebase](https://firebase.google.com/docs/guides), [Highcharts/D3](https://www.highcharts.com/), along with [JsonApi's](https://jsonapi.org/) to make my product come to life. This of course is followed by Javascript and HTML/CSS, to script the backhand(scripts running in the background) and frontend(what the user visually sees).

## Firebase

Google Firebase is a Google-backed application development software that enables developers to develop iOS, Android and Web apps. Firebase provides tools for tracking analytics, reporting and fixing app crashes, creating marketing and product experiment. How does it work? The Firebase Realtime Database lets you build rich, collaborative applications by allowing secure access to the database directly from client-side code. Data is persisted locally, and even while offline, realtime events continue to fire, giving the end user a responsive experience. I will be using Firebase to store/save local client side data such as username, password, and profile statistics. 

## Highcharts/D3

Highcharts and D3 are practically the same thing, but to make matters simple I will be using Highcharts. Highcharts is a pure JavaScript based charting library meant to enhance web applications by adding interactive charting capability. Highcharts provides a wide variety of charts. For example, line charts, spline charts, area charts, bar charts, pie charts and so on. I will be using Highcharts to make the statistics of the profile's visually appealing. In additon, I will make it so the *local* statistics can be customized by the user. For example the user can shift their statistics to left or to the right, put their most favorite in the top or in the bottom. Furthermore, I will also use Highcharts in order to make the *schedule creation experience* immersive. I want the user to feel like this schedule creation experience is "open world", meaning that the user control how they want their schedule to look like. Sure I will give them a lot of options from Highcharts, but I will allow the user to place their selected objects wherever they want. Most sites nowadays limit this feature with subscriptions as well as fees, some even just let the computer automatically place it without any command from the user. 



## JsonApis/Backup

JSON API is a format that works with HTTP. It delineates how clients should request or edit data from a server, and how the server should respond to said requests. I will be using JsonApi's in order for in order to *extract/fetch* the data from Firebase into my product. This way users will immediatley be given the data they were left with when the relogin to their account, basically fetch data. 



I am currently in stages 1 and 2 of the engineering design process: defining and researching the problem. Basically right now I am still researching the problem and visualizing what data I'm gonna store and what data I'm gonna fetch. In addition I am asking questions to my self about how will this impact the client based side along with how will this visually preload to the user when i fetch the data. Up next, I will be brainstorming possible javascript I can use to make the ability to store the data come to life. This will require thinking inside and outside the box about how to tackle this issue in a way that has been done before, but improving it and making sure the site loads in the fetches the data in a correct visually matter. So far in class, we’ve learned about the basics of Javascript, and I’m slowly realizing that the possibilities are endless with what I can create with Javacript.

Regarding skills, I think I’m growing in learning “being creative of solving the problem” specifically toggling the issues of the client as well as giving the user an immersive experience. There is plenty of sources out there and I learned that the tools I use are beneficial to me as they can be published with Javascript. I also noticed that I can implement other backup tools since Javascript is one of the most popular programming languages out there. Basically, the more I get the hang of Javascript, the better I will be able to understand the function of these tools and implement them too my product. 


[Next](entry02.md)

[Home](../README.md)
