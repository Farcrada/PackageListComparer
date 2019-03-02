# About:
It is meant to compare two lists of installed packages and print the version differences (see Prep-work on how to get these lists).

The `--firstfile` is assumed as the host, and will be shown on the left (or top when using `-c`), and `--secondfile`, `--checkfile` or `-p` will be assumed as the target, and will be shown on the right (or bottom when using `-c`) in the terminal. 

Difference is shown as yellow and missing shows as red. Green means there's no difference at that position. Missing packages will be dubbed as such at that list's version position from which list depends on (allowed) arguments) 

# Prep-work:
Run this command for systems with the apt package manager (usually **Debian** based):
    `apt --installed list > aptlist`
        
For pacman package manager (usually Arch based):
    `pacman -Q > aptlist`
        
For yum of dnf package manager (usually Red Hat based):
    `[yum|dnf] list installed > aptlist`
        
    NOTE: The formatting from yum/dnf might be a bit off,
    further testing is required.
        
For zypper package manager (usually SUSE based):
    `zypper pa -i > aptlist`
        
    NOTE: The formatting from zypper might be a bit off,
    further testing is required.
    
The way genlop (usually Gentoo based) outputs it's installed lists is fundamentally different to others'. Because of this extra development is needed.
    
On your host system and on the target system, append either with: "_one", or: "_two" respectively

Clone PackageListComparer via the button above (or click it -> "RAW" -> Right click the page -> "Save page as...");
`chmod +x PackageListComparer`
And then execute with the files as arguments.

# Usage:
    --help  Shows this page/text and exits
    
`[-dnctha] --firstfile PKGLIST_ONE [--secondfile PKGLIST_TWO | --checkfile PACKAGEFILE | -p "PACKAGE VERSION"] ]`
    

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
