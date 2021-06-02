# Chapter 4 | Getting to know the library

So now you've made a single command, let's dive deeper into the library!

Our previous part's code should look like this:
```python
from discord.ext import commands

bot = commands.Bot(command_prefix="?")

@bot.command(name="hello")
async def hello_world(ctx: commands.Context):
    await ctx.send("Hello, world!")

bot.run("token")
```

Here we made a simple bot command, explained in detail [here](./chapter-3-online.md)

### A simple ping command
In this part, I will teach you how to make a ping command to show the bot's latency. <br>
We will use the library's `bot.latency` for that. Note that `bot.latency` is given in seconds.

```python
@bot.command(name="ping")
async def _ping(ctx: commands.Context):
    await ctx.send(f"Pong! {bot.latency * 1000} ms")
```

This command will send `Pong! 100 ms`. In the `ctx.send` we are using a f-string (python 3.6+) so that we can use inline code within the string.
Try yourself now! Write a single `ping` command.<br><br>

By [reading the docs](https://discordpy.readthedocs.io/en/stable/) you can find out a lot of more useful stuff that the library provides. <br>
This is what I recommend you to read before asking for help anywhere. <br><br>

### Guide on events
We've only worked with the `bot.command` decorator so far, but did you know there's a lot more to the library?<br>
For example, there's also a `bot.event` decorator, and a lot more! Events are basically things that happen within discord e.g. a new message, a ban, a kick etc. <br>
Here's an example:

```python
@bot.event
async def on_message(message):
    await bot.process_commands(message)
```

What we are doing here:
- `@bot.event`: A decorator that registers the function as an event
- `async def on_message(message)`: This event is for when a new message is sent on discord (with as parameter `message` which will be an instance of `discord.Message`
- `await bot.process_commands(message)`: Processes the commands (without this your commands won't work. This is needed for events, but not for [listeners](https://discordpy.readthedocs.io/en/stable/ext/commands/api.html?highlight=listener#discord.ext.commands.Bot.add_listener)

And that's it for chapter 4!
