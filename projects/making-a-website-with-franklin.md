@def title = "Liam Doherty | Making a Website with Franklin"

# Making a Website with Franklin.jl

\toc

## Installing Julia and Franklin
Before we can get started with making a website using Franklin.jl, we have to first install the language it is based in: Julia! Julia is a (rapidly) maturing language with a vast amount of resources for computing in applied mathematics, physics, economics, and more! [Julia's website](https://www.julialang.org) is a great place to get a high-level view of what the language has to offer. For the purposes of this post, we will only be concerned with downloading Julia and installing Franklin, however. To download Julia, head over to [this page](https://julialang.org/downloads/) and download the appropriate version for your operating system. If you are not already using a specific IDE (integrated development environment) for other programming languages, I recommend using [Atom](https://atom.io/) with [Juno](https://junolab.org/). Once you get set up with these, you are ready to move on to installing Franklin!

Installation of any package in Julia follows the same format. Open up a Julia session (in your terminal app of choice or within Atom) and write `] add Franklin`. This will prompt Julia to retrieve and download Franklin and all of its dependencies. Once this is done, we can actually start to make the website!

## Initializing the Website
(For more in-depth instructions about how to use Franklin.jl, there are great resources on the [GitHub page](https://github.com/tlienart/Franklin.jl) and on the associated [documentation](https://franklinjl.org/).)

Now that we have Julia and Franklin installed and ready to use, we can begin by initializing a website! First, in an active Julia session, we write `using Franklin` to let Julia know that we are going to be using Franklin. This will allow us to use all of Franklin's functionality right from the REPL.

To initialize a new website, we use the function  `newsite`. As arguments, we can specify the location for the site to be made (you can specify a specific directory on your machine or simply use `"."` if you want to create it in your current folder) and optionally a template to get us started. As an example, I initialized this site using the command

```julia
newsite("liamfdoherty.github.io"; template = "minimal-mistakes")
```

If you would like to try a theme other than Minimal Mistakes, you can check out a bunch of them [here](https://tlienart.github.io/FranklinTemplates.jl/). This command will initialize a website in the specified folder that we can use as a base to modify and make our own.

## Customizing
When customizing the website, we can use the command `serve()` in the REPL. This will load a (local) version of the website in the browser that will update live as we update the information in the website! This is very useful, as it allows us to see in real time what our updates to the site look like and we can easily see if something is broken in the website before we go to deploy the website (in the next part). Now, onto the parts of the website we can customize.

The first part of the website that can be customized is the surrounding "scaffolding" (i.e., links to social media/GitHub, headers and footers that appear on every page). To modify these, we can look in the `_layout` folder. Here, there are pre-made HTML files that define how these appear. We can, for example, change the links at the top of the page (and the words that appear there) by modifying the information in `masthead.html`. The best way to figure out what everything is attached to is to have a live version of the website next to your IDE while modifying this HTML. Since we are only changing little pieces like text and links, we don't need to touch any of the surrounding HTML or even know what it does. Once we modify all of these bits, we will have our (personalized!) information appearing on every page that we create.

To create new pages, we can create corresponding Markdown files (e.g., `making-a-website-with-franklin.md`) and write everything for the webpage using standard Markdown syntax! If you are unfamiliar with Markdown, there is a great [Markdown guide](https://www.markdownguide.org/getting-started/) that can help get you started and at least familiar with some basic Markdown (admittedly, I was not too familiar with Markdown when starting this project, but much of it is so similar to plain text that it was not difficult to pick up). Once you have written a bit of a file, running  `serve()` if you don't have it already up and simply saving the file will allow you to view your new pages!

## Deployment
Now that the website is customized to our heart's content, we can deploy it for the world to see! First, make sure that you have an associated GitHub repository connected with your local project. You can create a repository on GitHub (for the standard user website you can name the repository username.github.io) and in your terminal, connect it to your local folder using `git init` and `git remote add origin (your repo link here)`. Once this is done, all you have to do to push your website to GitHub is use the `publish()` command within Franklin. This will push all of your source code and the generated website to GitHub in two branches: the `master` branch will contain all of your Markdown files and anything else you may have added, and the `gh-pages` branch will contain the generated site. GitHub will then begin working on deploying your website! A word of caution, though: make sure that you check in your repository settings that in the pages tab it says your source is the `gh-pages` branch. If this says that the source is the `master` branch, your website will not load properly and everything on it will look horrible. As long as you do that, you will then have a shiny new website for whatever you would like to share with the world!
