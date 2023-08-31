---
title: "PicoCTF 2023 writeup"
excerpt: "" 
categories:
  - ctf-archive
---

# General

## Permission

### Description

Can you read files in the root file? Additional details will be available after launching your challenge instance. **(100 points)**

### Solution

Description shows the flag at root file, so just use a command to find specific location of flag:

```sh
    grep -r "picoCTF" /
```

The flag is `picoCTF{uS1ng_v1m_3dit0r_xxxxxxxx}` in file **metadata.json**.  

## Chrono

### Description

How to automate tasks to run at intervals on linux servers? Additional details will be available after launching your challenge instance. **(100 points)**

### Solution

As the question of the description, the answer is [crontab](https://en.wikipedia.org/wiki/Cron) and configuration will use files ***.json**. Use this command to view:

```sh
    grep --include \*.json -r "picoCTF" /
```

The flag is `picoCTF{Sch3DUL7NG_T45K3_L1NUX_xxxxxxxx}` in in file **metadata.json**.

## Money wave

### Description

- Flag format: picoCTF{Malwarename} The first letter of the malware name should be capitalized and the rest lowercase. Your friend just got hacked and has been asked to pay **some bitcoins** to 1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX. He doesn’t seem to understand what is going on and asks you for advice. Can you identify **what malware** he’s being a victim of? **(100 points)**

#### Bonus hint

- Some crypto-currencies abuse databases exist; check them out!
- Maybe Google might help.

### Solution

The description shows this is crypto-malware. Using google look up the Bitcoin address `1Mz7153HMuxXTuR2R1t78mGSdzaAtNbBWX` with keyword `malware name`. The result is `Petya ransomware`.

The flag is `picoCTF{Petya}`.

## Repetitions

### Descripition

`Can you make sense of this file?` with attached file.

### Solution

The content of downloaded file (enc_flag) shows base64 text. Using any tools to decode. The flag is `picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_xxxxxxxx}`.

## Special

### Description

Don't power users get tired of making spelling mistakes in the shell? Not anymore! **Enter Special, the Spell Checked Interface for Affecting Linux**. Now, **every word is properly spelled and capitalized**... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM) Start your instance to see connection details. **(300 points)**

## Solution

In this challenge, the *Bash shell* is replaced by `Special shell` that make every normal systaxs like `cd` are converted into `Ad`. After few times trial, there are 2 methods to bypass including brackets with semicolon and double quotations.

The sample command to get flag:

```sh
  "grep" -"r" "picoCTF" "."
```

The flag is `picoCTF{5p311ch3ck_15_7h3_w0r57_xxxxxxxx}`.

## Useless

### Description

There's an **interesting script** in the **user's home directory**
The work computer is running SSH. We've been given a script which **performs some basic calculations**, explore the script and find a flag. **(100 points)**

### Solution

Using `cat useless` in user's home directory to view content inside. However, after many times trial, it seems not work and this script returns error `read the manual`. Using the command `man useless` to solve this challenge.

The flag is `picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_xxxx}`.
