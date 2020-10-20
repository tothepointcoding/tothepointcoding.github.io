---
layout: post
categories: [Web]
about: host a website on github
---
# Contents
{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}

# Description
Shows how to host a website on github which utilises HTML/CSS/JS.
This is NOT a HTML/CSS/JS and git tutorial, this will only show some basic examples!

# Preparation
Obviously you need a Github account and have Git installed on your machine.

# Github
Create a new repository on Github with following name **your_accountname**.github.io .


<figure>
  <img src="/assets/images/githubpages/newrepository.PNG" alt="new repository on github picture">
  <figcaption>Figure 1: new repository screen on github</figcaption>
</figure>

On Figure 1 you can see the newrepository screen.  
If you want to keep the repository private you need a pro account, which you can get for free if you are a student.  
Click on the green button to create the repository.

<figure>
  <img src="/assets/images/githubpages/createdrepository.PNG" alt="created new repository picture">
  <figcaption>Figure 2: created new repository</figcaption>
</figure>

Copy the marked link on Figure 2 by either marking and copying it or by pressing the marked button on the right.  
Now we will clone this repository, while doing so it will create a new folder on your machine with the repository name.  
For that open the command line at the path where you want to copy the repository and enter the following command with the copied link.

````
git clone https://github.com/tothepointcoding/tothepointcoding.github.io.git
````
Now you should see (Figure 3) the same warning, unless you created a README for the project on github.

<figure>
  <img src="/assets/images/githubpages/gitclone.PNG" alt="gitclone picture">
  <figcaption>Figure 3: cloning repository from Github</figcaption>
</figure>

It created a new folder with the repository name with a hidden .git folder inside it (Figure 4).  

<figure>
  <img src="/assets/images/githubpages/newrepositoryfolder.PNG" alt="new folder for repository picture">
  <figcaption>Figure 4: new folder for repository</figcaption>
</figure>

# Simple website
Finally we can work on our website.
Create a index.html file.
Fill it with your HTML content, here an example:

````html
<h1>This is a h1 title</h1>
<p>This is a paragraph</p>
````

Now to add the changes with the following commands:
````
git add .
git commit -m "init website"
git push
````

<details>
<summary>Error on push</summary>
If you have never pushed code to your github account before, it will ask you to log in.<br>
You could log in with your username and password, but this form of authentication will soon be deprecated on github.<br>
You have to generate a PAT (Personal Access Token) on github and use that as your password instead.
You can generate one at https://github.com/settings/tokens.
</details>

Go to your website on **acountname**.github.io and you will see your website (Figure 5).

<figure>
  <img src="/assets/images/githubpages/website.png" alt="website with title and paragraph picture">
  <figcaption>Figure 5: website with title and paragraph</figcaption>
</figure>

Congratulations you are hosting a website on github.

# Adding some content
Well this page is rather simple so let's add some more stuff.
We want a valid HTML page with css, js, image, navigation and a 404 page.  
All of which will be explained in each paragraph.  
The endresult of the index.html file is the following:

````html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>My simple github pages website</title>
  <meta name="description" content="dunno some description">
  <meta name="author" content="authorname">

  <link rel="stylesheet" href="main.css">
  <script src="main.js"></script>
</head>

<body>
<ul>
  <li><a href="index.html">Home</a></li>
  <li><a href="about.html">About</a></li>
</ul>

<br>

<button onclick="buttonclick()">a button</button>
<p id="loremipsum">Lorem ipsum dolor sit amet, consetetur sadipscing elitr,
 sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat,
 sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum.
 Stet clita kasd gubergren, no sea takimata sanctus est Lorem</p>

<img src="picture.png">

</body>

</html>
````

Figure 6 shows you how this example website looks like.

<figure>
  <img src="/assets/images/githubpages/websitecontent.PNG" alt="a simple website picture">
  <figcaption>Figure 6: a simple website</figcaption>
</figure>

Nothing fancy only the minimum, so YOU can start quickly.

## CSS
To add styling through an external css file, we first obviously need to create a css file.
Create in the root folder the file **main.css**.
Now we just add some styling to the css.

````css
body {
    background-color: lightgrey;
}

p {
    color: darkblue;
}

ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
}

li {
    display: inline;
}
````

To be able to use the css stlyesheet we added the following line to the **<head>** section in **index.html**.

````html
  <link rel="stylesheet" href="main.css">
````

Congratulations you added styling to your website.

## Javascript
Beside shining beauty we also need some functionality on our website.
Create a **main.js** file in the root folder.
For now, we just want our button in **index.html** to change the text of the paragraph.
Add the following code into **main.js**.

````js
let pressed = false;
function buttonclick(){
	pressed = !pressed;
	if (pressed) {
		  document.getElementById("loremipsum").innerHTML = "Lorem ipsum more like lorem noMoreSum;"
	} else {		
		  document.getElementById("loremipsum").innerHTML = "Lorem yesMoreSum"
	}
}
````

We obviously need to use the js file in our html page, to do that add the following line, also in the **<head>** section.

````html
  <script src="main.js"></script>
````

After the first click you will see on Figure 7, that the text changed.

<figure>
  <img src="/assets/images/githubpages/paragraphchange.PNG" alt="paragraph changed picture">
  <figcaption>Figure 7: paragraph changed after button click</figcaption>
</figure>

Congratulations the paragraph in index.html changes after you press the button.

## Image
Add a picture to the root folder and add the following html code, but change the name of the file.  

````html
    <img src="picture.png">
````

Don't pull your hair out, because you forgot to match the name of the file and the source of the file name in the code.
This happens more often than I'd like to admit.

## Navigation
We want to add an about page to our website.
Create a new file in the root folder **about.html**.
For simplicity just add the following code:

````html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>My simple github pages website</title>
  <meta name="description" content="dunno some description">
  <meta name="author" content="authorname">

  <link rel="stylesheet" href="main.css">

</head>

<body>
<ul>
  <li><a href="index.html">Home</a></li>
  <li><a href="about.html">About</a></li>
</ul>

<h1>About</h1>
<span>How about that!</span>
</body>

</html>
````

As you can see the about page also uses the main.css stylesheet.
The important bit for navigation is just the following line:

````html
<a href="about.html">About</a>
````

If you create a link to the name of the HTML file you can easily switch between them.  
As you can see on Figure 8, if you click on the link the URL points to the file.

<figure>
  <img src="/assets/images/githubpages/urlchange.PNG" alt="url changes after clicking on the navigation picture">
  <figcaption>Figure 8: url changes after clicking on the navigation</figcaption>
</figure>

Congratulations you can now add more pages to your website and navigate between them.
But if you manually change the URL to a page that doesn't exist you get a 404 page by github (Figure 9).

<figure>
  <img src="/assets/images/githubpages/404notfound.PNG" alt="github 404 page picture">
  <figcaption>Figure 9: github 404 page</figcaption>
</figure>

Instead of showing the generic github 404 page, we want to show our own.

### 404 page

Create a **404.html** file in the root folder and add the content you wish.
How about adding a navigation to our 404 page, so our lost visitors can find their way to an actual page?

````html
<!DOCTYPE html>
 <html>
<head>
  <meta charset="utf-8">
  <title>My simple github pages website</title>
  <meta name="description" content="dunno some description">
  <meta name="author" content="authorname">
  
  <link rel="stylesheet" href="main.css">
</head>

<body>
<ul>
  <li><a href="index.html">Home</a></li>
  <li><a href="about.html">About</a></li>
</ul>
<h1>404</h1>
<p>page not found :(</P>
</body>

</html>

````

Instead of serving the generic 404 page (Figure 9) it shows our own custom page (Figure 10).

<figure>
  <img src="/assets/images/githubpages/custom404page.PNG" alt="custom 404 page picture">
  <figcaption>Figure 10: our custom 404 page</figcaption>
</figure>

## Add custom domain
If you want to change the domain, you obviously need to buy one first.
I bought mine from namecheap. It doesn't matter from where you buy it from. Somehow everyone has bad experience with all domain providers, so you know if something happens I am not at fault.  
You can easily find already existing tutorials on how to change the domain for github pages.  
Here is the link for namecheap:
[Link for namecheap example](https://www.namecheap.com/support/knowledgebase/article.aspx/9645/2208/how-do-i-link-my-domain-to-github-pages)
You also need to change the domain in the settings of the repository (Figure 11).

<figure>
  <img src="/assets/images/githubpages/customdomain.PNG" alt="custom domain picture">
  <figcaption>Figure 11: custom domain setting</figcaption>
</figure>

It will create a new file called **CNAME** (Figure 12) with the domainname inside of it.

<figure>
  <img src="/assets/images/githubpages/cname.PNG" alt="CNAME file picture">
  <figcaption>Figure 12: generated CNAME file</figcaption>
</figure>

Once you changed the domain, you can enforce HTTPS after 24 hours.

# Conclusion
See how easy you can host a website on github pages.  
Now you can add some more stuff and flesh the website out, add a new page, more functionality, better design...

## Exercise
Try to create a static site for a restaurant or a cafe.  
Just list the menu with prices.  
Add an about page with telephone number, e-mail etc.

