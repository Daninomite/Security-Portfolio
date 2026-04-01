notepad \~/Security-Portfolio/cheatsheets/linux-argument-order-cheatsheet.md

```



Select \*\*all the text\*\* with \*\*Ctrl + A\*\*, delete it, then paste this properly formatted version:

```

\# Linux Command Argument Order Cheat Sheet



\## Command Reference



| Command | Syntax | Example |

|---|---|---|

| `chown` | `chown USER FILE` | `chown researcher9 project\_r.txt` |

| `chmod` | `chmod PERMISSIONS FILE` | `chmod g-x drafts` |

| `mv` | `mv SOURCE DESTINATION` | `mv file.txt reports/` |

| `cp` | `cp SOURCE DESTINATION` | `cp file.txt backup/` |

| `rm` | `rm FILE` | `rm tempnotes.txt` |

| `mkdir` | `mkdir DIRNAME` | `mkdir tryhackme` |

| `cd` | `cd DIRNAME` | `cd Security-Portfolio` |

| `grep` | `grep PATTERN FILE` | `grep "error" logs.txt` |

| `cat` | `cat FILE` | `cat notes.txt` |

| `touch` | `touch FILE` | `touch notes.md` |

| `useradd` | `useradd USER` | `useradd researcher9` |

| `usermod -g` | `usermod -g GROUP USER` | `usermod -g research\_team researcher9` |

| `usermod -a -G` | `usermod -a -G GROUP USER` | `usermod -a -G sales\_team researcher9` |

| `groupdel` | `groupdel GROUP` | `groupdel researcher9` |

| `git add` | `git add FILE` | `git add .` |

| `git commit` | `git commit -m "MESSAGE"` | `git commit -m "Add file"` |

| `git push` | `git push REMOTE BRANCH` | `git push origin main` |

| `git clone` | `git clone URL` | `git clone https://github.com/...` |



\## The Patterns to Remember



\*\*USER comes last:\*\*

\- `usermod` always — `usermod -g GROUP USER`



\*\*SOURCE before DESTINATION:\*\*

\- `mv`, `cp` always — think "from to"



\*\*PERMISSIONS before FILE:\*\*

\- `chmod` always — `chmod g-x FILE`



\*\*USER before FILE:\*\*

\- `chown` always — `chown USER FILE`

