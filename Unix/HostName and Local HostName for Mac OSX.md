# HostName and Local HostName for Mac OSX

Show DNS configuration

    scutil --dns

The hostname appears in the terminal prompt, to set it permanently for Mac OSX

    scutil --set HostName <your hostname>

Then, set the local network computer name to the same HostName

    System Preferences -> Sharing -> Computer Name (EDIT) -> Local HostName
