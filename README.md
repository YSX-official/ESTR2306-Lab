# ESTR2306-Lab

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
cat | paste | cut -d ' ' -f `echo $i` | paste -s -d + | bc
```
4. Read from stdin a matrix and calculate the sum of the i-th row by a single line of command.
```
cat | paste -s -d - | cut -d - -f `echo $i` | tr " " "+" | bc
```
