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

### sorting

- `sort ` sort lexicographically 
- `sort -n ` numerical data
- `sort -r` : reverse order
- `sort -t $'\t'`: specefiy delimiter
- `sort -k 2`: specify field 

### Uniq

**Uniq** is used to remove consecutive occurrences in a given file.

- `uniq -c` to indicate occurrences of each field
- `uniq -d ` : display only duplicates 
- `uniq -u`: display only unique lines
- `uniq -w`: limit comparison to the first w character
- `uniq -s`: skip the first s characters 
- `uniq -i`: ignore case.
- `uniq -f`: avoid comparing the first **f** fields.
    

### Paste

- `paste -s file`: join all the lines of a file using tab
- `paste -s -d, file`: change the delimiter using **,** 
- `paste - - < file`: paste using two columns
- `paste -d"-," - - - < file`: paste using two different delimiters
- `paste -d, file1 file2`: paste files (1, 2) in columns
- `cat file2 | paste -d, file1 -`: same result
- `cat -d'\n' file1 file2`: contcatnate in a single columns

### Arrays

In bash arrays are created automatically when the following syntax is
introduced:

```bash
name[index]=value
```


- `$(name[index])`: to access the element at index **index**.
- `declare -a arrayname={value1 value2 value3}`: declare and instantiate an
  element 
- `declare -a arrayname={'element with space'}`: to add an element with space.
- `echo $(array[@])`: print the full array.
- `${#array[@]}`: gives you the lenght of the array.
- `${#array[3]}`: lenght of the 3 element.
- `${array[@]:3:2}`: gives **2** elements starting from the **3** index
- `${array[2]:0:4}`: the fourth first characters of the third element.
- `${arra[@]/search/replace}` to execute a search replace
- `array=("${array[@]}" "AIX" "HP-UX")`: to add elements to the array.
- `unset ${array[3]}`: remove the fourth element in the array. 


### Grep

`Grep` command is used to find **pattern** using *regular expressins*.


1. `grep leteral expression` : find the literal in the given expression.
2. `grep literal file1 file2 ` : find the literal in multiple files.
3. `grep -i `: for insensitive search.
4. `grep "regular expression"`: to search regular expression.
5. `grep -w ` to search for a full word and not only a partial find.
6. `grep -A N`: print **Lines** after the match.
7. `grep -B N`: print lines before the match.
8. `grep -r ` search in file recurisevely.
9. `grep -v` to display only the non matched items.
10. `grep -c` to count the number of matches
11. `grep -l` matches with files
12. `grep -o` show only the matching string
13. `grep -n` show line number of the match


- [tldp tutorial](https://tldp.org/LDP/abs/html/x23170.html)
- [useful examples](https://www.folkstalk.com/2012/01/sed-command-in-unix-examples.html)
- [the geek stuff](https://www.thegeekstuff.com/2009/09/unix-sed-tutorial-printing-file-lines-using-address-and-patterns/)


**Examples**:

- `sed -n 'Adress'p filename`
- `sed -n '/pattern/p' filename`
## Resources

1. [quick guide](http://www.panix.com/~elflord/unix/bash-tute.html)
2. [handling input](https://tldp.org/LDP/Bash-Beginners-Guide/html/sect_08_02.html)
3. [bash loops](https://www.cyberciti.biz/faq/bash-for-loop/)
4. [tr](https://www.thegeekstuff.com/2012/12/linux-tr-command/)
5. [uniq](https://www.thegeekstuff.com/2013/05/uniq-command-examples/)
6. [Paste](https://www.theunixschool.com/2012/07/10-examples-of-paste-command-usage-in.html)
7. [Arrays](www.thegeekstuff.com/2010/06/bash-array-tutorial/)
8. [Grep examples](https://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/)


