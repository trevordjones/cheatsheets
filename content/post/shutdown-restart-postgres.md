+++
date = "2016-08-21T19:24:20-04:00"
draft = false
title = "Shutdown Restart Postgres"

+++

You've probably all gotten the error from Postgres
```bash
could not connect to server: No such file or directory
Is the server running locally and accepting
connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
```

This happens when you do not shut down your running Postgres properly. This can happen when you shut down your computer or when you just close the terminal. You can prevent this by first shutting down Postgres before shutting down your computer:
```bash
$ brew services stop postgres
```

Then the next time you open your terminal, you can run:
```bash
$ brew services start postgres
```

If you shut down before you had a chance to close Postgres, you'll need to remove the `postmaster.pid` file.

```bash
$ cd /usr/local/var/postgres
$ rm -rf postmaster.pid
# Now you can start Postgres again
$ brew services start postgres
```
