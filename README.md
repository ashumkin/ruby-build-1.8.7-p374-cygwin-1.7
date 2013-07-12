# ruby-build definition for 1.8.7-p374 to compile under Cygwin v1.7

This build definition allows for easily compiling ruby 1.8.7 on Cygwin v1.7.

Usually, ruby-build is run via rbenv, so the instructions below use `rbenv` for the installation.

```shell
git clone git://github.com/ashumkin/ruby-build-1.8.7-p374-cygwin-1.7.git
cd ruby-build-1.8.7-p374-cygwin-1.7
rbenv install ./1.8.7-p374-cygwin-1.7
```

## Why

This build definition patches `eval.c` and `gc.c` with the patch https://gist.github.com/kou1okada/3956838 (found here http://wiki.livedoor.jp/kou1okada/d/Cygwin%20-%20ruby-1.8.7-p371)

The symptom of needing the patch it output from `rbenv install 1.8.7-p374` that looks like:

```
/usr/bin/gcc -g -O2     -DRUBY_EXPORT  -I. -I. -I'/home/<user>/.rbenv/versions/1.8.7-p374/include'    -c eval.c
eval.c:221:16: error: conflicting types for '_longjmp'
In file included from /usr/include/setjmp.h:10:0,
                 from node.h:382,
                 from eval.c:16:
/usr/include/machine/setjmp.h:397:13: note: previous declaration of '_longjmp' was here
eval.c: In function 'rb_eval_string_wrap':
``
