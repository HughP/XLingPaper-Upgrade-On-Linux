# XLingPaper-Upgrade-On-Linux

I never remember how to upgrade XMLMind on Linux.

I follow the install directions here: http://www.xmlmind.com/xmleditor/_distrib/doc/help/installing_xxe.html

Gernally the instructions follow like those below for version 8:

> Make sure that the Java™ bin/ directory is referenced in the $PATH and, at the same time, check that the Java™ runtime in the $PATH has the right version:

> ```
~$ java -version
java version "10.0.1" 2018-04-17
Java(TM) SE Runtime Environment 18.3 (build 10.0.1+10)
Java HotSpot(TM) 64-Bit Server VM 18.3 (build 10.0.1+10, mixed mode)
Unpack the XXE distribution inside any directory you want:
```
>```
$ cd
$ unzip xxe-pro-8_2_0.zip
$ ls xxe-pro-8_2_0
addon/
bin/
demo/
doc/
...
```
>XXE is intended to be used directly from the xxe-pro-8_2_0/ directory. That is, you can start XXE by simply executing:
>```
$ xxe-pro-8_2_0/bin/xxe &
```

I can never remember what to do next. Here is the solution:

On my system `xxe &` is sym-linked to the version that I want to be primary. This is done in `/usr/local/bin`

So then there is a script in `/usr/local/bin` which points back to the application (I don't really know as I didn't write it), but the point is that the symlink needs to be adjusted and can be adjusted with a combination of these tips:

Find out which version of `xxe` the item in `local/bin` is pointed at with the following command:
`ls -l xxe` Then if you want to adjust the versions one needs to over write the existing symlink. Or create a new one. In my case I changed `xxe` to `xxe7`.

__Note__ *Do not adjust `~/.bash_profile` as that will only mess things up*
> I did this once with `export $PATH=/absolute/path/to/xxe/`and then my machine couldn't find `/usr/local/bin` any more.

If one wants an `xxe` command then use that, but for me so that I don't have to update the command all the time I use `xxe7` for XMLMind version 7 and `xxe8` and so forth.

then symlink like so:
`cd /usr/local/bin`

**`/usr/local/bin$`**` sudo ln -s /home/username/path/to/XMLMind/xxe-version-folder/bin/xxe /usr/local/bin/xxe8
`


##License
Copyright 2018 by Hugh Paterson III
Licensed Creative Commons CC-BY 4.0
