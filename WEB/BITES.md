# Bite

Let's visit one of the pages Bit

Go to the url http://jh2i.com:50010/?page=bit

Hmm, by observing the URL it seems that *?page=* can have some sort of local file inclusion as the specified file is imported into the template.

Then I changed the value to *page=flag* and it displays that flag can be found at /flag.txt

Let's go ahead and try to visit the http://jh2i.com:50010/?page=/etc/passwd

Oops, it gives an error that /etc/passwd.php doesn't exist.So, the server appends .php at the end of the parameter.

Now taking a hint from the name of the challenge I thought to try using a null byte as it will cause .php to become redundant because null bute terminates the string.

So I tried  http://jh2i.com:50010/?page=/etc/passwd%00

And boom, it works and displays /etc/passwd

So, did the same thing with http://jh2i.com:50010/?page=/flag.txt%00
 
We got the flag :)

#### Flag: flag{lfi_just_needed_a_null_byte}
