# Manually loading file to Glitch / Datasette

For those of you having trouble loading your dataset into Glitch for Datasette, here's another method.

## A link to the data

The only catch to this method is that the CSV you're using has to exist somewhere out on the internet. We need the URL to that data.

Often, your data already is online. Like [this collections](https://www.spc.noaa.gov/wcm/#data) of CSVs representing historical US tornadoes. You can right-click (PC) or control-click (Mac) on a link to copy it's URL.

If it's on your own computer, you'll need to put it online by uploading it to a service like [Dropbox](https://dropbox.com), which will give you 2GB of free storage.

For the dogs data, here's the online URL: `https://s3.amazonaws.com/media.johnkeefe.net/data/NYC_Dog_Licensing_Dataset_2018.csv`

Whether you're using the dogs data, or your own data, have the URL ready for the next steps.

## Working in Glitch

-  Go to [glitch.com](https://glitch.com) and log into your account.
-  In a new broswer tab, go to the [Datasette getting started](https://docs.datasette.io/en/latest/getting_started.html) and click on the "Remix on Glitch" button with the two fish.
-  Once the Glitch project has loaded ... in the lower-left corner, click on "Tools"
-  Click on "Terminal"
-  Now type the word `wget`, a space, and paste the link to your data. So for the dogs data, it would look like this:

```
wget https://s3.amazonaws.com/media.johnkeefe.net/data/NYC_Dog_Licensing_Dataset_2018.csv
```

**NOTE:** If you use a Dropbox link, be sure to remove the characters `?dl=0` from the end of the URL.

Your file will download into Glitch, though _it won't show up in the list of files_. I'm not quite sure why. You can confirm it's there by typing the command `ls` (lowercase LS).

Next, we'll manually put the CSV into a database for Datasette to use. The command is structured like this:

```
sqlite-utils insert .data/data.db [TABLE NAME] [FILE NAME] --csv
```

So for the dogs data, the command is:

```
sqlite-utils insert .data/data.db dogs NYC_Dog_Licensing_Dataset_2018.csv --csv
```

For tornado data, it might look like this:

```
sqlite-utils insert .data/data.db tornadoes 2019_torn.csv --csv
```

You'll see the "Status" and "Tools" icons start to whirl, and you may see a "warning" or "error" ... but just let it work. Once you see a green OK sign, use Glitch's "Show" button to show Datasette in a new window. Your data should be there!


- 

