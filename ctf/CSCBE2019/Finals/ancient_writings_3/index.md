# Ancient Writings #3

### [~$ cd ..](../)

The goal was the same as in [Ancient Writings #2](../../Qualifiers/ancient_writings_2), we needed to rewrite the missing line from a `Befunge` program:

```
>232+*""43*52**5+65+:*4::**3:*21+:** "b"$                 v    >
^"78"v $  $ \ $ \ $<"x32P"    _                           "    v
^|%24<"SC{key_Y3ByZXNzZXk=}"  ^7        *:+33 +*27*7 *44"key"  <
<>"PATCHING"47+:*1+7v"NEEDED"*:+33 +*27*7 *44 47+:*2+v    "   >^
```

```
>                                        >   <34*9g"CC":vv     ^
<                                                    v:,_@>"#_"^
>                                                    >  ^      <

0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZv^<>0123456789abcdefghijklmnopqrstuvwxyz
```

This one was way harder than the previous ones as the "path" the code execution takes was not the same at all, and the stack was filled with garbage on purpose.

Some parts of the code were still very similar. Most importantly, the part that displays the characters was the same (The loop with the `,` operator).

So, we had to come with a way to :

1. Get the code to the display loop
2. Remove the garbage from the stack
3. Add the missing output part into the stack

This meant we had to use the `$` operator, which pops the last element on the stack, the `""` to delimit character values to push on the stack and arrows to guide the code.

We finally managed to write the following line :

```
v                   >$$$$$$$$$$"z{CSCC"              v        ^<
```

Once submitted this gave us the flag.

DONE
