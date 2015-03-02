# As a dev, I want a web page that outputs a welcome message via HTML, so that I can learn how to test web pages

Use BDD to develop your own simple HTML page. You can create an html page with your text editor.

If you create a file called `index.html`, you can see it in your browser by putting the full file path in your browser's address bar. On a Mac, from the same directory as the file, you can type `open index.html`

Alternatively, get any directory's files online locally with a tiny ruby script:

```ruby
#!/usr/bin/env ruby

#
# example:
#  serve public 4001
#
# Spin up a quick web server for files in the specified directory (first arg)
# on the port number given (second arg).
#

require "webrick"

s = WEBrick::HTTPServer.new(
  :DocumentRoot => (ARGV[0] || Dir.pwd),
  :Port => (ARGV[1] || 4000)
  )

trap('INT') { s.shutdown }

s.start
```

Just save that to an executable file named `serve` in a bin directory that's in your path. Now when are in a directory with html files, you can run:`serve` to make those files accessible on port 4000.


**OR** you can create a serve function in your ~/.bashrc or ~/.bash_profile (in your home directory:

```bash
function serve {
            port="${1:-4000}"
            ruby -r webrick -e "s = WEBrick::HTTPServer.new(:Port => $port, :DocumentRoot => Dir.pwd); trap('INT') { s.shutdown }; s.start"
          }
  ```

  *important:* the commands inside the string (inside the double quotes) must all be on *one* line

How ever you decide to access the html file you made, you can then test that it's accessible by writing a spec, even before the HTML file exists.

The subsection has an example spec, but try writing your own first.

Once you have the spec coded up and running, get it to pass by making the appropriate HTML somewhere logical within your project.
