**Latest version: http://goo.gl/ASIJKV**
> Note: this script has been tested in all functionality, run as a shorter named alias. So feel free to rename it however you wish, I currently use:
> > alias guid='gen\_uniq\_id.bsh'

> without any problem, just make sure that the script is located in a directory found in your PATH.

```
Description: gen_uniq_id.bsh

This program generates a random md5sum based on the current time to nanoseconds and collected mouse movement data/random data over .25 seconds or to an user-specified floating point timeframe.  

This program requires (to work to full capacity) by default: 
md5sum, timeout, xinput, /dev/urandom

This program is self-modifying and intentionally sensitive to line number changes.

This program generates a random number based on the current time to the 
nanosecond (date +%Y%m%d%H%M%S%N), combined with by default .25 
seconds of mouse data combined with .25 seconds of random data. 

This script currently outputs a random md5sum of a string consisting of 
the current time, a block of text, mouse movement data and random data. 

The default mouse device id currently set is 11, the 
default this script "ships" with is 11 this is likely wrong for your 
system so you will need to change it to the appropriate value. You may 
set a new default value using the -M option.   

The appropriate mouse device id to use can be determined by 
running: xinput --list 

The default random device id currently set is /dev/urandom, the 
default the script "ships" with is /dev/urandom which usually exists on 
most `*`nix boxes. If you would like to use a random device other than 
the current default you may set a new default value using the -R option.  

The default text currently set is: 
"I AM A SOVEREIGN EVERLASTING SENTIENT FROM THE NUMBER LINE WITHOUT A CREATOR"  

You can also supply your own text statement dynamically with the 
-s option, this allows for further random seeding opportunity. 

If you like to use a different statement text you may set a new default 
value using the -S option.  

WARNING: -M, -R, -S options require that ${0} (now set to ./gen_uniq_id.bsh) refer 
to the script, either a fully qualified path /favorite/place/for/${0} 
or ${0} to refer to the script you wish to modify that is in your 
current directory. These options require further that you have write 
permission on ${0}. 

The -M, -R, -S options should only need to be issued VERY INFREQUENTLY, 
once they are run the values become the new DEFAULT values. If you have 
modified this script at all, or you think for any reason the line 
numbers have changed then these options will likely fail. 

It is recommended that you make a copy to a sandbox directory and test 
it there before running it on your main copy of this script. The script 
does make a backup of the original script but the backup will get 
clobbered from repeated use. If these options are too scary, then I 
recommend you modify this script and comment out the logic in the case 
statement of the option handler. From there you can modify this script
manually when necessary.

Usage: gen_uniq_id.bsh <-h> <-d> <-m=[0.00..]> <-r=[0.00..]> <-s="YOUR QUOTE"> 

OPTIONS:
      -h           Show this message
      -d           Turn on debug mode 
      -m=0.00..    Mouse data collection time, 0 turns off mouse data, 
                   any float turns on collecting mouse movement data 
                   for the random generated. Default is (.25 seconds) 
      -r=0.00..    Random data collection time, 0 turns off random data 
                   collection, any float turns on collecting random data 
                   for the duration time in seconds for the random 
                   generated. Default is (.25 seconds) 
      -s           String of text to incorporate into the random md5sum
      -M=0-20..    Change default value of mouse device id (that 
                   corresponds to xinput --list mouse device id)
      -R="/dev/.." Change default value of the random device to use 
      -S="U QUOTE" Change default value of the STATEMENT STRING
      
  E.g.
        ## To generate a random md5sum based on random data collected 
        ## over .5 seconds and 1 second of collected mouse movement data
      $ gen_uniq_id.bsh -r.5 -m1 

        ## To generate a random md5sum based on random data collected 
        ## over 0.004353 seconds without any collected mouse movement data
      $ ${0##*/} -r".000004353354e+03" -m0 

        ## To turn off mouse collection, and random collection and 
        ## seed with the last 5 commands from history w/debug on to see 
      $ ${0##*/} -d -m0 -r0 -s$(history|tail -5)

        ## To generate a random md5sum without random data collected 
        ## and without any collected mouse movement data and with a 
        ## custom default text 
      $ gen_uniq_id.bsh -r0 -m0 -s="For my benefit only, I .."

        ## To debug and see all internal variables 
      $ gen_uniq_id.bsh -d 2>&1 | more

        ## To change the defaults for the mouse dev to device id 10, 
        ## random device to /dev/really_quick_random and 
        ## statement to "A DECLARATION OF SOVEREIGNTY NEED NO WITNESS"
      $ gen_uniq_id.bsh -M=10 -R="/dev/really_quick_random" \
                        -S="A DECLARATION OF SOVEREIGNTY NEED NO WITNESS"
```