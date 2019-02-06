# Bash Environment
## Environment Variables
- VAR=path,command,alias

## Functions

    function yo()
    {
        echo "yo"
    }

Commands

    env         # Lists all environment variables
    set         # Displays shell settings of shell variables for the session
    set -x      # start debugging
    set +x      # end debugging
    unset       # Removes a variable
    unset -f    # Removes custom function
    shopt       # Displays shell options and their settings
    shopt -s    # set or enable an option

    export      # export var to the current shell and any shell spawned from this shell
    export YO=yo

    type        # determines if a command is a shell built-in, a binary, or an alias

    "Weak" quotes       # will expand $variables
    'Strong' quotes     # does not allow var expansion

