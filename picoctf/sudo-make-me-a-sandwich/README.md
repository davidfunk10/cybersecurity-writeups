# Sudo Make Me a Sandwich (picoCTF, General Skills, Easy)

## Initial Approach

- I tried to cat the flag.txt file, but I realized I did not have permission to do that.
- I attempted to `chmod +r` on the file to allow myself permission to read it, but I did not have permission for that either.
    
## Solution

- I tried using `sudo -l` to see what permissions I had for sudo.
- Then, I noticed I had permission to run /bin/emacs.
- Finally, I ran `sudo emacs ./flag.txt` and was able to view the flag.
    
## Key Commands

- `sudo -l`
- `sudo emacs`
    
## Takeaways

- When using sudo, it is important to be careful with file paths. In this case, I had to use `./flag.txt` instead of just `flag.txt`.
- Emacs is a useful file editor when you have permission to run it.
