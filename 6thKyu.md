
# Problem 1

Create a function that returns a christmas tree of the correct height.
For example:
```
hieght = 5 should return:
    *    
   ***   
  *****  
 ******* 
*********
```
Height passed is always an integer between 0 and 100.
Use \n for newlines between each line.
Pad with spaces so each line is the same length. The last line having only stars, no spaces.

```
function christmasTree(height) {
  let tree = ''
  let cnt=1
  
  for(let i=1;i<=height;i++){
    let end = (height==i || height == 1)? '' : '\n'
    tree += ' '.repeat(height-i) + '*'.repeat(cnt)+' '.repeat(height-i)+ end
    cnt+=2
  }
  return tree
}
```

# //Problem 2

Task
Given two cells on the standard chess board, determine whether they have the same color or not.
Example
For cell1 = "A1" and cell2 = "C3", the output should be true.
For cell1 = "A1" and cell2 = "H3", the output should be false.

Input/Output
[input] string cell1
[input] string cell2
[output] a boolean value
true if both cells have the same color, false otherwise.

```

function chessBoardCellColor(cell1, cell2) {
    cell1 = cell1.split('')
    cell2 = cell2.split('')
    let matrix= []
    let letters=['A','B','C','D','E','F','G','H']
    let current=true
    
    for(let i=0;i<8;i++){
        matrix[i] = []
      for(let j=0;j<8;j++){
        matrix[i][j] = current
        current = (current == true)? false : true
      }
        current = (current == false)? true : false
    }

    if(matrix[letters.indexOf(cell1[0])][cell1[1]-1]
       ==
       matrix[letters.indexOf(cell2[0])][cell2[1]-1]
      ){return true}

    
    return false
  }
```



# //Problem 3

You are developing an image hosting website.
You have to create a function for generating random and unique image filenames.
Create a function for generating a random 6 character string which will be used to access the photo URL.
To make sure the name is not already in use, you are given access to an PhotoManager object.
You can call it like so to make sure the name is unique
at this point, the website has only one photo, hosted on the 'ABCDEF' url

photoManager.nameExists('ABCDEF'); returns true
photoManager.nameExists('BBCDEF'); returns false
Note: We consider two names with same letters but different cases to be unique.

```
function generateName()
{
  function getRan(){
    let res=[]
    for(let i=0;i<6;i++){
      res.push(String.fromCharCode(Math.floor(Math.random() * (90 - 65) + 65)))
    }
    return res.join('')
  }
 
  let temp=getRan()
    while(photoManager.nameExists(temp)){
      temp=getRan()
    }
    return temp
}
```


# Problem 4

Given an array of integers, find the one that appears an odd number of times.
There will always be only one integer that appears an odd number of times.

```
const findOdd = (a) => a.reduce((a, b) => a ^ b);
```

# Problem 5

Complete the method/function so that it converts dash/underscore delimited words into camel casing. The first word within the output should be capitalized only if the original word was capitalized (known as Upper Camel Case, also often referred to as Pascal case).

Examples
"the-stealth-warrior" gets converted to "theStealthWarrior"
"The_Stealth_Warrior" gets converted to "TheStealthWarrior"
```
function toCamelCase(str){
    let res=''
    for(let i=0;i<str.length;i++){
      if(str.charAt(i)== '-' || str.charAt(i)=='_' ){
        res+=str.charAt(i+1).toUpperCase()
        i++
      }else{
        res+=str.charAt(i)
      }
    }
    return res
  }
```
#   Problem 6

Assume "#" is like a backspace in string. This means that string "a#bc#d" actually is "bd"

Your task is to process a string with "#" symbols.

Examples
"abc#d##c"      ==>  "ac"
"abc##d######"  ==>  ""
"#######"       ==>  ""
""              ==>  ""
```
function cleanString(s) {
    let res = []
    s.split('').forEach(element=>{
      (element != '#')?
        res.push(element)
        :
        res.pop()
    })
    
    return res.join('')
};
```

# Problem 7

In one city it is allowed to write words on the buildings walls. The local janitor, however, doesn't approve of it at all. Every night he vandalizes the writings by erasing all occurrences of some letter. Since the janitor is quite lazy, he wants to do this with just one swipe of his mop.

Given a word, find the minimum width of the mop required to erase each of the letters.
For word = "abacaba", the output should be:
[7, 5, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
(26 elements altogether)

First element 7 means: from first "a" to last "a" need a width of 7.
First element 5 means: from first "b" to last "b" need a width of 5.
First element 1 means: from first "c" to last "c" need a width of 1.

```
function theJanitor(word) {
    let start=65;
    let arr=[]


    for(let i=65; i<91; i++){
        let temp= String.fromCharCode(i).toLowerCase()
        if(word.includes(temp)){
        arr.push( (word.indexOf(temp)-word.lastIndexOf(temp)-1)*-1 )
        } else{
        arr.push(0)
        }
    }
    return arr    
}
```

# Problem 8

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.
```
function findOutlier(int){
    var even = int.filter(a=>a%2==0);
    var odd = int.filter(a=>a%2!==0);
    return even.length==1? even[0] : odd[0];
  }
  ```
