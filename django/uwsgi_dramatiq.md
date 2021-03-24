## Dramatiq with uwsgi

When running Django with Dramatiq using uwsgi, remember to set:
```
lazy-apps = true
```
in `project.ini` file.

lazy-apps setting in the uwsgi configuration should be set to True, not to copy the same communication file;
otherwise with multiprocessing project may write to dramatiq twice at the same time,
causing Exception Type: FileNotFoundError at /user/register/