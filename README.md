# About:
This is meant to compare two lists of installed packages and print the version differences. The `firstfile` is taken as a control and assumed as the host and will be compared to the `secondfile`, a.k.a. the target. Difference is shown as yellow and green means it is similar to the target version. Red means it's missing from either system.

# Prep-work:
Run this command:
`apt --installed list > aptlist`
    
On your host system and on the target system, append with either: "_one", or: "_two" respectively

Download AptListComparer from above (click it -> "RAW" -> Right click the page -> "Save page as...");
`chmod +x AptListComparer`
And then execute with the files as arguments.

# Usage:
    -h      Shows this page/text
    
    [-dmc] --firstfile APTLIST_ONE --secondfile APTLIST_TWO
    
    -d:     Show every package even if there is no difference.
    
    -m:     Show missing packages. This can also mean missing
            packages from the target system and not the host.
            
    -c:     No colors (for dumping to a file). This changes the
            make-up of the file by putting the versions on a new
            line and indented respectively.

If you want only the missing files; add: ` | grep MISSING` to the command, though, do read the description.

If you want to save the results to a file you can use the output symbol: `>` or append output: `>>` after the command. You can use this in combination with `grep` for finer details, though make sure you use `-c` or your file will not only be massive, it'll also be rather unreadable.
