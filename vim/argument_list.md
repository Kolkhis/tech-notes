# Vim Argument List

The argument list and the marked files list are connected, but they
don't need to be.  
The argument list has a lot of features to use on its own.  

---
#### Note:
For the commands that take an `{argument}`, these commands
allow `[++opt]` and `[+cmd]` (see help pages).  
* Exceptions: `:argadd` & `:argdelete`

---

## Commands for Manipulating the Argument List
Commands ending with a bang (`!`) usually discard changes to the current buffer.
| **Command**                | **Short Name**                | **Effect**                |
|----------------------------|----------------------------|------------------------------|
|  `:args`                   |  `:ar`              | Print the argument list.     |  
|  `:args {list}`            |  `:ar {list}`       | Define `{list}` as the new arglist.|  
|  `:args! {list}`           |  `:ar! {list}`      | Define `{list}` as the new arglist. Discard changes to current buffer.|  
|  `:argedit[!] {name}`      |  `:arge {name}`     | Add `{name}` to arglist and edit it. |  
|  `:argadd {name} .. `      |  `:arga {name} .. ` | Add `{name}s` (or current buffer) to arglist.  |  
|  `:argdelete {pattern}`    |  `:argd {pat}`      | Delete files from arg list that match `{pattern}`. `%` for current entry.|  
|  `:[range]argd `           |  `:[range]argd `    | Delete `range` (or current) files from arglist. `.` for current entry. `%` for all files.|  
|  `:argdedupe`              |  `:argded`          | Remove duplicate filenames from arglist.  |  
 
## Commands for Using the Argument List to Edit Files
| **Command**                | **Short Name**                | **Effect**                |
|----------------------------|----------------------------|------------------------------|
|  `[ct]argument[!] [ct]`    |  `:argu [ct]`       | Edit file `ct` (or current entry).  |  
|  `:[ct]next[!]`            |  `:n!`              | Edit `ct` next file.  |  
|  `:[ct]Next[!]`            |  `:N!`              | Edit `ct` previous file.  |  
|  `:[ct]previous`           |  `:prev`            | Same as `:Next`.  |  
|  `:next[!] {arglist}`      |  `:n {list}`        | Define `{list}` as the new arglist. Same as `:args[!] {list}`.|  
|  `:rewind[!]`              |  `:rew`             | Start editing first file in arglist.  |  
|  `:first`                  |  `:fir`             | Same as `:rewind`.  |  
|  `:last[!]`                |  `:la`              | Start editing last file in arglist.  |  
|  `:[ct]wnext`              |  `:wn`              | Write current file and start editing `ct` next file.  |  
|  `:[ct]wnext[!] {file}`    |  `:wn {file}`       | Write current file to `{file}` and start editing `ct` next file.|  
|  `:[ct]wNext[!]`           |  `:wN`              | Same as `:wnext`, but go to previous file instead. |  
|  `:[rng]argdo[!] {cmd}`    |  `:argdo {cmd}`     | Execute `{cmd}` for each file in arglist, or for arglist files in `[rng]`.|  

Most of these commands allow `[++opt]` and `[+cmd]` (see help pages).  

When writing to a different file (e.g., `:w ~/somedir/somesubdir`),  
the "++p" flag creates the parent directory of the file if it doesn't exist.  


## Adding Arguments to Argument List

The argument list is `a b c`, and `b` is the  
current argument. Then, these commands result in:  

| **command**   | **New Argument List** | **Effect**                   |
|---------------|-----------------------|------------------------------|
|  `:argadd  x` |     `a b x c`         | Adds after current argument  |  
|  `:0argadd x` |     `x a b c`         | Adds at index 0              |  
|  `:1argadd x` |     `a x b c`         | adds at index 1              |  
|  `:$argadd x` |     `a b c x`         | Adds to the end of the list  |  

And after the last one:
|    Command      |  New Argument List | **Effect**                                      |
|-----------------|--------------------|-------------------------------------------------|
|  `:+2argadd y`  |  `a b c x y`       | Add **after** the current index (`b` / 1), + 2  |  

There's no default duplicate check.  
You can add a file to the argument list twice.  

You can use ` | :argdedupe` to fix it afterwards: 
```vim
:argadd *.txt | argdedupe
```
The currently edited file is not changed.
you can also use this method:  
```vim
:args ## x
```
This will add the "x" item and sort the new list.









## Local Argument List
Make a local copy of the global argument list.

| **Command**                | **Short Name**                | **Effect**                |
|----------------------------|------------------------|------------------------------|
|  `:arglocal`             |  `:argl`               | Make a **local** copy of the **global** arglist. Doesn't start editing another file. |  
|  `:arglocal[!] {list}`   |  `:argl[!] {list}`     | Define a new **local** arglist, local to current window. |  
|  `:argglobal`            |  `:argg`               | Use the **global** arglist for current window. Doesn't start editing another file. |  
| `:argglobal[!] {list}`   |  `:argg[!] {list}`     | Use global arglist for current window. Define new global arglist (like `:args`). |  




