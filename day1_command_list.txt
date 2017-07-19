open terminal

mkdir project folder

cd to project folder

sudo apt-get install wget curl

wget https://raw.githubusercontent.com/fpdcc/webmap_data_updates/master/map%20data/points_of_interest.csv

# list files
ls

# list all files including hidden files
ls -a

#list files with size in Kb, Mb, or Gb
ls -lh

# Find current location/path
pwd

# Shorthand for users home directory
~

# Make a directory
mkdir data

#Remove a directory and contents
rm -rd(dont do this now)

# Remove a file
rm <filename>
rm *.txt
# * is a wildcard for all

# Copy
cp points_of_interest.csv ./data

# Quickly see a files content
cat points_of_interest.csv

# See first 10 lines of a file
head points_of_interest.csv

# See last 10 lines of a file
tail points_of_interest.csv

# Word Count
wc points_of_interest.csv

wc -c
wc -w
wc -l
wc -L

# Create file from output
head points_of_interest.csv > first_ten_lines.csv

#append to file
tail points_of_interest.csv >> firest_ten_lines.csv

# Try out some commands
ls
cat first_ten_lines.csv

head -100 points_of_interest.csv

#get an exact line in a csv
head -100 points_of_interest.csv > tmp.cav
tail -1 tmp.csv > 100.csv
cat 100.csv

head -100 points_of_interest.csv | tail -1

head -100 points_of_interest.csv | wc -c

cut -d',' -f1,2,3,4,5 points_of_interest.csv


grep 'phrase' points_of_interest.csv

#gives inverse of command
grep -v 'phrase' points_of_interest.csv

#not case sensitive
grep -i 'phrase' points_of_interest.csv

#include line number
grep -n 'phrase' points_of_interest.csv

cut -d',' -f2 points_of_interest.csv > points_names.csv

head - 25 points_names.csv | sort

cut -d',' -f1 points_of_interest.csv > points_num.csv

#sort number use -n option
head -5 points_num.csv | sort -n

#reverse
sort -r

#reverse numbers
sort -r -n

#sort unique numbered values
sort -n -u


#sort with a delimeter of ',' and key to sort on is second column
sort -t’,’ -k2 -n filename.csv

head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k2

head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k1 -n

#other ways to create a file
touch filename

echo hello world > filename

#doesnt give you wahts expected --it only identifies unique values in adjacent lines
cut -d',' -f5 points_of_interest.csv | uniq

#sorted should
cut -d',' -f5 points_of_interest.csv | sort | uniq

#you can also do
cut -d',' -f5 points_of_interest.csv | sort -u

#count each unique value
cut -d',' -f5 points_of_interest.csv | sort | uniq -c

#create bash script
touch bash-test.sh

#open in nano
nano bash-test.sh

#put in
#!/usr/bin/env bash <<include this line>>

echo 'print this message!'
cut -d',' -f5 points_of_interest.csv | sort | uniq -c

#close nano with ctrl+x and enter

#make sure the file is executable
chmod 777 bash-test.sh

#run file
./bash-test.sh

#look at your command history
history

#use with grep to filter output

#type clear to clear screen
clear 





stolen almost entirely from https://data36.com/learn-data-analytics-bash-scratch/
