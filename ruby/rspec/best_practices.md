When testing methods that relay on IO,
the best approach seems to be dependency injection,
in such a way in test condition `$stdin` or `$stout`
can by easily replaced by other object
[link to gist](https://gist.github.com/myronmarston/d9a699c1c0c74b992ceb1bbe6b4b2c6c)

If you wont to use upper scope `let` definition use `super()` exp.:
`let(:params) { super().merge(second_params: :smg) }`

When using stubs and checking if method have been called with different set of
arguments one can use multiple with's
```ruby
  expect(object)
    .to have_received(call)
    .ordered # if order of call got metter
    .with(some_args)
    .wtih(some_other_args)
    .with() # etc as long as you need
```
