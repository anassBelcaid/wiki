# Tutorial on hacker Rank

- `echo ` : print a message
- `seq`: print a **sequence** of number separated by a jump
- `read`: Read the value of a variable.
- Simple for:
    ```shell
    for var in `seq `; 
    do 
        work with $var
    done
    ```
- **comparing numbers**: 
```
if [[ condition  ]]
then 
    do this
elif [[ condition  ]]
then 
    do this
else 

fi
```

> We must be careful to add **spaces** in the `[[`` condition.


- Calculator `echo expression | bc`
    - To set a precision `echo "scale = 2 ; 22/ 7" | bc `


### Cut

- `cut -d ' ' -f 
- `cut -b ` to cut on bytes.
- By default the separator for **cut** is `\t`.
- `IFS` to set he default internal file separator.


### Head  and Tail

- head -n number of lines
- head -c size in bytes
- `tail` have the same use


```bash
while read L
do
     work
done
```


### tr

**tr** translates all the occurences of a character.

```bash
tr  find_character replace_characer < filename
```

- translate lower to upper
    - `tr [:lower:] [:upper:]`
    - `tr a-z A-Z`
- translate braces into parentheses
    - `tr '{}' '()' < input > output`
- translate spaces to tab
    - `tr [:space:] '\t'`
- delete 
    - `tr -d [:digit:]`
- Complement the set
    - `tr -cd [:digit:]`  will remove antyhing but digits
- remove non printable 
    - `tr -cd [:print:]`
    

## Resources

1. [quick guide](http://www.panix.com/~elflord/unix/bash-tute.html)
2. [handling input](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)
3. [bash loops](https://www.cyberciti.biz/faq/bash-for-loop/)
4. [tr](https://www.thegeekstuff.com/2012/12/linux-tr-command/)
    


