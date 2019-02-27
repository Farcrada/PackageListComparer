# AptListComparer
This takes two lists of apt packages from a system and compares versions.

# About:
This script is meant to compare two lists of installed packages and print the differences. The 'firstfile' is taken as a control and will be compared to the 'secondfile'. Missing is shown as red and difference is shown as yellow

# Prep-work:
Run this command:
`apt --installed list > aptlist`
    
On your host system and on the target system, append with either: "_one", or: "_two" respectively

Download AptListComparer from above (click it -> "RAW" -> Right click the page -> "Save page as...");
`chmod +x AptListComparer`
And then execute with the files as arguments.

# Usage:
    -h      Shows this page/text
    
    [-dmc] --firstfile <aptlist_one> --secondfile <aptlist_two>
    
    -d:     Show every package even if there is no difference.
    
    -m:     Show missing packages. This can also mean missing
            packages from the target system and not the host.
            
    -c:     No colors (for dumping to a file). This changes the
            make-up of the file by putting the versions on a new
            line and indented respectively.
            
    If you want to save the results to a file you can use the
    output symbol: ">" or append output: ">>" after the command
