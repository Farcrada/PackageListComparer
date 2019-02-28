# About:
This is meant to compare two lists of installed packages and print the version differences. The `--firstfile` is assumed as the host, and will be shown on the left (or top when using `-c`), and `--secondfile`, `--checkfile` or `-p` will be assumed as the target, and will be shown on the right (or bottom when using `-c`). Difference is shown as yellow and missing (depending on arguments either the host or target system is shown or both if allowed) shows as red. Green means there's no difference at that position.

# Prep-work:
Run this command:
`apt --installed list > aptlist`
    
On your host system and on the target system, append with either: "_one", or: "_two" respectively

Download AptListComparer from above (click it -> "RAW" -> Right click the page -> "Save page as...");
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

If you want only the missing files; add: ` | grep MISSING` to the command, though, do read the description.

If you want to save the results to a file you can use the output symbol: `>` or append output: `>>` after the command. You can use this in combination with `grep` for finer details, though make sure you use `-c` or your file will not only be massive, it'll also be rather unreadable.
