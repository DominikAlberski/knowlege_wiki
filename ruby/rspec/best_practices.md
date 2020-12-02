When testing methods that relay on IO,
the best approach seems to be dependency injection,
in such a way in test condition `$stdin` or `$stout`
can by easily replaced by other object
[link to gist](https://gist.github.com/myronmarston/d9a699c1c0c74b992ceb1bbe6b4b2c6c)
