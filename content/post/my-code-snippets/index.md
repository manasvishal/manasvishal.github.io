---
title: 💻 My most used code snippets
summary: Just some pieces of code
date: 2024-12-04
authors:
  - admin
tags:
  - Code
image:
  caption: ''
---

## List of Bash Commands

- This command will print out the top 10 folders that occupy the most space in Gigabytes

```SHELL
du -a --block-size=1G ~/ | sort -n -r | head -n 10
``` 

- This command redefines the conda cache directory

```SHELL
conda config --add envs_dirs <"target conda directory"/.conda/envs>
```

- This command requests power9 node from Unity
```
salloc --partition=power9 -t 4:00:00 --mem=60G -n 32
```

- This command runs a Perl script that changes the precision in HyperNTC Fortran Code

```
Perl -pi -e ’s/real\*8/real\*16/g’ *.f *.inc
```

## VScode tips and tricks

- On Windows one needs to specify the path properly as well as the MACs to do a proper connection with Unity
	- [ssh on windows - Corrupted MAC on input - Server Fault](https://serverfault.com/questions/994646/ssh-on-windows-corrupted-mac-on-input)

```

[](https://serverfault.com/posts/1002293/timeline)

Raoul's answer to his own question is correct. I ran into the same issue and adding the correct algorithm name after the `-m` option works (in my case the option was `-m hmac-sha2-512` to connect from PowerShell to a machine running Ubuntu 18.04).

I wasn't sure which algorithm to use, but you can list all the available ones by running:


ssh -Q mac


I selected one at random, tried it and the remote server returned saying that algorithm wasn't supported, but it handily told me which one's were so that I could amend my command. Using this command I could then ssh into the remote machine:

ssh -m hmac-sha2-512 <user_name>@<remote_address>



If you need to use `scp` too, the parameter is different:

scp -o MACs=hmac-sha2-512 <and the rest of your scp command>

You can add this to you ~/.ssh/config also:
Host name
    Hostname <fqdn>
    IdentityFile ~/.ssh/<key-file>
    User <username>
    MACs hmac-sha2-512
```


## Did you find this page helpful? Consider sharing it 🙌
