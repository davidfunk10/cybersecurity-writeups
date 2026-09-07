## Head Dump (picoCTF, Forensics, Medium)

For this challenge, I was given a compressed disk image and told to retrieve the flag. First, I started off by decompressing the file using `gzip -d` and performing a `strings disk.img | grep "pico"` to see if there was any useful metadata.
After running this, I got a useful piece of information that hinted that the file contained metadata from a Github repository. This made me think to carve the file using `binwalk`. After carving the file, I ran 
strings on the newly extracted binary file to obtain the flag. The flag was hidden deep in linux's file system, so a little file carving was necessary to retrieve it.
