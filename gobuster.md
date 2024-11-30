# Gobuster

#### **1. Attempted to Run Gobuster**

You tried to run Gobuster to perform directory enumeration on the target `10.129.238.211` using a wordlist:

```bash
sudo gobuster dir -w /usr/share/wordlists/common.txt -u 10.129.238.211
```

#### **2. Encountered an Error**

*   The command failed with the error:

    ```
    wordlist file "/usr/share/wordlists/common.txt" does not exist
    ```
* This occurred because the specified wordlist file (`/usr/share/wordlists/common.txt`) does not exist on your system.

***

#### **Key Takeaways**

1. **Missing Wordlist**:
   * The wordlist path was incorrect or the file was missing.
2. **Potential Solutions You Could Apply**:
   *   Install the default wordlists on Kali:

       ```bash
       sudo apt install wordlists
       ```
   *   Use an alternative wordlist, such as:

       ```bash
       /usr/share/wordlists/dirb/common.txt
       ```
   *   Download a specific wordlist like `common.txt` from SecLists:

       ```bash
       wget -O /usr/share/wordlists/common.txt https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/common.txt
       ```

***

#### **Revised Command Example**

Once the wordlist is available, you can run:

```bash
sudo gobuster dir -u http://10.129.238.211 -w /usr/share/wordlists/dirb/common.txt
```

***

```bash
gobuster dir --url http://10.129.62.143/ --wordlist /usr/share/wordlists/dirb/small.txt
```

#### **Summary**

* You used Gobuster for directory brute-forcing but encountered a missing wordlist error.
* Solution steps involved installing or downloading the appropriate wordlist.
* After resolving this, the Gobuster command can effectively enumerate directories.

Let me know if you'd like further clarification! 🚀
