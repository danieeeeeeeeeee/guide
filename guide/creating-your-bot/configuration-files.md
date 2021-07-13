# Configuration files

::: tip
This page is a follow-up and bases its code on [the previous page](/creating-your-bot/).
:::

As you get deeper into development, you may need to interact with sensitive data or data that gets used in multiple locations, such as:

* Database passwords
* API keys
* Command prefix(es)
* A list of bot owner IDs

Having that kind of data hard-coded in each of your files can be bothersome and less than ideal. This is where configuration files come in–they're great for storing static data you can easily update in a single place.

## Implementing your config file

Go to your code editor and make a new file. Add in the code below and save it as `config.json`, in the same directory as your main bot file.

```json
{
	"prefix": "/",
	"token": "ODY0NTcwODY3ODUyNTA5MTg0.YO3YXQ.I0gnTqanHPdoNcFAB4k0mZZ0-wU"
}
```

Go back to your main bot file, locate the `const client = new Discord.Client()` line, and add this above it:

```js
const config = require('./config.json');
```

Next, copy your token from the `client.login('ODY0NTcwODY3ODUyNTA5MTg0.YO3YXQ.I0gnTqanHPdoNcFAB4k0mZZ0-wU')` line and paste into the `config.json` file. Make sure to keep it between the double-quotes.

Now you can simply do `client.login(config.token)` to login! If you want to use a different prefix than `!`, you can change that as well.

## Storing additional data

As previously mentioned, you'll probably want to store more than just your token and prefix at one point or another. If you're going to store more data, add another key/value pair to the list!

```json
{
	"prefix": "!",
	"token": "ODY0NTcwODY3ODUyNTA5MTg0.YO3YXQ.I0gnTqanHPdoNcFAB4k0mZZ0-wU",
	"meaning_of_life": 42,
	"passwords_array": ["please", "dont", "hack", "me"],
	"8CYKuF3waq6FvLYlXGgK25D3hgBYqgl2": {
		"bank": 1234,
		"home": 4321
	}
}
```

## Resulting code

<resulting-code />
