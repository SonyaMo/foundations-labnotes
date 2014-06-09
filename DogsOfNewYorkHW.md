#My notes and code on Dogs of New York homework

## Intro
I actually didn't get a chance to get started on the homework until Tuesday night, but I was able to at least attempt the homework based on notes from class and searching online. The rough patches came from probably not having enough time to come back and think about the work I was doing, because after working through the homework assignment with Cathy on Wednesday morning, I was able to "fix" the last parts of it and pull together the threads of thought I had before turning in the earlier version I emailed to you. Below is the updated version.

###Counting the number of dogs

This portion of the homework I was able to figure out based on our class notes.

I grabbed the .csv import code from class notes. While I wasn't able to type this out from memory, I'm hoping eventually steps like this will become more intuitive. 

*(Would actually appreciate more homework or any suggested extracurricular exercises to to work through things.)*

```
import csv
import urllib
urllib.urlretrieve ("http://jonathansoma.com/lede/dogs.csv", "dogs.csv")
```

The code below I tried reading more to figure out what it does. According to [this link](https://docs.python.org/2/library/csv.html), basically it's just reading the .csv file. And from class I remember that the delimiter tell Python that the cells are separated by commas. We got rid of the quotechar that would explain the style of any additional characters within the cells.

```
dog_file = open("dogs.csv","rb")
dogcsv = csv.reader(dog_file, delimiter=',')
```

This turns the file into a list and assigns it to the variable rows.

```
rows = list(dogcsv)
```

I started by following exactly from the notes, and printed the first row to orient myself within the list we've created.

```
print rows[1]
```

### Number of dogs registered
This hung me up a bit because I was still hung up on understanding rows in this program. I tried several versions such as putting something in brackets, which just ended up printing individual cells. I talked with Cathy and realized that the len(rows) prints everything, and then I just had to minus one.

```
print len(rows) - 1
```
I was actually able to figure out this portion of the homework by  adapting the code from the homework that counted the number of dogs named "Lola" by changing the column number to reflect to the one refering to Borough and setting the thing to find as Brooklyn.

```
import csv
with open('dogs.csv', 'rb') as csvfile:

    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[9] == "Brooklyn":
            count = count + 1
    print count
```

I repeated this for the boroughs of:

Staten Island:
```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[9] == "Staten Island":
            count = count + 1
    print count
```

Queens:

```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[9] == "Queens":
            count = count + 1
    print count
```

Manhattan:
```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[9] == "Manhattan":
            count = count + 1
    print count
```

and the Bronx:
```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[9] == "Bronx":
            count = count + 1
    print count
```

###Max in the City
This was an interesting exercise because it looked like as far as how much I could get done by 2 am I was pretty much 2/3 of the way there. I just needed a little push and possibly use the programming mindset that Dennis mentioned to help me get through stuff, because I definitely get easily frustrated and need to think in pseudo code more and break things down into manageable pieces before getting caught up in the programming panic.

The "and" hint came from online. I had tried variations of adding additional lines to the loop, but without fully understanding loops I was definitely lost.

While searching for "more than one conditions," I came across [this link](http://stackoverflow.com/questions/7809698/can-you-make-multiple-if-conditions-in-python) and decided to use "and" and "or" for more than one condition.

```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        if dog[0] == "Max" and dog[10] == "10002":
            count = count + 1
    print count
```

I had trouble figuring out Max in different zip codes because while I understood how operators worked, I was again 1/3 of the way from fully grasping what I was doing wrong. I definitely knew that this was not working because probably the and was evaluating against the multiple ors. I couldn't really Google to trouble shoot because I think I was lacking the vocabulary to make it work. I ended up talking with Cathy who pointed out the lack of parentheses.

```
import csv
with open('dogs.csv', 'rb') as csvfile:
    dog_csv = csv.reader(csvfile, delimiter=',')
    count = 0
    for dog in dog_csv:
        ## And between name and zip codes because it needs to fulfill both conditions
        ## But for the zip codes you are using or because if it's and it needs to full fill all those, which probably not everything does
        ## if you're just looking for instance of Max in each zip code, not all the zip codes absolutely
        if dog[0] == "Max" and (dog[10] == "11205" or dog[10] == "11206" or dog[10] == "11206" or dog[10] == "11216" or dog[10] == "11221" or dog[10] == "11233"):
            count = count + 1
    print count
```

For dogs with Brindle as primary or secondary colors I basically misunderstood it as AND and not OR so I was able to fix this by changing that operator.

```
import csv

with open('dogs.csv', 'rb') as csvfile:

    dog_csv = csv.reader(csvfile, delimiter=',')

    count = 0

    for dog in dog_csv:

        ## Same concept as above, but again understand the difference was finding dogs who had brindle as primary OR secondary

        ## color not fitting both.

        if dog[4] == "BRINDLE" or dog[5] == "BRINDLE":

            count = count + 1

    print count
```

###Last question

I actually did not attempt this.I feel bad because I didn't get a chance to come into lab or have time to really think this through so I'm hoping to look at the homework samples to figure this out better.

#Conclusion
I definitely need more time to look through the lessons, notes and homework. I plan on hopefully having more time to review.
