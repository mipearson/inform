# Inform

**Inform** prints colourised, interactive logging output to the console.
It includes support for timings and thread-local prefixes.

For example:

``` ruby
# Controllable log level filtering
Inform.level = :info

# Accept a block, print timing information once completed if > 0.1s
frozbot = Inform.info("Initializing the frozbot") do
  Frozbot.new
  sleep 1
end

# Other log levels than info
Inform.level = :debug
Inform.debug("Madness")
Inform.warning("and")
Inform.error("Nonsense")

# Thread-local log prefixing
Thread.current[:inform] = '1'
Inform.info("Frozbot is %{name}", :name => frozbot.name)
```

Will print:

```
>>> Initializing the frozbot : Done (1.00s)
    Madness
WARNING: and
ERROR: Nonsense
1 *** Frozbot is myfrozbot
```

### TODO

 * Make debug, warning, error accept blocks
 * Refactor tests
 * Colourisation isn't tested at all - should it be?
 * RDoc

## License

(The MIT License)

Copyright (c) 2011 PlayUp, 2012-13 Michael Pearson

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
