# Chapter 1 | Setup your bot

What you shoud have by now is an application, made on the discord developer portal. <br>
If you do not know how, please see [here](https://discordpy.readthedocs.io/en/latest/discord.html)

Make sure to have your bot invited to your server so we can test it while coding it.

### Tips before we begin
- Keep your bot token safe. People can use this to access your bot. I'll explain it thoroughly [here](#tokens-and-how-to-keep-them-safe)
- Do not give your bot `Administrator` permissions, this to prevent someone doing bad things with your bot.

### Tokens and how to keep them safe
By now you should have a bot token and the bot is in your server. <br>
To be sure not to accidentally leak it, we can keep them safe in an `.env` file. <br>

This is one of the most standard methods in programming to keep credentials safe is in `.env` files. <br>
To use this for your token is quite simple, place this inside your `.env` file to store your token to a key `TOKEN`

```env
TOKEN = "<YOUR_TOKEN>"
```

And that's it! To access it in Python, you'll need to do a bit more. <br><br>
First, you'd need to have `python-dotenv` module installed using the `pip install python-dotenv` <br>
or the equivalent from other OSes than Windows.<br><br>
Having the module installed, import the module and load the file.
```python
from dotenv import load_dotenv

load_dotenv("PATH/TO/YOUR/.ENV/FILE") # I recommend to use a relative path
```

After that, the `.env` file is loaded. Then you can access the token from it. <br>
For this, we will need `os` module
```python
from dotenv import load_dotenv
from os import environ

load_dotenv("PATH/TO/YOUR/.ENV/FILE") # I recommend to use a relative path

token = environ.get("TOKEN") # Note that this will return None if it cannot find the TOKEN key
```

<br>
That's it for keeping your token safe! Of course there are other methods, but I'll keep it to this method as it is the one I use for my bot.

**Next: [Chapter 2 | What is discord?](https://github.com/dank-tagg/dpy-tutorial/blob/main/chapter-2-what-is-discord.md)**
