Project file take from the [Effective Minidumps](https://web.archive.org/web/20060715203155/http://www.debuginfo.com/articles/effminidumps.html) article.

To compile and run the project issue the following commands:

```
$ cmake -S . -B build -DCMAKE_BUILD_TYPE=RelWithDebInfo -GNinja
$ cmake --build build --target run
```

Then load the `build/MaxiDump.dmp` mini dump file into `WinDbg` via `Ctrl + D`. Then issue the `.excr` command.

With Visual C++ 2019 it should look like this:

![windbg-minidump](https://github.com/cristianadam/MaxiDump/blob/master/windbg-minidump.png)
