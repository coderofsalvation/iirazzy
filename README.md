IIRAZZY publishing daemon
=========================

### why ###

An IRCdaemon is a welltested environment for broadcasting large volumes of data.
Many clients (whether it be bots, people, applications) can connect to it.
To handle high volumes of (logging)data, collect it on IRC, and distribute elsewhere.
Also the fifo-characteristics of ii make it easy for *any* programming language to log to irc.

### How ###

PHP example

    file_put_contents('irc/irc.freenode.net/#foo/in', "test123\n", FILE_APPEND | LOCK_EX);

This will output the line on IRC in channel #foo, and using `pipefiles` it can easily be redistributed elsewhere:

example pipefile: pipes/irc.freenode.net/#foo/example :

    nick="$1"; mesg="$2"; ircd="$3"; netw="$4"; chan="$5"; self="$6"

    echo "[$(date) $chan] $nick $mesg $ircd $netw $self" | bashdownrss add news.rss 

Ofcoarse you need to tweak this more (grepping/matching *interesting* text), but you'll get the idae.
Btw. rssgenerating is done by [bashdownrss](https://github.com/coderofsalvation/bashdownrss)

### To get started ###

Edit your networks/channels in config.d/config, and run:

    ./iirazzy start

or
  
    ./iirazzy stop

### Credits ###

* ii 
* iibot
