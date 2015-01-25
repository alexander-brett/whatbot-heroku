#whatbot-heroku: get your inane chatter in THE CLOUD

##How to use

```
heroku login
heroku create
heroku config:set WHATBOT_CONFIG=$(perl -pe "s/\n//g" conf/whatbot.conf)
heroku config:set BUILDPACK_URL=https://github.com/alexander-brett/whatbot-buildpack.git
git push heroku master
```

##Adding more modules

Add the module's file tree here, for intance as `Whatbot-Command-Foo`, then
add a corresponding line to `install_modules`. Follow the existing format.

##Build time

Note that heroku has a 15-min build timer. I suggest you build this distribution
BEFORE adding in loads of other stuff, because the module are cached. This was the reason I gutted the Whatbot core module.

##Config

```json
{
    "io":
    [
	{
            "interface": "HipChat",
            "username": ###########,
            "password": ###########,
            "nick": "dev bot",
	    "alias": "@devbot",
            "rooms": ["bot-development"]
        }
    ],
    "database" : {
        "database" : "./whatbot.db",
        "handler" : "SQLite"
    },
    "commands": {
        "excuse": {}
    },
    "silent": 1
}

```

##Credit

I didn't write Whatbot, [he did](https://github.com/nmelnick/whatbot). It's pretty cool!