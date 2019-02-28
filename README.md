# About:
Aimed at Debian based systems, though if you use the `apt` package manager, this should just work, since it's made for the apt package manager. It is meant to compare two lists of installed packages and print the version differences (see Prep-work on how to get these lists).

The `--firstfile` is assumed as the host, and will be shown on the left (or top when using `-c`), and `--secondfile`, `--checkfile` or `-p` will be assumed as the target, and will be shown on the right (or bottom when using `-c`) in the terminal. 

Difference is shown as yellow and missing shows as red. Green means there's no difference at that position. Missing packages will be dubbed as such at that list's version position from which list depends on (allowed) arguments) 

# Prep-work:
Run this command:
`apt --installed list > aptlist`
    
On your host system and on the target system, append with either: "_one", or: "_two" respectively

Clone AptListComparer via the button above (or click it -> "RAW" -> Right click the page -> "Save page as...");
`chmod +x AptListComparer`
And then execute with the files as arguments.

# Usage:
    --help  Shows this page/text and exits
    
`[-dnctha] --firstfile APTLIST_ONE [--secondfile APTLIST_TWO | --checkfile PACKAGEFILE | -p "PACKAGE VERSION"] ]`
    

    -d:     Show every package even if there is no difference.
    
    -n:     Only show missing, no differences.
            
    -c:     No colors. This changes the make-up of the output by
            putting the versions on a new line and indented
            respectively; usefull for dumping to a file.
    
    -t:     Show target system's missing packages.
    
    -h:     Show host system's missing packages.
    
    -a:     Show ALL missing packages from either system.
    
    -p "PACKAGE VERSION":
            Check for specific package via commandline. This also
            assumes -h so you'll be prompted if the host is missing
            a package.
                Note: multiple if done like so:
                -p "PACKAGE VERSION;PACKAGE VERSION;PACKAGE VERSION"
    
    --checkfile
            Check for specific packages via file. This also assumes
            -h so you'll be prompted if the host is missing a
            package.
                Note: seperate packages in the file by a newline.

If you want to save the results to a file you can use the output symbol: `>` or append output: `>>` after the command. You can use this in combination with `grep` for finer details, though make sure you use `-c` or your file will not only be massive, it'll also be rather unreadable.
