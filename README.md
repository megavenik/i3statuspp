i3statuspp
==========

i3status plugin patch

Config example:

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
