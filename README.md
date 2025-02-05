# ESTR2306-Lab
There are some Linux commands to solve problems of ESTR2306 Lab session.

## Linux
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
5. Join two files with matched labels.
```
sort -n math.txt | join -s $'\t' name.txt | cut -d $'\t' -f2-
```
6. Extract the path of the default shell the current user uses.
```
getent passwd $USER | cut -d : -f7
```
7. Adder
```
echo $((`cat | tr -s ' ' | tr ' ' +`))
```
