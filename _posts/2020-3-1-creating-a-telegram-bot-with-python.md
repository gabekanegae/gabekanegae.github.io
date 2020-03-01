---
layout: post
title: Creating a Telegram Bot with Python
show-more-link: true
---

Hey! This is a step-by-step guide on creating a **[Telegram Bot](https://core.telegram.org/bots)** in a couple minutes! This tutorial will be using the **[python-telegram-bot](https://python-telegram-bot.org/)** wrapper and **[Heroku](https://www.heroku.com/)** to host it 24/7.

<!--more--> ---

If you are already familiar with Python 3 and its `virtualenv`, simply create a `venv`, install `python-telegram-bot` via `pip`, do `pip freeze > requirements.txt`, and skip to section 1.

At the time of writing, Python's latest version is 3.8.2, and `python-telegram-bot`'s is 12.4.2.

### 0. Requirements and dependencies

Before you start, be sure to have `python3` and its package installer `pip` ready to go in whatever platform you are using. If for some reason you don't have Python 3 on your system, install it via your distro's package manager or, if on Windows, via the [official website](https://www.python.org/downloads/windows/).

Depending on your setup, Python 3 might be simply called `py` or `python`, and the package installer might be `pip3`, so be sure to adjust the commands accordingly.

Create a directory for your bot and enter it:
{% highlight shell %}
mkdir my_first_bot
cd my_first_bot
{% endhighlight %}

Now, install `virtualenv` via Python's package manager, to create a virtual environment for your bot and thus keep things neatly organized:
{% highlight shell %}
pip install virtualenv
{% endhighlight %}

Inside your directory, create a Python 3 virtual environment. Here, we will be calling it simply `venv`:
{% highlight shell %}
virtualenv -p python3 venv
{% endhighlight %}

To start using the virtual environment, run `source venv/bin/activate` if on Linux, or `venv\Scripts\activate` if on Windows.

While inside it, install `python-telegram-bot` via `pip`:
{% highlight shell %}
pip install python-telegram-bot
{% endhighlight %}

Save a list of your newly installed packages in a text file called `requirements.txt`:
{% highlight shell %}
pip freeze > requirements.txt
{% endhighlight %}

You are all set!

### 1. Creating and naming your bot

Your Telegram API access is granted by [@BotFather](http://t.me/BotFather). Talk to him via Telegram and try using `/newbot`. You will choose a **display name** and a **@username** (that ends with *bot*).

After naming your creation, you will receive your **HTTP API token**, and that's what you will need to control the bot. Store it safely, as it can be used by malicious people to tamper with it.

You may also want to try `/setdescription` (Text shown when starting a chat), `/setabouttext` (Profile description) and `/setuserpic` (Upload image with compression), along with many other commands BotFather has to offer.

### 2. It's alive!

Here's some boilerplate code for you to start building on. Create a `main.py` file and paste the content below in it:
{% highlight python linenos %}
from telegram.ext import Updater, CommandHandler
import logging

TOKEN = ""

def start(update, context):
    s = "hello, world!"
    context.bot.send_message(chat_id=update.effective_chat.id, text=s)

def main():
    logger = logging.getLogger(__name__)
    logging.basicConfig(level=logging.INFO,
                        format="%(asctime)s [%(levelname)s] %(message)s")

    updater = Updater(token=TOKEN, use_context=True)
    dp = updater.dispatcher

    dp.add_handler(CommandHandler("start", start))

    updater.start_polling()
    logging.info("=== Bot running! ===")
    updater.idle()
    logging.info("=== Bot shutting down! ===")

if __name__ == "__main__":
    main()
{% endhighlight %}

**Make sure to add your API token in the `TOKEN` variable on line 4!**

To start your bot, enter your virtual environment (if not already in it) and run your file:
{% highlight shell %}
python3 main.py
{% endhighlight %}

If everything went well, you shall see the message `=== Bot running! ===`. Congrats! Try talking to him via Telegram. Send `/start` and it should answer `hello, world!`. To shut it down, press `CTRL+C` and wait for it to exit properly.

If you want to exit from the current virtual environment, simply run `deactivate`.

### 3. Making it your own

To add your own commands, three simple steps are needed. As an example, let's create a **/random** command, that [returns a random number](https://xkcd.com/221/).

Start by sending `/setcommands` to [@BotFather](http://t.me/BotFather), selecting your bot and sending him **a list of all commands it should respond to**, as well as their description. Be sure to send all commands and their descriptions, not only the one you're adding! As it's our bot's first command (apart from **/start**, which doesn't need to be listed here), our message should contain only one line: 
{% highlight shell %}
random - Generates a random number
{% endhighlight %}

Then, in your `main.py` file, create a new function for the command, with `update` and `context` as arguments:
{% highlight python %}
def random(update, context):
    random = int(((192*39)/48+15)/855*20)
    s = "Your totally random number is {}. :)".format(random)

    context.bot.send_message(chat_id=update.effective_chat.id, text=s)
{% endhighlight %}

Finally, add the corresponding `CommandHandler` right after line 18:
{% highlight python %}
    dp.add_handler(CommandHandler("random", random))
{% endhighlight %}

After restarting, the bot should now be responding to **/random**!

For advanced API features and more detailed instructions, do check out the [Telegram Bot API docs](https://core.telegram.org/bots/api) and the [`python-telegram-bot` docs](https://python-telegram-bot.readthedocs.io/en/stable/).

### 4. Running your bot 24/7

~WIP~