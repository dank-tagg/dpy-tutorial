# Chapter 3 | Get your bot online!
In this chapter, we will get your bot online and send a simple message!<br>
Before we do that, let's check our `discord.py` version.

## Checking the `discord.py` version
Run this in Python Interpreter:

```py
>>> import discord
>>> discord.__version__
1.7.2
```

At the moment of writing, the newest version is `1.7.2`. <br>
This should be above `1.7`, since some features won't work in lower versions.
If it isn't, try solving the problem by `pip install -U discord.py`.

**NOTE: If you aren't able to fix this, contact me on discord**


## Hello, world!
If you've successfully installed `discord.py`, we now can start coding our bot!
First, you'd need to import the `discord.ext.commands` module for creating our bot.
```python
from discord.ext import commands
```
Now that we have imported it, we need to create a bot instance:
```python
from discord.ext import commands
bot = commands.Bot(command_prefix='?') #This will create a bot instance, and it will respond on the prefix '?'
```

As you can see on the comment, we created a bot instance with the prefix `?`. <br>
Later, when we add commands, it will respond to `?<command>`.<br>
The bot constructor is also where we would want to specify the gateway intents. These are required for specific actions and events such as `on_member_*`. <br>
We will ignore this now, but this will be covered later. <br>

After you've done this, we need to actually run our bot.

```python
from discord.ext import commands
bot = commands.Bot(command_prefix='?')
```
Let's add a simple command using the `bot.command` decorator
```python
@bot.command(name="hello")
async def hello_world(ctx: commands.Context):
    await ctx.send("Hello, world!")
```
This may be a lot to take in, even if you are familiar with Python. Let me explain what each part does:
- `@bot.command(name="hello")` is a decorator that converts the function below it into a command called `hello` that you can run from Discord.

- `async def hello_world(ctx: commands.Context):` defines a function that takes 1 argument - `ctx` - which is a `commands.Context` object that's passed with every command. All commands will be passed a `commands.Context` object as their first argument.

- `await ctx.send("Hello, world!")` makes an API call to Discord to send a message to the channel the command was run in with the content "Hello, world!". Note that `ctx.send()` is an alias of `ctx.channel.send()`, and functions exactly the same, just in a more concise way. 
Next, get your bot online!
```python
bot.run("<your_token>") # Refer to Chapter 1 to store your token securely
```
This part runs your bot through your token. This abstracts away creating an event loop and runs the bot through `coroutines`

After this, your bot should be up and running. The bot should answer the command expectedly.<br>
If this is not the case, reread this part.

Reminder: restart your bot everytime you edit your code! Later, I'll explain a workaround, for now just restart the bot.<br>
**NOTE: Good naming matters, please don't follow YouTube tutorials and name your `bot` instance `client`.**
