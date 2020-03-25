---
layout: post
title: Creating a Telegram Bot with Python
show-more-link: true
---

Hey! This is a step-by-step guide on creating a **[Telegram Bot](https://core.telegram.org/bots)** in a couple minutes!

This tutorial will be using the **[python-telegram-bot](https://python-telegram-bot.org/)** wrapper and **[Heroku](https://www.heroku.com/)** to host it 24/7.

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

Inside your directory, create a Python 3 virtual environment. Here, I will be calling it simply `venv`:
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

I also recommend saving the list of commands and descriptions in a text file called something like `BotFather_setcommands.txt`, for reference.

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

Having to leave your terminal window open and your computer powered on for your bot to be working can't be the best option, right? Well, if you already know your way through VPS, cloud providers and the like, then just leave it running on your preferred platform. Otherwise, keep on reading.

To leave your chatbot running (almost) all the time, this tutorial will be using **[Heroku](https://www.heroku.com/), a cloud platform as a service (PaaS)** that has a free tier for small personal projects, which should handle a simple bot just fine. It also has a large list of add-ons for databases, logging, testing, and much more. Alongside it, you will also need `git` for a quick and easy deployment method.

Before we start, be sure to install the [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli#download-and-install) as well as `git` itself, via your distro's package manager or, if on Windows, via the [official website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

Let's get on it! First, [create a free Heroku account](https://signup.heroku.com/):

![]({{site.baseurl}}/images/heroku-signup.jpg)

Then, create a new app and give it whatever name you feel like.

![]({{site.baseurl}}/images/heroku-newapp.jpg)

Now that your app is created, you need to tell Heroku how to start it. For that, in your bot folder alongside your other files, create a blank file named `Procfile`, **with no file extension**. It should contain only the line `worker: python main.py`. Alternatively, simply run:
{% highlight shell %}
echo "worker: python main.py" > Procfile
{% endhighlight %}

Also, let's have `git` ignore our `venv` folder, as Heroku will later recreate it for us via the file `requirements.txt` created back in section 0. Same idea as before: blank file named `.gitignore`, containing `venv/`. Or, simply:
{% highlight shell %}
echo "venv/" > .gitignore
{% endhighlight %}

Now, let's upload the bot files to Heroku using the Heroku CLI. This step is also detailed in the **Deploy tab**, "Deploy using Heroku Git" section.

Log in to your account using `heroku login` and following the messages. Then, initialize a `git` repository in your bot folder and link it to your Heroku app, replacing `bot-tutorial` with your Heroku app name:
{% highlight shell %}
git init
heroku git:remote -a bot-tutorial
{% endhighlight %}

Finally, add your files, commit and push:
{% highlight shell %}
git add --all
git commit -m "Initial commit"
git push heroku master
{% endhighlight %}

All that's left is to turn your bot on. In the **Resources tab**, click the edit button, flip the switch and confirm:

![]({{site.baseurl}}/images/heroku-worker.png)

Your bot should now be working! Try sending it a command via Telegram! To check your console logs, go on More > View logs:

![]({{site.baseurl}}/images/heroku-logs.jpg)

To deploy any additions or changes, commit them via `git` and push. Be sure to add a commit message describing what changed:
{% highlight shell %}
git add --all
git commit -m "Added command /ahoy"
git push heroku master
{% endhighlight %}

And you should be all set! Thanks for following along, and I hope you enjoy your new creation!