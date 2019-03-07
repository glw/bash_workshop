# Terminal basics

### make a directory
```bash
mkdir project folder
```

### cd - move into directories
```bash
cd to project folder
```

### cd .. - move out of directories
```bash
cd ..
```

### installing something with apt-get
```bash
sudo apt-get install wget curl
```

### wget - download a file
```bash
wget https://raw.githubusercontent.com/fpdcc/webmap_data_updates/master/map%20data/points_of_interest.csv
```

### ls - list files
```bash
ls
```

### list all files including hidden files
ls -a

### list files with size in Kb, Mb, or Gb
ls -lh

### Find current location/path
```bash
pwd
```

### Shorthand for users home directory
```bash
~
```

### Make a directory
```bash
mkdir data
```

### Remove a directory and contents
```bash
rm -rd(dont do this now)
```

### Remove a file
```bash
rm <filename>
rm *.txt
# * is a wildcard for all
```

### Copy
```bash
cp points_of_interest.csv ./data
```

### Quickly see a files content
```bash
cat points_of_interest.csv
```

### See first 10 lines of a file
```bash
head points_of_interest.csv
```

### See last 10 lines of a file
```bash
tail points_of_interest.csv
```

### Word Count
```bash
wc points_of_interest.csv
 #try
wc -c
wc -w
wc -l
wc -L
```

### Create file from output
```bash
head points_of_interest.csv > first_ten_lines.csv
```

### Append to file
```bash
tail points_of_interest.csv >> firest_ten_lines.csv
```

### Try out some commands
```bash
ls
cat first_ten_lines.csv

head -100 points_of_interest.csv
```

### Get an exact line in a csv
```bash
head -100 points_of_interest.csv > tmp.cav
```

```bash
tail -1 tmp.csv > 100.csv
```

```bash
cat 100.csv
```

```bash
head -100 points_of_interest.csv | tail -1
```

```bash
head -100 points_of_interest.csv | wc -c
```

```bash
cut -d',' -f1,2,3,4,5 points_of_interest.csv
```

### Grep
```bash
grep 'phrase' points_of_interest.csv
```

#### gives inverse of command
```bash
grep -v 'phrase' points_of_interest.csv
```

#### not case sensitive
```bash
grep -i 'phrase' points_of_interest.csv
```

#### include line number
```bash
grep -n 'phrase' points_of_interest.csv
```

### Using CUT with csv's
```bash
cut -d',' -f2 points_of_interest.csv > points_names.csv
```

```bash
head - 25 points_names.csv | sort
```

```bash
cut -d',' -f1 points_of_interest.csv > points_num.csv
```

### Sort on number use -n option
```bash
head -5 points_num.csv | sort -n
```

#### reverse sort
```bash
sort -r
```

#### reverse sort numbers
```bash
sort -r -n
```

#### sort unique numbered values
```bash
sort -n -u
```

#### sort with a delimeter of ',' and key to sort on is second column
```bash
sort -t’,’ -k2 -n filename.csv
```

```bash
head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k2

head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k1 -n
```

### Other ways to create a file
```bash
touch filename
```

```bash
echo hello world > filename
```

### UNIQ, doesnt give you whats expected --it only identifies unique values in adjacent lines
```bash
cut -d',' -f5 points_of_interest.csv | uniq
```
#### sorted should
```bash
cut -d',' -f5 points_of_interest.csv | sort | uniq
```

#### you can also do
```bash
cut -d',' -f5 points_of_interest.csv | sort -u
```

#### count each unique value
```bash
cut -d',' -f5 points_of_interest.csv | sort | uniq -c
```

### Create bash script
```bash
touch bash-test.sh
```

### Open in nano
```bash
nano bash-test.sh
```

#### Include this line when creating a script for bash
```bash
#!/usr/bin/env bash
```

```bash
echo 'print this message!'
cut -d',' -f5 points_of_interest.csv | sort | uniq -c
```

##### close and save in nano with '<ctrl+x>', '<y>', then '<enter>'

#### make sure the file is executable
```bash
chmod +x bash-test.sh
```

#### run file
```bash
./bash-test.sh
```

### Look at your command history
```bash
history
```

#### Use with grep to filter output
```bash
history | grep 'phrase'
```

### Type clear to clear screen
```bash
clear 
```
### Bonus
Copy a list of files to another folder
```bash
cp $(<list.txt) new_folder
```

stolen almost entirely from https://data36.com/learn-data-analytics-bash-scratch/
