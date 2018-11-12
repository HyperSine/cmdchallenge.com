# cmdchallenge.com

## Challenges

### 1. hello_world

```
$ echo "hello world"
```

### 2. current_working_directory

```
$ pwd
```

### 3. list_files

```
$ ls
```

### 4. print_file_contents

```
$ cat access.log
```

### 5. last_lines

```
$ tail -n 5 access.log
```

### 6. find_string_in_a_file

```
$ grep "GET" access.log
```

### 7. search_for_files_containing_string

https://stackoverflow.com/questions/6637882/how-can-i-use-grep-to-show-just-filenames-no-in-line-matches-on-linux

```
$ grep -l "500" *
```

### 8. search_for_files_by_extension

```
$ find -name "access.log*" -exec echo {} \;
```

### 9. search_for_string_in_files_recursive

```
$ find -name "access.log*" -exec grep "500" {} \;
```

### 10. extract_ip_addresses

```
$ find -name "access.log*" -exec grep -E -o '([0-9]{1,3}\.){3}[0-9]{1,3}' {} \;
```

### 11. delete_files

```
$ rm -rf ./* ./.* 2>/dev/null
```

### 12. count_files

```
$ find -name "*" -type f -maxdepth 1 | wc -l
```

### 13. simple_sort

```
$ sort access.log
```

### 14. count_string_in_line

```
$ grep "GET" access.log | wc -l
```

### 15. split_on_a_char

```
$ cat split-me.txt | tr ';' "\n"
```

### 16. print_number_sequence

```
$ echo {1..100}
```

### 17. remove_files_with_extension

```
$ find -name "*.doc" -type f -exec rm {} \;
```

### 18. replace_text_in_files

```
$ find -name "*.txt" -type f -exec sed -i "s/challenges are difficult//g" {} \;
```

### 19. sum_all_numbers

```
$ awk 'BEGIN{sum=0} {sum+=$1} END{print sum}' sum-me.txt
```

### 20. just_the_files

```
$ find -name "*" -type f -exec basename {} \;
```

### 21. remove_extensions_from_files

```
$ find $PWD -type f -exec rename 's/\..*$//' {} \;
```

### 22. replace_spaces_in_filename

```
$ ls | tr ' ' '.'
```

### 23. dirs_containing_files_with_extension

```
find -type f -name '*.tf' -printf '%h\n' | awk '!a[$0]++'
```

### 24. files_starting_with_a_number

```
$ find -type f -name '[0-9]*' -printf '%f\n'
```

### 25. print_nth_line

```
$ awk 'NR==25' faces.txt
```

### 26. reverse_readme

```
$ tac README
```

### 27. remove_duplicate_lines

```
$ awk '!a[$0]++' faces.txt
```

### 28. disp_table

```
$ awk -F ',' '{printf "%-6s%-7s%s\n",$1,$2,$3}' table.csv
```

### 29. find_primes

```
$ cat random-numbers.txt | awk '!a[$0]++' | xargs factor | awk 'NF==2' | wc -l
```

### 30. corrupted_text

```
$ sed 's/!!*/!/g;s/ !\([A-Za-z]\)/ \1/g;s/!\( [a-z]\)/\1/g;s/!.!/./g;;s/a!v/av/g' war_and_peace.txt
```

## User Contributed Challenges

### 1. print_common_lines

```
$ comm -12 <(sort <(cat access.log.1 | cut -d ' ' -f1)) <(sort <(cat access.log.2 | cut -d ' ' -f1))
```

### 2. print_line_before

```
$ find -type f -name 'access.log*' -exec awk '{ lines[NR]=$0 } END{ for(i=1;i<NR;i++) { if(match(lines[i+1], /404/)) { print lines[i] } } }' {} \;
```

### 3. print_files_if_different

```
$ find -name '*.bin' ! -name 'base.bin' -exec sh -c 'cmp --silent {} base.bin || basename {}' \;
```

### 4. list_files_adv

```
$ ls -Fa1
```

### 5. nested_dirs

```
$ cat './.../  /. .the flag.txt'
```

### 6. find_tabs_in_a_file

```
$ grep $'\t' file-with-tabs.txt | wc -l
```

### 7. remove_files_without_extension

```
$ find -type f ! -name '*.txt' ! -name '*.exe' -exec rm {} \;
```

### 8. remove_files_with_a_dash

```
$ find -type f -name '-*' -exec rm {} \;
```

### 9. print_sorted_by_key

```
$ head -n 1 ps-ef1 && sort -u -k 2 <(awk '{if(FNR>1){print $0}}' ps-ef1 ps-ef2)
```

### 10. IPv4_listening_ports

```
$ grep -E '^tcp[^6].*LISTEN$' netstat.out | awk '{print $4}' | awk -F ':' '{print $2}' | sort -nr
```

### 11. rot13_decoding

```
$ cat les_miserables.txt | tr 'N-ZA-Mn-za-m' 'A-Za-z'
```

