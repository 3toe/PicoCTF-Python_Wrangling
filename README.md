# PicoCTF-Python_Wrangling
Write-up for a PicoCTF challenge

Location: https://play.picoctf.org/practice/challenge/166

Category: General Skills

Description: Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script] using [this password] to get [the flag]?

How to solve: 
1. Must be solved in PicoCTF's "webshell" (or the needed libraries must be imported otherwise). First, both the python script and flag file (links are given at the location provided above) need to be loaded into the user's temporary storage via the webshell with a "wget" command followed by the web path of each file.
2. Running "$ python ende.py" gives the response "Usage: ende.py (-e/-d) [file]" I am under the assumption that -d or -e stands for decrypt or encrypt, so I will try -d and the file we want to decrypt.
3. Running "$ python ende.py -d flag.txt.en" gives the response "Please enter the password:" (flag.txt.en is the file name of the flag, which I wget'ed in step 1. The ".en" at the end could mean "english" but more likely stands for "encrypted")
4. The third file provided in the description (pw.txt) is a simple text file with a string that presumeably is the passworded needed in step 3. Upon entering it, the flag is returned.

Flag: picoCTF{4p0110_1n_7h3_h0us3_ac9bd0ff}

Notes:
After looking at the python code, you can see there are encode and decode blocks that use a cryptography method called "Frenet." This confirms our above assumptions about -d, -e and the .en at the end of the flag file name.
