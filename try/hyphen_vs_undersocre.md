---
title: Hyphen vs Underscore in file names
parent: Try
has_children: false
nav_order: 1
---
`Date: 6 Oct 2021`

# Do you prefer to use `-` or `_` in your file names?
`-` is quicker to type, but `_` looks better imo (plus consistency with names in programming)

Use `Underscore` for the simple reason that the `Hyphen` is a character used in certain words,
as well as when descibing dates.

`Undersocres` because it's sort of annoying if you make a type and get a file name `super-file`
then try to do a shell command on it. The `-file` can get read as an option unless you use quoting.

The technical terms for this is [Shell Expansion](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html) 
and [Globbing](https://tldp.org/LDP/abs/html/globbingref.html).

Bash itself cannot recognize RegEx, Inside scripts, it is commands and utilities -- such as `sed` and `awk`
that interpret RegEx's. Bash essentially tends to glob and expand on elements that are typically used in filenames or in 
regular expression, in the instance they don't have encapsulation.

Example: File is named `-rf`
cd /homedir
rm -rf 
(ohshit) You deleted your home directory `;_;`

vs

rm ./-rf

(a-ok) You just deleted the `-rf` file :-)

