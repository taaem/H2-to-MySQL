# H2-to-MySQL

This script does exactly that: **automatically** reads all the information in a H2 database and exports it into a MySQL database. If you're as lucky as me this is the best you'll find.

To run, look at `__main__` and change the global variables that set paths and server configurations.

It was tested in one DB with `Python3` and works flawlessly. It's not very sophisticated but if it saves you a few hours than it is good enough for me.

### Some details

The script reads H2 using [`JayDeBeApi`](https://pypi.python.org/pypi/JayDeBeApi/) with the H2 driver (the `h2-1.4.196.jar` included here) and writes to MySQL with [`PyMySQL`](https://github.com/PyMySQL/PyMySQL). These are the only two dependencies.

The only thing you *might* need to edit is the function `convert_types`, which converts H2 types into MySQL types. I did not implement this function exhaustively, only the types I needed, but it is fairly straightforward. Currently, it converts:

* `VARCHAR(*)` -> `TEXT`
* `BOOLEAN` -> `Boolean`
* `DOUBLE(N)` -> `FLOAT(N,N)`
* `REAL` -> `FLOAT(10,10)`

If you have any problems, please submit an issue. If you update it, please consider submitting a pull request.

Happy coding!
