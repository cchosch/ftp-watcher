# ftp-watcher
This simple python script watches files for changes and then uploads them to an SFTP or FTP server.

## Setup
Obviously, install the dependencies
```
pip3 install -r requirements.txt
```
Then setup your `<watched_project_directory>/.vscode/sftp.json`. 
Although this project was setup to be used in conjunction with
[this SFTP extension](https://marketplace.visualstudio.com/items?itemName=Natizyskunk.sftp),
it's not a requirement. If you are using it, just append 
`transferFiles` to the existing fields. If not just create the
`.vscode/sftp.json` file and add the fields as specified below.


#### `<watched_project>/.vscode/sftp.json` Schema
|   Field Name    | Required |     Type      |
|-----------------|----------|---------------|
|          `host` |       ✅ |      `string` |
|      `username` |       ✅ |      `string` |
|      `password` |       ✅ |      `string` |
|    `remotePath` |       ✅ |      `string` |
| `transferFiles` |       ✅ |    `string[]` |
|          `port` |       ❌ |      `number` |
|      `protocol` |       ❌ | `ftp \| sftp` |
_____________

<br>

<small>**Note: file paths listed under `transferFiles` are globs**</small>

```json
{
    // optional
    "port": 22,
    "protocol": "ftp",

    // required
    "host": "my_ftpserver.com",
    "username": "john",
    "password": "pa$$word",
    "remotePath": "/path/to/folder/on/server",
    "transferFiles": [
        "style.css",
        "style.css.map",
        "assets/index-*.js",
    ]
}
```

## Usage
Then the usage of this script is as follows:

```python
python3 main.py <project_directory>
```

For example:

```python
python3 main.py ~/workspace/project_with_transfer_files
```

