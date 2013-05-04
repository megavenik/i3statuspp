i3statuspp
==========

i3status plugin patch. Adds support of third-party plugins to the i3status.

#### Plugin structure:

* It should be executable
* It should accept no parameters
* It should print the pure resulting string to STDOUT (no trailing NL simbols and any other crap)
* All plugins should be placed in one folder (exact plugin folder could be set in i3status.conf)

## Installing

Get the proper version of the i3status source code [here](http://i3wm.org/i3status/):
```bash
wget http://i3wm.org/i3status/i3status-2.7.tar.bz2
tar xjvf http://i3wm.org/i3status/i3status-2.7.tar.bz2
```

Clone this repo:

```bash
git clone https://github.com/megavenik/i3statuspp.git
```

Patch the original sources:

```bash
cd i3status-2.7
patch -p0 < ../i3statuspp/simple_plugin.patch
```

And build i3status!:)

## Config example:

    general {
        colors = true
        interval = 5
        plugins_path = "/etc/i3status/plugins" // describing, where to search for plugin binaries
    }
    
    plugin test {                              // "test" is the name of the plugin binary
        plugins_list = "ololo"                 // right now means absolutely nothing. May be used for some aaditional funcs in the future
    }
    
    plugin weather {
    }

    order += "disk /"
    order += "plugin test"
    order += "disk /home"
    order += "wireless wlan0"
    order += "ethernet eth0"
    order += "battery 0"
    #order += "load"
    order += "plugin weather"                  // putting the weather plugin in the right place on the panel
    order += "tztime local"
