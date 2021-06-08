# Moving Around

When moving around on the terminal you use the `cd` command with the *relative path* to your desired destination.

`cd /code` would move you from my current directory into a subdirectory named `code`

`cd ..` Will move you from your current directory to the containing directory. `..` means "go up one level from my current location."

You can use more complicated relative paths to go through multiple directories

`cd ../../labs/bug-hunts` would take you up two levels (into the location that contains the directory that contains the directory you started in) then it will look for a sub directory named `labs` and a further subdirectory named `bug-hunts` which is where you end up.