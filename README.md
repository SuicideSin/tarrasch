<img src=http://i.imgur.com/Z3KZf4K.png width=400></img>

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

A Chess bot for Slack. Uses a fully-functional chess engine, graphical boards (none of that low-budget ASCII stuff), and keeps track of your record against your friends and coworkers.

![](http://i.imgur.com/cDPLZl1.png)

![](http://i.imgur.com/eC0NWDq.png)

### Features

1. [Fully-functional chess engine](https://pypi.python.org/pypi/python-chess) with en passant, castling, minor promotion, all that good stuff
2. Graphical boards courtesy of jinchess.com
3. Keeps track of personal and org-wide records against each opponent
4. Lets you undo moves for when your friends screw up algebraic notation
5. Optional waiting period between moves to force you to get some amount of work done

### Configuration

Tarrasch is configured through environment variables.

* `TARRASCH_MESSAGE_PREFIX`: Set the word Tarrasch listens for at the beginning of your messages to know you're talking to it. Default: `chess`.
* `TARRASCH_COOLDOWN_SECONDS`: Number of seconds to wait after each move before accepting another move. Default: `0`.

There are also various `TARRASCH_REDIS_*` variables for configuring the Redis connection, but if you're deployed on Heroku this should Just Work™.

#### Interaction Model

To keep things simple, Tarrasch can manage one game per channel it is in. The recommended way of playing a game is to invite your opponent and Tarrasch to a group DM. You can also play in public channels if you want an audience, but only one game can go on in that channel at a time.

#### Using Heroku Free Dynos

You'll need to take Tarrasch offline for 6 hours a day if you plan to deploy it on Heroku free dynos. See the [scaling](scaling.md) doc for more information.
