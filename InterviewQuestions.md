###Question 1 - What have you learned recently about iOS development? How did you learn it? Has it changed your approach to building apps?

Recently I learned how to use dependency managers like Cocoapods and Carthage in order to use third party frameworks. This has vastly changed my approach to building apps because it opens many more possibilites. For my Nanodegree capstone project, I used Carthage to configure an open-source pitch detection framework I found on GitHub. I would not have been able to build Play That Note without using some sort of framework.

###Question 2 - Can you talk about a framework that you've used recently (Apple or third-party)? What did you like/dislike about the framework?

Like I said in the previous question, for my capstone project I used an open-source pitch-detection framework called Beethoven. I like the current version very much, ever since they implemented the YIN algorithm, which does a much better job at detecting low notes than the other algorithms available in the framework. While I was working on my project, someone also implemented a feature to set a level threshhold to ignore sounds below a certain decibal value, which I ended up using and allowed my users to set the level threshhold with a slider in the settings view depending on the noise pollution they are encountering.

###Question 3 - Describe how you would construct a Twitter feed application (here is an example of Udacity's Twitter feed) that at minimum can display a company's Twitter page. Please include information about any classes/structs that you would use in the app. Which classes/structs would be the model(s), the controller(s), and the view(s)?

The first thing I would do is read the Twitter API documentation to see what data Twitter allows me to use and interact with. After deciding or understanding exactly how the app should work, I would build my storyboard and my model. I would likely have a struct `Tweet` with various properties such as `userHandler`, `date`, `text`, `numRetweets`, etc. I would also have a subclass of a UIView or descendant of UIView like perhaps UITableViewCell called `TweetView` with various IBOutlets for the properties of the `Tweet` struct that I want to display to the user. I'm not familiar with the Twitter API but it may be that Twitter already has a view set up in HTML/CSS/JS available, in which case I could use a WKWebView as my `TweetView`. Then I would build my networking code to fetch the data and parse it, and my view controller(s) to fetch the data from the network and inject it into my view controller to display on the screen via my `TweetView` class.

###Question 4 - Describe some techniques that can be used to ensure that a UITableView containing many UITableViewCell is displayed at 60 frames per second.

In this case you want to assign the cell class a reuse ID and dequeue so that only the cells visible at that time are loaded into memory, and therefore doesn't overload the system.

###Question 5 - Imagine that you have been given a project that has this ActorViewController. The ActorViewController should be used to display information about an actor. However, to send information to other ViewControllers, it uses NSUserDefaults. Does this make sense to you? How would you send information from one ViewController to another one?

This does not make sense. First of all NSUserDefaults is a simple persistence class that is meant to persist raw values instead of objects, which is perfect for something like user settings. If you want to persist the actor data you should use CoreData or another persistence framework like Realm, but persistence isn't even necessary to send the information from one ViewController to another. I would probalby set up a separate set of model structs and classes for the initial ViewController to pass the data to, which can be accessed by any other ViewController in the project. 

###Question 6 - Imagine that you have been given a project that has this GithubProjectViewController. The GithubProjectViewController should be used to display high-level information about a GitHub project. However, it’s also responsible for finding out if there’s network connectivity, connecting to GitHub, parsing the responses and persisting information to disk. It is also one of the biggest classes in the project.

How might you improve the design of this view controller?

I would encapsulate my networking and persistence code in separate classes for reusability and make it more managable, and then call the methods in those classes where appropriate in the `GithubViewController`. What I have done in the past for my projects is to create a `SuperClient` class that handles all the generic netowrking functionality, and then for each individual client implement a subclass for the specific needs of that client (i.e. parsing the data and calling specific API methods). Similarly in my persistence code I would have separate classes that handle the persisting functionality, and call the appropriate methods in those classes from the `GithubViewController` where necessary.

###Before answering the final question, insert a job description for an iOS developer position of your choice!
###Your answer for Question 7 should be targeted to the company/job-description you chose.

[Mobile Developer 
Covenant Eyes - Owosso, MI ](https://goo.gl/MHP1CQ)

###Question 7 - If you were to start your iOS developer position today, what would be your goals a year from now?

I would hope to continue working with the company as an iOS developer to help improve the products of CovenantEyes. I love Apple products but unfortunately because of the way Apple has constructed iOS they make it difficult to develop the type of software CovenantEyes develops without sacrificing many of the integrated features such as Siri. Fortunately Apple has recently released API's such as SiriKit that allow third party developers more power to replicate some of those integrated features in their own apps, so I would like to not only implement someone else's design but also come up with creative ways to improve the product specifically on iOS devices.