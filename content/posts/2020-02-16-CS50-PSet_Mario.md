---
title: "CS50: Week One - Problem Set: Mario"
date: 2020-02-16T10:13:30+05:30
description: "A solution and walkthrough for the Mario problem set"
tags: [cs50, study-notes]
disqus: false
---

<p>
This problem set comes in two levels, more comfortable and less comfortable. I will run through both problems and my thought process for them in this post.
</p>

### Problem Set 1 - Mario (more comfortable)
Create a pyramid in C, albeit in text, using hashes (#) for bricks, a la the below. Each hash is a bit taller than it is wide, so the pyramid itself is also be taller than it is wide.

```
       #
      ##
     ###
    ####
   #####
  ######
 #######
########
```

The program we’ll write will be called mario. And let’s allow the user to decide just how tall the pyramid should be by first prompting them for a positive integer between, say, 1 and 8, inclusive.

Here’s how the program might work if the user inputs 8 when prompted:

```
$ ./mario
Height: 8

       #
      ##
     ###
    ####
   #####
  ######
 #######
########
```
Here’s how the program might work if the user inputs 4 when prompted:

```
$ ./mario
Height: 4
   #
  ##
 ###
####
```

If the user doesn’t, in fact, input a positive integer between 1 and 8, inclusive, when prompted, the program should re-prompt the user until they cooperate:

```
$ ./mario
Height: -1
Height: 0
Height: 42
Height: 50
Height: 4

   #
  ##
 ###
####
```

<br>


## My thoughts breaking down the problem
```
   #
  ##
 ###
####
```
For the above pyramid:

- We need 4 lines
-  Each line has 4 characters, either a # or a space
- From top to bottom, the number of spaces decrease and the the number of hashes increase


So to type it out for each line:

- The first line we need, 4-1=3 spaces and 1 hash.
- The second line we need, 4-2=2 spaces and 2 hashes.
- The third line we need, 4-3=1 spaces and 3 hashes.
- The fourth line we need, 4-4=0 spaces and 4 hashes.

...Now we’re seeing a pattern.

If we look at using a loop, we’ll need:

- 4-0-1=3, 0+1=1
- 3-0-1=2, 1+1=2
- 2-0-1=1, 2+1=3
- 1-0-1=0, 3+1=4

So for a pyramid of size n:

- (n-1)-0=(n-1), 0+1=1
- (n-1)-1=(n-2), 1+1=2
......

- The last line will be: (n-1)-(n-1)=0, (n-1)+1=n

<h3>Solution</h3>
First make sure the user can input a number between 1-8 inclusive.
```
int main(void) {
int height;

 do {
   height = get_int("Height: \n");
 }
 while ( height < 1 || height > 8);

}
```

Once that is done we can think about adding the hashes. It is easier to add make a left aligned pyramid:
```
int main(void) {
int height;

 do {
   height = get_int("Height: \n");
 }
 while( height < 1 || height > 8);

    // use a loop to add the #
for(int i=0; i < height; i++){
   for(int j=0; j< i +1 ; j++){
       printf("#");
   }
   printf("\n");
}
}

// Output for 3
#
##
###
```

Great! Now we need to get those hashes to the right side, best way to visualise this is to use '.'
```
int main(void) {
int height;

 do {
   height = get_int("Height: \n");
 }
 while( height < 1 || height > 8);

for(int i=0; i < height; i++){
       
       // use a loop to add . according to the height (user's input) 
   for(int j=0; j < height-1-i ; j++){
       printf(".");
       }

        // use a loop to add the #
   for(int j=0; j< i + 1 ; j++){
       printf("#");
       }
  
   printf("\n");
}
}

// OUTPUT for 3
..#
.##
###
```

Now all we need to do is replace the '.' with a ' '

```
int main(void) {
int height;

 do {
   height = get_int("Height: \n");
 }
 while( height < 1 || height > 8);

for(int i=0; i < height; i++){
   for(int j=0; j < height-1-i ; j++){
       printf(" ");
       }

        // use a loop to add the #
   for(int j=0; j< i + 1 ; j++){
       printf("#");
       }
  
   printf("\n");
}
}

// OUTPUT for 3
  #
 ##
###
```

Tada! That's it! Mario (more comfortable done).
Note: I think we can definitely make this more readable. Those for loops are a little hard to read, we could take them out (abstraction) probalby take them out as an improvement.


<br>

## Problem Set 1: Mario - less comfortable

The slightly more difficult version of mario is to make a pyramid that looks like this.

```
$ ./mario
Height: 8
       #  #
      ##  ##
     ###  ###
    ####  ####
   #####  #####
  ######  ######
 #######  #######
########  ########
```

### My thoughts
Since we have the harder bit out of the way, we just need to add two spaces in the middle and a right aligned pyramid (ie: no spaces).
```
int main(void)
{
   int height;

   do
   {
       height = get_int("Height: \n");
   }
   while (height < 1 || height > 8);

   for (int i = 0; i < height; i++)
   {
       for (int j = 0; j < height - 1 - i ; j++)
       {
           printf(" ");
       }
       
       for (int j = 0; j < i + 1 ; j++)
       {
           printf("#");
       }
    
    // add the middle space
       printf("  ");
       
       for (int j = 0; j < i + 1 ; j++)
       {
        // add the hash on the right pyramid
           printf("#"); 
       }
        printf("\n");
   }
}


// OUTPUT

$ ./mario
Height: 5

    #  #
   ##  ##
  ###  ###
 ####  ####
#####  #####
```