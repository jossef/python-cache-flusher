# python-cache-flusher
This utility removes all python *.pyc files (that has a matching *.py file) to force usage of new code

### Background

I had an issue with a custom python package (packed as a debian) that got updated.
After i did an update (replaced old `.py` files with new `.py` files) 

Iv'e noticed that when importing the package,
**old compiled code** (stored as `*.pyc` files) **got referenced** instead of the newer code (lying in the `.py` files).

i asked [this question](http://stackoverflow.com/q/38057302/3191896) and learned from it's comments that it's safe removing all of `pyc` files (that has a matching *.py file) so they will get lazy initialized on first use.


### The cause

a `pyc` **should be re-generated** when it's matching `py` file is newer.
the reason that it took the pyc file is because i'm using a custom debian package and the modification date of these files was newer (since i did a re-build of an old version and re-packed, then updated to a newer version that was packed before.)

### License

MIT
