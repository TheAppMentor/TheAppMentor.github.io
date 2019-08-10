---
layout: post
title: JXA Automation 
categories:
  - Automation
  - JXA
---

Every morning I sit down with my cup of coffee, I visit three websites, cnn.com to check the latest news, www.moneycontrol.com to check how my stocks are doing, and www.weather.com to check todays weather. It takes me about a mintue to open my browser (Safari) and launch these webpages.
If do that everyday for the year thats roughly 300 minutes of type URLs.

This is just a trivial example, but there are a lot of other similar tasks I am sure I do every day. 
```let a = 10```

What if My mac can do that for me? Well, it can. We can write short programs that instructs your mac on what steps to perform and in what order. Such a program is called a script. 

The kind of programs play a different kind of role, their puprpose is co-ordinate with other scriptable applications.
For eg : We can write a script to go to open your browser( which a appjlication) a particular website to fetch the value of currency, populate the value in microsoft Excel and plot a time series chart and then store the chart copy that chart over to Apple Notes application.

Yes we could write a program that could do all this, but the scripting approach allows you to leverage the strengths of programs that already exist on your computer.

That is where scripting shines, it lets each powerful application do what its good at and 
and enable these normally independent co-ordiante with each other.

*Mac Automation is very powerful and can do more than just open a few websties. The ability to chain together scripts and make different applications talk to each other is what give mac autoation its strength.* 

Advantages of using a script :

- Frees you from doing boring repetetive tasks.
- Scripts can run automatically in the background. You can decided the time and frequency. 
- It can be a lot of fun to watch the computer do things for you.

-------------

Language of instrunction :
On a Mac there are two popular languages you can use to write your script. 
 	1. AppleScript - This is language created by Apple for primarily for writing scripts.
 	2. JavaScript - An extremely popular language used widely to build things on the internet.

**Note :** There a other lanuages too, the two above are the most popular.

We will use JavaScript in this post. 

_You can Automate Stuff on the Mac_

_Show some simple examples Of Mac Automation_

Setup required to start Automation.
1. Any Apple Mac.
2. Script Editor : Comes pre-installed on your mac
3. Basic understanding of programming. (Nice to have)

-------------

Launch Script Editor :
Applications > Utilities > Script Editor 
![alt text](./open_script_editor.png)

Lets look at some example.

Lauching an Application. This script will open the 'Finder' appliation and bring it to the front.

**1.1** : Launch Finder
{% highlight javascript %}
const finder = Application('Finder')
finder.activate()
{% endhighlight %}

When you run this script the finder application should launch and become the frontmost app.

<br />
Next, we can now ask the finder application to create a folder.

**1.2** : Create a new folder named "MyScripts" 
{% highlight javascript %}
// Create a new folder on the Desktop
finder.make({
    new: 'folder',
    withProperties: {
        name: 'MyScripts'
    }
})
{% endhighlight %}

<br />

By default the finder app creates the new folder on the Desktop. We can change it any other path by adding an `at` property. 

**1.3** : _Create a new folder in the *Documents* folder_ 
{% highlight javascript linenos %}
// Create a new folder in the 'Documents' folder 
finder.make({
    new: 'folder',
    at: finder.home.folders['Documents'],
    withProperties: {
        name: 'MyScripts'
    }
})
{% endhighlight %}

<br />

### Checking for conditions.
When we re-run the scripts we wrote above, we will see an error because the folder with the name 'MyScripts' already exists.

We can fix this by first checking if the folder already exists.

**1.4** : Check if a folder exits at a location 
{% highlight javascript %}
// Create a new folder in the 'Documents' folder 
if (finder.folders['MyScripts'].exists() == false) {
  // Create 'MyScripts' folder.    
}
{% endhighlight %}

## Sample code :

- Automating Finder.


- Launch Safari and Open a webpage

Every morning, I visit a few websites to check the news, check how the my stocks are doing and check the weather.

#### Next Steps :
- Automating Other application, Notes.



