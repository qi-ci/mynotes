## get office file hash
```
$ python3 /usr/share/john/office2john.py text.xlsx > hash.txt
$ cat hash.txt
$office$*2013*100000*256*16*818483eeb775a9d991e9de78bd7c5ea6*16368da262bbf465213e035b78c83d6f*f8e084d431672fe59ecf4cca0d23ac6cae1cf55112e1a0df6266c259b31417c0
```
## hashcat crack
[hashcat install](https://hashcat.net/hashcat/)
```
$ hashcat -hh | grep Office
```
> 9400 | MS Office 2007                                             | Document
   9500 | MS Office 2010                                             | Document
   9600 | MS Office 2013                                             | Document
  25300 | MS Office 2016 - SheetProtection                           | Document
   9700 | MS Office <= 2003 $0/$1, MD5 + RC4                         | Document
   9710 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #1            | Document
   9720 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #2            | Document
   9810 | MS Office <= 2003 $3, SHA1 + RC4, collider #1              | Document
   9820 | MS Office <= 2003 $3, SHA1 + RC4, collider #2              | Document
   9800 | MS Office <= 2003 $3/$4, SHA1 + RC4                        | Document
```
$ hashcat -m 9600 hash.txt ../tools/rockyou.txt
```