### 🛑 Microsoft SharePoint: CVE-2023-29357 🛑
**Microsoft SharePoint Server Elevation of Privilege Vulnerability**

### 📌 Summary:
This script exploits a vulnerability (CVE-2023-29357) in Microsoft SharePoint Server allowing remote attackers to escalate privileges on affected installations of Microsoft SharePoint Server. While this script focuses on elevation of privilege, attackers with malicious intent might chain this vulnerability with a Remote Code Execution (RCE) vulnerability ([CVE-2023–24955](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-24955)) to compromise the integrity, availability, and confidentiality of the target system.

### 📖 Description:
The exploit script facilitates the impersonation of authenticated users, allowing attackers to execute arbitrary code in the context of the SharePoint application pool and the SharePoint server farm account, potentially causing a denial of service (DoS). The script outputs details of admin users with elevated privileges and can operate in both single and mass exploit modes. However, to maintain an ethical stance, this script does not contain functionalities to perform RCE and is meant solely for educational purposes and lawful and authorized testing.

### 🚀 Usage:

#### Prerequisites:
- Python 3.8 or above
- Install the necessary Python packages:
  ```sh
  pip install -r requirements.txt
  ```

#### Script Execution:

1. **Single URL**
   ```sh
   python3.10 exploit.py -u <Target SharePoint URL> [-v]
   ```
   `-v` is an optional parameter to run the script in verbose mode.

2. **List of URLs**
   
   ```sh
   python3.10 exploit.py -l <file-containing-SharePoint-URLs> [-v]
   ```
   
   `-l` specifies a file containing a list of SharePoint URLs.

3. **Usage with [LeakIX](https://leakix.net)**

   To utilize this script with LeakIX, please note that this feature is only accessible to LeakIX Pro API key holders as it relies on the SharePointPlugin which is private. You can run the following command:

    ```sh
    python3.10 exploit.py --leakpy (--bulk | --pages=<number_of_pages>) [-v]
    ```
   
   - You can use either `--bulk` without a value or `--pages=<number_of_pages>`, but not both. 
   - Use `--pages` with a value, up to a maximum of `500`, to specify the number of pages. 
   - Add the `-v` flag for verbose output.
   
   **Note**: Using `--leakpy` triggers the mass exploit mode, fetching URLs from [LeakIX](https://leakix.net/). Keep in mind, using `--leakpy`, `--bulk`, and `--pages` are contingent upon possession of a Pro API key from LeakIX.

### 📎 Parameters:

- `-u, --url <URL>`: Specifies a single SharePoint URL.
- `-l, --list <file>`: Specifies a file containing a list of SharePoint URLs.
- `--leakpy`: Enables mass exploit mode, fetching URLs from LeakIX.
- `--bulk <bulk_size>`: Specifies the bulk size when using LeakIX.
- `--pages <number_of_pages>`: Specifies the number of pages to fetch from LeakIX.
- `-v, --verbose`: Enables verbose mode.
- `-o, --output <output_file>`: Specifies a file to output vulnerable URLs.

### 📄 Output:
The script will output the details of each admin user found with 'IsSiteAdmin' set to true, along with their `Title`, `Email`, `NameId`, and `NameIdIssuer`. If you are in mass exploit mode (`args.leakpy` or `args.list`), it will run through each URL without executing the spoofing function and output any vulnerable URLs to the specified output file.

### ⚠️ Disclaimer:
**IMPORTANT: This script is provided for educational, ethical testing, and lawful use ONLY. Do not use it on any system or network without explicit permission. Unauthorized access to computer systems and networks is illegal, and users caught performing unauthorized activities are subject to legal actions. The author is NOT responsible for any damage caused by the misuse of this script.**

