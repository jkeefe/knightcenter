# Using Datasette on your own computer

This is actually an awesome option. It gives you the independence from cloud services that ... well ... might not work!

I had gone for Glitch because installing Datasette will vary a little depending on your computer. But once it's there, it's yours to use whenever!

## Installing

We're going to install Datasette on our computers.

First we need to get you to the command line. That will mean opening "Terminal" on a Mac ([Here's how](https://www.howtogeek.com/682770/how-to-open-the-terminal-on-a-mac/)), or the "Command Prompt" on Windows. ([Here's how](https://www.howtogeek.com/235101/10-ways-to-open-the-command-prompt-in-windows-10/) to get there on a PC.)

### If you use a Mac ...

You can install datasette and the tools we need by entering these two lines into the terminal:

```
brew install datasette
brew install sqlite-utils
```

**OR** you can use `pip`. (If you don't know the difference, use `brew`.)

```
pip install datasette
pip install sqlite-utils
```

### For PCs or other platforms ...

You can try installing Datasette using `pip`, which is a Python installation program. 

```
pip install datasette
pip install sqlite-utils
```

Your system is going to vary, so if `pip` doesn't work you may want to try one of the [advanced installation](https://docs.datasette.io/en/latest/installation.html#advanced-installation-options) options, such as `pipx` in the Datasette documentation. 

For those of you on Windows, you may need to add Python to your system. Datasette needs at least Python 3.6, and you can get Python 3.8 free [from the Microsoft Store](https://www.microsoft.com/en-us/p/python-38/9mssztt1n39l#activetab=pivot:overviewtab).

## Loading your CSV

We need to turn your CSV into a database. Here's the command:

```
sqlite-utils insert data.db dogs [FILE NAME] --csv
```

Where I have `[FILE NAME]` you'll need the entire path to your dog data CSV. For me, the file is on my desktop and my command is:

```
sqlite-utils insert data.db dogs /Users/johnkeefe/Desktop/NYC_Dog_Licensing_Dataset_2018.csv --csv
```

Again, your situation will vary. One way to find the full path of a file on a Mac is to drag the file into the Terminal window. It'll print the path!

(Note that sometimes it seems to get "stuck" at 99% ... just hit enter; it's done.)

Jump into the forums if you have trouble finding the path for your dog data CSV.

### For all future datasets

For any other datasets you use ... including your second dataset for this class ... just load the data into your database using this pattern:

```
sqlite-utils insert data.db [TABLE NAME] [FILE NAME] --csv
```

Again, `[FILE NAME` is the full path to the file. 

`[TABLE NAME]` is just a short name for your data you'll use in Datasette.


## Starting Datasette

The next part is easy!

Just type this:

```
datasette data.db
```

You'll get something that looks like this:

```
INFO:     Started server process [10918]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://127.0.0.1:8001 (Press CTRL+C to quit)
```

Datasette has loaded the data and is now running a little web server for you right on your computer. 

Go to your favorite browser and enter the url in the message: http://127.0.0.1:8001 

Your personal Datasette instance is now up and running!



