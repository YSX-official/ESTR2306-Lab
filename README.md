# ESTR2306-Lab
There are some Linux commands to solve problems of ESTR2306 Lab session.

## Lab 1
Compression: .tar.gz file, .tar.bz file and .zip file.
## Lab 2
1. Excluding directories, symbolic links and hidden files, find the 2nd largest file size in /bin by a single line of command.
```
ls -l /bin | grep -v "^d" | grep -v "^l" | grep -v "^\." | tr -s " " | cut -d " " -f 5,9 | sort -n | tail -n 2 | head -n 1
```
2. Write a single line of command that reads two integers from standard input (using cat) and print their sum on standard output. Assume you use Ctrl+D to close the standard input stream after entering the two integers (and pressing Enter).
```
cat | xargs -I {} echo {}+p | dc
```
3. Read from stdin a matrix and calculate the sum of the i-th column by a single line of command.
```
cat | cut -d ' ' -f `echo $i` | paste -s -d + | bc
```
4. Read from stdin a matrix and calculate the sum of the i-th row by a single line of command.
```
cat | paste -s -d - | cut -d - -f `echo $i` | tr " " "+" | bc
```
## Lab 3
1. Join two files with matched labels.
```
sort -n math.txt | join -t $'\t' name.txt | cut -d $'\t' -f2-
```
2. Extract the path of the default shell the current user uses.
```
getent passwd $USER | cut -d : -f7
```
3. Adder
```
echo $((`cat | tr -s ' ' | tr ' ' +`))
```
## Lab 4
1. Join three files with matched labels.
```
sort -n math.txt | join -t $'\t' name.txt - > tmp.txt && sort -n prog.txt | join -t $'\t' tmp.txt - > scoresheet.txt
```
2. Add a date at the end of the file names.
```
#!/bin/bash

read -p "Enter path: " dir_path
current_date=$(date +"%Y%m%d")

for file in "$dir_path"/*; do
        new_name="${file}_${current_date}"
        mv "$i" "$new_name"
done
```
3. Check if the content of the file test.txt is exactly the two lines:
```
hello
world
```
If test.txt is exactly the above two lines, print "same" on the screen. Otherwise, print "different".
```
#!/bin/bash

content="hello
world"

file_content=$(<test.txt)

if [[ "$file_content" == "$content" ]]; then
        echo "same"
else
        echo "different"
fi
```
