#How the hell to use Sass and SCSS

So this is a small repo that's going to summarize my experiences with Sass and hopefully simplify the process for you, the newbie developer so that you suffer less than me. yay.

##Install Ruby
If you already have ruby installed just skip to the next step.

[Ruby](https://www.ruby-lang.org/en/downloads/) is a super cool high level language that's built on top of C.

[Here's](https://gorails.com/setup/ubuntu/14.10) a convenient guide for Ubuntu users, but either way it's not hard.

Once you've got ruby you can start messing with the gems you'll need. "Gems"are what ruby calls its dependencies.

##Installing [Sass](http://sass-lang.com/)
First things first, you need to install Sass itself. I actually made [this](https://github.com/DavidAwad/sass-site/commit/ba06b865ecd285bab9e026a7b6bb9d680804e994) pull request to the Sass docs because they somehow didn't have this.

The command to use is :
```bash
sudo su -c "gem install sass"
```
You might not need to use sudo, so feel free to do it however you wish.

Now that all the configuring is out of the way, we can get to some simple SASS pre-processing

##Get cracking
So go into your project directory

```shell
david@plato:~$ ls
myCoolProject/
david@plato:~$ cd  myCoolProject/
```
Now if you want, download the ```style.sass``` file I have in this repo. Place it in your myCoolProject directory and then you can use Sass commands to convert it into SCSS or directly to CSS.

```shell
david@plato:~$ ls
style.sass
sass style.sass output.css
```

So what's happening here is pretty simple. sass is the command, ```style.sass``` is the file we're going to send to sass to be converted into something else. And we're going to name it ```output.css```

And now if you look at the folder you'll find the output is right there in the myCoolProject directory.

```shell
david@plato:~$ pwd
myCoolProject/
david@plato:~$ ls
output.css  output.css.map style.sass
```
Now if you're like me you like to keep your code inside of a ```css/``` folder. So you can edit your commands accordingly. I've included a Makefile(if you don't know what a Makefile is check out the notes below) that will allow you to simply type ```make style``` and it will open up the ```sass/``` folder and look for a style.sass and then pre-process it and leave it waiting for you in your ```css/``` folder.(You'll find that [compass](http://compass-style.org/) is a much better way to do this!) so you don't have to mess with your html and can just refresh your browser. Keeping your mind on what matters :)


###So that's it! Enjoy Sass and have fun learning about everything CSS was meant to be!


#Notes:
So a Makefile is essentially a very convenient way for you to run series of bash commands by typing much shorter commands where the user knows exactly what these shortened aliases will execute. If you want to more more, check out [this resource](http://www.sis.pitt.edu/~mbsclass/tutorial/advanced/makefile/whatis.htm).

Apparently if you have a "css" rule in your make file, and also have a folder called "css" then your Makefile will complain which is why it's ```make style``` and not ```make css``` if you're interested in solving this issue and want a make css command check out [this stackoverflow](http://stackoverflow.com/questions/3931741/why-does-make-think-the-target-is-up-to-date). Seems simple to fix but just didn't matter enough for the purposes of this guide.

##Additional Packages
In your experimenting around you may find people using a plugin called bourbon.

Bourbon is a mixin library for Sass that it uses to process your css.

##Installing [Bourbon](bourbon.io)

Here's the command to install the bourbon dependency :

```bash
sudo gem install bourbon
```
Again you may not need sudo, but if it complains with something along the lines of "are you  root?" Then use sudo.

Now let's put it into our web app.
```shell
david@plato:~$ ls
myCoolProject/
david@plato:~$ cd  myCoolProject/
david@plato:~$ bourbon install
david@plato:~$ ls
bourbon/
```
You now have bourbon. You're almost there!

Lastly the way you can get your sass to import it is just like including something like a font.

```Sass
@import "bourbon/bourbon";
```
In this case there is a file called "bourbon" inside of the bourbon folder we created when we used the command "bourbon install".
Just be aware that "bourbon/bourbon" is the path to this file from the root directory of your app, in our case that would be "myCoolProject".
