# Bash Day 2

---

## Install pip for python 2.x
```sudo apt-get install python-pip```

## Install pip for python 3
```sudo apt-get install python3-pip```


## Install virtualenv and virtualenvwrapper

```pip3 install virtualenv```
```pip3 install virtualenvwrapper```

## Create a new environment for csvkit

```mkvirtualenv csvkit```

## Search for library in pypi
```pip search csvkit```

## Install csvkit
```pip install csvkit```

## csvlook
```head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k2 | csvlook```

## csvstat
```head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k1 -n| csvstat```

# To see manual of almost any command use man
```man grep```

## Variables
```x=2```
```echo $x```

## When creating variables in bash do not use spaces
```food='hamburger'```
```drink='chocolate shake'```
```echo 'I would like a' $food 'and a' $drink```

```a=3```
```b=$((x+a))```
```echo $b```

---
* come up with GIS specific examples of if and while loops
---

## While loop
```i=0```
while
[ $i -lt 4 ]
do
echo $i
i=$((i + 1))
done


#if statements
i=2

if (( $i % 2 == 0 ))
then
echo 'even'
else
echo 'odd'
fi <<---means end of statement

#dynamic input
touch dynamic_input.sh
chmod 777 dynamic_input.sh

nano dynamic_input.sh

#!/usr/bin/env bash

i=$1
if (( $i % 2 == 0 ))
then
echo 'even'
else
echo 'odd'
fi

#cntrl+x and enter
#run script
./dynamic_input.sh 6
./dynamic_input.sh 7


#for loops
for i in *.txt
do echo "$i"
done

#if doing this on one line ';' are necessary
for i in *.txt; do echo "$i"; done

for shp in *.shp
do
echo “Processing $shp”
ogr2ogr -f “ESRI Shapefile” -t_srs EPSG:4326 geo/$shp $shp
done 


#random bonus command
#find
#this command recursively searches thru directories and copies all txt files into the parent diretory. For duplicates it will append a number to the file name so that no files are lost

find ./data/recursive_search/ -name '*.txt' -exec cp --backup=numbered -t ./ {} +
