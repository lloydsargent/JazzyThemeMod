## Why?

I like documentation. I really do. I like to document my code, unlike a friend who says "code is hard to write, it should be hard to read" (I think he meant this in jest). I even like Jazzy.

But the documentation that it outputs is, to put it mildly, user unfriendly. Clicking on things is NOT the way to go.

### Oh, It Looks Like Apple Documentation

Well, its close. If you are a CSS expert, knock yourself out to make this play with PDF's as well as just regular web-pages. I just needed it to not require me to click on everything.

### Didn't you just copy most of what Realm did?

Yes. In fact there are very FEW changes. Just enough to make it usable. For me. If you like it, then knock yourself out.

## Installation

Installation is not trivial, but it isn't hard either. Do the following:

### Step 1 - Install Jazzy

Install Jazzy. You can find it here with instructions:

https://github.com/realm/jazzy

I suggest you do the following to get things working smoothly:

    sudo gem install jazzy

### Step 2 - Break out the Terminal

Next open up a terminal console. If you are afraid of the terminal, then you probably don't want to use jazzy. 

### Step 3 - Edit the Jazzy Code (really easy)

I'm going to assume you know how to use the terminal, sudo, and the like. If anything I've said sounds foreign, I suggest you abandon it now.

Enter the following:

    cd /Library/Ruby/Gems/2.0.0/gems/jazzy-0.7.0/lib/jazzy
    
This assumes that jazzy is still at 0.7.0 (it may have changed - you should be able to find it). Then do the following:

    nano config.rb
    
Yes, we are going to edit a Ruby file. But it will be teeny changed.

Starting at line 286 you will see the following:

      command_line: '--theme [apple | fullwidth |  DIRPATH]',
      description: "Which theme to use. Specify either 'apple' (default), "\
                   "'fullwidth' or the path to your mustache templates and " \
                   'other assets for a custom theme.',
      default: 'apple',
      parse: ->(t) do
        return expand_path(t) unless t == 'apple' || t == 'fullwidth' || t == 'canna'

We want to change it to the following:

      command_line: '--theme [apple | fullwidth | canna |  DIRPATH]',
      description: "Which theme to use. Specify either 'apple' (default), "\
                   "'fullwidth', 'canna' or the path to your mustache templates and " \
                   'other assets for a custom theme.',
      default: 'apple',
      parse: ->(t) do
        return expand_path(t) unless t == 'apple' || t == 'fullwidth' || t == 'canna'

On the first line we added **| canna** after **fullwidth** which is trivial.

On the third line we added **, 'canna'** after **'fullwidth'** which is also trival.

On the last line we added **|| t == 'canna'** at the end which (all together) is trivial.

Save the file. We are done editing the code. See? **That was easy!**

### Step 4 - Copy the Canna.zip file to Theme Directory

Copy the **canna.zip** file anywhere you feel like. Then, in the terminal, go to the folder with the file and type the following:

	sudo mv canna.zip /Library/Ruby/Gems/2.0.0/gems/jazzy-0.7.0/lib/jazzy/themes/
	
Cool! Now:

	cd /Library/Ruby/Gems/2.0.0/gems/jazzy-0.7.0/lib/jazzy/themes/
    unzip canna.zip
    
If you do an **ls** you should see the following:

    drwxr-xr-x   6 root   wheel    204 Aug 13 18:43 .
    drwxr-xr-x  22 root   wheel    748 Aug 12 17:33 ..
    drwxr-xr-x   4 root   wheel    136 Aug 12 17:33 apple
    drwxr-xr-x   4 root   wheel    136 Aug 12 17:33 canna
    drwxr-xr-x   4 root   wheel    136 Aug 12 17:33 fullwidth

### Step 5 - Congratulate Yourself

Pat yourself on the back. You are through the horror. Seriously, it really wasn't that bad, was it?

### Step 6 - Using Jazzy

The simplest way to use jazzy is to go to your terminal (again) and **cd** to your projects directory. Then type the following:

    jazzy --theme canna
    
Canna is the theme you just installed (remember editing code?) It looks very similar to Apples documentation.
    
However, if you are like me, nothing shows up. Bummer. -_-

What I use is the following:

    jazzy --theme canna --min-acl private

This tends to grab everything.

### Step 7 Go read the Jazzy documentation

We are done!
