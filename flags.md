
# Linux Command Line Tool Flags Standard

This is the 0.1 version attempt of standardising linux command line flags for arguments.
Over the last 60 years of UNIX development of command line tools has been done by millions of people,
unfortunatly there is no set rules on how to present the user with options. This leaves users sometimes comfused on which flags to use on what tool. 

For example some tools will use --help and others --h or even --? or none at all!
This standardised list has been created in order to provide new developers a guide on what flags to use.

Where possible is it prefered to use single - to deliniate the flags available e.g. mytool.py -h

As a general rule, getopt() requires single character flags [getopt(3)](https://man.openbsd.org/getopt.3) except where [getopt_long(3)](https://linux.die.net/man/3/getopt_long) is being used which enables longer flags in the form --flag. Single hyphens should only be used to indicate single user flags, so as to avoid the ambiguity as to whether -help is a long form flag called help or 4 separate single character flags e.g. -h -e -l -p.


## Terminology
*Argument* or *args* are positional parameters to a command. For example, the file paths you provide to the cp command are args. The order of args is often important: cp foo bar means something different to cp bar foo.

*Flag* are named parameters, denoted with either hyphen and a single letter name (-r) or a double hyphen and multiple letter name (--recursive). They may or may not also include a user-specified value (--file foo.txt) or (--file=foo.txt). The order of flags, should not affect the program semantics.


## Guidelines
These guidelines have been based on the POSIX syntax standard. 

1. argument names should be no longer than nine characters
2. argument names should lowercase for more common flags 
3. use only alphanum characters from the portable character set
4. all arguments should be proceeded by the '-' or '--' 
5. If the order of options matter, this should be stated in the help file
6. Try to use flags over arguments
7. Have full length versions of all flags (e.g. -h and --help)
8. Use only one-letter flags for commonly used flags
9. Use the commonly used options listed below
10. make the default right for MOST users
11. do not read passwords from arguments (use --password-file and force the user to specify the file to prevent it leaking data to shell history)


## The List

| Single Flag|Double Flag| Command  |Note 
|---|---|---
|  -? | Help   | should be implemented alongside help
| -a  | --all  |   
| -d  | --debug  |   
| -f  | --force  |   
|   | --json  |   
| -h  | --help  |   
| -o  | --output  |   
| -u  | --user  |   
| -v  | --version  |   
|   |   |   
|   |   |   

## Links and other sources
https://clig.dev/#arguments-and-flags
https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap12.html
