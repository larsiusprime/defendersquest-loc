# defendersquest-loc
Localization Repository for Defender's Quest series

**NOTE:**
This page is for *amateur/volunteer fan translators.* If you are a *professional translator*, we might be interested in hiring you to do an *official translation* of Defender's Quest sometime in the future.

We have a limited budget for hiring professionals and are focusing on the largest language markets.
If you would like to be added to our list for consideration, please send us an email: *LevelUpLabs [at] Gmail [dot] Com* with the subject line "Professional Translator."

We now return you to your regularly scheduled fanlation page:

---

First of all, thank you for taking an active role in the improvement of Defender's Quest. We deeply appreciate your contribution and hope that not only you, but other players are able to benefit from that contribution. Below are the guidelines and terms and conditions for your submission. 

---

1. Read the <a href="#instructions">Instructions</a>
2. Read & Accept the <a href="#terms">Terms and Conditions</a>
3. Click <b>"I Agree"</b> at the bottom to get DropBox access. 

---
<a id="instructions"></a>
**Instructions**

*This [continuously updated forum thread](http://www.leveluplabs.com/forum/viewtopic.php?f=14&t=1234) is the best place to get the latest information.<br>
"Getting Started" info is found below.*

**1. Get the latest test build**<br>
Send requests for a testing invite to *leveluplabs [at] gmail [dot] com* if you don't have one already. You'll receive instructions on how to get the latest in-development version of the game. 

**2. Download/install the test build**

**3. Find the "locales" folder**<br>
It's in the game's installation directory; on windows the default location is C:\Program Files (x86)\DefendersQuest. There should be a "locales" folder inside.

Once you're in this folder, it should show you all the locales (language packs) that the game supports. Right now you'll see a few files: 

* _flags (folder)
* en-US (folder)
* de-DE (folder)
* index.xml 

Open index.xml in a text editor, you will see something like this: 
<br><br>
<textarea rows="9" cols="75" style="border:none;">
<locale id="en-US" default="true" sort="0">   <!--American English-->
	<ui language="Language" region="Region" accept="Okay" />
	<label id="en-US,en-GB,en-CA" language="English" region="United States"/>
	<label id="es-ES" language="Inglés" region="Estados Unidos"/>
	<label id="de-DE" language="Englisch" region="Vereinigte Staaten"/>
	<label id="fr-FR" language="Anglais" region="États-Unis"/>
	<label id="nb-NO" language="Engelsk" region="U.S.A."/>
</locale>   
</textarea>

The index.xml controls what languages the user can select from the languages menu in the save slot screen. This is the entry for American English, or "en-US". "en-US" is American English's locale id. The locale id is the ISO 639-1 language code with 2-letter country suffix.

This includes the name of that language and region in its native language as well as other supported languages. You can just put placeholders in and you only need to define stuff for languages you plan on supporting. Right now only en-US and de-DE (German in Germany) are supported, so if you were to add, say, Polish, you would add an entry for "pl-PL". The tag has the words for the interface elements on the locale menu in the specified language.

You might also want to add a flag for your country. Those are stored in the "_flags" folder and are 16x11 png files. We got ours from famfamfam. Just make your flag's name match the locale id and it will automatically select it for your locale.

Each locale is a combination of a language ("English") with a region ("United States"). This is because there are often regional variants of languages, and languages often cross country borders. For instance, there is German as spoken in Germany (de-DE) and German as spoken in Austria (de-AT). There's also Canadian English, Costa Rican Spanish, etc.

Anyway, that just defines what languages are available. You then have to supply actual text. The simplest way to get started is to just copy the en-US folder and rename it to your country code, then open the contents and start replacing text. That way, you will have something that works right away, but can slowly work through it and see your changes in game.

So, open up en-US and take a look. You'll see a lot of files. Generally, these are all CSV files, which are spreadsheets formatted as plain text. Generally, a row of cells is written like this: 
<br><br>
<textarea rows="1" cols="75" style="border:none;">
	"Text between","two quote marks and","separated by commas.",
</textarea>

Note that these are normal quotation marks, not fancy left/right variants, and regular commas. Every line MUST end with a comma or the game will choke. Furthermore, in some files we use 4 commas as a separator as a brute-force hack. That might change. Just follow whatever format you see in the given file and you SHOULD be fine. Do not add extraneous punctuation, extra lines, or break the pattern or you risk the file not working. Also, use a plain text editor like Notepad++, do NOT use a word processor like Microsoft Word.

Anyway, we'll have lots of fun dealing with encoding issues and CSV stuff as time goes on. This is kind of wild territory we're in and we'll figure it out as we go - for now this looks *pretty* stable.

So, let's look at data_status_effects.csv:
<br><br>
<textarea rows="3" cols="75" style="border:none;">
"$FLAV_SLOW","Slow",
"$FLAV_FREEZE","Freeze",
"$FLAV_LIGHT","Light",
</textarea>

This defines the names of the flavors "slow", "freeze", and "light". So, in data files where you're putting the names of flavors, these flavors are now just ids - the game will attach "$FLAV_" to the front of a flavor id and then try to look up that value in the locale database to display the name. So, you might do this for, say, Norwegian:
<br><br>
<textarea rows="3" cols="75" style="border:none;">
"$FLAV_SLOW","Sakte",
"$FLAV_FREEZE","Frys",
"$FLAV_LIGHT","Lys",
</textarea>

And save the file. Keep in mind, if you use a spreadsheet program to edit these files, they might trash the formatting and it will have to be put back in manually. That's not *TOO* big of a deal - We can be on hand to give tips for fixing them after the fact, but in general if the formatting breaks, the game will choke, guaranteed. It might even choke if they're perfectly formatted! We'll be here to bail you out, either way.

So, basically all a translator has to do is make their own localization folder, enable it in the localization index file, replace English strings in their copied folder, and your localization folder is ready for submission. 

---

#Caveats:

**Encoding.** Save your text files as UTF-8. If you don't know what this is, just save your files normally and if they choke, talk to me and we'll fix it 

**Fonts.** Font support will take some time. The latest version of the game uses an extended Latin character set, so I know it will pick up ümläüts and Nørwegiån characters, etc., but We are not so sure about those little cross-lines on Polish characters, for instance. Also, Asian, Arabic and Cyrillic characters DEFINITELY won't work, I'll have to do some major overhauling to support that, which means there'd have to be either proven interest in Asian markets, or a lot of demand from Asian/Arabic fans, for us to consider it. Cyrillic is not as big a deal and we'll add that soon because it's only a few extra dozen characters and otherwise behaves mostly like latin text (i.e., left to right, similar word lengths, etc.). So, if you do a translation and some characters aren't showing up, post a list of them on this forum and we'll add them in the next build if we can. 

**Syntax.** Grammar, word order, word length, varies wildly between languages. More than likely, a translation you're working on might not fit in the space allotted. There are two solutions: 1) get us to make the game more flexible, and 2) get creative, perhaps by thinking of a shorter synonym. We'll try to help where we can, but often you'll have to resort to option 2. In reasonably situations, We will try to add support to the game in places we anticipate this will happen - such as cut-scenes. There is already support for making cut-scene lines show only if a certain locale is active, so if one line in English becomes enough for two in German, you can add a second line for the German one in this way and still have the cut-scene play smoothly. Again, contact us and we'll work it out. 

**Documentation.** Full documentation is forthcoming. This is just to get you started. There are a lot of tips/tricks and tools available to you that we don't have time to cover just yet, but we will get to them all eventually. 

<p style="text-align:center">
	<a href="#top">Back to Top</a>
</p>
---
