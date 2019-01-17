# Bash Day 2

---

### Install pip for python
```bash
wget https://bootstrap.pypa.io/get-pip.py
```

```bash
python get-pip.py
```

#### pip will work with any installed version of python 

* use -p or --python=python2.7 or --python3.5 option to specify version


### Install virtualenv and virtualenvwrapper

```bash
pip -p python3.5 install virtualenv #use your installed version
```

```bash
pip -p python3.5 install virtualenvwrapper
```

* Once virtualenvwrapper is installed, edit your .bashrc file

```bash
sudo nano ~/.bashrc
```

```bash
#add this to the end of the file
#virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/Devel
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
source /usr/local/bin/virtualenvwrapper.sh
```

* reload bash profile with...
```bash
source ~/.bashrc
```

### Create a new environment for csvkit

```bash
mkvirtualenv csvkit
```

### Search for library in pypi
```bash
pip search csvkit
```

### Install csvkit
```bash
pip install csvkit
```

### csvlook
```bash
head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k2 | csvlook
```

### csvstat
```bash
head -25 points_of_interest.csv | cut -d',' -f1,2 |sort -t',' -k1 -n| csvstat
```

### To see manual of almost any command use man
```bash
man grep
```

### Variables
```bash
x=2
```

```bash
echo $x
```

### When creating variables in bash do not use spaces

#### Example 1
```bash
food='hamburger'
```

```bash
drink='chocolate shake'
```

```bash
echo 'I would like a' $food 'and a' $drink
```

#### Example 2
```bash 
a=3
b=$((x+a))
echo $b
```


---
* come up with GIS specific examples of if and while loops
---


### While loop
```bash
i=0
while
[ $i -lt 4 ]
do
echo $i
i=$((i + 1))
done
```

### If statements
```bash
i=2
if (( $i % 2 == 0 ))
then
echo 'even'
else
echo 'odd'
fi  << means end of statement
```

### Dynamic input
```bash
touch dynamic_input.sh
```

```bash
chmod 777 dynamic_input.sh
```

```bash
nano dynamic_input.sh << (assuming nano is installed. if not sudo apt-get install nano)
``` 

```bash
#!/usr/bin/env bash
i=$1
if (( $i % 2 == 0 ))
then
echo 'even'
else
echo 'odd'
fi
```

* To save hit cntrl+x and enter.

### Run script

#### Try
```bash
./dynamic_input.sh 6
```

```bash
./dynamic_input.sh 7
```


### For loops
```bash
for i in *.txt
do echo "$i"
done
```

### If doing this on one line ';' are necessary
```bash
for i in *.txt; do echo "$i"; done
```

Another example

```bash
for shp in *.shp
do
echo “Processing $shp”
ogr2ogr -f “ESRI Shapefile” -t_srs EPSG:4326 geo/$shp $shp
done 
```

### Random bonus command
#### find
* This command recursively searches thru directories and copies all txt files into the parent diretory. 
For duplicates it will append a number to the file name so that no files are lost

find ./data/recursive_search/ -name '*.txt' -exec cp --backup=numbered -t ./ {} +

#### copy 
* All files within a txt file from one dir to another

```bash
cp $(<list.txt) new_folder
```
