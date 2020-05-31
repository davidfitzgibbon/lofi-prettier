This is a general guide in how to set up Prettier with VS Code. The aim of this guide is not to be exhaustive, this is the minimum you need to get started. The reason for this is that it will show you the minumum of what is truly needed to get going with Prettier, so when you set up or adopt a more complicated setup, you will be better informed about what's needed and what isnt.

If you DO want info on a solid, industry standard Prettier / VS Code setup, I recommend [this video from Wes Bos](https://www.youtube.com/watch?v=lHAeK8t94as&t=522s).

## Step 1: VS Code setup

The first thing you need is to set up VS Code for Prettier. By default it doesnt know what Prettier is, so we need to get it up to speed.

Go to the Extensions Tab. You can get there through by clicking View > Extensions.

Type "Prettier - Code formatter" into the search box. Install the one by Esben Peterson.

![Esben Petersons Extension in VS Code Extensions List](https://raw.githubusercontent.com/davidfitzgibbon/lofi-prettier/master/img/prettier-vscode.png "Esben Petersons Extension in VS Code Extensions List")

#### [Optional] only run Prettier in folders with a .prettierrc

Sometimes you dont want Prettier to run. For example, if you bring in a file from a project that DOESNT have Prettier and you save a file, you could reformat every line in any file you save. That means in code review your peers wont be able to tell what changes you made, because every line of code has changes! Oh no!

To avoid this, change the Settings on the Prettier extension we just installed. Go to the overall VS Code settings. You should see a search bar at the top. Search for "Prettier:Require Config" and check the box. This will make it so that Prettier will only run in a folder that has a Prettier config file, called `.prettierrc`.

![Prettier settings with Prettier:Require Config searched for and ticked](https://raw.githubusercontent.com/davidfitzgibbon/lofi-prettier/master/img/prettier-settings.png "Prettier settings with Prettier:Require Config searched for and ticked")

If you have followed this step, add a `.prettierrc` file. It needs to be a valid Prettier config file, so it needs content. All you need to create a valid config is an empty object, so this should be the entire content of your file
`{}`

## Step 2: Choose a version of Prettier to run

When I say choose here, I dont mean you need to go through a list. What we need here is any version, we just need to note it, so that everyone in our team can be using the same version.

Note: if you have downloaded the demo files here, just run `npm i` to install Prettier and [skip this step](#step-3-write-some-terrible-code)

The best way to do this is with a `package.json`, and using npm is the best way to achieve that.

To begin, we need a package.json. These can be a little intimidating to set up, and they often come with lots of stuff in there that you might not need on a smaller team.

To get the basics going, open up a terminal in your folder ( Terminal > New Terminal ) and type `npm init -y`. This will create a package.json for you. The `-y` command just says "yes" to all the qutesions you would usually be asked when setting up a `package.json`. If your repo is private this might not matter too much, but if you're going public with it, then you should actually look into what everything in this file means at some point. Especially the licence info.

Ok, so we have a `package.json`. Now we need to tell it which Prettier package we want to use. In your terminal run `npm install --save-dev prettier`.

This command has done a few things. First, it has installed Prettier locally in your node_modules. Second, it has saved in your `package.json` the version of Prettier that you're now using. Third it has saved this version only as a dev dependancy. This means that when a developer `npm install`s locally, Prettier will install, but when you're deploying, eg to Netlify, then Prettier doesnt install, because it's not needed. Neat!

## Step 3: Write some terrible code

Now you should be set up. You have Prettier installed in VS Code. You may or may not have a .prettierrc file to enable Prettier. You have a version of Prettier installed locally in your project folder. You should be able to write some terribly formatted code now, and see it Prettier magically fix it when you save!

If you have downloaded this repo, you'll see some demo files in the folder `demo_files`. If everything is working, you should be able to open these, hit save and see Prettier update them. You shouldnt even need to change the content here, just hit save.
