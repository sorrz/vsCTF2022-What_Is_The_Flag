# vsCTF2022-What_Is_The_Flag
Writeup for the "What Is The Flag" challenge during vsCTF 2022


#################################################
## The Challenge:
##
## Forensics/What Is The Flag
## pamLELcu
## 16 solves / 490 points
## Someone sent me this PDF claiming that he has found the flag, 
## but things don’t really seem that obvious. Also, did you notice 
## that something is a bit off with the text?
## 
## Flag format (RegEx): vsctf\{[a-z]+\}
##
#################################################

File: https://ctf.viewsource.me/uploads?key=2e4836cdb7d7e5f1387059e27b7e25f976276b17fc6a172a348dda43f203386d%2Fwhatistheflag.pdf

#############
# 1) What is the file?
#  As normal when looking at a forensics challenge, we start by examine the files supplied. 
#  We run file in a linux terminal, giving it the filename whatistheflag.pdf this generates:
#
#  ┌──(sorrz㉿kali)-[~/Documents/vsCTF/whatistheflag]
#  └─$ file flag.pdf   
#  flag.pdf: PDF document, version 1.7 (zip deflate encoded)
#
#  Interesting, so we have something bundled within the file. 
#
#  Opening the file we see a flag in the PDF: vsctf{whatistheflag} this is obviously not the correct one. 
#  As the challenge mentioned, something seems a bit off with the text, as its not quite the same, this is especially noticable   #  when highlighting the text in the pdf, as it's marked one character at a time, not as a string. 
#############

#############
# 2) What we know or can assume with some certainty!
# PDF's, DOCX and other popular filetypes can be saved with meta-data and added information, such as fonts nestled within them.
# So, we find a tool used for checking this. A quick google-search gives us a site: 
# https://www.pdfconvertonline.com/extract-pdf-fonts-online.html
# This extract fonts and gives us a .zip file containing them all. 
# (I'll admit, at first I unpacked them, looking for a flag file)
# But upon closer inspection, the files in the order they come in the zip file is in the order they are used in the PDF.
# It looked like this: https://imgur.com/a/KtBvaTW
# Reading the first letter of each font spells out: KNOWYOUR?ONT?
# I can guess where this is going...
# Using: https://www.extractpdf.com/ gives us 2 more, https://imgur.com/a/5zae2wV
# Deduction Puts thoose two in the holes we have, KNOWYOURFONTS
# 
# vsctf{knowyourfonts}
# Flag sent, and challenge blooded.
# #############

ps. Sorry for the long ass text for a simple chall, but wanted to make sure everyone could understand the process.
                                                     
