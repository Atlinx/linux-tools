# Linux Tools 🐧

Collection of various tools for working in a linux environment

## Filepaths

Files and directories are accessed by file paths

```
./path/to/file
```

- A file path relative to your terminal's current directory

```
/path/to/file
```

- A file path relative to the root of your filesystem

## Navigation

```
cd {directory}
```

- Changes directory of the terminal to `directory`
- Use `..` to navigate to a parent directory

```
mkdir {directory_path}
rmdir {directory_path}
```

- Makes/removes a directory

```
cat {file_path}
```

- Inspects the contents of a `file`

```
rm {path}
```

- Removes a file or directory at path
- use `-rf` flags to recursive delete a directory that has contents 


## Installing packages

```
sudo apt-get update
```

- Updates the package registry so `apt-get` can install the latest packages 

```
sudo apt-get install {package}
```

- Installs a `package` onto your machine

## Locating files

```
whereis {application}
```

- Shows all locations relevant to an `application`

```
updatedb --prunepaths="/mnt/c"
```

- Updates the databased used for the `locate` command. Should be run before the `locate` command
- `--prunepaths` argument can hide paths, such as the Windows filesystem mnt in WSL 

```
locate {filename}
```

- Searches the filesystem database made by `updatedb` for a `filename`

## Links

Links are pointers to files

```
ln {file_path} {link_path}
ln -s {file_path} {link_path}
```

- Creates a hard link
    - Hard links point directly to the file contents
    - If you removing the original file after making a hard link, you can still access the file through the hard link
- Creates a soft link
    - Soft links point to the file path, which then points to file contents 
    - Acts like a shortcut
    - If the original file is destoryed then the soft link is invalid and must be deleted 

## Services

Services are processes that run in the background of Linux. They can be configured with a `.service` file, which should be placed inside of `/etc/systemd/system/`. 

> **NOTE:**
>
> You can also just create a symbolic link to the `.service` file 
> and move the link inside of `/etc/systemd/system`

```bash
sudo systemctl status {service}
```

- Returns status of service

```bash
sudo systemctl stop {service}
sudo systemctl start {service}
```

- Stops/starts a service

```bash
sudo systemctl enable {service}
sudo systemctl disable {service}
```

- Enables/disables a service inside of `/etc/systemd/system/`

## Postgresql

```
sudo apt-get install postgresql
sudo systemctl start postgresql
```

Postgresql has it's own cli called `psql`. To use it run

```
sudo -U postgres psql
```

- Connects to your local database with root user privledges

### PSQL

You can execute Postgres SQL statements directly within PSQL cli. 
- [Postgres Cheatsheet](https://postgrescheatsheet.com/#/tables)

```
\q
```

- Exists the CLI

```
\conninfo
```

- Information about your connection to the database.
- Useful for finding the port it's hosted at.