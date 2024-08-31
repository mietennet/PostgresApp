---
layout: documentation
title: Using PL/Python with Postgres.app
---

## PL/Python

PL/Python allows you to create stored procedures and functions in Python.

PL/Python is an *untrusted* language.
This means that only a superuser can create procedures with it, but other users can use them.
The default user created by Postgres.app is a superuser, so this shouldn't be an issue in most cases.

To use PL/Python with Postgres.app, you first need to install Python using the [installers from python.org](https://www.python.org/downloads/macos/).

Unfortunately, PostgreSQL can only link with a specific version of Python.
Please install the correct version of Python, depending on the PostgreSQL version you are using:

<style>
  .documentation table {
    border-collapse: collapse;
    border: 1px solid #999;
    margin: 2em 0;
  }
  .documentation table td, .documentation table th {
    border: 1px solid #999;
    padding: 0.5em 1em;
  }
</style>

| PostgreSQL Version | Python Version                                                           |
| ------------------ | ------------------------------------------------------------------------ |
| PostgreSQL 17      | Python 3.13.x from [python.org](https://www.python.org/downloads/macos/) |
| PostgreSQL 16      | Python 3.12.x from [python.org](https://www.python.org/downloads/macos/) |
| PostgreSQL 15      | Python 3.11.x from [python.org](https://www.python.org/downloads/macos/) |
| PostgreSQL 14      | Python 3.9.x from [python.org](https://www.python.org/downloads/macos/)  |
| PostgreSQL 13      | Python 3.8.x from [python.org](https://www.python.org/downloads/macos/)  |
| PostgreSQL 12 and earlier | Python 2.7 (included with macOS)                                  |

Make sure to install the correct version of Python, then use the SQL command `CREATE EXTENSION plpython3u;` to enable the extension.

### Use a Homebrew installation of Python

You can also install Python via Homebrew and then have to link Homebrews Python.framework-folder to /Library/Frameworks.

Just make sure the correct Python version mention in the table above is installed like:

```
brew install python@3.12
```

Now you can do:

```
sudo ln -s /usr/local/Frameworks/Python.framework /Library/Frameworks/.
```

Any additional Python version you install later is then automatically available for the specific PostgreSQL version.
